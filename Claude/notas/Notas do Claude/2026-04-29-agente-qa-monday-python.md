---
titulo: Agente Python de QA para implantações Monday
data: 2026-04-29
tipo: agente
projeto: interno
tags: [monday, qa, python, gemini]
status: superseded
relacionados:
  - "[[2026-07-02-mcp-validator-fase1]]"
  - "[[INDEX]]"
---

# Agente QA Monday (Python, abril 2026)

## O que era
MCP server em Python (`src/server.py` + `advanced-validator.py`) para QA de implantações Monday.com. Ferramentas: registrar conta (token), validar board (score 0-100, errors/warnings/info), histórico de reports, feedback. Acesso via MCP no Claude, CLI (`cli.py`) e web dashboard (FastAPI). Projeto em `C:\Users\lmeninelli\Documents\Claude\monday-validator-final`.

## Correções
- [CRÍTICO] server reescrito no padrão MCP SDK: `Server` + funções `async` + `stdio_server()`; removido `print()` que corrompia stdout.
- 10→11 regras de validação implementadas com score dinâmico; campo `rule_id` consistente nos issues.
- Integração real GraphQL Monday: com token + board ID valida nome, colunas, grupos etc. (antes só regra de prefixo `[DEPT]`, resto era `info`).
- Persistência de estado em JSON; feedback com aprendizado EMA.
- Fixes de ambiente: `.env` (chave errada em `.env.txt`), YAML de regras com lista malformada, pastas duplicadas aninhadas.
- Teste real: board "Backlog Banzai" (390 items) — score 75/100, 1 warning (falta prefixo `[DEPT]`).

## Regras e Gemini
- `rules.yaml`: 11 regras de best practices editáveis (parâmetros, templates de remediação, exemplos) — customização sem tocar no Python.
- `gemini_planner.py`: gera plano de ação com timeline via Gemini 2.0 Flash, fallback 1.5 Pro; chave em `GOOGLE_API_KEY`/.env. Funcionou até estourar quota free tier.
- Governance: board `[GOVERNANCE] Best Practices` criado no Monday (coaktion, depois movido para Workise) com 5 items + docs; módulo `governance_integration.py` sincroniza regras do board e mapeia issues → documentação (2 tools MCP novas). CLI melhorado: validar → ENTER encadeia governance linked + sync; feedback com link para doc/board.

## Por que foi superado
Protótipo virou base do monday-validator (fases 1-3, julho 2026). Limitações: fluxo manual (CLI/zip), quota Gemini free, regras parcialmente dependentes de dados da API, muita sessão gasta em setup de ambiente Windows.
