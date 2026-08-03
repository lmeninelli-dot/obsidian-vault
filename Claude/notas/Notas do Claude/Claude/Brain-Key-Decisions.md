---
titulo: Brain — Decisões Importantes
data: 2026-06-25
tipo: referencia
projeto: interno
tags: #brain #decisoes #historico
status: ativo
relacionados: [[Brain-North-Star]] [[Brain-Memories]] [[INDEX]]
---

# 🔑 Key Decisions

> Registro de decisões estratégicas importantes. Adicionar sempre que uma decisão relevante for tomada.

---

## 2026-06-25

### Setup Claude Desktop + Obsidian
- **Decisão:** Usar node.exe portátil (v22.13.1) + `@modelcontextprotocol/server-filesystem` instalado localmente via npm.cmd
- **Motivo:** Sem permissão de admin no notebook corporativo. `npx` causava timeouts por verificar updates na rede.
- **Config:** `node.exe` aponta direto para `dist/index.js` do pacote instalado.
- **Resultado:** MCP estável, sem timeouts.

### Estrutura do Vault Obsidian
- **Decisão:** Adotar estrutura inspirada no obsidian-mind com `brain/`, `work/`, `org/`, `perf/`, `reference/`.
- **Motivo:** Nossa estrutura inicial (só `Claude/notas/`) era simples demais para crescer bem.
- **Próximo passo:** Corrigir config MCP para ter acesso ao vault inteiro, depois criar estrutura completa.

### GitHub como base de skills
- **Decisão:** Usar repos forkados em lmeninelli-dot como biblioteca pessoal de skills e ferramentas.
- **Repos prioritários:** obsidian-mind, awesome-agent-skills, caveman, claude-code-toolkit.

---

## Template para novas decisões

```
### [Título da decisão]
- **Decisão:** O que foi decidido
- **Motivo:** Por que foi tomada
- **Alternativas descartadas:** O que foi considerado e rejeitado
- **Resultado:** Impacto observado
```

---

*Atualizado 2026-06-25.*
