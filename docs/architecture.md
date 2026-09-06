# Architecture | UnasCraft: Clube de Servers

> Topologia de rede, camadas lógicas e ADRs. Hardware mínimo e pedido à TI: [README](../README.md) e [solicitacao-ti.md](solicitacao-ti.md).

---

## Visão geral

Cluster Proxmox VE em hardware legado, rede em VLANs, OPNsense na borda. Serviços self-hosted e open source.

```
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

## Camadas

### 1. Física e rede

| Componente | Tecnologia | Função |
| ---------- | ---------- | ------ |
| Nodes | Desktops legados (x86_64) | Hipervisor Proxmox |
| Switch | Gerenciável (802.1Q) | VLANs |
| Firewall | OPNsense | NAT, regras por VLAN |
| NAS | OpenMediaVault ou TrueNAS | Backups e volumes |

| VLAN | ID | Uso | Acesso |
| ---- | -- | --- | ------ |
| Management | 10 | Cluster / hipervisores | Sysadmins |
| Student | 20 | Sandbox de projetos | Membros autenticados |
| Storage | 30 | NFS/iSCSI | Interno (Proxmox ↔ NAS) |
| DMZ | 40 | Serviços com acesso via VPN | Firewall |

### 2. Virtualização

| Componente | Tecnologia | Função |
| ---------- | ---------- | ------ |
| Hipervisor | Proxmox VE | VMs e LXC |
| HA (desejável) | Proxmox HA Manager | Reinício se um node cair; não bloqueia a Fase 1 |
| Volumes | NFS (NAS) ou Ceph básico | Compartilhados entre nodes |
| Templates | LXC Debian/Ubuntu | Base para containers |

Preferência: LXC para serviços leves; VM quando precisar de kernel próprio ou isolamento mais rígido.

### 3. Identidade e acesso

| Componente | Tecnologia | Função |
| ---------- | ---------- | ------ |
| SSO | Authentik ou Keycloak | Login único interno |
| VPN | WireGuard | Acesso externo (sujeito à TI) |
| Proteção | Fail2Ban | Bloqueio de força bruta |

### 4. Serviços educacionais

| Serviço | Tecnologia | Função |
| ------- | ---------- | ------ |
| Arquivos | Nextcloud | TCCs e projetos |
| Wiki | BookStack | Base de conhecimento |
| Git interno | Gitea (padrão) | Código dos alunos; GitLab CE só se CI completo for prioridade |
| Dados | JupyterHub | Notebooks |
| DNS | DNS local | Nomes internos |

### 5. Observabilidade e CI/CD

| Componente | Tecnologia | Função |
| ---------- | ---------- | ------ |
| Métricas | Prometheus | Nodes e serviços |
| Dashboards | Grafana | Visualização |
| Alertas | Alertmanager | Notificações |
| CI/CD | Runners no Git interno | Deploy automatizado |
| IaC | Terraform + Ansible | Provisionamento |
| Backup | Proxmox Backup Server | Backups de VMs/LXCs |

---

## ADRs

### ADR-001: Proxmox VE

Open source, sem licença de hipervisor, LXC nativo. Serve à capacitação em stack aberto. Evita VMware e Hyper-V.

### ADR-002: OPNsense

Fork ativo, WireGuard nativo, interface atual. Padrão do lab (não pfSense).

### ADR-003: Docker dentro de LXC

Docker roda nos LXCs do Proxmox, não no host bare-metal. Assim há snapshots e backups nativos e isolamento entre projetos de alunos.

### ADR-004: GitOps

Novos serviços entram via Git (Compose, Ansible ou Terraform). Fica rastreável e treina prática de mercado.

### ADR-005: Git

- Agora: este repositório no GitHub.
- No lab: Gitea por padrão (mais leve no hardware legado). GitLab CE só se a Fase 3 exigir CI completo no mesmo produto.

---

> Atualizar este arquivo quando houver decisão arquitetural nova (novo ADR).
