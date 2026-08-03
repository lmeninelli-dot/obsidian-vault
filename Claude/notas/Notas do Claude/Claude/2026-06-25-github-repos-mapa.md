---
titulo: GitHub — Mapa de Repositórios lmeninelli-dot
data: 2026-06-25
tipo: referencia
projeto: interno
tags: #github #claude-code #skills #referencia
status: ativo
relacionados: [[2026-06-24-github-caveman]] [[INDEX]]
---

# GitHub — Mapa de Repositórios lmeninelli-dot

32 repos forkados em Jun 2026. Todos públicos. Acesso confirmado pelo Claude.

---

## 🔴 PRIORIDADE ALTA — Usar agora

### obsidian-mind
**Repo:** https://github.com/lmeninelli-dot/obsidian-mind  
**O que é:** Vault Obsidian que dá memória persistente a agentes de IA (Claude Code, Codex, Gemini CLI).  
**Por que importa:** É exatamente o que estamos construindo aqui — mas mais avançado. Tem:
- 5 lifecycle hooks (SessionStart, UserPromptSubmit, PostToolUse, PreCompact, Stop)
- 18 slash commands (/om-standup, /om-dump, /om-wrap-up, /om-review-brief...)
- 9 subagentes especializados
- Busca semântica via QMD
- Carregamento em tiers (sempre ~2K tokens, on-demand via QMD)
- Estrutura: brain/, work/, org/, perf/, reference/, thinking/
> ⚠️ **Ação:** Considerar migrar nosso vault atual para esta estrutura.

---

### awesome-agent-skills
**Repo:** https://github.com/lmeninelli-dot/awesome-agent-skills  
**O que é:** 1000+ skills de agentes — Claude Code, Codex, Gemini, Cursor e mais.  
**Por que importa:** Biblioteca enorme de skills prontas. Pode ter skills úteis para monday, make, hubspot.

### caveman *(já documentado)*
**Repo:** https://github.com/lmeninelli-dot/caveman  
**Ver:** [[2026-06-24-github-caveman]]

---

## 🟡 PRIORIDADE MÉDIA — Explorar

| Repo | O que é |
|---|---|
| **everything-claude-code** | Compilação completa de recursos Claude Code |
| **awesome-claude-code** | Curated list de recursos Claude Code (Python) |
| **awesome-claude-skills** | Skills específicas para Claude |
| **claude-code-toolkit** | Toolkit Shell para Claude Code |
| **claude-code-settings** | Settings/configurações para Claude Code (Python) |
| **claude-codex-settings** | Settings combinados Claude + Codex (Python) |
| **Claude-Command-Suite** | Slash commands profissionais para Claude Code (Shell) |
| **commands** | Coleção de comandos gerais |
| **skills** | Fork do repo oficial Anthropic de skills (Python) |
| **marketingskills** | Skills de marketing para agentes (JavaScript) |
| **scientific-agent-skills** | Skills científicas (Python) |
| **cc-devops-skills** | Skills DevOps para Claude Code (Python) |
| **humanizer** | Faz texto gerado por IA soar mais humano |
| **taste-skill** | Skill de refinamento estético/qualidade |

---

## 🟢 REFERÊNCIA — Manter bookmarkado

| Repo | O que é |
|---|---|
| **claude-mem** | Contexto persistente cross-sessions |
| **claude-counter** | Extensão browser: token count no claude.ai (JS) |
| **claude-code-docs** | Documentação Claude Code (Shell) |
| **claude-code-system-prompts** | System prompts do Claude Code (JS) |
| **system_prompts_leaks** | Vazamentos de system prompts (JS) |
| **awesome-n8n-templates** | 280+ templates n8n |
| **ccpm** | Claude Code Package Manager (Shell) |
| **cloud-mcp-server** | Servidor MCP cloud (Python) |

---

## ⬜ FORA DO ESCOPO ATUAL

| Repo | Linguagem | Motivo |
|---|---|---|
| DroidconKotlin | Kotlin | Conferência Android |
| lamoom-python | Jupyter | ML/Data Science |
| jsbeeb | JavaScript | Emulador BBC Micro |
| inkline | TypeScript | UI component library |
| hash | Rust | Sistema de tipos |
| giselle | TypeScript | Plataforma de agentes IA |
| ai-intellij-plugin | Java | Plugin JetBrains |

---

## 🚨 Insight Principal: obsidian-mind

O **obsidian-mind** é essencialmente a versão avançada do que construímos hoje. Diferenças-chave:

| Nossa implementação atual | obsidian-mind |
|---|---|
| Notas manuais por entrega | Hooks automáticos por evento |
| INDEX manual | Bases dinâmicas com queries |
| Sem busca semântica | QMD semantic search |
| Sem lifecycle hooks | 5 hooks (start, message, write, compact, stop) |
| Estrutura simples Claude/ | Estrutura completa: brain/work/org/perf/reference/ |

**Recomendação:** Clonar o obsidian-mind como vault base e migrar o que já criamos.

---
*Nota criada automaticamente pelo Claude em 2026-06-25.*
