---
titulo: Escopo monday Service — Ajinomoto (Workise)
data: 2026-05-26
tipo: documento
projeto: workise
tags:
  - monday-service
  - escopo
  - sales-engineer
status: concluído
relacionados:
  - "[[INDEX]]"
---

# Escopo monday Service — Ajinomoto (Workise)

Papel: Sales Engineer Workise. RFP de ESM da Ajinomoto, entrega via monday Service. Benchmark de qualidade: proposta Ligga. Brandbook aplicado: Azul #032032, Vermelho #EE3048, Creme #FEF5CC, Poppins.

## Cliente / contexto
- Ajinomoto — 544 fluxos ativos, 11 departamentos, canais WhatsApp + portal web (Teams retirado como intake por decisão do Lucas).
- SE de férias; média inicial 1.300h sem integrações.

## Escopo final
- **544 fluxos** (não 250 — racionalização removida a pedido), migração/configuração completa, classificação de complexidade na Consultoria.
- **Integrações no escopo atual**: só WhatsApp (app marketplace: WhatsBoard ou WhatsApp Integrator, PoC na Consultoria) + importação usuários CSV/XLSX. Sem middleware.
- **Fase Posterior** (FUT-01 a FUT-06): SAP SFSF, SAP Rise HANA (bidirecional, confirmado no Q&A), ServiceNow, chatbot IA, CMDB via API, BI, IoT (24 dispositivos).
- **Horas: 1.800 total** — 1.160 implantação, 360 integração, 180 GP, 100 S.A.
- **Cronograma**: 12 meses de entrega (Fase 1 meses 1-3, 20 workshops; Fase 2 meses 4-12) + sustentação 24 meses (80h/mês, meses 13-36).

## Premissas-chave (70+ codificadas: PG, PE, PI, IW, IS, IT, IP, IE, PM, PS, PF, PT, PA, PL)
- WhatsApp sem IA (NLP/LLM fora), árvore de decisão máx 3 níveis, teto 2.000 conversas/mês; BSP e número verificado por conta do cliente.
- SAP: somente leitura no desenho inicial → movido para Fase Posterior; fallback CSV sempre.
- Arquitetura (input do time de produto — Hanan Zaguri): workspaces por departamento + área administrativa; máx 20k tickets operacionais/board com arquivamento periódico; máx 200 blocos/workflow (dividir fluxos complexos); add-on de extensão de limites na comercial.
- Créditos de IA/automações/workflows esgotados: execução para até renovação/upgrade; upgrade é responsabilidade do cliente (PL-01 a PL-07).
- Change Request formal obrigatório (regra de ouro); aceite tácito 10 dias úteis; DEP-01 a DEP-10 com 6 dependências críticas.
- Migração: histórico de e-mails não migra; histórico >12 meses precificado por GB/TB via CR (aditivo, aviso mínimo 30 dias).
- N1/N2/N3 só para TI; RDM se < 40h e baixo investimento; CMDB inicial via export CSV do SCCM.

## Documento entregue
- Pacote inicial: Proposta Técnica + Anexo de Premissas + SOW → consolidado em **documento único v2** (12 seções, 544 parágrafos) com diagrama de arquitetura embutido (PNG 1400×1080: quadro de tickets direto → 11 quadros departamentais → área administrativa consolidada).
- Validação cruzada: 45 itens rastreados, 42 OK, 3 atenções — referências residuais a "250 processos" (Ctrl+F), horas da Sustentação fora da tabela principal, tabela GB/TB pendente (ajuste definido na seção 5.4 apontando para seção 9 — Condições Comerciais).
- Pendências: valores comerciais, nomes dos 11 departamentos no diagrama, cases de sucesso (RFP 3.1.2.6).
