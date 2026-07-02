---
titulo: MCP Monday Validator — Captura
data: 2026-07-02
tipo: thinking
tags: #thinking #mcp #monday-validator #captura
status: ativo
relacionados: [[2026-06-24-monday-referencia-2026]] [[2026-06-24-github-caveman]]
---

# 📋 Captura — MCP Monday Validator

## ✅ Fatos confirmados

### Estado atual
- **Problema:** Servidor MCP Monday Validator mostra "Server disconnected" em Claude Code
- **Causa raiz (sessão anterior):** Logging contaminando stdout (usado para MCP protocol)
- **Fix aplicado:** Removeu StreamHandler em logging_config.py
- **Status:** Servidor ainda não testado após fix

### Referências funcionais disponíveis
1. **monday_mcp.py** (seu repositório)
   - Implementação Python que já funciona
   - Usa stdio (JSON-RPC 2.0) corretamente
   - Logging em stderr (não stdout) ✅
   - Estrutura simples e clara

2. **documentacao_mcp_monday.md** (seu repositório)
   - Config completa com MONDAY_API_TOKEN
   - 5 ferramentas: query_monday_api, list_boards, get_board_items, create_item, add_update
   - Setup em diferentes clientes MCP

3. **monday-validator-final/src/**
   - server.py (500 linhas, 7 ferramentas)
   - advanced-validator.py (600 linhas, extensões)
   - requirements.txt com mcp>=0.1.0, fastmcp>=0.1.0

### Stack existente (Workise)
- monday.com Platinum Advanced Delivery Partner
- Stack: monday.com, Make, Slack, HubSpot, Claude
- Repositórios: caveman (token compression), pnytail (?)
- Objetivo: validar boards contra best practices

---

## [suposição] Suposições

- [ ] pnytail contém padrões de integração Monday ou Make
- [ ] caveman pode ajudar na otimização de output/tokens do validator
- [ ] Melhor caminho: usar monday_mcp.py como base (pronto) vs reescrever monday-validator do zero
- [ ] monday-validator atual tem regras de validação que precisa preservar

---

## ❓ Perguntas em aberto

1. **Qual base arquitetural usar?**
   - Opção A: Usar monday_mcp.py como base (já funciona)
   - Opção B: Consertar monday-validator-final mantendo estrutura atual
   - Opção C: Hibridizar — padrão de monday_mcp.py + regras do validator

2. **Qual usar como ponto de partida?**
   - Parâmetro: tempo até funcionar (rápido vs resiliente)
   - Parâmetro: legibilidade/manutenção futura
   - Parâmetro: extensibilidade para novos validadores

3. **Integração com Make/automações?**
   - Precisa rodar como standalone MCP ou ser chamado de Make?
   - Como passará dados de volta para boards?

4. **Quais repositórios consultados?**
   - caveman: para otimização?
   - pnytail: para padrão de integração?

---

## 🔗 Contexto relacionado

- [[2026-06-24-monday-referencia-2026]] — Monday.com é agora AI Work Platform
- [[2026-06-24-github-caveman]] — caveman comprime output em ~65%
- [[2026-06-24-make-referencia-2026]] — Make integração com Monday

---

*Criado em 2026-07-02 para estruturar decisão de arquitetura do validator.*
