# Operação | UnasCraft: Clube de Servers

> Papéis, fluxo de mudança, DoR/DoD e MoSCoW. Versão curta para a Fase 0: ainda sem BookStack nem sprint completo.

---

## Filosofia

- Mudança de infra sem registro não conta.
- O que não está documentado some para o próximo membro.
- Erro vira post-mortem curto: causa, correção, prevenção.

---

## Papéis

| Papel | Responsabilidade |
| ----- | ---------------- |
| Core / maintainer | Prioriza backlog; revisa MRs críticos (Proxmox, OPNsense, identidade) |
| Sysadmin do mês | A partir da Fase 3: alertas, patches, handoff documentado |
| Membro ativo | Workshops, sandbox via MR, documenta o próprio trabalho |

---

## Fluxo de mudança (infra)

1. Issue: o quê, por quê, impacto, esforço (P / M / G).
2. Aprovação de pelo menos 1 maintainer.
3. Branch a partir de `main` (`feature/B-XXX`, `fix/B-XXX`, `docs/...`).
4. Implementar como código (Ansible, Terraform ou Compose); testar no sandbox.
5. Documentar em Markdown neste repo (BookStack quando existir).
6. MR / PR: 1 revisão humana; CI quando houver.
7. Deploy: merge; sysadmin monitora; fechar a issue e atualizar [backlog.md](backlog.md).

### Commits

[Conventional Commits](https://www.conventionalcommits.org/). Assunto em português se o time preferir:

```
feat(proxmox): adiciona node 3 ao cluster
fix(opnsense): corrige regra VLAN Student
docs(backlog): marca B-002 em andamento
```

Segredos nunca em texto plano. Usar Vault ou variáveis protegidas no CI.

---

## Incidentes (quando o lab existir)

| Sev | Critério | Resposta alvo |
| --- | -------- | ------------- |
| P1 | Cluster inacessível, perda de dados, incidente de segurança | Imediato |
| P2 | Serviço essencial fora (Nextcloud, Git, SSO) | ≤ 4 h |
| P3 | Degradação secundária | ≤ 24 h |
| P4 | Cosmético / alerta baixo | Próxima manutenção |

P1 e P2: post-mortem no wiki ou em `docs/`.

---

## DoR (pronto para iniciar)

- [ ] Descrição clara (o quê / por quê)
- [ ] Responsável identificado
- [ ] Dependências externas resolvidas (ex.: TI, hardware)
- [ ] Critérios de aceitação definidos
- [ ] Esforço estimado (P / M / G; XG: quebrar)
- [ ] Vinculado a épico/fase; sem bloqueador conhecido

## DoD (pronto para concluir)

Infra: funciona conforme a aceitação; config no Git; doc atualizada; revisão por outro membro; sem regressão óbvia; status concluído no backlog.

Workshop: ministrado; presença; material publicado; feedback coletado; certificado se aplicável.

Documento: revisão por outro membro; Markdown no lugar certo; links ok.

| Esforço | Significado |
| ------- | ----------- |
| P | ~4 h |
| M | 1-2 dias |
| G | 3-5 dias |
| XG | Quebrar antes de iniciar |

---

## MoSCoW (resumo)

IDs completos: [backlog.md](backlog.md).

| Categoria | Itens-chave |
| --------- | ----------- |
| Must | B-001 inventário; B-002 pedido/aprovação TI ([solicitacao-ti.md](solicitacao-ti.md)); B-003 local; B-006 custos; B-008 Proxmox nos nodes; B-010 VLANs; B-011 OPNsense; B-012 NAS; B-014 VM de teste; B-004 Git interno (Gitea) quando o lab existir (até lá, este GitHub basta) |
| Should | B-009 HA (não bloqueia Fase 1); B-028 WireGuard; B-013 SSO; B-016 a B-020 self-host + monitor; B-015 docs de firewall; B-023 CI leve; B-030 PBS; B-033 rotação sysadmin; onboardings O1-O2 |
| Could | JupyterHub; GitOps completo; Fail2Ban; Alertmanager; onboardings O3-O4; canal oficial; meta de 20 alunos; certificados |
| Won't (12 meses) | Exposição pública à internet; multi-site; integração SIGA; Red Team (B-032), salvo lab maduro e acordo da TI; docs de replicação para outros campi (ano 2) |

Revisar MoSCoW no início de cada fase.
