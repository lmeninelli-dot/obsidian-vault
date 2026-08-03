---
titulo: Lead Enrichment Pipeline — Python 6 módulos
data: 2026-06-01
tipo: automacao
projeto: workise
tags: #automacao #python #lusha #hubspot #slack #agente #claude-code
status: ativo
relacionados: [[2026-06-22-estrategia-dual-motor-smb]] [[Brain-Memories]]
fonte: https://claude.ai/chat/a788d74b-8da0-4988-913c-5f07b67e96fe
---

# Lead Enrichment Pipeline — Python 6 módulos

## Arquitetura
Pipeline modular em Python integrando Lusha → Claude API → HubSpot → Slack.

## Arquivos do projeto
| Arquivo | Função |
|---|---|
| `config.py` | HubSpot owner IDs, configurações globais |
| `icp_scorer.py` | Claude API — scoring ICP 0–100 (score, tier, reason, risk) |
| `hubspot_client.py` | Deduplicação por email/domínio, upsert contato/empresa, enrollment em sequences |
| `slack_notifier.py` | Resumo semanal via Block Kit |
| `pipeline.py` | CLI com flags `--run`, `--dry-run`, `--list-sequences` |
| `README.md` | Documentação completa |

## Roteamento de leads
- **Hot (≥75)** → Jonas Barboza (HubSpot: `86994764`) — assignment + sequence enrollment
- **Warm (≥45)** → Karol Hirata (HubSpot: `1372086544`)
- **Cold** → lista estática

## Ponto de integração
`get_leads_from_lusha()` em `pipeline.py` — conecta ao agente Lusha existente no Claude Code.

## Custo estimado
- Lusha: 225–1.000 créditos/semana
- Claude API: baixo (só qualificação, CRM via Make)

## Localização
GitHub: `lmeninelli-dot` (repositório do agente Lusha)  
Desktop: `C:\Users\lmeninelli\Desktop\Claude`

---
*Importado do histórico em 2026-06-25.*
