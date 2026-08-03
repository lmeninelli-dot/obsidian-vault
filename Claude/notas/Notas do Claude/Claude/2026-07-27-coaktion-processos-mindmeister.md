---
tema: Estruturação de processos Workise na Coaktion (MindMeister + monday)
data: 2026-07-27
status: BLOQUEADO — acesso ao mapa e ao board pendente
tags: [coaktion, workise, processos, mindmeister, bloqueio, permissoes]
---

# Processos Workise na Coaktion — Sessão Bloqueada por Acesso

## Contexto

Objetivo: usar mind map do MindMeister como guia estrutural para construir os processos internos da Workise dentro da conta monday.com da Coaktion.

## Recursos com bloqueio de acesso

1. **MindMeister mapa `2871197995`** — link exige autenticação. `web_fetch` só retornou o application shell, zero nós do mapa
2. **monday board `6631516379`** — retorna "not found or you don't have access" via `get_board_info`. Padrão consistente com o PDI board (`18402357804`, USER_UNAUTHORIZED): board carrega para o Lucas na UI mas API não vê. Provavelmente workspace privada onde o token API não é membro
3. `monday.com:search` com `searchType: BOARD` e term "processos" também retornou zero — confirma que o board não é visível ao escopo do token

## Framework proposto (aguarda dados reais)

Mapear cada nó do mind map para uma camada do monday:
- Macroprocesso → **board**
- Etapa → **grupo**
- Atividade → **item**
- Colunas: Responsável, SLA, Entregável

Sinalizado que aplicar este framework antes de ver o mapa real vai **impor estrutura inventada**, não a taxonomia que o Lucas já pensou. Melhor esperar o mapa.

## Sessão-identidade validada

- `get_user_context` confirmou: Lucas Meninelli, Coaktion enterprise, 49 membros
- Sessão autenticada, o problema é escopo de acesso ao board específico, não credencial

## Opções apresentadas ao Lucas (não decididas)

**Para o MindMeister:**
- Exportar e fazer upload (PDF/PNG/imagem)
- Colar outline em texto
- Tornar o mapa público temporariamente

**Para o board:**
- Confirmar link/ID correto
- Adicionar acesso ao user do token na workspace privada
- Criar board novo do zero

## Padrão de bloqueio recorrente (documentar)

**Sintoma**: board URL carrega na UI do Lucas mas API retorna "not found".
**Diagnóstico**: workspace privada + token API sem member access — NÃO invalid ID.
**Workaround**: pedir para verificar workspace membership do user API, ou provisionar board em workspace de acesso confirmado.

Este é o mesmo bloqueio do PDI board `18402357804` (People Analytics Summit) do sync anterior.

## Pendências

- Lucas decidir como passar o conteúdo do mind map
- Resolver acesso ao board `6631516379` (ou criar novo)
- Consolidar sprint de permissões MCP: PDI (`18402357804`) + Coaktion processos (`6631516379`) + verificar Coaktion CAC/CRC (já resolvido em sessão Claude Code anterior)

## Fontes

- https://claude.ai/chat/078932b6-d3fd-469e-abf4-d7266c5daa21 (27/07 — bloqueio identificado)
