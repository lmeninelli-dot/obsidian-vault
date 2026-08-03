---
titulo: Validação de horas VW/Volkswagen — doc Camila vs calendário real
data: 2026-06-17
tipo: analise
projeto: workise
tags: [vw, horas, calendario, validacao]
status: concluido
relacionados:
  - "[[2026-06-17-otimizacao-calendario]]"
  - "[[INDEX]]"
---

# Validação de horas VW/Volkswagen

## Contexto
Documento `eventos_vw.pdf` criado pela Camila Santos (IC do stack) declara **454 eventos / 506h30min** de trabalho VW (Mai/2025–Jun/2026). Horas discrepantes do esperado. Pedido: cruzar contra o Google Calendar real do Lucas e validar.

## Metodologia
1. Extração do PDF com Python (pypdf). Parse validado contra o total oficial: 454 eventos, 30390 min = 506h30 exatos — base confiável.
2. Coleta via subagente de **3.099 eventos** do calendário `lmeninelli@workise.com.br` (13 meses), JSONs brutos em `cal_raw/`.
3. Matching de↔para dos 454 eventos do PDF contra o calendário real.
4. v1: filtro por título (menção a VW) — 59 reuniões, 54h; teto generoso de ~156h incluindo cerimônias genéricas.
5. v2: refinamento por **participantes/organizer/description**. Achado decisivo: das 138 cerimônias genéricas (74h50), só 2 eventos (1h15) tinham sinal de VW — o resto era de outros clientes (Boticário 54, Naos 33, BTG, ABC Brasil) ou blocos pessoais sem participante (105). O teto de 156h desabou.

## Números
- Declarado (doc Camila): **506h30 / 454 eventos**.
- Auditoria do PDF: 60 grupos de duplicatas (2-3× no mesmo dia, +53h15), 11 blocos de 4h–10h30, 33 cerimônias infladas. Piso conservador: **~354h** (≥30% de inflação comprovável).
- Estimativa só pelo calendário real (v2): **~55h15** de reunião VW efetiva; **~83h** incluindo blocos "Arena VW" (≥4h).

## Conclusão
Horas infladas e comprovável: calendário real sustenta ~55h (~83h com blocos) contra 506h30 declaradas. Inflação vem de duplicações, blocos de dia inteiro e cerimônias genéricas que na verdade pertencem a outros clientes.

## Entregáveis
- `Validacao_Horas_Volks.xlsx` — 10 abas (auditoria do doc + v2 do calendário) + `.docx` executivo.
- `Projeto_Validacao_VW_Calendario_v2/` — Excel, Word e LEIA-ME, 100% a partir do calendário, refinado por participantes.
- `estimativa_meu_calendario.csv`.
