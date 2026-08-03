---
titulo: Migração de quadros e Vibes entre contas Monday
data: 2026-03-30
tipo: entrega
projeto: workise
tags:
  - monday
  - migracao
  - vibe
status: concluído
relacionados:
  - "[[2026-06-17-vibe-design-system-waterfall]]"
  - "[[INDEX]]"
---

# Migração de quadros e Vibes entre contas Monday

Duas sessões: 2026-03-30 (600+ quadros) e 2026-04-13 (recriar Vibe).

## Contexto
Copiadora cross-account nativa do Monday deu erro. 600+ quadros para migrar. Limite Make: 30.000 operações.

## Método de migração escolhido
- **Script Node.js zero-dependências** (toolkit: `monday-cross-account-migration.js`, `list-boards.js`, `validate-migration.js`), tokens API de ambas as contas.
- Batches de 100 quadros, executáveis em paralelo (6 terminais/máquinas ≈ 6-8h para 600 quadros).
- Batching de 50 itens/vez, retry 3x, rate limiting, log por board, relatório JSON final, validação origem×destino.
- Preserva 100%: colunas (tipos, settings, labels, ordem), grupos, itens, subitens, valores. Arquivos: download + reupload. Updates: consolidados em 1 update markdown (datas originais não recriáveis).

## Make
- Blueprint de 37 módulos criado (webhook → lista boards → recria estrutura → migra itens 500/batch → relatório → Slack).
- **Inviável para 600 quadros**: ~500 ops/board × 600 = 300.000 ops vs limite de 30.000. Só serviria para ~60 quadros críticos (estratégia híbrida).

## Automações — armadilha central
- **API do Monday NÃO permite criar/copiar automações.** Nem script, nem Make. Não existe `create_automation`.
- Possível apenas: detectar, contar, exportar JSON (nome, ID, trigger, ações básicas) via `trigger_events`, `block_events`, `account_trigger_statistics`.
- Recriação sempre manual (~2-5 min/automação). Mitigar: priorizar por frequência de uso, templates de automações repetidas, dividir entre equipe.
- Duplicar board dentro da mesma conta preserva automações, mas não funciona cross-account. Templates com automações exigem Enterprise e não resolvem cross-account.

## Recriar Vibe em outra conta (04-13)
Vibe "Cronograma de Projetos" — 5 arquivos, ordem de cópia:
1. `waterfallCalculator.js` → `/src/utils/` (íntegro)
2. `useProjectData.js` → `/src/hooks/` (íntegro)
3. `syncToMonday.js` → `/src/utils/` — **substituir Board ID**
4. `ProjectTable.jsx` → `/src/components/` (íntegro)
5. `App.jsx` → `/src/` (íntegro)

**Armadilha crítica**: colunas do board destino devem ter títulos EXATOS (camelCase sem acento) — origem da regra de coluna do Vibe:
`nmeroDoContrato` (Text), `ondas` (Tag), `status` (Status), `responsvel` (People), `statusEtapa` (Status), `duraoDiasTeis` (Number), `prazoFinal` (Text).

Teste: console F12 → `"Iniciando fetch de dados..."` = funcionou.

## Armadilhas (resumo)
1. Automações/integrações não migram via API — só export + recriação manual.
2. Make estoura limite de operações em migração massiva.
3. Histórico de updates perde datas originais.
4. Títulos de coluna divergentes quebram o Vibe — nomes idênticos obrigatórios.
5. Copiadora cross-account nativa instável para volume.
