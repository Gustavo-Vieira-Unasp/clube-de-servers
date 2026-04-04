# BACKLOG.md — UnasCraft | Clube de Servers

> Backlog geral do projeto, organizado por épico e fase de implementação. Itens são rastreados como issues no GitLab e priorizados conforme MoSCoW (ver `PRIORITY_MOSCOW.md`).

---

## Épico 0 — Preparação Institucional

| ID | Item | Responsável | Status |
| ---- | ------ | ------------- | -------- |
| B-001 | Inventário completo de hardware legado disponível | TBD | 🔲 A fazer |
| B-002 | Reunião com TI para aprovação de VLANs dedicadas | TBD | 🔲 A fazer |
| B-003 | Definir localização física do servidor (sala, rack, energia) | TBD | 🔲 A fazer |
| B-004 | Criar repositório GitLab interno com estrutura de pastas | TBD | 🔲 A fazer |
| B-005 | Documentar topologia de rede inicial (Draw.io) | TBD | 🔲 A fazer |
| B-006 | Mapear custos operacionais (energia, domínio, cabos, mídias) | TBD | 🔲 A fazer |
| B-007 | Definir canal de comunicação oficial do clube | TBD | 🔲 A fazer |

---

## Épico 1 — Infraestrutura Base

| ID | Item | Responsável | Status |
| ---- | ------ | ------------- | -------- |
| B-008 | Instalar Proxmox VE nos 3 nodes | TBD | 🔲 A fazer |
| B-009 | Configurar cluster Proxmox com HA | TBD | 🔲 A fazer |
| B-010 | Configurar VLANs (Management, Student, Storage, DMZ) | TBD | 🔲 A fazer |
| B-011 | Instalar e configurar OPNsense como firewall de borda | TBD | 🔲 A fazer |
| B-012 | Configurar NAS com OpenMediaVault ou TrueNAS | TBD | 🔲 A fazer |
| B-013 | Implantar Authentik ou Keycloak para identidade unificada | TBD | 🔲 A fazer |
| B-014 | Criar primeira VM de teste e validar live migration | TBD | 🔲 A fazer |
| B-015 | Documentar topologia final e regras de firewall | TBD | 🔲 A fazer |

---

## Épico 2 — Self-Hosting de Serviços Educacionais

| ID | Item | Responsável | Status |
| ---- | ------ | ------------- | -------- |
| B-016 | Deploy do Nextcloud para armazenamento de projetos e TCCs | TBD | 🔲 A fazer |
| B-017 | Deploy do BookStack como wiki do clube | TBD | 🔲 A fazer |
| B-018 | Deploy do Gitea ou GitLab CE como repositório interno | TBD | 🔲 A fazer |
| B-019 | Configurar DNS interno com domínio local | TBD | 🔲 A fazer |
| B-020 | Deploy do Grafana + Prometheus para monitoramento | TBD | 🔲 A fazer |
| B-021 | Deploy do JupyterHub para uso em aulas e projetos | TBD | 🔲 A fazer |
| B-022 | Onboarding de 20 alunos no sandbox | TBD | 🔲 A fazer |

---

## Épico 3 — Pipeline DevOps & CI/CD

| ID | Item | Responsável | Status |
| ---- | ------ | ------------- | -------- |
| B-023 | Configurar GitLab CE com runners em containers LXC | TBD | 🔲 A fazer |
| B-024 | Criar pipelines de CI/CD com Terraform + Ansible | TBD | 🔲 A fazer |
| B-025 | Implementar fluxo GitOps para provisionamento de serviços | TBD | 🔲 A fazer |
| B-026 | Garantir que todo novo serviço seja deployado via Git push | TBD | 🔲 A fazer |
| B-027 | Documentar processo de contribuição e deploy para membros | TBD | 🔲 A fazer |

---

## Épico 4 — Segurança, Monitoramento Avançado & Expansão

| ID | Item | Responsável | Status |
| ---- | ------ | ------------- | -------- |
| B-028 | Configurar WireGuard VPN para acesso externo seguro | TBD | 🔲 A fazer |
| B-029 | Configurar Fail2Ban nas superfícies expostas | TBD | 🔲 A fazer |
| B-030 | Configurar Proxmox Backup Server com backups automáticos | TBD | 🔲 A fazer |
| B-031 | Configurar Alertmanager com notificações para a equipe | TBD | 🔲 A fazer |
| B-032 | Realizar Workshop "Red Team" com ataques simulados no sandbox | TBD | 🔲 A fazer |
| B-033 | Implementar rotação formal de "sysadmins do mês" | TBD | 🔲 A fazer |
| B-034 | Produzir documentação completa para replicação em outros campi | TBD | 🔲 A fazer |

---

## Épico 5 — Formação & Comunidade

| ID | Item | Responsável | Status |
| ---- | ------ | ------------- | -------- |
| B-035 | Executar Workshop de Onboarding 1 (Ressurreição de Hardware) | TBD | 🔲 A fazer |
| B-036 | Executar Workshop de Onboarding 2 (Docker 101) | TBD | 🔲 A fazer |
| B-037 | Executar Workshop de Onboarding 3 (Redes e Segurança) | TBD | 🔲 A fazer |
| B-038 | Executar Workshop de Onboarding 4 (Infra as Code) | TBD | 🔲 A fazer |
| B-039 | Executar Trilha Principal — Workshop 1 (Linux Server) | TBD | 🔲 A fazer |
| B-040 | Executar Trilha Principal — Workshop 2 (Redes & VLANs) | TBD | 🔲 A fazer |
| B-041 | Executar Trilha Principal — Workshop 3 (Proxmox VE) | TBD | 🔲 A fazer |
| B-042 | Executar Trilha Principal — Workshop 4 (Contêineres & Docker) | TBD | 🔲 A fazer |
| B-043 | Executar Trilha Principal — Workshop 5 (Self-Hosting Educacional) | TBD | 🔲 A fazer |
| B-044 | Executar Trilha Principal — Workshop 6 (CI/CD, Monitoring & Segurança) | TBD | 🔲 A fazer |
| B-045 | Emitir certificados de horas complementares ao fim de cada onboarding | TBD | 🔲 A fazer |

---

## Legenda de Status

| Ícone | Significado |
| ------- | ------------- |
| 🔲 A fazer | Não iniciado |
| 🔄 Em andamento | Em progresso |
| ✅ Concluído | Finalizado e validado |
| ⏸️ Bloqueado | Depende de outro item ou aprovação externa |
