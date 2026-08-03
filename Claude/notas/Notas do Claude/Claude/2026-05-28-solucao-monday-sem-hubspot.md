---
titulo: Solução de gravações no Monday sem HubSpot
data: 2026-05-28
tipo: entrega
projeto: workise
tags: [monday, hubspot, integracao]
status: em-implantacao
relacionados:
  - "[[2026-06-15-cac-crc-coaktion]]"
  - "[[INDEX]]"
---

# Solução de gravações no Monday sem HubSpot

## Problema
Capturar e processar todas as agendas gravadas do time (22 pessoas, ~150 agendas/semana) com zero esforço do time e custo mínimo. Versão anterior enviava notas para HubSpot (Companies/Deals) — HubSpot saiu completamente; tudo dentro do Monday.

## Arquitetura final (após iterações)
```
Evento criado no Calendar → integração nativa Monday+Google Calendar cria item (título, início/fim, participantes internos/externos, entity_id)
→ reunião acontece; Gemini Workspace "Take notes for me" (PT-BR suportado) gera notas + link no evento
→ Make (watch Calendar) detecta gravação/notas → busca item pelo entity_id (coluna integration_mm3s97d6) → atualiza link gravação + transcrição + status "Novo"
→ Agentes AI nativos do Monday processam: tipo, sentimento, score, action items, alertas
→ Router distribui: Vendas/CS → board Contas; Projeto → board Projetos; Checkpoint/Interno → board Equipe; sentimento Negativo/Crítico → alerta Slack
```
Iterações descartadas: board "Hub" intermediário (removido — vai direto aos boards finais), Shared Drive central + Apps Script, forwarding de emails para ps@, watch de 22 pastas/caixas individuais.

## Board criado
**📹 Gravações — Workise** (ID `18413775650`, workspace Workise).
- 15 colunas: Data da Reunião, Responsável, Tipo de Reunião, Sentimento, Score Sentimento, Origem, Link Gravação, Transcrição, Participantes, Alertas, Action Items, NPS Inferido, Tom da Reunião, Tags, Status Processamento + Calendar Event ID.
- Integração Calendar criou automaticamente: Externos, Internos, Data (fim), Google Calendar event (entity_id).
- 6 grupos: 📥 Novos, ⚙️ Em Processamento, ✅ Processados, ⚠️ Sem Gravação (compliance), ❌ Erro, 📊 Relatórios.

## Automações e agentes
- 5 automações nativas: mover entre grupos por status; notificar sentimento Negativo/Crítico; mover item criado pela integração Calendar para "Novos". API não cria automações/agentes (exigem aprovação na UI) — guia interativo gerado com prompts prontos.
- 3 agentes AI Monday: Analisador de Gravações, Monitor Semanal, Digest Diário.
- Labels de status não alteráveis via GraphQL — ajuste manual na UI (Tipo: Vendas/CS/Projeto/Checkpoint/Parceiro/Interno; Sentimento: Positivo/Neutro/Negativo/Crítico; Status: Agendado/Novo/Em Processamento/Processado/Erro).

## Make
- 40K ops/mês disponíveis; consumo estimado ~17K. MCP do Make não tem `scenarios_create` — blueprints importados manualmente via UI.
- Blueprint final: Watch Calendar → detecta attachments (gravação .mp4 + notas Gemini .gdoc) → match por entity_id → atualiza item.
- Gemini API descartada por ora (usuário no free tier do AI Studio; Gemini Advanced ≠ API). Se precisar: Gemini 2.5 Flash-Lite + Batch ≈ $7/mês para 650 calls; free tier com `sequential: true` + Sleep 7s (~8 calls/min < 15 RPM).
- Custo adicional atual: $0 — notas/transcrição vêm do Gemini Workspace já pago.

## Pendências
Admin do Workspace ativar gravação automática do Meet + transcrição automática (Gemini settings). Ajustar labels na UI, criar agentes e automações, importar blueprints.

## Extra: skill criada
`recording-hub-builder` (.zip): SKILL.md + 3 refs (ingestion-patterns, ai-processing, cost-matrix), refatorada sem Hub/HubSpot.

## Contexto relacionado: report semanal HubSpot (2026-05-22)
Report interativo (artifact) para o time SMB (<500 funcionários) do Lucas — Jonas, Patricia, Karol Hirata, Karol Paiva.
- Estrutura: KPIs (deals fechados, pipeline, conversão, ciclo), deals por estágio, performance por pessoa, insights acionáveis (inativos, hot leads), metas vs realizado, forecast global.
- Filtros: owners reais (Jonas 86994764, Patricia 558207897, K. Hirata 1372086544, K. Paiva 1410595864); lifecycle "customer" + `numberofemployees` < 500 (grupo econômico também <500) → 251 contas; BDR via propriedade `sdr_bdr_envolvido`; forecast via categoria prevista (Won/Commit/Best Case).
- Metas cruzadas com board Monday 18399728622 (Metas 2026, Sales Corporate Q2); meta universal consolidada do Squad R$ 405K; Karol Hirata meta 35 opps como BDR (10 abertas via `sdr_bdr_envolvido`).
