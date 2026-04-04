# PROCESS.md — UnasCraft | Clube de Servers

> Descreve os processos de trabalho do clube: como tarefas são gerenciadas, como mudanças na infraestrutura são propostas e aplicadas, e como a rotação de responsabilidades funciona.

---

## Filosofia de Trabalho

O UnasCraft opera com uma mentalidade de **"infraestrutura como código e documentação como cidadã de primeira classe"**. Isso significa:

- Nenhuma mudança na infra é feita manualmente sem registro.
- Tudo que não está documentado não existe para o próximo membro.
- Erros são oportunidades de aprendizado — registre o que deu errado e o que foi feito para corrigir.

---

## Papéis e Responsabilidades

### Sysadmin do Mês

- Papel rotativo entre membros ativos (a partir da Fase 3)
- Responsável pelo monitoramento diário do cluster, resposta a alertas e aplicação de atualizações de segurança
- Documenta incidentes e ações tomadas no BookStack
- Duração: 1 mês por ciclo

### Membro Ativo

- Participa dos workshops e onboardings
- Pode propor e implementar serviços no sandbox (via MR no GitLab)
- Responsável por documentar seus próprios projetos

### Maintainer / Core Team

- Revisa Merge Requests de infraestrutura
- Aprova mudanças em serviços críticos (Proxmox, OPNsense, Authentik)
- Define prioridades do backlog em conjunto com o grupo

---

## Fluxo de Trabalho para Mudanças na Infraestrutura

Todo serviço novo ou mudança significativa deve seguir este fluxo:

```.
1. PROPOSTA
   └── Abrir uma Issue no GitLab descrevendo:
       - O que será feito
       - Por que é necessário
       - Impacto esperado em outros serviços
       - Estimativa de esforço (P / M / G)

2. REVISÃO
   └── Pelo menos 1 maintainer revisa a issue e aprova o início

3. IMPLEMENTAÇÃO
   └── Criar branch a partir de `main`
   └── Implementar configuração como código (Ansible playbook, Terraform, docker-compose, etc.)
   └── Testar no sandbox antes de aplicar em produção

4. DOCUMENTAÇÃO
   └── Atualizar ou criar página no BookStack
   └── Atualizar BACKLOG.md e arquivos relevantes no repositório

5. CODE REVIEW
   └── Abrir Merge Request para `main`
   └── Pelo menos 1 outro membro revisa o código/configuração
   └── CI/CD roda validações automáticas (lint, dry-run Ansible, etc.)

6. DEPLOY
   └── Merge aprovado → pipeline executa automaticamente
   └── Sysadmin do mês monitora o deploy por 24h

7. FECHAMENTO
   └── Issue fechada com link para o MR e para a documentação
   └── Status no BACKLOG.md atualizado para ✅ Concluído
```

---

## Fluxo de Trabalho para Workshops

```.
1. PLANEJAMENTO (2 semanas antes)
   └── Definir facilitador e data
   └── Preparar material (slides, comandos, links) e publicar no BookStack (rascunho)
   └── Abrir issue no GitLab para rastreamento

2. EXECUÇÃO
   └── Registrar lista de presença
   └── Facilitar o workshop conforme ementa

3. PÓS-WORKSHOP
   └── Publicar material final no BookStack
   └── Coletar feedback dos participantes
   └── Emitir certificados de horas complementares (quando aplicável)
   └── Fechar issue com resumo do que foi coberto
```

---

## Gestão de Incidentes

Quando um serviço ficar fora do ar ou houver comportamento anômalo:

| Severidade | Critério | Tempo de resposta alvo |
| ----------- | --------- | ---------------------- |
| **P1 — Crítico** | Cluster Proxmox inacessível, perda de dados, falha de segurança | Imediato — acionar sysadmin do mês e core team |
| **P2 — Alto** | Serviço essencial fora do ar (Nextcloud, GitLab, Authentik) | Até 4 horas |
| **P3 — Médio** | Serviço secundário com degradação | Até 24 horas |
| **P4 — Baixo** | Problema cosmético, alerta não crítico | Próximo ciclo de manutenção |

**Registro de incidentes:** Todo incidente P1 e P2 deve ter um post-mortem registrado no BookStack com: o que aconteceu, causa raiz, ações tomadas e o que será feito para evitar recorrência.

---

## Rotação de Sysadmins do Mês

- A rotação começa na **Fase 3** (Mês 7), quando o cluster estiver estável
- O sysadmin do mês é anunciado no início de cada mês no canal de comunicação oficial
- O membro sainte faz um handoff documentado para o entrante (estado atual do cluster, alertas ativos, pendências)
- A experiência como sysadmin do mês conta como **entregável de CV** e deve ser registrada no portfólio do membro

---

## Padrões de Documentação

- Todos os documentos em Markdown, seguindo a estrutura deste repositório
- Títulos em português; comandos e nomes de tecnologias em inglês (sem tradução)
- Toda página do BookStack deve ter: data de criação, autor, data da última revisão
- Diagramas em Draw.io exportados como `.drawio` e `.png` no repositório
- Segredos e credenciais **nunca** em texto plano — usar Vault ou variáveis de ambiente protegidas no GitLab CI

---

## Convenções de Branches e Commits no GitLab

### Branches

```.
main          → produção / estado atual do lab
feature/B-XXX → nova funcionalidade ou serviço (referencia ID do backlog)
fix/B-XXX     → correção de problema existente
docs/tema     → atualização de documentação
```

### Commits

Seguir o padrão [Conventional Commits](https://www.conventionalcommits.org/):

```.
feat(proxmox): adiciona configuração de HA para 3 nodes
fix(opnsense): corrige regra de firewall para VLAN Student
docs(backlog): atualiza status do B-008 para concluído
chore(ansible): refatora playbook de instalação do Nextcloud
```

---

> **Revisão deste documento:** Deve ser revisado coletivamente ao fim de cada fase de implementação. Sugestões de melhoria via issue no GitLab.
