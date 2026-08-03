---
titulo: Vibe Design System — Patch Waterfall App
data: 2026-06-17
tipo: documento
projeto: workise
tags: #monday #vibe #design-system #frontend #waterfall #demo
status: finalizado
relacionados: [[2026-06-24-monday-referencia-2026]] [[Brain-Memories]]
---

# Vibe Design System — Patch Waterfall App

## Contexto
Correção de app Waterfall (visualização de cronograma) para usar tokens corretos do Vibe Design System.

## Paleta Vibe aplicada
| Token | Valor | Uso |
|---|---|---|
| `--color-primary` | #6161FF | Ações principais |
| `--color-success` | #258750 | Status positivo |
| `--color-warning` | #FAB234 | Alertas |
| `--color-error` | #D83A52 | Erros/bloqueios |
| `--color-dark` | #1C1F3B | Background dark |

## Temas disponíveis
- **Dark Blue** — fundo #0A1628, azul profundo
- **Night/Black** — fundo #111111, máximo contraste
- **Glassy Night** — efeito glassmorphism, blur + transparência

## Correções aplicadas
- Substituição de cores hardcoded por CSS variables
- Tipografia: Inter/Poppins via CDN
- Ícones: monday.com Icon Registry
- Responsividade para sidebar 280px → 400px

## Componentes corrigidos
- Header com logo Workise
- Timeline bars (cores de status)
- Tooltips com dados de projeto
- Legenda de fases

---
*Importado do histórico em 2026-06-25.*
