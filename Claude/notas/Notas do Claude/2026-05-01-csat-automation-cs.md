---
titulo: CSAT Automation — CS Team
data: 2026-05-01
tipo: automacao
projeto: workise
tags: #csat #make #hubspot #gmail #automacao #cs
status: ativo
relacionados: [[Brain-Memories]] [[2026-06-15-cac-crc-coaktion]]
---

# CSAT Automation — Time de CS

## Contexto
Automação de CSAT para o time de CS da Workise sem usar HubSpot Service Hub (custo). Solução alternativa usando Make + HubSpot CRM + Gmail.

## Stack
- **Trigger:** Make (após fechamento de ticket/entrega)
- **Email:** Gmail (template personalizado)
- **Dados:** HubSpot custom properties (nota CSAT, comentário, data)
- **Relatório:** Dashboard monday.com com médias por CS

## Fluxo
1. CS marca entrega como "Concluída" no monday.com
2. Make detecta mudança de status
3. Envia email personalizado ao cliente via Gmail
4. Cliente responde (escala 1-5 + comentário aberto)
5. Make processa resposta e salva no HubSpot
6. Dashboard atualiza automaticamente

## Custom Properties HubSpot criadas
- `csat_score` (number)
- `csat_comment` (text)
- `csat_date` (date)
- `csat_delivery_id` (text)

## Métricas monitoradas
- CSAT médio por CS (Karol Paiva, Lucas Pia)
- CSAT por tipo de entrega
- Tendência mensal
- Respostas com score ≤3 (alerta automático no Slack)

## Resultado
Implementado sem custo adicional de Service Hub (~$50/mês economizados).

---
*Importado do histórico em 2026-06-25.*
