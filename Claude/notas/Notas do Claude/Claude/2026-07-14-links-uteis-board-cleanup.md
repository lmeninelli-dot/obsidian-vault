---
tema: Links Úteis board — cleanup e migração Drive
data: 2026-07-14
status: cleanup completo, 4 itens pendentes decisão humana
tags: [links-uteis, monday-com, drive, migracao, cleanup, board]
---

# Links Úteis — Cleanup Completo (Board 18401909759)

## Contexto

Board `Links Úteis` (ID `18401909759`) tinha 120+ itens no grupo Workise precisando de cleanup + migração de links Drive para novo shared drive (ID começando com `0AKY5FIG_3mo7Uk9PVA`). O que começou como update de 5 links virou auditoria completa do grupo.

## Tarefas executadas

- **5 links Drive atualizados** para o novo shared drive: Banner Linkedin, Background Reuniões, Pasta Marketing Drive, Pasta de propostas, Brandbook Workise
- **23 itens bulk-import** com metadata completada (Área responsável, Tipo, Empresa/BU)
- **5 itens novos criados** para pastas do shared drive sem entrada correspondente: Gestão financeira, Sales Ops e CRM, All Hands e Apresentações Institucionais, Segurança da informação, Planejamentos
- **Link corrompido corrigido** em "Template da apresentação dos produtos"
- **Coluna "Atualizado" populada** em todos os itens (Concluído / Em andamento / Atrasado / Cancelado)
- **21 itens** tiveram link copiado da coluna "Arquivos" para "Link" onde Link estava vazio
- **"Segundo dia - Novidade e serviços"** ganhou substituto: "Serviços Workise Slides" do board "🚀 Onboarding Workise"
- **40 itens** com Área responsável e Tipo corrigidos (valores broken de bulk operation anterior)

## Itens flagged para decisão humana

1. **7 auto-gerados "Partner Knowledge Base"** — marcados Cancelado, recomendação: deletar
2. **2 duplicatas Workagency** — decidir qual manter
3. **"Videos criados para a"** — título incompleto, deixado Atrasado
4. **"Portfolio de PCSM"** — link para board `monday.monday.com` inacessível

## Tool knowledge útil

- Filtrar items por grupo no monday: `{'columnId': 'group', 'compareValue': ['group_title'], 'operator': 'any_of'}` no `get_board_items_page` funciona confiável
- Status values armazenados como `{"index": 5}` **quando id=5 não existe no label list** = referências broken/null de bulk operation anterior. Não interpretar como "Vendas" (index correto ≠ index broken)
- Setar status via `{"label": "Vendas"}` retorna `{"index": 2}` confirmando id maps direto para o index nos responses

## Preferência de trabalho (registrada)

Lucas prefere approach proativo: **fazer as mudanças e flagar decisões que precisam de julgamento humano**, não pedir permissão antes de cada ação. Comunica em PT-BR e espera Claude trabalhar direto nas ferramentas, não propor changes para approval primeiro.

## Pendências

- Decisão sobre os 4 itens flagged acima
- Confirmar que o novo shared drive tem estrutura de permissões correta para todos os times

## Fontes

- https://claude.ai/chat/58d1081b-41de-4976-a7a3-b2e2168981cd (14/07 — cleanup completo)
