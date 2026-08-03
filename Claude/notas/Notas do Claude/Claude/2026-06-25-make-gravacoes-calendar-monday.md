---
titulo: Make "Gravações Workise" — Calendar → Gemini → Monday
data: 2026-06-25
tipo: automacao
projeto: workise
tags:
  - make
  - monday
  - calendar
  - gemini
  - lgpd
status: em-andamento
relacionados:
  - "[[2026-06-24-make-referencia-2026]]"
  - "[[INDEX]]"
---

# Make "Gravações Workise" — Calendar → Gemini → Monday

## O que é
Automação Make que captura gravações/notas do Gemini das reuniões (Google Meet), analisa a transcrição com Gemini API e grava tudo no board central Monday **📹 Gravações — Workise** (ID `18413775650`, conta Coaktion). Depois, um agente nativo do Monday distribui a análise para os boards de cada cliente (grupo "Agenda"). Time: 22 pessoas, ~3 agendas/dia por pessoa. Budget: 15 mil créditos Make/mês.

## Arquitetura
Evoluiu v1→v17. Estado final: **v17 "Captura Direta" — 1 cenário Make por pessoa**, template `blueprint-17-captura-direta-POR-PESSOA.json`.

Fluxo por cenário (~7+ módulos, roda a cada 2h, janela `{{addHours(now; -3)}}` — janela > intervalo para sobreposição):
1. **Google Calendar › Search Events** (conexão Google da pessoa) — eventos das últimas 3h; filtro "evento já terminou" usa `1.end` (não existe `1.end.dateTime` no output achatado do Make).
2. **Monday › Execute GraphQL Query** — dedup: busca `entity_id` na coluna Calendar Event ID (`text_mm3sm3fw`); filtro barra se já existe ("primeiro ganha").
3. **Calendar › Make an API Call** `GET /v3/calendars/primary/events/{{1.id}}` — retorna `body.attachments[]` (módulos nativos `getAnEvent`/`searchEvents` não expõem attachments; nota: Search Events já traz attachments, módulo 3 é candidato a remoção).
4. **Google Docs › Get a Document** (Include Tabs Content: Yes) — lê o doc de notas do Gemini (transcrição fica em aba do mesmo doc).
5. **HTTP POST Gemini API** — modelo `gemini-3.1-flash-lite` (500 RPD grátis; `gemini-1.5-flash` descontinuado e os Flash "normais" só têm 20 RPD). Chave `AIza...` fixa (token `AQ.Ab8...` do AI Studio expira em ~30 min). Prompt único: extrai transcrição + analisa (tipo, sentimento, tom, arco emocional, action items, alertas, NPS/churn, nome_projeto, resumo executivo). Error handler: Retry 3x/2min (503 por alta demanda).
6. **JSON Parse** — `{{5.data.candidates[1].content.parts[1].text}}`.
7. **Monday › Create Item / Change Multiple Column Values** — preenche colunas (status via `label`, não index); Status Processamento (`color_mm3f3r3a`) → "Em Processamento".
8–9. **Google Drive › Download a File** (doc → PDF) + **Monday › Upload File to Column** — anexa o PDF da transcrição.

Custos: HTTP direto ao Gemini ≈ 1 crédito/reunião vs 43–50 com AI Agents nativos do Make (descartados — estourariam 2,6x os 15k).

## Decisões-chave
- **DWD/Service Account barrado**: TI negou por LGPD. Era a solução grátis e escalável (1 conexão lê docs de todos). Sem ela, cada conexão OAuth só lê os docs do Gemini da própria conta → obrigou 1 cenário por pessoa (Notetaker do Monday descartado por custo).
- **Integração nativa Monday↔Calendar abandonada** no v17: só aceita 1 calendário por board e não expõe Event ID limpo (v16 dependia dela; descoberta chave: `integration_mm3s97d6.entity_id` contém o Event ID).
- **Dedup por `entity_id`** via GraphQL (mesmo entity_id para todos os participantes; GraphQL sempre retorna resultado, Search Items trava com 0 resultados). Sequential processing ON necessário — mas trava fila quando um item falha (503).
- **Gemini via HTTP direto**, não AI Agents do Make (custo) e não escalar billing Google (usuário não quer custo extra).
- **Agente Monday de distribuição** (ID 126344, criado via MCP, INACTIVE): gatilho "Status Processamento → Em Processamento"; descobre colunas do board do cliente em runtime, posta update formatado no grupo "Agenda" do board com nome do cliente, anexa PDF (fallback: link), risco destacado no update sem notificação automática. Prompt em `agente-monday-distribuicao.md`.
- Limpeza de backlog: 24 itens antigos (2023–2025) marcados "Sem Gravação" para não queimar quota.

## Pendências
- Terminar clonagem/correção dos cenários por pessoa — erros recorrentes nos clones: chave API antiga `AQ.Ab8...` (Pedro), conexão/`primary` desalinhados no módulo 1 (404), filtros com caminho errado.
- 404 no Google Docs quando a conta do cenário não tem permissão no doc de notas de outra pessoa.
- Remover módulo 3 (Make an API Call) do template — Search Events já traz attachments; evitaria 404 em clones.
- Ativar o agente Monday 126344 (está INACTIVE; falta acesso ao board — chamada de permissão falhou; MCP do Monday retornava respostas trocadas em chamadas paralelas).
- Validar dedup com múltiplas pessoas na mesma reunião e sequential + fila travada em 503.
- Onboarding do time: `guia-conexao-google-calendar.md` / `Guia-Conexao-Google-Calendar-Workise.docx`; runbook em `RUNBOOK-gravacoes-workise.md`.
