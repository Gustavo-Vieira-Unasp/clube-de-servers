# UnasCraft — Clube de Servers

![Status](https://img.shields.io/badge/status-em%20implantação-yellow)
![Licença](https://img.shields.io/badge/licença-open%20source-blue)
![Campus](https://img.shields.io/badge/campus-UNASP--EC-green)

> **Missão:** Criar o primeiro laboratório de infraestrutura open source gerido por estudantes — inicialmente gratuito, isolado e escalável — que sirva de referência para outros campi UNASP, outras universidades, centros universitários e faculdades, não só adventistas, mas também confessionais ou não.
>
> **Visão:** Em 2 anos, tempo esperado para a formação da primeira turma de Engenharia da Computação do Campus-EC, o UnasCraft será um hub de projetos reais que enriquecem o currículo dos membros e geram publicações e palestras.

---

Este é o repositório inicial e oficial do **"Clube de Servers"**, apelidado de **UnasCraft**.

A iniciativa surgiu no contexto do Projeto de Extensão e Projeto Integrador das turmas de 5º Semestre em 2026, que consistia na criação de uma automação para hortas. Um servidor para captar dados foi uma das soluções discutidas, e daí nasceu a ideia de estruturar uma infraestrutura permanente gerida pelos próprios alunos.

---

## Propósito

Dentre os objetivos do UnasCraft encontram-se:

- **Capacitação de Estudantes:** Através da construção e operação de infraestrutura real, com conhecimento open source e democrático — auxiliando aqueles que pretendem trabalhar futuramente com DevOps, SRE ou SysAdmin (Proxmox/K8s).
- **Sandbox para TCCs:** Redução da evasão e aumento da qualidade dos projetos finais ao oferecer hospedagem gratuita interna para bancos de dados e APIs.
- **Sustentabilidade:** O projeto estende a vida útil do patrimônio da universidade (computadores legados) em 3 a 5 anos por meio de sistemas leves (Linux/Docker), evitando o descarte prematuro.

---

## Requisitos Mínimos de Hardware

Para replicar esta iniciativa, são necessários no mínimo:

- 3 nodes (computadores legados compatíveis com virtualização)
- 1 switch gerenciável (com suporte a VLANs 802.1Q)
- Mídia para backups (HD externo, NAS ou similar)
- Cabos de rede e patch panel (conforme escala)

> **Nota sobre custos:** Embora o hardware seja reutilizado, haverá custos operacionais com energia elétrica, registro de domínio interno, mídias de backup e eventuais cabos e acessórios. Recomenda-se mapear esses custos com a TI e a administração da universidade antes da Fase 0.

---

## Como Contribuir

1. Leia a documentação disponível no [BookStack interno](disponível após Fase 2).
2. Abra uma *issue* no repositório descrevendo sua sugestão ou problema encontrado.
3. Para propor melhorias na infraestrutura, siga o fluxo GitOps: crie um *branch*, implemente a mudança e abra um *merge request*.
4. Novos membros devem participar dos **Workshops de Onboarding** antes de assumir responsabilidades técnicas.

Para entrar em contato com a equipe atual, procure os responsáveis pelo projeto junto à coordenação dos cursos de Engenharia da Computação e Sistemas de Informação do UNASP-EC, ou acesse o canal de comunicação oficial do clube *(a definir pela equipe)*.

---

## Cronograma Consolidado – UnasCraft | Clube de Servers

> Visão unificada dos workshops, roadmap técnico e fases de implementação (12 meses).

---

## Fases de Implementação (12 Meses)

| Fase | Período | Objetivos principais | Marcos | Projeto para CV |
| ------ | --------- | ---------------------- | -------- | ----------------- |
| **Fase 0 – Preparação** | Mês 1 | Inventário de hardware legado (mín. 3 nodes + 1 switch gerenciável); reunião com TI para aprovação de VLANs dedicadas; criação do repositório GitLab interno + documentação (Markdown + Draw.io) | Infra física mapeada e aprovação institucional obtida | *(Fase preparatória — sem entregável de CV)* |
| **Fase 1 – Infra Base Segura** | Meses 2–3 | Instalação cluster Proxmox VE + VLANs (Management separada); firewall OPNsense na borda; NAS (OpenMediaVault/TrueNAS) para backup; gestão de identidade via Authentik/Keycloak | Cluster rodando com 3 nodes e primeira VM de teste | "Cluster Proxmox HA com VLANs isoladas" |
| **Fase 2 – Self-Hosting** | Meses 4–6 | Nextcloud + BookStack + Gitea; registro de domínio interno via DNS local; Grafana + Prometheus para monitoramento em tempo real | 20 alunos hospedando projetos no sandbox | "Plataforma self-hosted para 50+ usuários" |
| **Fase 3 – DevOps & CI/CD** | Meses 7–9 | GitLab CE completo com runners em LXC; pipelines automáticos com Terraform + Ansible; integração GitOps para provisionamento | Todo deploy de serviço novo via Git push | "Pipeline CI/CD GitOps para infraestrutura como código" |
| **Fase 4 – Segurança, Monitoramento & Expansão** | Meses 10–12 | Prometheus/Grafana avançado + backups automáticos; VPN WireGuard para acesso externo; Workshop "Red Team" (ataques simulados no sandbox); rotação de "sysadmins do mês" | Lab 100% operacional e documentado para o próximo semestre | "Dashboard de observabilidade completo + hardening de cluster" |

---

## Roadmap Técnico por Camada

> As camadas abaixo representam a progressão técnica interna e são independentes das fases do cronograma de implementação acima.

| Camada | Período Sugerido | Componentes | Tecnologias | Finalidade |
| -------- | ----------------- | ------------- | ------------- | ------------ |
| **Camada 1 – Fundação** | Mês 1 | Hipervisor, Rede Isolada, Armazenamento | Proxmox VE, VLANs, OpenMediaVault / TrueNAS | Base física e virtual segura |
| **Camada 2 – Serviços Essenciais** | Mês 2 | Identidade unificada, Monitoramento | Authentik / Keycloak, Grafana + Prometheus | Login único + visibilidade de recursos |
| **Camada 3 – Pipeline DevOps** | Mês 3+ | CI/CD interno | Gitea + GitHub Actions Runner / Jenkins | Automação de deploys no sandbox |

---

## Workshops de Formação (Trilha Principal – ~28 semanas)

| # | Workshop | Objetivo | Conteúdo Principal (Open Source) | Duração | Projeto para CV |
| --- | ---------- | ---------- | ---------------------------------- | --------- | ----------------- |
| 1 | **Linux Server & Hardware Legacy** | Entender hardware obsoleto e Linux bare-metal | Instalação Debian/Ubuntu Server, BIOS/UEFI, RAID software (mdadm), ZFS básico, CLI mastery | 4 semanas | "Migrei 5 PCs antigos para servidores headless com ZFS e monitorei com Netdata" |
| 2 | **Redes & Isolamento com VLANs** | Garantir segurança na rede universitária | Switches gerenciáveis (TP-Link/Cisco legacy), VLANs 802.1Q, bridges no Linux, pfSense/OPNsense como firewall | 4 semanas | "Configurei rede isolada com 4 VLANs (Management, Student, Storage, DMZ) – diagrama + regras de firewall" |
| 3 | **Virtualização com Proxmox VE** | Criar o cluster base do lab | Instalação Proxmox em cluster (3+ nodes), LXC vs VM, Ceph básico ou NFS, HA, live migration | 5 semanas | "Implantei cluster Proxmox 3 nodes com HA usando hardware legado – documentação completa" |
| 4 | **Contêineres & Docker no Proxmox** | Praticar DevOps leve | Docker + Portainer, Docker Compose, LXC templates, Registry privado | 4 semanas | "Criei 10 serviços em Docker Compose (Nextcloud, GitLab, Wiki) rodando em LXC no Proxmox" |
| 5 | **Self-Hosting & Serviços Educacionais** | Oferecer sandbox real para alunos | Nextcloud (projetos/TCCs), BookStack (wiki do clube), Gitea/GitLab CE, JupyterHub | 5 semanas | "Deploy de plataforma self-hosted completa para 50+ alunos hospedarem TCCs" |
| 6 | **CI/CD, Monitoramento & Segurança Avançada** | Fechar o ciclo DevOps | GitLab CI/CD + runners em LXC, Prometheus + Grafana + Alertmanager, Fail2Ban + WireGuard VPN, backup automático (Proxmox Backup Server) | 6 semanas | "Pipeline CI/CD completo + dashboard de monitoramento do cluster inteiro" |

---

## Workshops de Onboarding (Ementa Sugerida – Novos Membros)

> Geram certificados de horas complementares e servem como porta de entrada para novos membros.

| # | Workshop | Conteúdo Prático | Hardware Foco |
| --- | ---------- | ----------------- | --------------- |
| 1 | **Ressurreição de Hardware** | Limpeza técnica, troca de pasta térmica e instalação de Proxmox | Desktops Legados |
| 2 | **Docker 101** | Subir um servidor web Nginx e um banco de dados PostgreSQL via CLI | Containers LXC |
| 3 | **Redes e Segurança** | Configuração de Firewalls (pfSense/OPNsense) e Reverse Proxy (Nginx Proxy Manager) | Roteadores/Switches |
| 4 | **Infra as Code** | Introdução ao Ansible para configurar 5 máquinas simultaneamente | Automação |

---

## Visão Geral Consolidada (Mês a Mês)

| Mês | Fase | Workshops Ativos | Entregáveis Técnicos | Gestão / Comunidade |
| ----- | ------ | ----------------- | ---------------------- | ---------------------- |
| 1 | Fase 0 – Preparação | Onboarding 1 (Hardware) | Inventário de hardware, repositório GitLab, documentação inicial | Reunião com TI da universidade |
| 2 | Fase 1 – Infra Base | Workshop 1 (Linux Server) + Onboarding 2 (Docker 101) | Proxmox instalado, VLANs configuradas, OPNsense na borda | Formação de equipe de sysadmins |
| 3 | Fase 1 – Infra Base | Workshop 2 (Redes & VLANs) + Onboarding 3 (Redes e Segurança) | Cluster 3 nodes operacional, NAS configurado, Authentik/Keycloak | Marco: 1ª VM de teste rodando |
| 4 | Fase 2 – Self-Hosting | Workshop 3 (Proxmox VE) + Onboarding 4 (Infra as Code) | Nextcloud + BookStack + Gitea no ar, DNS interno | Início de hospedagem de projetos de alunos |
| 5 | Fase 2 – Self-Hosting | Workshop 3 (continuação) | Grafana + Prometheus para monitoramento | — |
| 6 | Fase 2 – Self-Hosting | Workshop 4 (Contêineres & Docker) | Domínio interno registrado, JupyterHub disponível | Marco: 20 alunos usando o sandbox |
| 7 | Fase 3 – DevOps & CI/CD | Workshop 4 (continuação) | GitLab CE com runners LXC | Início da rotação de sysadmins do mês |
| 8 | Fase 3 – DevOps & CI/CD | Workshop 5 (Self-Hosting Educacional) | Pipelines Terraform + Ansible funcionando | — |
| 9 | Fase 3 – DevOps & CI/CD | Workshop 5 (continuação) | Todo novo serviço via Git push | Marco: GitOps operacional |
| 10 | Fase 4 – Segurança & Expansão | Workshop 6 (CI/CD, Monitoring & Segurança) | WireGuard VPN, Fail2Ban, backups automáticos | Workshop "Red Team" interno |
| 11 | Fase 4 – Segurança & Expansão | Workshop 6 (continuação) | Proxmox Backup Server configurado, alertas no Alertmanager | — |
| 12 | Fase 4 – Fechamento | — | Lab 100% documentado, dashboard de observabilidade completo | Entrega de certificados, planejamento do próximo semestre |

---

## E depois dos 12 meses?

O cronograma cobre o primeiro ano de operação do UnasCraft. No segundo ano — coincidindo com a formatura da primeira turma de Engenharia da Computação do Campus-EC — a expectativa é que o clube esteja maduro o suficiente para:

- Servir de referência para outros campi do UNASP e instituições externas;
- Publicar estudos de caso e relatos de experiência em eventos técnicos e acadêmicos;
- Receber novas turmas de membros com um processo de onboarding já consolidado;
- Sustentar projetos de TCC mais complexos com infraestrutura estável e documentada.

---

> **Manutenção contínua:** Rotação de "sysadmins do mês" entre membros ao longo de todo o ano para garantir experiência prática real para o CV.
