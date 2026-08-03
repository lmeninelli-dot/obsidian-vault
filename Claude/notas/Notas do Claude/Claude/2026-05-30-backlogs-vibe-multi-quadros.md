---
titulo: Backlogs Vibe multi-quadros — Project Schedule Calculator
data: 2026-05-30
tipo: entrega
projeto: workise
tags: [monday-vibe, waterfall, backlog]
status: concluído
relacionados: ["[[2026-06-17-vibe-design-system-waterfall]]", "[[INDEX]]"]
---

# Backlogs Vibe multi-quadros

## O que é
Extensão do Project Schedule Calculator (Monday Vibe, cronograma waterfall) do Backlog Banzai para 6 quadros irmãos: **Canastra, The Boua, SAT's, Nada Contra, Tudo Legal, LATAM**. Análise via exports xlsx de cada quadro. Estrutura idêntica confirmada: grupo `Cronograma` (+ `Templates [NÃO EXCLUIR]`), duração sempre em `Duração planejada` (`Duração (dias úteis)` vazia em 100%). Diferenças: `5ª Onda` em Canastra e Tudo Legal; "Contratos Ex. / Legal Intake" em The Boua e SAT's; "Prazo final" com grafia diferente em Tudo Legal e LATAM.

## Lógica das ondas
- **Bug original**: código lia `duraoDiasTeis` (vazia em 3.788 subitens do Banzai) → toda tarefa D+X colapsava em 1 dia. Fix: fallback lendo `Duração planejada`.
- **Ondas em paralelo**: cascata entre ondas removida — todos os projetos partem do mesmo Kickoff (`items.map(item => processItemWithRealColumns(item, kickoffDate))`). Encadeamento por duração continua dentro de cada projeto.
- **Dias corridos**: `getContractCalendarDays` passou a contar do Kickoff (Início) até o Término — antes o projeto "durava anos".
- **Offset por onda** (ajuste posterior, cliente): `prazoFinal` do **item** (ex.: D+14 na 2ª Onda) define `waveKickoffDate`. Mudança: `'prazoFinal'` em `ITEM_COLUMNS` (`useProjectData.js`) + leitura em `processItemWithRealColumns`. Genérico — cada board controla offset pelo dado, sem hardcode.

## Correções
1. Subitens "não entravam": tentativas de fix no fetch (página 50, `withSubItems` por página, fallback de colunas; depois chamada separada por item) — não era isso.
2. Diagnóstico real via debug JSON: subitens **sempre carregaram**; o cálculo pulava todos quando `Prazo Final` do subitem vinha `null` (`parsePrazoFinal → null → skip`). Fix: remover o skip, fallback encadeando pela `Duração planejada`.
3. Causa dos apps quebrados no do-zero: prompts geravam Chakra UI; ambiente Vibe usa **shadcn/ui** (confirmado pelo Banzai funcional).
4. Sync confiável: retry + throttle + isolamento por subitem + resumo.
5. Status de subitens: incluídos "Recebido" e "Parado".

## Prompts entregues
- `prompt-migracao-vibe-cronograma.md` — prompt mestre de migração (checklist do board + 5 arquivos).
- `prompt-correcoes-vibe-cronograma.md` — versão curta, 5 correções para app existente.
- `prompt-board-{canastra,the-boua,sat-s,nada-contra,tudo-legal,latam}.md` — um por quadro, com particularidades.
- `prompt-correcoes-board-canastra.md` — 6 correções (5 padrão + 5ª Onda).
- `ajuste-carregar-subitens.md`, `correcao-subitens-chamada-separada.md` — tentativas de fix do fetch.
- `correcao-subitens-prazofinal.md` — o fix real (1 troca no `waterfallCalculator.js`); funcionou, aplicável aos 6.
- `prompt-correcoes-completo.md` — correção consolidada única.
- `prompt-do-zero-DEFINITIVO.md` — do zero em shadcn/ui, 5 arquivos completos, todas as correções + offset das ondas.
- `correcao-offset-ondas.md` e prompt inline para remover debug.
