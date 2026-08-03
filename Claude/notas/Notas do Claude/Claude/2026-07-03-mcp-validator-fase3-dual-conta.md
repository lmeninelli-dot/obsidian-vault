---
titulo: MCP Monday Validator — FASE 3 Dual-Conta Operacional (20 ferramentas)
data: 2026-07-03
tipo: entrega
projeto: interno
tags: #mcp #validator #fase3 #monday #api #dual-conta
status: em-uso
relacionados: [[2026-07-02-mcp-validator-fase1]] [[2026-07-02-mcp-validator-fase2]] [[2026-07-02-mcp-validator-sintese]] [[2026-06-24-monday-referencia-2026]]
---

# ✅ FASE 3 — Dual-Conta Operacional + CRUD Completo

## 🎯 Objetivo alcançado

O objetivo original do projeto foi cumprido: **um MCP que opera nas duas contas Monday
(Workise e Coaktion) com escolha de conta por linguagem natural** — coisa que o conector
oficial da Monday não permite (fica preso a 1 conta).

Uso no chat: *"cria um item no board X da **coaktion**"* / *"lista os boards da **workise**"*.
Toda ferramenta recebe `account_name`.

## 🔑 Descoberta crítica: endpoint da API

**O bug que travou tudo por ~1h:** `src/config.py` usava `https://api.monday.com/graphql`,
que retorna **401 "You need to log in"** mesmo com token válido. O endpoint correto é:

```
https://api.monday.com/v2
```

Aprendizados associados:
- Tokens pessoais da Monday **são JWT** (`eyJ...`) — não existe formato `stoken_`
- Header: `Authorization: <token>` direto, sem "Bearer"
- Playground (developer.monday.com) foi o que provou que o token era válido → problema era o cliente
- Schema atual: `items_count` (não `item_count`), `owners` (não `owner`),
  `column_values.column.title` (não `column_values.title`), boards não expõem `items` direto (usar `items_page`)
- API pública v2 **não expõe automações** de board
- Labels de status respeitam o idioma da conta (ex: "Concluído", não "Done") — a API retorna os labels válidos no erro

## 🧰 As 20 ferramentas do MCP

**Contas:** register_account, list_accounts, delete_account
**Leitura:** list_boards, get_items (valores em texto), get_users, get_workspaces
**Validação (fase 2):** validate_board (5 regras MVP), get_report, list_history, record_feedback
**Escrita:** create_board, create_group, create_item, create_subitem, create_column, update_item, create_update (comentário), delete_item
**Coringa:** `monday_api_request` — GraphQL arbitrário na conta escolhida (cobre qualquer operação sem ferramenta dedicada, ex: delete_board)

## 🧪 Testes executados (tudo real, conta limpa depois)

- 11 testes unitários (validação de entrada/erros) — 100% PASS
- Smoke test das 2 contas: 100 boards cada, validação com score 80/100 nas duas
- Ciclo de escrita completo na Workise: board → grupo → coluna status → item →
  update status "Concluído" → subitem → comentário → leitura → deleção (item + board via api_request)
- Servidor MCP stdio testado: initialize, tools/list (20), tools/call

## 🏗️ Arquitetura final

```
monday-validator-final/
├── .mcp.json                    ← Claude Code carrega automaticamente
├── src/
│   ├── server.py                ← MCP stdio JSON-RPC, 20 ferramentas
│   ├── validator.py             ← multi-conta + validação + operações CRUD
│   ├── monday_api.py            ← cliente GraphQL v2 (last_error capturado)
│   ├── rules.py                 ← 5 regras MVP
│   └── config.py                ← endpoint /v2
├── data/accounts.json           ← tokens das 2 contas (gitignored)
├── test_mcp_implementations.py  ← unitários
├── test_contas_registradas.py   ← smoke sem tokens hardcoded
└── test_operacoes_escrita.py    ← ciclo CRUD completo
```

Melhoria importante: `MondayAPIClient.last_error` captura a mensagem de erro do GraphQL,
então falhas retornam o motivo exato (ex: lista de labels válidos de status).

## ⚠️ Pendências

- [ ] **Regenerar os 2 tokens** (Workise e Coaktion) — passaram pelo chat durante o debug → re-registrar via `monday_register_account`
- [ ] Criptografar tokens em `data/accounts.json` (hoje texto puro, local)
- [ ] Fase 4 (opcional): mais regras de validação, dashboard, Monday App oficial

## ➡️ Como usar

1. Abrir Claude Code na pasta `monday-validator-final` (o `.mcp.json` carrega o servidor)
2. Pedir em linguagem natural, sempre citando a conta: workise ou coaktion

---
*Fase 3 entregue em 2026-07-03 — MCP dual-conta 100% operacional, testado de ponta a ponta.*
