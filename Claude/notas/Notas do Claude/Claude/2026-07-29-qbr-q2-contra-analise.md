---
tema: QBR Q2 — Contra-Análise Workise (2 slides)
data: 2026-07-29
status: 2 slides PPTX entregues, prontos para inserir no deck do Marcelo
tags: [qbr, monday-com, marcelo-morais, executivos, ppt, contra-analise]
---

# QBR Q2 — Contra-Análise Workise em 2 Slides

## Contexto

O QBR de Q2 2026 foi montado pelo Marcelo Morais (CPM monday.com) com framing que Workise considerou excessivamente prejudicial. Objetivo do trabalho: 2 slides complementares ao deck original, com **leitura Workise honesta — nomear os fatores estruturais reais, não esconder problemas, mas contextualizar e mostrar que H2 já está em execução com evidências, não promessas**.

Decisão de estilo: **dark theme espelhando o deck monday.com** (não identidade Workise) — 2 slides densos, ângulo balanceado (contexto + forças + plano).

## Números-chave (H1)

- Enterprise 500+ **+57,7% YoY**
- Win Rate **82%** em 340 deals fechados
- SMB/Outbound NB **−61%**
- PME **−42%**
- Q2 total achievement: **50% da meta**, Partner-sourced principal gap (13% da meta, −78% vs Q1)

## Descoberta puxada do HubSpot (dado que faltava no deck do Marcelo)

**Ajinomoto — 2 deals RFP totalizando R$ 1,43M em "Decision Maker Bought In"** (60% probabilidade, close setembro). Não estava mencionado no QBR original.

## Estrutura dos 2 slides

**Slide 1 — "H1 pela ótica Workise"**
- Esquerda (3 fatores de contexto Q2):
  1. Enterprise RFPs absorvendo bandwidth
  2. Exaustão da cadência SMB legacy
  3. Investimentos estruturais em ops em andamento
- Direita (3 forças de execução):
  1. Crescimento Enterprise 500+
  2. Qualidade de WR (gap é volume, não conversão)
  3. Volume de pipeline

**Slide 2 — "H2 já está rodando — evidências, não promessas"**
- 3 pilares operacionais:
  1. Dual-Motor comercial (NB coverage 1.16x, Base 0.43x)
  2. Expansion Wave com 30 accounts mapeados
  3. Ops & IA checklist
- Tabela com top 6 deals abertos HubSpot: R$ 2,50M total (ponderado ~R$ 1,14M)
- Fechamento: statement formal amarrando H2 target ao pipeline real, não à meta original

## Paleta usada (espelha deck monday.com)

```
bg=#000000, card=#141414, cardHi=#1C1C1C, border=#2D2D2D,
purple=#6B5FE8, green=#22C55E, yellow=#FCD34D, red=#EF4444,
workise=#EE3048 (acento sutil, 1 elemento por slide)
```

Rodapé mantido no padrão monday.com (3 bolinhas coloridas + texto).

## Tool knowledge útil

- **HubSpot deals search**: filtro `dealstage NOT_IN ['closedwon','closedlost']` + `amount GT [threshold]` + sort `amount_in_home_currency DESCENDING` = top open pipeline em BRL
- Sempre pedir `amount_in_home_currency` junto com `amount` e `deal_currency_code` — Workise trabalha em BRL mas monday CPM reporta USD. Rate usado na sessão: ~5,5 BRL/USD
- `pptxgen` layout `LAYOUT_WIDE` (13.3 × 7.5") = mesmo aspect ratio do deck original

## Pendências

- Confirmar como/onde inserir os 2 slides no deck do Marcelo (depois do slide 9 ou como bloco final)
- Feedback dos executivos monday após apresentação

## Fontes

- https://claude.ai/chat/2f1fc419-7e19-4b07-b1e9-32f057a8c09e (29/07 — 2 slides QBR)
