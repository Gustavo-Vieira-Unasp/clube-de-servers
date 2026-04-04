# ARCHITECTURE.md — UnasCraft | Clube de Servers

> Documentação da arquitetura de infraestrutura do lab. Este documento descreve as camadas lógicas, componentes tecnológicos, decisões de design e o diagrama de topologia da rede.

---

## Visão Geral

O UnasCraft é construído sobre hardware legado reutilizado, organizado em um cluster de virtualização gerenciado pelo **Proxmox VE**. A rede é segmentada por VLANs para garantir isolamento entre os diferentes perfis de uso. Todos os serviços são autogerenciados (self-hosted) e open source.

```.
┌─────────────────────────────────────────────────────────┐
│                    Rede Universitária                   │
│                  (uplink / internet)                    │
└────────────────────────┬────────────────────────────────┘
                         │
                  ┌──────┴──────┐
                  │  OPNsense   │  ← Firewall de borda
                  │  (borda)    │
                  └──────┬──────┘
                         │
              ┌──────────┴──────────┐
              │  Switch Gerenciável │  ← VLANs 802.1Q
              └──┬──────┬──────┬───┘
                 │      │      │
          VLAN10 │ VLAN20│ VLAN30│ VLAN40
        Mgmt     │Student│Storage│  DMZ
                 │      │      │
       ┌─────────┴──┐   │      │
       │ Cluster    │   │      │
       │ Proxmox VE │   │      │
       │ (3 nodes)  │   │      │
       └─────┬──────┘   │      │
             │          │      │
     ┌───────┴──────┐   │    ┌─┴──────────┐
     │  NAS (OMV /  │   │    │  Serviços  │
     │  TrueNAS)    │   │    │  Expostos  │
     └──────────────┘   │    │  (DMZ)     │
                        │    └────────────┘
                   ┌────┴─────────┐
                   │  VMs / LXCs  │
                   │  (Sandbox)   │
                   └─────────────┘
```

---

## Camadas da Arquitetura

### Camada 1 — Física e Rede

| Componente | Tecnologia | Função |
| ---------- | ---------- | ------- |
| Nodes de computação | Desktops legados (x86_64) | Executam o hipervisor Proxmox |
| Switch gerenciável | TP-Link / Cisco legacy | Segmentação de rede por VLANs |
| Firewall de borda | OPNsense | Controle de tráfego, NAT, regras por VLAN |
| Armazenamento compartilhado | OpenMediaVault ou TrueNAS | NAS para backups e volumes de VMs |

#### VLANs

| VLAN | ID | Uso | Acesso |
| ---- | -- | --- | ------ |
| Management | 10 | Administração do cluster e hipervisores | Apenas sysadmins |
| Student | 20 | Sandbox de projetos dos alunos | Membros autenticados |
| Storage | 30 | Tráfego de armazenamento (NFS/iSCSI) | Interno (Proxmox ↔ NAS) |
| DMZ | 40 | Serviços com acesso externo via VPN | Controlado por firewall |

---

### Camada 2 — Virtualização

| Componente | Tecnologia | Função |
| ---------- | ---------- | ------- |
| Hipervisor | Proxmox VE | Gerenciamento de VMs e containers LXC |
| Alta disponibilidade | Proxmox HA Manager | Reinicialização automática de VMs em caso de falha de node |
| Armazenamento de VMs | NFS (via NAS) ou Ceph básico | Volumes compartilhados entre nodes |
| Templates | LXC Templates (Debian/Ubuntu) | Base padronizada para novos containers |

**Decisão de design:** LXC é preferido para serviços leves (menor overhead), enquanto VMs completas são usadas para ambientes que exigem kernel próprio ou isolamento mais rígido.

---

### Camada 3 — Identidade e Acesso

| Componente | Tecnologia | Função |
| ---------- | ---------- | ------ |
| SSO / Identity Provider | Authentik ou Keycloak | Login único para todos os serviços internos |
| VPN | WireGuard | Acesso externo seguro para membros e sysadmins |
| Proteção de superfícies | Fail2Ban | Bloqueio automático de IPs com tentativas de força bruta |

---

### Camada 4 — Serviços Educacionais

| Serviço | Tecnologia | Função |
| ------- | ---------- | ------ |
| Armazenamento de projetos | Nextcloud | Hospedagem de arquivos de TCCs e projetos |
| Wiki e documentação | BookStack | Base de conhecimento interna do clube |
| Repositório de código | Gitea ou GitLab CE | Controle de versão para projetos dos alunos |
| Ambiente de dados | JupyterHub | Notebooks para projetos de ciência de dados e automação |
| DNS interno | Serviço DNS local | Resolução de nomes para os serviços internos |

---

### Camada 5 — Observabilidade e CI/CD

| Componente | Tecnologia | Função |
| ---------- | ---------- | ------- |
| Métricas | Prometheus | Coleta de métricas de todos os serviços e nodes |
| Dashboards | Grafana | Visualização de métricas em tempo real |
| Alertas | Alertmanager | Notificações automáticas para a equipe |
| CI/CD | GitLab CI/CD + runners LXC | Pipelines automáticos de deploy |
| Provisionamento | Terraform + Ansible | Infraestrutura como código (IaC) |
| Backup | Proxmox Backup Server | Backups automáticos e incrementais de VMs/LXCs |

---

## Decisões Arquiteturais

### ADR-001: Proxmox VE como hipervisor principal

**Decisão:** Usar Proxmox VE em vez de VMware ou Hyper-V.
**Justificativa:** Open source, sem licença, interface web completa, suporte nativo a LXC e Ceph, amplamente usado no mercado de homelab e empresas. Alinha com o objetivo de capacitação em tecnologias abertas.

### ADR-002: OPNsense como firewall de borda

**Decisão:** Usar OPNsense em vez de pfSense ou solução de hardware proprietária.
**Justificativa:** Fork mais ativo do pfSense, atualizações frequentes, interface moderna, suporte a plugins e integração com WireGuard nativamente.

### ADR-003: LXC preferido sobre Docker diretamente no host

**Decisão:** Rodar containers Docker dentro de LXCs no Proxmox, não diretamente nos nodes.
**Justificativa:** Mantém o isolamento correto por VM/LXC, permite snapshots e backups nativos do Proxmox, e evita conflitos entre diferentes projetos de alunos.

### ADR-004: GitOps como padrão de deploy

**Decisão:** Todo novo serviço deve ser provisionado via Git push, usando Terraform/Ansible.
**Justificativa:** Rastreabilidade, reversibilidade e aprendizado real de práticas de mercado para os membros.

---

## Requisitos de Hardware Mínimos por Node

| Recurso | Mínimo recomendado |
| ------- | ------------------ |
| CPU | x86_64 com suporte a virtualização (VT-x / AMD-V) |
| RAM | 8 GB (16 GB recomendado) |
| Armazenamento | 120 GB SSD (OS) + HD adicional para dados |
| Rede | 1 porta Gigabit Ethernet |

---

> **Nota:** Este documento deve ser atualizado sempre que uma decisão arquitetural significativa for tomada. Usar o padrão ADR (Architecture Decision Record) para registrar novas decisões.
