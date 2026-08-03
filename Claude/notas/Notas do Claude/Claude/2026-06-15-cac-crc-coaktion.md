---
titulo: CAC/CRC — Processo Centralizado Coaktion
data: 2026-06-15
tipo: automacao
projeto: workise
tags: #cac #crc #coaktion #monday #hubspot #make #kpi
status: ativo
relacionados: [[Brain-Memories]] [[2026-06-22-estrategia-dual-motor-smb]]
---

# CAC/CRC — Processo Centralizado Coaktion

## Contexto
Automação de input mensal de CAC e CRC para todas as empresas do ecossistema Coaktion.

## Fluxo
HubSpot → Make → Board monday.com Coaktion → Dashboard executivo

## Empresas do ecossistema
Workise, Aktie Now, Droz, Callwe, Syntrika

## KPIs monitorados
| Métrica | Fórmula |
|---|---|
| CAC | Investimento Marketing + Vendas / Novos clientes |
| CRC | Investimento CS + Suporte / Clientes retidos |
| LTV | Ticket médio × tempo médio de contrato |
| LTV/CAC | Meta: ≥3x |

## Automação Make
- Trigger: 1º dia útil do mês
- Busca dados do mês anterior no HubSpot
- Calcula CAC e CRC por empresa
- Atualiza board Coaktion
- Envia resumo no Slack #coaktion-metricas

---
*Importado do histórico em 2026-06-25.*
