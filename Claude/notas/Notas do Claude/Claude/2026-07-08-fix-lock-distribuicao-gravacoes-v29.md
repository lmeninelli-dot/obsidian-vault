---
titulo: Fix lock concorrência — Distribuição Gravações v29 (Make)
data: 2026-07-08
tipo: fix
projeto: Gravações Workise
tags: [make, monday, error-handling, lock, blueprint, gravacoes]
status: entregue
relacionados: ["[[2026-06-25-make-gravacoes-calendar-monday]]", "[[2026-06-24-make-referencia-2026]]", "[[2026-05-28-solucao-monday-sem-hubspot]]"]
---

# Fix lock concorrência — Distribuição Gravações v29

## Erro
Cenário Make **📹 Distribuição — Gravações (Trigger por Item)** parou com:
```
[200] failed to acquire lock on '12454499469|color_mm3f3r3a' (ColumnValueException)
Path: ["change_simple_column_value"]  · Status 200
```
`color_mm3f3r3a` = Status Processamento. Lock de célula (`item|coluna`): duas escritas na mesma célula ao mesmo tempo.

## Causa
Board central 18413775650. No Router (Mód 8):
- Rota 1/2 escrevem `color_mm3f3r3a`="3" (Concluído) no item de origem (Mód **11** / **12**).
- Rota 3 (sem filtro, roda SEMPRE) faz `move_item_to_group` no MESMO item (Mód **13**).
As operações batem no mesmo item no mesmo ciclo; somado a provável **automação nativa do Monday** que reage a status/move e reescreve a coluna → colisão de lock. `sequential` já era `true` (não é run sobreposto).

## Fix entregue
Error handler **Break (retry)** em Mód 11, 12 e 13: `count 3, interval 1min`. Em erro transitório de lock, o Make guarda incomplete execution e reexecuta o módulo até 3× (lock já soltou em <1min). Schema validado via MCP Make. Arquivo:
`Downloads/📹 Distribuição — Gravações (Trigger por Item) v29 (retry lock).blueprint.json`

```json
"onerror": [ { "module": "builtin:Break", "mapper": { "count": 3, "interval": 1 } } ]
```

## Fix durável (pendente do usuário)
Checar no board 18413775650 se existe **automação** "status muda → move grupo" ou "move grupo → muda status". Se existir, ela briga com o Make pela mesma célula → desligar uma das pontas (Make OU automação), não as duas escrevendo `color_mm3f3r3a`.

## Aprendizado
`builtin:Break` no blueprint: `mapper: {count, interval}` (interval em minutos), anexado como `onerror` (irmão de `mapper`/`metadata`). `dlq:true` no cenário guarda incomplete executions p/ auto-retry. Lock error do Monday = retry resolve; fix real = remover escritor duplicado.
