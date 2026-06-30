---
titulo: Setup — Integração Claude + Obsidian
data: 2026-06-24
tipo: documento
projeto: interno
tags: #obsidian #setup #claude
status: finalizado
relacionados: [[INDEX]] [[PROTOCOLO]]
---

# Setup — Integração Claude + Obsidian

## Contexto
Configuração do sistema de memória persistente entre Claude Desktop e Obsidian Vault do Lucas Meninelli (lmeninelli@workise.com.br).

## O que foi feito
- Instalação do Node.js portátil v22.13.1 sem permissão de admin (via winget + zip)
- Configuração do MCP Filesystem no `claude_desktop_config.json`
- Cache do pacote `@modelcontextprotocol/server-filesystem` via npx.cmd
- Criação da estrutura de pastas no vault
- Definição do protocolo de criação de notas automáticas

## Configuração aplicada
```json
"mcpServers": {
  "filesystem": {
    "command": "C:\\Users\\lmeninelli\\node\\node-v22.13.1-win-x64\\npx.cmd",
    "args": [
      "-y",
      "@modelcontextprotocol/server-filesystem",
      "C:\\Users\\lmeninelli\\Desktop\\Claude",
      "C:\\Users\\lmeninelli\\Documents\\Obsidian"
    ]
  }
}
```

## Estrutura criada
- `Claude/INDEX.md` — índice central de todas as entregas
- `Claude/PROTOCOLO.md` — regras de comportamento do Claude
- `Claude/notas/` — onde ficam as entregas individuais

## Como funciona agora
A partir desta data, toda entrega relevante vira uma nota em `notas/` automaticamente.
O Claude lê o INDEX antes de responder sobre temas recorrentes.
Notas se conectam via `[[links]]` nativos do Obsidian.

---
*Nota criada automaticamente pelo Claude em 2026-06-24.*
