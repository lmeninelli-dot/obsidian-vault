---
tema: Análise Inbound ARR Q2 + reconciliação Salesforce/GSheets/HubSpot
data: 2026-07-29
status: análise concluída, dados prontos para QBR
tags: [qbr, inbound, arr, salesforce, hubspot, karol, jonas, bcr, xdr]
---

# Inbound ARR Q2 — Breakdown e Reconciliação Cross-Source

## Contexto

Preparação de dados para o QBR Q2. Cruzamento de 4 fontes: Salesforce export (Excel), Google Sheets performance tracker, Google Sheets da Karol Hirata, HubSpot CRM.

## Números finais

- **Inbound ARR total**: $259.729 · 124 deals
- **Base**: $243.193 (93,6%)
- **New Business**: $16.536 (6,4%)
- **Q2 achievement**: 50% da meta, com Partner-sourced sendo o maior driver do gap (13% da meta, −78% vs Q1)

## Reconciliações resolvidas

**1. Discrepância $13.950 Salesforce vs GSheets**
- Classificação divergente de um deal Partner Outbound entre as fontes. Cross-referenciado e explicado.

**2. BCR / XDR classificação**
- Só existem 3 deals com essas tags em Q2:
  - 2 BCR (ambos Closed Lost)
  - 1 XDR (ainda em pipeline)
- Todos do Jonas
- **Zero Closed Won revenue do canal monday.com direct** em Q2

**3. Karol Hirata: 289 contatos no GSheets vs 682 no HubSpot**
- Explicado por bulk enterprise import de 19/05 distribuído em 4 owners: Karol, Andreia, Aline, Beatriz

## Owner IDs HubSpot confirmados

- Karolina Hirata (BDR) — `1372086544`
- Andréia Oliveira — `86264158`
- Aline Uliana Medeiros — `84025214`
- Beatriz Valverde — `87375522`
- Jonas Barboza (AE) — `86994764`
- Patrícia Cardoso (AM) — `558207897`
- Lucas Meninelli — `556276034`

## Tool knowledge útil

- Para HubSpot contact search com múltiplos owners, `IN` operator com múltiplos owner IDs funciona — mas quando **um owner tem volume desproporcional** (Karol 682 vs ~402 dos outros 3 combinados), rodar queries separadas evita bater o limite de 200 results e perder dados
- Classificação BCR/XDR na Workise vive **exclusivamente no `dealname`** com operator `CONTAINS_TOKEN`, NÃO em source properties estruturadas
- `hs_analytics_source` em contatos retorna `OFFLINE` para virtualmente todos — o que distingue é `hs_analytics_source_data_1`: `CRM_UI` (outbound prospecting manual) vs `IMPORT` (bulk lists BCR/monday enterprise)

## Pendências

- Reforçar disciplina de classificação: deals Partner precisam de source property estruturada, não só prefixo no dealname
- Investigar por que Partner-sourced caiu −78% vs Q1 (mudança de política monday, saída de Partner Manager, ambos?)

## Fontes

- https://claude.ai/chat/1338240e-ecf2-4408-81d9-dbaa207430f5 (29/07 — análise Inbound ARR)
