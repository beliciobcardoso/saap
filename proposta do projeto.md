# Projeto SAAP (Sistema de Agendamento de Atendimentos Profissionais)

## Introdução

- **Contextos:**
  - Clínicas
  - Consultórios
  - Serviços especializados

## Visão do Problema

- **Situação:**
  - Muitos atendimentos ainda são gerenciados de forma manual ou pouco estruturada.
- **Problemas comuns:**
  - Conflito de horários
  - Falta de controle de agenda
  - Dificuldade de gestão de atendimentos

## Objetivo

O Projeto SAAP tem como objetivo estruturar um sistema de agendamento de atendimentos profissionais que reduza conflitos de horários, melhore o controle da agenda e apoie a gestão dos atendimentos de forma organizada e rastreável.

## Escopo

O escopo inicial contempla o cadastro de entidades principais, o agendamento e o gerenciamento do ciclo de vida dos atendimentos. O desenvolvimento será evolutivo ao longo da disciplina, com refinamento dos artefatos de análise, projeto e arquitetura.

## Funcionalidades Iniciais

**O sistema deverá permitir:**

- Cadastro de pacientes
- Cadastro de profissionais
- Cadastro de serviços (consulta, exame, etc.)
- Agendamento de atendimentos
- Cancelamento e remarcação
- Controle de horários disponíveis

## Visão do Projeto

**O que vamos construir ao longo da disciplina:**

- Casos de uso
- Diagrama de classes (conceitual -> projeto)
- Diagramas de sequência
- Diagrama de estados
- Arquitetura do sistema

## Dinâmica

- **5 funcionalidades adicionais (proposta inicial):**
  - Notificações e Lembretes Automáticos: Envio de confirmações via E-mail ou WhatsApp para reduzir faltas.
  - Prontuário Eletrônico / Histórico de Atendimento: Registro das notas e observações feitas pelo profissional durante cada sessão.
  - Gestão de Convênios e Planos: Configuração de diferentes formas de pagamento e cobertura para os atendimentos.
  - Confirmação de presença pelo paciente: Reduz drasticamente o no-show (faltas) e otimiza o tempo do profissional.
  - Lista de Espera Inteligente: Sistema que notifica pacientes interessados quando surge uma desistência em um horário concorrido.
  - Histórico de atendimentos por paciente: Fundamental para a continuidade do cuidado e organização clínica.
  - Relatórios de Desempenho: Visão analítica para o administrador (ex: taxa de cancelamento, faturamento por período e serviços mais procurados).
- **2 ou mais atores do sistema (proposta inicial):**
  - Paciente/Cliente: Quem busca o serviço e solicita o agendamento.
  - Profissional (Médico/Consultor): Quem presta o serviço e possui a agenda.
  - Recepcionista/Administrador: Responsável por gerenciar as agendas de múltiplos profissionais, cadastros e fluxos financeiros.

## Critérios de Sucesso e Entregáveis

- Casos de uso documentados para os atores definidos
- Diagrama de classes conceitual evoluído para projeto
- Diagramas de sequência dos fluxos principais
- Diagrama de estados de uma entidade central do domínio
- Visão arquitetural do sistema com justificativas
- Protótipo funcional cobrindo as funcionalidades iniciais

## Próxima Aula

- **Transformar nossas ideias em:**
  - Casos de uso
  - Classes conceituais
  - Primeiros diagramas UML
