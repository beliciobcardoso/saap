# SAAP — Sistema de Agendamento de Atendimentos Profissionais

O **SAAP** é um projeto de análise e modelagem orientada a objetos para um sistema de agendamento em clínicas, consultórios e serviços especializados.  
O foco é reduzir conflitos de horário, melhorar o controle de agenda e organizar o ciclo de vida dos atendimentos.

## Objetivo

Estruturar um sistema rastreável de agendamentos, com regras claras de negócio para confirmação, atendimento, cancelamento, remarcação e controle de no-show.

**Proposta completa:** [docs/proposta_do_projeto.md](docs/proposta_do_projeto.md)

## Escopo inicial (MVP)

- Cadastro de **pacientes**, **profissionais** e **serviços**
- **Agendamento** com validação de conflito de horário
- **Confirmação de presença** (login opcional, link ou recepção)
- **Cancelamento/remarcação** (remarcação gera novo agendamento)
- Estados principais do agendamento: `PENDENTE`, `CONFIRMADO`, `REALIZADO`, `CANCELADO`, `NO_SHOW`
- Notificações básicas de confirmação/cancelamento
- Controle de acesso por perfil (RBAC): administrador, recepcionista e profissional

## Regras de negócio centrais

- O agendamento organiza capacidade por período.
- O paciente confirmado entra no fluxo presencial após **check-in**.
- A ordem efetiva de atendimento no período é por chegada (**FIFO**).
- Agendamento confirmado sem check-in no período deve ir para **NO_SHOW**.

## Atores do sistema

- Paciente
- Profissional de Saúde
- Recepcionista
- Assistente
- Administrador

## Artefatos do projeto

Toda a documentação está em `docs/`:

- `docs/proposta_do_projeto.md` — visão completa do problema, casos de uso, classes, estados, RNFs e priorização
- `docs/rascunho.md` — notas de análise OO
- `docs/assets/` — diagramas e arquivos-fonte (`.dbml`, `.puml`, imagens)

## Estrutura do repositório

```text
.
├── README.md
└── docs/
    ├── proposta_do_projeto.md
    ├── rascunho.md
    └── assets/
```
