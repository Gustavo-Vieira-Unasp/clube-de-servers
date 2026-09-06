# UnasCraft: Clube de Servers

![Status](https://img.shields.io/badge/status-em%20implantação-yellow)
![Licença](https://img.shields.io/badge/licença-open%20source-blue)
![Campus](https://img.shields.io/badge/campus-UNASP--EC-green)

> **Missão:** Montar no UNASP-EC um laboratório de infraestrutura open source gerido por estudantes, isolado da rede de produção, com reuso de hardware e uso real em capacitação e TCCs.
>
> **Visão:** Em cerca de 2 anos, ter documentação e operação estáveis o bastante para outros campi (e outras instituições) replicarem o modelo.

Repositório de documentação do Clube de Servers (UnasCraft). A ideia saiu do Projeto de Extensão / Integrador do 5º semestre (2026): de um servidor para automação de hortas para uma infraestrutura permanente sob gestão dos alunos.

---

## Propósito

- Capacitação: operar de verdade Proxmox, Docker, redes e segurança (perfil DevOps / SRE / SysAdmin).
- Sandbox para TCCs: hospedagem interna gratuita para bancos, APIs e experimentos.
- Reuso: estender a vida útil de computadores legados da universidade.

---

## O que pedimos à TI (Fase 0)

Texto completo: [docs/solicitacao-ti.md](docs/solicitacao-ti.md).

| Pedido | Detalhe |
| ------ | ------- |
| Hardware | 4 a 6 PCs legados (mínimo do lab: 3 nodes; o resto vira reserva, NAS ou firewall) |
| Espaço | Sala com energia, ventilação e segurança para operação contínua |
| Rede | Sub-rede / VLAN dedicada, isolada da produção do UNASP |
| Acesso remoto | VPN (WireGuard) ou o que a TI definir (sem porta pública aberta por padrão) |

Pode haver um evento de Minecraft de curto prazo (`[data a definir]`) no mesmo hardware, antes do lab permanente.

---

## Hardware mínimo (lab)

- 3 nodes x86_64 com virtualização (VT-x / AMD-V); 8 GB RAM no mínimo (16 GB recomendado)
- 1 switch gerenciável (802.1Q)
- Mídia de backup (HD externo / NAS)
- Cabos e patch panel conforme o local

Antes de subir o cluster, mapear com a TI e a administração os custos de energia, mídias e cabos.

---

## Documentação

| Documento | Conteúdo |
| --------- | -------- |
| [docs/solicitacao-ti.md](docs/solicitacao-ti.md) | E-mail oficial à TI |
| [docs/roadmap.md](docs/roadmap.md) | Fases 0-4 (12 meses) e workshops por fase |
| [docs/architecture.md](docs/architecture.md) | Topologia, VLANs e ADRs |
| [docs/backlog.md](docs/backlog.md) | Itens B-001 a B-045 |
| [docs/operacao.md](docs/operacao.md) | Papéis, fluxo de mudança, DoR/DoD e MoSCoW |

---

## Como contribuir

1. Leia o [roadmap](docs/roadmap.md) e a [arquitetura](docs/architecture.md).
2. Abra uma issue neste repositório (GitHub) com a sugestão ou o problema.
3. Doc: branch `docs/...` e pull request.
4. Infra (quando o lab existir): fluxo em [operacao.md](docs/operacao.md); config como código (Ansible / Terraform / Compose).
5. Novos membros passam pelos workshops de onboarding da fase em andamento.

Git deste projeto: GitHub, até existir Git interno no lab (padrão: Gitea; GitLab CE só se CI completo for prioridade na Fase 3).

Contato: coordenação de Engenharia da Computação / Sistemas de Informação do UNASP-EC, ou o canal oficial do clube (a definir).
