---
titulo: Segmentação Marketing Contacts — 42k registros
data: 2026-06-15
tipo: automacao
projeto: workise
tags: #monday #marketing #segmentacao #bulk #automacao #dados
status: finalizado
relacionados: [[Brain-Memories]] [[2026-06-01-lead-enrichment-pipeline]]
---

# Segmentação Marketing Contacts — 42k registros

## Contexto
Board Monday.com com 42.000+ contatos de marketing. Segmentação em massa para campanhas direcionadas.

## ⚠️ INCIDENTE CRÍTICO — Lição aprendida
Durante operação de consolidação de grupos, um grupo não-vazio foi deletado.
**monday.com deleta TODOS os itens do grupo junto com o grupo — sem aviso, sem lixeira.**
Dados perdidos permanentemente. Nunca deletar grupos sem verificar se estão vazios.

## Segmentação aplicada
- Por setor/vertical
- Por tamanho de empresa
- Por estágio no funil
- Por engajamento (abertura de emails, clicks)
- Por região geográfica

## Automações criadas
- Tag automática por comportamento
- Movimentação entre segmentos baseada em score
- Integração com HubSpot para sincronização de status

## Regra crítica para operações em bulk
1. Sempre exportar backup antes de operações em massa
2. Verificar grupo vazio antes de deletar
3. Usar `archive` em vez de `delete` quando possível
4. Testar em grupo de teste (10-20 itens) antes de escalar

---
*Importado do histórico em 2026-06-25.*
