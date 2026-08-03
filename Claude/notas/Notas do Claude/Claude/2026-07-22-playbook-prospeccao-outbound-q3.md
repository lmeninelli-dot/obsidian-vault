---
tema: Playbook Prospecção Outbound Workise Q3
data: 2026-07-22
status: playbook completo entregue, aguardando implementação
tags: [prospeccao, outbound, q3, cadencias, karol, jonas, carine]
---

# Playbook de Prospecção Outbound Workise (Q3)

## Contexto

Construção do playbook operacional a partir do board Miro "Processos Geração de Demanda Workise". Complementa a nota `q3-sales-planning-corporate` do sync anterior: aqui está o **como** por trás dos números do plano Q3 (54 opps/trimestre).

Time envolvido:
- **Jonas Barboza** (AE/New Business, HS `86994764`) — motor Inbound
- **Karol Hirata** (BDR, HS `1372086544`) — motor Outbound
- **Carine** — segmento Financeiro (papel exato ainda pendente clarificação vs Karol)
- **Lucas Meninelli** (Sales Manager, HS `556276034`)
- **Patrícia Cardoso** (AM/Base, HS `558207897`)
- **Isabela Gomes** — diretora (igomes@coaktion.com)

## Arquitetura: 2 motores, 3 cadências

- **Motor Inbound** (Jonas, AE) — Lead Contact Rate + Lead Sign Up do monday
- **Motor Outbound** (Karol/Carine, BDR) — 6 campanhas segmentadas

**Cadências**:
- **A1 — Cold Operacional** (analistas, supervisores, coordenadores): 5 touches, dias 1/2/4/6/8
- **A2 — Warm/Hot Operacional**: mesma estrutura, abertura mais rápida
- **B — Decisor** (gerente, diretor, head, CFO): 5 touches, dias 1/3/5/8/10; variantes B1 cold e B2 warm

Cada cadência com A/B copy testável, LinkedIn connection notes, InMail, guidance de call, breakup email, biblioteca de variáveis reutilizável por campanha.

## As 6 campanhas outbound

| Campanha | Segmento | Cargo-alvo | Cadência | Dono |
|----------|----------|-----------|----------|------|
| A | Varejo | operacional + decisor | A + B | Karol |
| B | Agrupamento | operacional + decisor | A + B | Karol |
| C | Alimentação | operacional + decisor | A + B | Karol |
| D | Mensalidade | operacional + decisor | A + B | Karol |
| E | Ag. de Billing | operacional + decisor | A + B | Karol |
| F | Financeiro | Coord / Ger / Head / CFO | A (coord) + B (resto) | Carine / Karol |

## Setup no HubSpot

3 sequences reutilizáveis (não uma por campanha — variáveis mudam, estrutura não):
1. **Sequence A1 — Cold Operacional** (5 steps, delays 1/2/4/6/8)
2. **Sequence A2 — Warm Operacional** (5 steps, delays 1/2-3/5/6/8)
3. **Sequence B — Decisor** (5 steps, delays 1/3/5/8/10)

E-mails = automáticos, A/B ativo no dia 1. Ligação/LinkedIn/InMail = task manual. Último step = breakup. Enrollment via lista, com propriedade de origem por campanha registrada.

## Board de prospecção no monday

Colunas propostas: Contato, Empresa, Segmento (status), Campanha (A–F), Cargo, Cadência (A1/A2/B1/B2), Status (Nova → Em cadência → Respondeu → SQL → Reunião agendada → Descartada), Dono, Próximo touch, Origem (Lusha/Evento/Indicação/Inbound).

**Automação-chave (handoff)**: `Status = Reunião agendada` → cria/atualiza deal no HubSpot + notifica Jonas. É onde o Outbound (Karol) entrega para o AE (Jonas).

## Amarração com o pipeline

Fluxo de dados: **Lusha (Karol) → enriquecimento → HubSpot**, amarrando com o Lead Enrichment Pipeline existente (Hot ≥75 → Jonas, Warm ≥45 → Karol). Meta Q3: 54 opps = BDR monday (6) + 2 agentes prospecção (7) + GTM Karol (35) + Inbound (6).

## Deliverable

- `Playbook_Prospeccao_Outbound_Workise.md` salvo em `/mnt/user-data/outputs/`

## Pendências

- Conta reversa de volume por campanha (contatos → SQL → opps para bater Q3) — opção não escolhida na sessão, pode pedir quando quiser
- Clarificar papel da Carine vs Karol no segmento Financeiro para evitar sobreposição

## Fontes

- https://claude.ai/chat/ab66600c-d7bb-4844-b97f-29a090b4a4da (22/07 — playbook completo)
