# PRIORITY_MOSCOW.md — UnasCraft | Clube de Servers

> Priorização dos itens do backlog usando o método MoSCoW (Must have, Should have, Could have, Won't have).
> Referência cruzada com `BACKLOG.md` pelos IDs (B-XXX).

---

## O que é MoSCoW?

| Categoria | Significado |
| ----------- | ------------- |
| **Must Have** | Essencial. Sem isso o projeto não funciona ou não pode ser entregue. |
| **Should Have** | Importante, mas não crítico. Deve ser incluído se possível. |
| **Could Have** | Desejável, mas de baixo impacto se omitido. |
| **Won't Have** | Fora do escopo atual. Pode ser reconsiderado no futuro. |

---

## 🔴 Must Have — Sem isso, não há projeto

| ID | Item |
| --- | ------ |
| B-001 | Inventário completo de hardware legado |
| B-002 | Aprovação da TI para VLANs dedicadas |
| B-003 | Localização física definida (sala, rack, energia) |
| B-006 | Mapeamento de custos operacionais |
| B-008 | Instalação do Proxmox VE nos 3 nodes |
| B-009 | Cluster Proxmox com HA configurado |
| B-010 | Configuração das VLANs (Management, Student, Storage, DMZ) |
| B-011 | OPNsense como firewall de borda |
| B-012 | NAS configurado para backup |
| B-014 | Primeira VM de teste validada |
| B-004 | Repositório GitLab interno criado |

---

## 🟠 Should Have — Importante para a qualidade e sustentabilidade

| ID | Item |
| ---- | ------ |
| B-013 | Identidade unificada via Authentik/Keycloak |
| B-016 | Nextcloud para armazenamento de TCCs |
| B-017 | BookStack como wiki do clube |
| B-018 | Gitea ou GitLab CE como repositório interno |
| B-019 | DNS interno com domínio local |
| B-020 | Grafana + Prometheus para monitoramento |
| B-005 | Topologia de rede documentada (Draw.io) |
| B-015 | Regras de firewall documentadas |
| B-023 | GitLab CE com runners LXC |
| B-030 | Proxmox Backup Server com backups automáticos |
| B-033 | Rotação formal de sysadmins do mês |
| B-035 | Onboarding 1 — Ressurreição de Hardware |
| B-036 | Onboarding 2 — Docker 101 |

---

## 🟡 Could Have — Agrega valor, mas pode esperar

| ID | Item |
| ---- | ------ |
| B-021 | JupyterHub para aulas e projetos |
| B-024 | Pipelines CI/CD com Terraform + Ansible |
| B-025 | Fluxo GitOps para provisionamento |
| B-028 | WireGuard VPN para acesso externo |
| B-029 | Fail2Ban nas superfícies expostas |
| B-031 | Alertmanager com notificações para a equipe |
| B-037 | Onboarding 3 — Redes e Segurança |
| B-038 | Onboarding 4 — Infra as Code |
| B-007 | Canal de comunicação oficial do clube |
| B-022 | Onboarding de 20 alunos no sandbox |
| B-045 | Certificados de horas complementares |

---

## ⚫ Won't Have — Fora do escopo dos 12 meses iniciais

| ID | Item | Justificativa |
| ---- | ------ | --------------- |
| B-032 | Workshop "Red Team" com ataques simulados | Requer maturidade de segurança das fases anteriores — previsto para Fase 4 |
| B-034 | Documentação para replicação em outros campi | Produto do segundo ano, após estabilização do lab |
| — | Alta disponibilidade geográfica (multi-site) | Fora de escopo e custo para o período inicial |
| — | Integração com sistemas acadêmicos da universidade (SIGA, etc.) | Depende de aprovação institucional e APIs externas |
| — | Ambiente de produção público (exposição à internet) | Sandbox interno apenas — segurança em primeiro lugar |

---

> **Revisão:** A priorização deve ser revisada ao início de cada fase de implementação ou quando houver mudanças significativas de recursos ou escopo.
