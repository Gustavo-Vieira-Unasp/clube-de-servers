# Roadmap | UnasCraft: Clube de Servers

> Cronograma oficial: Fases 0-4 em 12 meses. Workshops entram dentro de cada fase, não como trilha paralela.

---

## Fases de implementação

| Fase | Período | Objetivos | Marco |
| ---- | ------- | --------- | ----- |
| **0 - Preparação** | Mês 1 | Inventário de hardware (4-6 PCs / mín. 3 nodes); envio e aprovação do pedido à TI (VLAN, sala, VPN); docs neste repo | Aprovação institucional; local e máquinas definidos |
| **1 - Infra base** | Meses 2-3 | Proxmox nos nodes; VLANs; OPNsense na borda; NAS; VM de teste | Cluster básico no ar (HA desejável, não bloqueia) |
| **2 - Self-hosting** | Meses 4-6 | Nextcloud, BookStack, Gitea (Git interno), DNS local, Grafana + Prometheus | Alunos usando o sandbox |
| **3 - DevOps & CI/CD** | Meses 7-9 | CI no Git interno (ou runners leves); Ansible/Terraform; deploy via Git | Novos serviços sobem por Git push |
| **4 - Segurança & estabilidade** | Meses 10-12 | WireGuard (conforme TI); Fail2Ban; backups (PBS); rotação de sysadmins; docs de fechamento | Lab documentado e estável para o semestre seguinte |

---

## Workshops por fase

A formação acompanha o que está sendo implantado. Não adianta o workshop de Proxmox antes do cluster existir.

### Onboarding (entrada)

| # | Workshop | Fase sugerida |
| - | -------- | ------------- |
| O1 | Ressurreição de hardware (limpeza, pasta térmica, instalação base) | 0-1 |
| O2 | Docker 101 (Nginx + PostgreSQL) | 1-2 |
| O3 | Redes e segurança (OPNsense, reverse proxy) | 1-2 |
| O4 | Infra as Code (Ansible básico) | 2-3 |

### Trilha principal

| # | Workshop | Fase sugerida | Foco |
| - | -------- | ------------- | ---- |
| T1 | Linux Server e hardware legado | 1 | Debian/Ubuntu Server, CLI, armazenamento |
| T2 | Redes e VLANs | 1 | Switch 802.1Q, bridges, OPNsense |
| T3 | Virtualização com Proxmox VE | 1-2 | Cluster, LXC vs VM, snapshots |
| T4 | Contêineres e Docker no Proxmox | 2 | Compose, LXC, registry privado |
| T5 | Self-hosting educacional | 2-3 | Nextcloud, BookStack, Gitea, JupyterHub |
| T6 | CI/CD, monitoramento e segurança | 3-4 | Pipelines, Prometheus/Grafana, WireGuard, backups |

Certificados de horas complementares: conforme as regras do curso, ao fim de cada onboarding aplicável.

---

## Ano 2 (fora do detalhe deste roadmap)

- Documentação para replicar em outros campi
- Publicações e relatos de experiência
- Onboarding já consolidado para novas turmas
- TCCs maiores em infra estável

---

## Manutenção contínua

A partir da Fase 3: rotação de sysadmin do mês entre membros ativos (ver [operacao.md](operacao.md)).
