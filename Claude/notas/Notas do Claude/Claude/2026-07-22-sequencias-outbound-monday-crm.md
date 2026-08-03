---
tema: 23 sequências outbound no monday CRM (Mid-Market + Enterprise)
data: 2026-07-22
status: 2 sequências criadas via API, 21 restantes com script Python pronto
tags: [monday-crm, sequences, outbound, mcp, api, batch]
---

# Batch de 23 Sequências Outbound no monday CRM

## Contexto

Criação em massa de 23 sequências de e-mail outbound no monday CRM, distribuídas em 2 boards:
- **Mid-Market** — board `18422844559` — 12 sequências, 21 steps cada
- **Enterprise** — board `18422844841` — 11 sequências, 15 steps cada

Segmentação por vertical: agronegócio, alimentação, construção, financeiro, logística, manufatura, marketing, saúde, tecnologia, varejo, expansão, C-Level.

## O grande bloqueador que travou tudo

A ferramenta `get-connected-email-accounts` **referenciada pelo gate do create-sequence não existe no catálogo MCP**. Sem ela, não dá para resolver `sender.id` — e o tool proíbe fabricar o id.

**Resolução**: extração via JavaScript no React fiber state do seletor de remetente aberto na UI. Padrão que funcionou:

```javascript
Object.keys(el).find(k => k.startsWith('__reactFiber'))
```

Depois walk na fiber tree checando `memoizedProps` para `value.id`.

**Feedback registrado** no monday.com via `send_feedback` MCP: bug de `create-sequence` referenciar tool inexistente.

## IDs confirmados

- **Sender**: `{"email": "lmeninelli@workise.com.br", "id": 99807, "provider": "gmail"}` — `id` é do email account conectado, NÃO do usuário monday
- **emailColumnId**: `email_mm5eyr8e` (mesmo nos dois boards)
- **Placeholders reais do monday**: `{pulse.name}` (nome completo — não existe coluna "primeiro nome" separada nos boards) e `{pulse.text_mm5e82ws}` (empresa)
- **Conversão do arquivo original**: `{{contact.firstname}}` → `{pulse.name}` e `{{contact.company}}` → `{pulse.text_mm5e82ws}`
- Account slug `coaktion`, account ID `1632076`, workspace `9507973`, user ID `17823886`

## Sequências criadas (2 de 23)

- **BR | Alimentação Decisores** — `f66cc2be-c1a1-4230-b2be-35a9ac936b67` (Mid-Market)
- **BR | Construção Decisores** — `131af535-0d9a-4e1b-a442-f3cf0e93b319` (Mid-Market)

Ambas confirmadas via `create-sequence` MCP direto (não via UI insert), aceitando tokens plain-text nos strings `subject` e `body`.

## Deliverables

- `/home/claude/all_sequences.json` (122 KB) — todas 23 sequências parseadas com placeholders convertidos
- `/home/claude/remaining_sequences.json` — 21 pendentes de criação
- `/home/claude/batch_create_sequences.py` (149 KB) — script batch com todos os dados embedados
- Parcial de Agronegócio (3 dos 21 steps) via browser automation antes do API path ser confirmado

## Anti-padrão descoberto

`execute_code` do Claude retorna "No approval received" ao tentar HTTP para `mcp.monday.com/mcp`. Sandbox não permite HTTP arbitrário — batch não roda via Python script no sandbox, precisa ser via chamadas MCP diretas.

## Pendências

- Rodar as 21 sequências restantes (via chamadas MCP `create-sequence` diretas, uma por uma ou em lotes)
- Ativar todas via `activate-sequence` depois de criadas
- Documentar `id 99807` como "sender ID lmeninelli@workise.com.br monday CRM" para não perder de novo

## Fontes

- https://claude.ai/chat/1060e848-4a55-48c9-a648-15852f6c9b84 (22/07 — batch monday CRM)
