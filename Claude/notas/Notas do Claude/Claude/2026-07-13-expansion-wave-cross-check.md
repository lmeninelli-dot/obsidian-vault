---
tema: Expansion Wave — cross-check HubSpot/Lusha (4 accounts)
data: 2026-07-13
status: 4 accounts analisados, cross-check dos ~24 restantes pendente
tags: [expansion, base, paty, hubspot, lusha, mac, b4a, involves, flow-gestora]
---

# Expansion Wave — Cross-Check das Primeiras 4 Contas

## Contexto

Lista de "expansion wave" da Paty precisava ser validada contra HubSpot antes de qualquer outreach. Framing original: 4 contas uniformes como "expansion candidates". Realidade revelada pelos dados: **framing estava errado — só 1 das 4 é expansão limpa**.

## Reframing das 4 contas

| Conta | Categoria real | Detalhe |
|-------|----------------|---------|
| **MAC Empreendimentos** | **Closing deal, não prospecting** | Deal "MAC - Melhoria Contínua" ativo, R$ 149.400, proposal production stage, close 30/07 |
| **B4A** | **Retention risk, não expansion** | Deal aberto flagged como downgrade, valor zero. Precisa CS, não expansão |
| **Involves** | **Expansion limpa** ✓ | Histórico saudável de renewals fechados (mais recente 02/2026), sem deal aberto. Candidato válido |
| **Flow Gestora** | **Data gap** | Zero resultados no HubSpot. Verificar nome/domínio com Paty antes de qualquer outreach |

## Discussão estratégica que veio antes (framework onde IA agrega mais valor)

- **Fechar gap de cobertura da Base** (0,43x hoje) — maior alavanca
- **Documentação viva vs artefatos estáticos**
- **Camada de decisão, não só geração de conteúdo**
- Claude especificamente: camada de síntese cross-tool, fechar loop do IA Outputs Tracker, reutilizar frameworks (Architect Protocol, Monday Vibe Architect, skills-router) em vez de conteúdo ad-hoc

## Tool knowledge útil

- HubSpot company search com `CONTAINS_TOKEN` em `name` funciona para partial match mas gera **falsos positivos com nomes comuns** — ex.: buscar "Mac" retorna MAC Empreendimentos + um "Mac" não-relacionado com 8 deals
- Resolução: cross-reference por lifecycle stage e deal count desambigua na hora
- Deal searches com múltiplos company IDs: batch numa call só usando `objectIdValues` como array no `associatedWith`, mais eficiente que sequencial

## Pendências

- Cross-check dos ~24 accounts restantes da lista da Paty
- Arquivo blacklist para o Claude Code agent (mencionado na sessão mas não localizado no Google Drive)
- Verificar nome/domínio real da Flow Gestora com Paty
- Coordenar CS na B4A antes que downgrade vire churn

## Fontes

- https://claude.ai/chat/7e9e8a35-4ab2-4ace-929e-22d986d93b56 (13/07 — cross-check)
