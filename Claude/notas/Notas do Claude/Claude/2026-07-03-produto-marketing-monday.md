---
titulo: Produto de marketing na Monday — Workise Marketing Command Center
data: 2026-07-03
tipo: entrega
projeto: workise
tags:
  - monday
  - marketing
  - produto
status: concluido
relacionados:
  - "[[INDEX]]"
---

# Workise Marketing Command Center

## O que é
Novo produto de marketing na Monday (workspace 1928618, Workagency - Template), baseado no vídeo monday Brasil "Processos de Marketing: Automatize sua operação com a monday.com" — tese: centralizar do planejamento à execução. Base existente era motor de agência (request → produção → campanha); faltava o elo de planejamento editorial/conteúdo multi-canal. Posicionamento dual: mesmo produto atende agência (cliente externo) e time de marketing interno, sem duplicar template — via campo "Request Source" (Internal/External) espelhado nos boards.

## Estrutura criada
- **Board Content & Editorial Calendar** (https://workise.monday.com/boards/18420249298), pasta Campaign Management. 16 colunas: Editorial Status (Ideia→Em produção→Em revisão→Aprovado→Agendado→Publicado), Canal (dropdown multi), Data de Publicação, Responsável, Tipo de Conteúdo, Briefing/Copy, Link do Asset Final, Contexto (Agência/In-house), etc. Board relations → General Campaign Board, Requests, Products Catalog, Client List. 4 grupos por estágio editorial. 7 itens de exemplo (demo).
- **Dashboard "Marketing Command Center - Visão Geral"** (pasta Info), agrega os 3 boards centrais.
- Colunas "Origem (Agência/Time Interno)" espelhadas no General Campaign Board e no calendário editorial.
- **Framework 5 pilares**: Planejamento Estratégico, Execução Multi-canal, Governança e Aprovações, + calendário editorial como elo novo.
- **Deck "Workise-Marketing-Command-Center.pptx"** refeito na identidade real do Workagency (creme, laranja, Poppins, header padrão) após usuário subir os decks originais — 9 slides, números atualizados (12 boards / 259 colunas / 93 automações / 11 dashboards), preços 2023 mantidos (R$ 14.990 / R$ 18.100).

## Decisões
- Dropdowns de Canal/Tipo NÃO ligados ao Products Catalog (catálogo é esforço/precificação, granularidade diferente).
- Modo dual estrutural, não dois templates.
- Automações, views e create_doc via API bloqueados por "No approval received" (gate do conector MCP) → entregues como receita manual + blueprint Make (Request Approved + Campaign=Yes → item no calendário editorial). Views manuais: Por Canal, Calendário, Agência vs In-house, Kanban Editorial.
- Primeiro deck foi feito sem ver o pptx original (Drive também bloqueado); refeito depois que o usuário forneceu o arquivo.
- Pendentes: screenshot do board novo no deck, possível reprecificação, versão uso interno do deck.
