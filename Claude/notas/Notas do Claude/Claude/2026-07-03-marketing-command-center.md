---
tema: Workise Marketing Command Center (novo produto)
data: 2026-07-03
status: board + dashboard + 2 automações criados; deck v2 pronto; 3 pendências manuais
tags: [marketing, workagency, produto, monday-com, dashboard, content-calendar]
---

# Workise Marketing Command Center — Novo Produto

## Contexto

Criação de novo produto Workise para marketing, com posicionamento dual: **agências (multi-cliente)** e **times in-house**. Base: workspace `Workagency - Template` (ID `1928618`), motor maduro de operação de agência (Requests → Productions → Campaign Hub). Gap identificado e preenchido: **planejamento editorial/conteúdo multi-canal**.

Vídeo de referência: "Processos de Marketing: Automatize sua operação com a monday.com" (monday Brasil).

## Posicionamento Dual

| Aspecto | Modo Agência | Modo In-house |
|---|---|---|
| Cliente-alvo | Agências, consultorias criativas | Times de marketing internos |
| Coluna Contexto | Agência (Cliente Externo) | Time Interno (In-house) |
| Relations ativas | Cliente + Produto Relacionado | Produto Relacionado |
| Intake | Formulário externo público | Formulário interno |
| Pitch | "Centralize a operação dos seus clientes num único hub" | "Elimine o gargalo de ferramentas fragmentadas" |

## 5 Pilares

1. **Planejamento Estratégico** — Content & Editorial Calendar (ideação → aprovação → agendamento)
2. **Execução Multi-canal** — Productions + Events linkados à campanha-mãe
3. **Governança e Aprovações** — Requests com formulários condicionais
4. **Visibilidade Centralizada** — Dashboard cross-board
5. **Automação** — Request aprovada → item criado no calendário

## O que foi construído

- **Board Content & Editorial Calendar** — ID `18420249298`, 16 colunas, 4 grupos por estágio, relations para General Campaign Board, Requests, Client List e Products Catalog. Coluna Contexto para modo dual. 7 itens demo populados
- **Dashboard Marketing Command Center - Visão Geral** agregando os 3 boards centrais
- **Automação ativa** (workflow `7920297632`) no Requests board: Request Status → Approved + Campaign = Yes → cria item no grupo "📋 Backlog de Ideias" do calendário editorial
- **Deck `Workagency-Command-Center-v2.pptx`** (9 slides) reconstruído no brandbook original (cream #FDF5D7, navy #0B2233, orange #ED7D31, Poppins). Métricas: 12 boards, 259 colunas, 93 automações, 11 dashboards. Pricing preservado: R$ 14.990 / R$ 18.100

## Colunas do Content & Editorial Calendar

Name, Editorial Status (Ideia → Em produção → Em revisão → Aprovado → Agendado → Publicado), Canal, Data de Publicação, Responsável, Tipo de Conteúdo, Briefing/Copy, Campanha Vinculada → General Campaign Board, Request de Origem → Requests, Link do Asset Final, Linha de Produto/Serviço → Products Catalog, Origem (mirror), Contexto (Agência/In-house), Produto Relacionado, Cliente → Client List, Assets/Anexos

## IDs do workspace (para não perder)

- Workspace `1928618` (Workagency - Template)
- General Campaign Board `4711376846`
- Requests board `4711376686`
- Content & Editorial Calendar `18420249298`
- Campaign Management folder `11994728`
- Info folder `12073831`

## Pendências manuais (não passaram no MCP)

1. **Excluir automação redundante** (workflow `7920295990`) no Requests board — direção invertida, risco de duplicar itens
2. **Criar 4 views** no Content & Editorial Calendar: Kanban Editorial (por Editorial Status), 📊 Por Canal (table agrupada), 📅 Calendário (por Data), 🏢 Agência vs In-house (por Contexto)
3. **Revisar pricing** R$ 14.990 / R$ 18.100 antes de vender

## Tool knowledge útil

- MCP monday.com: `create_automation`, `create_view`, `create_view_table`, `create_doc`, `manage_automations` retornam "No approval received" (permission boundary do connector). `create_board`, `create_column`, `create_item`, `move_object`, `create_dashboard` funcionam
- Automations que passaram: trigger e condição precisam de status columns **separadas por column ID** — "Request Status" (`estado7`) trigger + "Campaign" (`status_1`) condition, NÃO combinar numa cláusula
- Google Drive MCP: `read_file_content` e `get_file_metadata` retornaram "No approval received" para `.pptx` nativo (não Google Slides). Search por `name contains 'X'` com paginação funciona; fullText e mimeType filters inconsistentes

## Fontes

- https://claude.ai/chat/a6e5a611-4f49-45b0-9631-bc149c0efe42 (03/07 — construção completa)
