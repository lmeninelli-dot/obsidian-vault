---
titulo: Casos de uso e demos Monday — masterclass e workspace Demos
data: 2026-06-10
tipo: entrega
projeto: workise
tags:
  - monday
  - demos
  - casos-de-uso
  - masterclass
status: concluído
relacionados:
  - "[[2026-06-16-quadros-prompts-agentes]]"
  - "[[INDEX]]"
---

# Casos de uso e demos Monday — mai–jul/2026

Consolidação de 6 sessões (27/mai a 02/jul) de construção, validação e correção de casos de uso Monday para demos Workise.

## Caso Manufatura (27/mai — workspace Co.Aktion 2990431)
- Pasta Manufatura: 10 boards MFG 01–10 (P&D, PCP, Manutenção, Qualidade/ISO, Produtos, Gestão de Manutenção, Incidentes, Ativos, Fornecedores, Documentação Técnica). IDs 18411102240–18411102494.
- Dashboard Executivo Industrial (36912195) — 12 widgets (4 NUMBER, 3 BATTERY, 3 PIE, 2 BAR).
- 8 conexões board_relation entre boards. Playbook de Soluções em Monday Doc (18411472457).
- 10 automações documentadas para configurar manualmente (API não cria).
- Na mesma sessão: diagnóstico de mais 4 segmentos (Serviços Financeiros, Varejo, Saúde, Educação).

## Catálogo de 16 segmentos (workspace Demos - Criadas 15837325)
- 16 verticais: MAN, SFI, VAR, SCV, EDU, AUT, EOG, TUR, MID, TRL, CSB, TEC, JUR, COS (renomeado de CON), AGM, GAM — 114 boards.
- 9 pastas transversais T1–T9 (PMO, RHX, FIN, JCO, FAC, MKT, TIT, VEN, ATD) — 41 boards.
- 14–15 dashboards executivos por segmento (IDs 37612218–37612254).
- 4+ agentes Monday criados (Guardião de Prazos, Triagem, Resumo Semanal, Onboarding) — nascem INACTIVE; triggers/skills/knowledge exigem aprovação na UI.
- 8 forms de intake (Help Desk, Reembolsos, Atendimento, MKT, RH, etc.).
- 12 conexões cross-segmento (PMO↔verticais, Vendas↔Contratos, Compras↔Fornecedores...).

## Correções (09–10/jun)
- Workspace tinha ~230 boards; 85 duplicatas excluídas (CSI/COS×2, AGM×5 gerações, ADV, GAM, transversal incompleta série 18417027…).
- **Incidente:** excluir pasta-mãe "⚡ Soluções Transversais" causou cascata — 41 boards + subpastas T1–T9 para a lixeira. Restauração manual pela UI trouxe de volta também as 85 duplicatas → limpeza reexecutada. Estado final: 157 boards ativos, zero duplicatas, T1–T9 flat (sem pasta-mãe).
- Boards esqueléticos (4 colunas + grupo fantasma "Group Title"/"topics") corrigidos em lote: AGM 01–05, COS 01–08, GAM 03–07, transversais.

## Demo People Analytics Summit (workspace 14536640 — People Experience, jul)
- Auditoria criteriosa slide a slide: pasta People Analytics vazia (dashboard existia mas API não lê dashboards), zero automações, itens lixo "Item 1–5", grupos "Group Title", board PDI bloqueado (USER_UNAUTHORIZED).
- Reconstruído: Pipeline R&S (11 vagas reais), Onboarding (checklists e status coerentes), 5 boards de RH enriquecidos (Saúde/Segurança, Remuneração, Clima, Projetos, Compliance), Férias (16 itens limpos), Triagem (13 candidatos), Portal do Colaborador populado, board novo ⏱️ Registro de Ponto (14 colunas, 16 registros, CLT).
- Dashboard "People Analytics — Visão Executiva" (37895524) — ~28 widgets; dashboard demo compacto (38041598).
- 8 agentes IA ativos renomeados "Workise IA —" (Triagem, Onboarding, Digest, Compliance, Férias, Offboarding, Clima, Validador de Ponto). Agentes são `kind: PERSONAL` — não transferíveis; recriar com a conta do dono definitivo.
- Produto derivado: WorkPeople — 4 docs de venda (sales deck, PPTX 10 slides, proposta comercial, diferenciais vs Workday/Gupy/Totvs) + roteiro de demo de 15–20 min.

## Lições aprendidas
- API Monday não lê dashboards (queries retornam vazio) mas mutations `create/update/delete_dashboard` funcionam — usuário vira os "olhos" via UI.
- `workspace_info` tem cache defasado e lista pastas de forma plana (esconde aninhamento) → excluir pasta sem confirmar hierarquia causa cascata. Validar via GraphQL direto (fonte autoritativa).
- Restauração da lixeira é só via UI e em massa — traz de volta o que foi excluído de propósito.
- MCP degrada após ~30–40 tool calls pesadas (create_widget/automation/doc falham com "No approval received") → sessão nova.
- Widgets exigem schema `settings` específico (`all_widgets_schema`) e dashboard com board_ids vinculados na criação.
- Automações e fórmulas não são criáveis/configuráveis via API — documentar para setup manual.
- Agentes Monday: nomes/avatares vêm genéricos (Jean, Gregory...), renomear via update; testar disparo do trigger antes de demo ao vivo.
- Itens template sem dados não demonstram valor — popular colunas-chave com dados realistas; remover "Item 1–5" e grupos "Group Title".

## Estado final
- Workspace Demos (15837325): 157 boards (16 verticais + 9 transversais), dashboards por segmento, agentes e forms criados, limpo e validado via GraphQL.
- Workspace People Experience (14536640): demo pronta para o Summit; pendências manuais — fórmula de horas do Ponto, links board_relation do Ponto, campos do form de Férias, automação de Ponto, liberar acesso ao PDI (18402357804).
