---
titulo: GitHub — Repositório caveman
data: 2026-06-24
tipo: referencia
projeto: interno
tags: #github #claude-code #tokens #skills #caveman
status: ativo
relacionados: [[INDEX]] [[2026-06-24-setup-obsidian-claude]]
---

# caveman — Skill de Compressão de Tokens

**Repo:** https://github.com/lmeninelli-dot/caveman  
**Fork de:** JuliusBrussee/caveman  
**Linguagens:** JavaScript (66%), Python (26%), PowerShell (4%), Shell (4%)

---

## 🪨 O que é

Skill para Claude Code (e 30+ outros agentes) que faz o agente falar como caveman — cortando **~65-75% dos tokens de output** sem perder precisão técnica.

> "why use many token when few do trick"

---

## 📊 Benchmarks reais

| Tarefa | Normal | Caveman | Economia |
|---|---|---|---|
| Explicar bug React re-render | 1180 | 159 | 87% |
| Fix auth middleware | 704 | 121 | 83% |
| Setup PostgreSQL pool | 2347 | 380 | 84% |
| Docker multi-stage build | 1042 | 290 | 72% |
| **Média** | **1214** | **294** | **65%** |

---

## ⚙️ Comandos disponíveis

| Skill | O que faz |
|---|---|
| `/caveman` | Comprime respostas (lite / full / ultra / wenyan) |
| `/caveman-commit` | Commit messages convencionais ≤50 chars |
| `/caveman-review` | PR comments de uma linha |
| `/caveman-stats` | Tokens salvos na sessão + USD |
| `/caveman-compress <file>` | Reescreve CLAUDE.md em caveman (~46% menor) |
| `caveman-shrink` | MCP middleware — comprime descrições de tools |
| `cavecrew-*` | Subagentes caveman (~60% menos tokens) |

---

## 🌐 Ecossistema caveman

| Repo | Função |
|---|---|
| caveman | Compressão de output |
| caveman-code | Agente terminal completo (~2x menos tokens que Codex) |
| cavemem | Memória cross-agent |
| cavekit | Spec-driven build loop |
| cavegemma | Gemma 4 31B fine-tuned em pares caveman |

---

## 💡 Relevância para Workise/Claude Code

- Reduz custo de API em ~65% em sessões longas de Claude Code
- `caveman-compress` no CLAUDE.md reduz tokens de contexto em ~46% toda sessão
- Suporte a português nativo

---
*Nota criada automaticamente pelo Claude em 2026-06-24.*
