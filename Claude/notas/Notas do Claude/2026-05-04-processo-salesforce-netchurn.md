---
titulo: Processo mensal Salesforce → Netchurn (sem API)
data: 2026-05-04
tipo: automacao
projeto: workise
tags: [salesforce, netchurn, processo]
status: concluido
relacionados: ["[[INDEX]]"]
---

# Processo mensal Salesforce → Netchurn

## Contexto
- Sem acesso à API do SF; acesso só via interface (portal de parceiros monday.com).
- Report já salvo: **Base instalada - Workise - Netchurn** — `https://monday.my.site.com/partners/s/report/00Oav0000006721EAA/base-instalada-workise-netchurn`
- Objetos: Accounts + Oportunidades. Export via botão Export → xlsx. ~351 contas, 14 colunas, ~$5M ARR.
- Ideia inicial (Make + subscribe de report por e-mail) descartada — SF não envia CSV; escolhido **Cowork + Claude in Chrome**.

## Fluxo desenhado
1. **Extração** — Cowork via Claude in Chrome navega no SF (sessão já logada), abre o report, exporta xlsx, salva/renomeia em pasta local.
2. **Validação** — confere 14 colunas, ≥100 linhas, linha de Total; para e avisa se divergir. Nunca faz login, nunca clica em Edit.
3. **Atualização histórico** — importa Current ARR do mês na aba Histórico ARR (1 linha por conta, 1 coluna por mês; chave = BigBrain ID).
4. **De-Para mensal** — Δ ARR mês vs mês anterior; classifica Expansão / Estável / Contração / Churn / Novo; GDR por conta.
5. **Resumo GDR/NDR** — geral, por Plan Tier, por Partner CSM + relatório de execução com alertas.

## Ferramentas
- Salesforce (interface, portal parceiros)
- Cowork (Claude Desktop) + tarefa `/schedule` mensal (dia 5) — roda só com PC ligado e app aberto
- Claude in Chrome (navegação/export)
- Google Drive/Sheets (planilha destino)

## Entregáveis
- `Cowork_Prompt_NetChurn_Completo.md` — prompt das 5 etapas, colar no `/schedule`.
- `NetChurn_Tracking_Workise.xlsx` (salva no Google Drive) — 4 abas: Histórico ARR, De-Para Mensal, Resumo GDR, Instruções.
- Histórico migrado: 8 snapshots, 530 contas únicas (Q1–Q4 + Q1 2025 da planilha antiga trimestral).

## Passos mensais (dia 5)
1. Garantir sessão SF ativa no Chrome, PC ligado, Claude Desktop aberto.
2. Tarefa agendada roda as 5 etapas.
3. Revisar relatório de execução e alertas (contrações/churns).

## Mudanças vs planilha antiga
- Trimestral por pessoa → mensal por conta.
- BigBrain ID como chave (evita duplicata por rename).
- GDR separado de NDR; contas novas isoladas do cálculo de retenção.
