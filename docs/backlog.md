# Backlog | UnasCraft: Clube de Servers

> Itens por épico. MoSCoW resumido em [operacao.md](operacao.md). Status: Fase 0.

---

## Épico 0 - Preparação institucional

| ID | Item | Responsável | Status | MoSCoW |
| -- | ---- | ----------- | ------ | ------ |
| B-001 | Inventário de hardware legado (meta: 4-6 PCs; mín. 3 nodes) | TBD | 🔲 A fazer | Must |
| B-002 | Pedido / reunião com TI (VLAN, sala, VPN); texto em [solicitacao-ti.md](solicitacao-ti.md) | TBD | 🔲 A fazer | Must |
| B-003 | Definir localização física (sala, rack, energia) | TBD | 🔲 A fazer | Must |
| B-004 | Git interno no lab (Gitea por padrão); até lá usar este GitHub | TBD | 🔲 A fazer | Must* |
| B-005 | Documentar topologia de rede (Draw.io) | TBD | 🔲 A fazer | Should |
| B-006 | Mapear custos operacionais (energia, cabos, mídias) | TBD | 🔲 A fazer | Must |
| B-007 | Definir canal de comunicação oficial do clube | TBD | 🔲 A fazer | Could |

\*Must quando o lab existir; neste repositório o GitHub já cobre a Fase 0.

---

## Épico 1 - Infraestrutura base

| ID | Item | Responsável | Status | MoSCoW |
| -- | ---- | ----------- | ------ | ------ |
| B-008 | Instalar Proxmox VE nos nodes | TBD | 🔲 A fazer | Must |
| B-009 | Configurar HA no cluster Proxmox | TBD | 🔲 A fazer | Should |
| B-010 | Configurar VLANs (Management, Student, Storage, DMZ) | TBD | 🔲 A fazer | Must |
| B-011 | Instalar e configurar OPNsense na borda | TBD | 🔲 A fazer | Must |
| B-012 | Configurar NAS (OpenMediaVault ou TrueNAS) | TBD | 🔲 A fazer | Must |
| B-013 | Implantar Authentik ou Keycloak | TBD | 🔲 A fazer | Should |
| B-014 | Criar primeira VM de teste | TBD | 🔲 A fazer | Must |
| B-015 | Documentar topologia final e regras de firewall | TBD | 🔲 A fazer | Should |

---

## Épico 2 - Self-hosting educacional

| ID | Item | Responsável | Status | MoSCoW |
| -- | ---- | ----------- | ------ | ------ |
| B-016 | Deploy Nextcloud | TBD | 🔲 A fazer | Should |
| B-017 | Deploy BookStack | TBD | 🔲 A fazer | Should |
| B-018 | Deploy Gitea (Git interno) | TBD | 🔲 A fazer | Should |
| B-019 | DNS interno | TBD | 🔲 A fazer | Should |
| B-020 | Grafana + Prometheus | TBD | 🔲 A fazer | Should |
| B-021 | JupyterHub | TBD | 🔲 A fazer | Could |
| B-022 | Onboarding de ~20 alunos no sandbox | TBD | 🔲 A fazer | Could |

---

## Épico 3 - DevOps e CI/CD

| ID | Item | Responsável | Status | MoSCoW |
| -- | ---- | ----------- | ------ | ------ |
| B-023 | CI/runners leves no Git interno | TBD | 🔲 A fazer | Should |
| B-024 | Pipelines com Terraform + Ansible | TBD | 🔲 A fazer | Could |
| B-025 | Fluxo GitOps para provisionamento | TBD | 🔲 A fazer | Could |
| B-026 | Novos serviços deployados via Git push | TBD | 🔲 A fazer | Could |
| B-027 | Documentar contribuição e deploy | TBD | 🔲 A fazer | Should |

---

## Épico 4 - Segurança, monitoramento e estabilidade

| ID | Item | Responsável | Status | MoSCoW |
| -- | ---- | ----------- | ------ | ------ |
| B-028 | WireGuard VPN (conforme TI) | TBD | 🔲 A fazer | Should |
| B-029 | Fail2Ban nas superfícies expostas | TBD | 🔲 A fazer | Could |
| B-030 | Proxmox Backup Server | TBD | 🔲 A fazer | Should |
| B-031 | Alertmanager | TBD | 🔲 A fazer | Could |
| B-032 | Workshop Red Team (só com lab maduro e acordo da TI) | TBD | 🔲 A fazer | Won't* |
| B-033 | Rotação formal de sysadmins do mês | TBD | 🔲 A fazer | Should |
| B-034 | Docs de replicação para outros campi | TBD | 🔲 A fazer | Won't (ano 2) |

\*Reconsiderar no fim da Fase 4 se fizer sentido; não é meta dos 12 meses iniciais.

---

## Épico 5 - Formação e comunidade

| ID | Item | Responsável | Status | MoSCoW |
| -- | ---- | ----------- | ------ | ------ |
| B-035 | Onboarding 1: ressurreição de hardware | TBD | 🔲 A fazer | Should |
| B-036 | Onboarding 2: Docker 101 | TBD | 🔲 A fazer | Should |
| B-037 | Onboarding 3: redes e segurança | TBD | 🔲 A fazer | Could |
| B-038 | Onboarding 4: Infra as Code | TBD | 🔲 A fazer | Could |
| B-039 | Trilha: Workshop 1 (Linux Server) | TBD | 🔲 A fazer | Should |
| B-040 | Trilha: Workshop 2 (Redes e VLANs) | TBD | 🔲 A fazer | Should |
| B-041 | Trilha: Workshop 3 (Proxmox VE) | TBD | 🔲 A fazer | Should |
| B-042 | Trilha: Workshop 4 (Contêineres e Docker) | TBD | 🔲 A fazer | Could |
| B-043 | Trilha: Workshop 5 (Self-hosting) | TBD | 🔲 A fazer | Could |
| B-044 | Trilha: Workshop 6 (CI/CD, monitoring e segurança) | TBD | 🔲 A fazer | Could |
| B-045 | Certificados de horas complementares | TBD | 🔲 A fazer | Could |

---

## Legenda de status

| Ícone | Significado |
| ----- | ----------- |
| 🔲 A fazer | Não iniciado |
| 🔄 Em andamento | Em progresso |
| ✅ Concluído | Finalizado e validado |
| ⏸️ Bloqueado | Depende de outro item ou aprovação externa |
