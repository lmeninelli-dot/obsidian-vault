---
tema: AI Workflow Audit + Enablement do time (auditoria completa)
data: 2026-07-07
status: 4 deliverables entregues; 3 playbooks de team enablement entregues; IA Outputs Tracker board pendente construção
tags: [ia, workflow, audit, enablement, jonas, karol, paty, tracker, guardrails]
---

# AI Workflow Audit + Enablement — Sessão Completa

Nota complementar à `ai-workflow-audit-enablement` do sync 20/07. Aqui ficam os **detalhes granulares** dos deliverables e a verificação pendente que o próprio sync-log flagou.

## Contexto

Sessão de auditoria estruturada de como Lucas usa IA e onde pode melhorar. Objetivo: transformar o audit em entregáveis concretos, não relatório teórico.

## 5 forças identificadas

1. Executor mindset — usar IA como executor, não oráculo
2. Sistema de memória persistente (Obsidian + GitHub + Claude Desktop)
3. Personas/frameworks reutilizáveis (Contract Guardian, Monday Vibe Architect, Números, Document Analyzer)
4. Stack integrado (Make + HubSpot + monday + Claude/Gemini API)
5. Cadência semanal já implícita nas sessões

## 5 lacunas → 4 deliverables markdown produzidos

**Lacuna 1: Guardrails para operações destrutivas em massa**
- **Deliverable**: Protocolo Dry-Run → Backup → Approval → Execução em lotes
- Motivação real: perda de itens quando deletamos grupo não-vazio no monday (sessão de segmentação 42k contatos)

**Lacuna 2: Captura de conhecimento das sessões**
- **Deliverable**: Template de nota de fechamento de sessão + backlog de 14 sessões ainda não capturadas na época
- (Este próprio vault-sync é parte da resposta a essa lacuna)

**Lacuna 3: Bloqueios de permissão MCP**
- **Deliverable**: Guia de sprint de permissões, focado em:
  - PDI board `18402357804` (USER_UNAUTHORIZED)
  - Listas de contatos HubSpot
- Miro **removido do escopo** (Lucas não usa)
- Coaktion CAC/CRC verificado como já resolvido em sessão Claude Code anterior (verificação de 5 min, não bloqueio ativo)

**Lacuna 4: Fechar loop output → resultado**
- **Deliverable**: Spec completa do board **IA Outputs Tracker** no monday.com
- **Não foi construído** — próximo passo natural

**Lacuna 5: Democratizar IA para o time**

3 playbooks entregues:

- **Karol (BDR)** — Pipeline Lusha → CSV → enriquecimento IA → HubSpot. Prompt Claude pronto, classificação em tiers A/B/C, checklist de qualidade, métricas mensais
- **Jonas (AE)** — Discovery e geração de proposta em 3 fases: pré-discovery brief, notas pós-discovery estruturadas, geração de proposta. Prompts Claude prontos ancorados nas diretrizes de marca Workise, pre-send checklist, convenção de placeholders
- **Paty (AM)** — playbook de expansion + retention baseado nos dados do HubSpot (registrado como direção geral na sessão)

**Guia de handoff de 45 minutos** para Lucas usar no onboarding de cada membro do time, com ritmo D+7 e D+30 e guidance de failure-mode.

## ⚠️ Verificação pendente crítica

O próprio sync-log do 20/07 **flagou como pendente**: confirmar se os 4 arquivos markdown gerados nesta sessão (guardrails, session-closing template, permissions sprint, IA Outputs Tracker spec) foram efetivamente salvos no vault.

**Ação sugerida**: `ls "Notas do Claude" | grep -E "guardrails|session-closing|permissions-sprint|outputs-tracker"` no vault e reconciliar.

## Pendências consolidadas

- **Construir o board IA Outputs Tracker no monday** (dry-run antes da criação, seguindo o próprio protocolo do deliverable 1)
- **Verificar** que os 4 arquivos markdown estão no vault (senão, regerar da sessão)
- **Executar sprint de permissões** — resolver PDI board + Coaktion processos board (`6631516379`, ver nota 27/07)
- **Sessão de handoff** com cada membro do time (Karol, Jonas, Paty) usando o guia de 45 min

## Fontes

- https://claude.ai/chat/bd8aaf5e-427f-4183-aeb4-25050bca66ec (07/07 — audit completo e enablement)
