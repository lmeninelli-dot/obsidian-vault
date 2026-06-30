# 📋 Protocolo Claude ↔ Obsidian

Este arquivo define como o Claude se comporta ao usar o Obsidian como memória persistente.

---

## ✅ O que o Claude faz automaticamente

### Ao CRIAR uma entrega
1. Gera o conteúdo normalmente na conversa
2. Cria uma nota `.md` em `Claude/notas/` com frontmatter estruturado
3. Adiciona link no `INDEX.md` na categoria correta
4. Linka notas relacionadas entre si com `[[nome-da-nota]]`

### Ao INICIAR uma conversa sobre tema recorrente
1. Lê o `INDEX.md` para ter contexto do histórico
2. Lê a nota anterior antes de responder

### Ao ITERAR sobre algo existente
1. Busca a nota original
2. Atualiza o conteúdo ou cria versão `v2`

---

## 📁 Estrutura de pastas

```
Obsidian/
└── Claude/
    ├── INDEX.md              ← mapa central
    ├── PROTOCOLO.md          ← este arquivo
    └── notas/
        └── YYYY-MM-DD-nome-da-entrega.md
```

---

## 🗒️ Formato padrão de nota

```markdown
---
titulo: Nome da Entrega
data: YYYY-MM-DD
tipo: estrategia | documento | automacao | agente | analise | jd | demo | blueprint
projeto: workise | people-analytics | vmo | smb | interno
tags: #tag1 #tag2
status: rascunho | finalizado | em-uso
relacionados: [[nota-1]] [[nota-2]]
---

# Título

## Contexto
...

## Conteúdo
...

## Próximos Passos
...
```

---

*Criado em 2026-06-24. Não editar manualmente.*
