# DOR_DOD.md — UnasCraft | Clube de Servers

> Definições de **Pronto para Iniciar (Definition of Ready — DoR)** e **Pronto para Entregar (Definition of Done — DoD)** para tarefas e entregáveis do projeto.

---

## O que são DoR e DoD?

**Definition of Ready (DoR)** define os critérios mínimos que um item do backlog precisa cumprir *antes* de poder ser iniciado. Evita trabalho bloqueado ou mal especificado.

**Definition of Done (DoD)** define os critérios que um item precisa cumprir *para ser considerado concluído*. Garante qualidade e rastreabilidade.

---

## ✅ Definition of Ready (DoR)

Um item do backlog está **pronto para ser iniciado** quando:

- [ ] Possui descrição clara do que deve ser feito e por quê
- [ ] Tem pelo menos um responsável identificado
- [ ] Dependências externas estão resolvidas (ex: aprovação da TI, hardware disponível)
- [ ] Critérios de aceitação estão definidos (o que significa "funcionar"?)
- [ ] Está estimado em esforço (P / M / G ou story points)
- [ ] Está vinculado a um épico e fase do cronograma
- [ ] Não há bloqueadores conhecidos no momento do início

---

## ✅ Definition of Done (DoD)

### Para tarefas técnicas de infraestrutura

Um item técnico está **concluído** quando:

- [ ] A implementação foi realizada e testada no ambiente do lab
- [ ] O serviço/configuração está funcionando conforme os critérios de aceitação definidos no DoR
- [ ] A configuração está versionada no repositório GitLab (código, playbook Ansible, Terraform, ou arquivo de configuração)
- [ ] A documentação foi atualizada no BookStack ou em arquivo Markdown no repositório
- [ ] Pelo menos um outro membro revisou a implementação (code review ou pair review)
- [ ] Não há regressões em serviços previamente funcionando
- [ ] O item foi movido para ✅ Concluído no `BACKLOG.md`

### Para workshops e eventos de formação

Um workshop está **concluído** quando:

- [ ] O conteúdo foi ministrado conforme a ementa planejada
- [ ] A lista de presença foi registrada
- [ ] O material (slides, comandos, links) foi publicado no BookStack ou repositório
- [ ] O projeto de CV associado foi documentado pelos participantes
- [ ] O feedback dos participantes foi coletado (formulário ou conversa registrada)
- [ ] Certificado de horas complementares foi emitido (quando aplicável)

### Para documentos e artefatos de projeto

Um documento está **concluído** quando:

- [ ] Passou por revisão de pelo menos um membro além do autor
- [ ] Está no repositório correto (wiki, `/docs`, ou raiz do repositório)
- [ ] Segue o padrão de formatação Markdown do projeto
- [ ] Links internos e referências cruzadas estão funcionando
- [ ] Tem data de criação e histórico de revisões visível via Git

---

## 📏 Escala de Estimativa de Esforço

| Tamanho | Estimativa | Exemplos |
| --------- | ----------- | --------- |
| **P** (Pequeno) | Até meio período (~4h) | Atualizar documentação, criar uma VM simples, configurar um serviço já conhecido |
| **M** (Médio) | 1 a 2 dias | Configurar uma VLAN, instalar e testar um novo serviço, preparar um workshop |
| **G** (Grande) | 3 a 5 dias | Configurar cluster Proxmox, implantar pipeline CI/CD, realizar workshop completo |
| **XG** (Extra Grande) | Mais de 5 dias | Deve ser quebrado em itens menores antes de entrar no sprint |

---

## 🔁 Fluxo de Estado dos Itens

```.
🔲 A fazer → 🔄 Em andamento → 👀 Em revisão → ✅ Concluído
                    ↓
              ⏸️ Bloqueado (retorna para A fazer quando desbloqueado)
```

---

> **Revisão:** DoR e DoD devem ser revisados coletivamente ao final de cada fase de implementação e ajustados conforme a maturidade do time.
