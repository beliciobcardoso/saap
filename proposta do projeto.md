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
  - **Paciente:** pessoa que solicita atendimentos, acompanha seus agendamentos e confirma presença quando necessário.
  - **Profissional de Saúde:** ator responsável por executar os atendimentos e registrar as evoluções clínicas ou operacionais relacionadas ao serviço prestado.
  - **Assistente:** ator de apoio que auxilia na preparação do atendimento, organização de materiais e suporte ao fluxo operacional da clínica.
  - **Recepcionista:** ator que centraliza o relacionamento com a agenda, realizando agendamentos, remarcações, cancelamentos e suporte aos pacientes.
  - **Administrador:** ator com maior nível de permissão, responsável por cadastros, gestão de usuários, relatórios e configuração geral do sistema.

  Esses atores podem ser modelados com generalização e especialização quando fizer sentido no diagrama, especialmente para representar comportamentos comuns, como autenticação, identificação e permissões de acesso, sem perder as diferenças de responsabilidade de cada papel.

  Isso enriquecerá a Análise Orientada a Objetos, pois demonstra uma compreensão clara de permissões e responsabilidades (RBAC (Role-Based Access Control)).

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

## Modelagem Funcional (Casos de Uso)

Nesta etapa, o foco está em descrever o que o sistema faz do ponto de vista dos atores, consolidando os principais casos de uso do SAAP.

### Identificação dos Casos de Uso

| ID   | Caso de Uso                             | Ator Principal           | Descrição Resumida                                      |
| ---- | --------------------------------------- | ------------------------ | ------------------------------------------------------- |
| UC01 | Manter Cadastro (Usuário/Paciente/Profissional) | Administrador | Incluir, alterar, excluir e consultar dados cadastrais e de acesso. |
| UC02 | Agendar Atendimento                     | Paciente / Recepcionista | Selecionar profissional, serviço e horário disponível.  |
| UC03 | Confirmar Presença                      | Paciente                 | O paciente valida que comparecerá ao horário agendado.  |
| UC04 | Registrar Atendimento                   | Profissional             | Evolução do prontuário e histórico durante a consulta.  |
| UC05 | Gerenciar Fila de Espera                | Recepcionista            | Alocar pacientes em desistências de horários.           |
| UC06 | Cancelar/Remarcar                       | Paciente / Recepcionista | Alterar o status de um agendamento existente.           |
| UC07 | Emitir Relatórios                       | Administrador            | Gerar dados de faturamento e produtividade.             |

## Modelagem Estrutural (Classes Conceituais)

Nesta etapa, o objetivo é identificar as entidades centrais do domínio e seus relacionamentos, sem entrar em detalhes técnicos de implementação.

### Entidades Core (Domínio)

- **Usuário (User):** Representa a credencial de acesso ao sistema, concentrando autenticação, status de ativação e vínculo com perfis de negócio.
- **Paciente:** Armazena dados pessoais e histórico clínico.
- **Profissional:** Contém especialidade, registro profissional e vinculação a serviços.
- **Serviço:** Define o que é oferecido, como consulta ou exame, incluindo duração e valor.
- **Agendamento:** Classe central que relaciona Paciente, Profissional e Serviço em uma data e hora específica.
- **Agenda/Grade:** Define os intervalos de tempo em que um profissional está disponível.
- **Prontuário/Histórico:** Registro cronológico de interações e observações clínicas de um paciente.
- **Convênio:** Regras de aceitação e tabelas de preços para diferentes planos.

### Relacionamentos Iniciais (Visão OO)

- Um Usuário pode estar vinculado a um perfil de Paciente, de Profissional, ou a ambos, conforme as regras de acesso da clínica.
- O vínculo entre Usuário e perfis de domínio permite aplicar RBAC com separação clara entre autenticação e regras de negócio.
- Um Agendamento possui exatamente um Paciente, um Profissional e um Serviço.
- Um Paciente pode ter N Agendamentos.
- Um Profissional possui uma Grade de horários composta por múltiplos intervalos.
- Um Agendamento possui um Status, como Pendente, Confirmado, Realizado ou Cancelado.
- Um Prontuário é associado a um Paciente e pode conter múltiplas entradas de atendimento.
- Um Convênio pode ser associado a múltiplos Pacientes e definir regras para múltiplos Serviços.

## Justificativa da Abordagem Orientada a Objetos

Esta estrutura reforça a natureza orientada a objetos do projeto, pois organiza o domínio por responsabilidades, comportamentos e regras de negócio.

### Abstração e Especialização

Ao trabalhar com os diferentes papéis do sistema, aplicamos o conceito de especialização. Embora todos compartilhem características comuns, como identificação, autenticação e permissões, o comportamento muda conforme a função exercida. Um Profissional de Saúde possui recursos ligados à execução do atendimento, enquanto um Recepcionista atua diretamente sobre a agenda e os agendamentos de terceiros.

### Encapsulamento de Regras de Negócio

A lógica de transição de estados do agendamento permanece encapsulada na entidade Agendamento. Isso evita alterações inconsistentes de status e garante que regras como confirmação, cancelamento e conclusão do atendimento sejam tratadas de forma centralizada.

### Polimorfismo de Relacionamento

A entidade Serviço pode ser associada a diferentes perfis de profissionais, como médicos, enfermeiros e assistentes, por meio de relacionamentos flexíveis. Dessa forma, o sistema pode crescer sem exigir mudanças estruturais no núcleo do agendamento.

### Entidades e Objetos de Valor

Fica claro que Usuário, Paciente e Profissional são entidades, pois possuem identidade própria e ciclo de vida independente. Já o status do agendamento funciona como um objeto de valor ou enumeração de domínio, representando o estado atual do processo em um determinado momento.

### Baixo Acoplamento com a Arquitetura

Ao manter a lógica de negócio separada da persistência e da interface, o projeto adota uma base alinhada à Clean Architecture. Isso facilita manutenção, evolução e testes, além de proteger as regras do domínio contra dependências tecnológicas.

### Reflexão para o Projeto

Essa estrutura resolve de forma consistente os problemas de conflito de horários e falta de controle mencionados na visão do problema, pois permite validar regras de negócio antes da persistência e organizar o sistema com objetos bem definidos.

## Modelagem Comportamental (Diagramas de Sequência)

Nesta etapa, o foco é descrever a interação entre os objetos do sistema para realizar um caso de uso específico, detalhando a sequência de mensagens trocadas.

### Exemplo: Caso de Uso "Agendar Atendimento" (UC02)

1. O Paciente ou Recepcionista inicia o processo de agendamento.
2. O sistema exibe a lista de profissionais disponíveis para o serviço desejado.
3. O usuário seleciona um profissional e um horário disponível.
4. O sistema valida a disponibilidade e confirma o agendamento.
5. O sistema envia uma notificação de confirmação para o paciente.

### Exemplo: Caso de Uso "Confirmar Presença" (UC03)

1. O Paciente envia a confirmação de presença para um agendamento específico.
2. O sistema atualiza o status do agendamento para "Confirmado".
3. O sistema notifica o profissional sobre a confirmação.
4. O sistema registra a confirmação no histórico do paciente.

### Exemplo: Caso de Uso "Registrar Atendimento" (UC04)

1. O Profissional inicia o registro do atendimento durante a consulta.
2. O sistema exibe o prontuário do paciente.
3. O profissional insere observações, diagnósticos e prescrições.
4. O sistema salva as informações no histórico do paciente e atualiza o status do agendamento para "Realizado".
5. O sistema gera um relatório de atendimento para o profissional e o paciente.

## Modelagem de Estados (Diagrama de Estados)

Nesta etapa, o objetivo é descrever os diferentes estados que uma entidade central do domínio pode assumir ao longo de seu ciclo de vida, bem como as transições entre esses estados.

### Exemplo: Entidade "Agendamento"

- **Estados:**
  - Pendente: O agendamento foi criado, mas ainda não foi confirmado.
  - Confirmado: O paciente confirmou que comparecerá ao atendimento.
  - Realizado: O atendimento foi concluído com sucesso.
  - Cancelado: O agendamento foi cancelado pelo paciente ou pela recepção.

- **Transições:**
  - De Pendente para Confirmado: O paciente confirma a presença.
  - De Pendente para Cancelado: O paciente ou recepção cancela o agendamento.
  - De Confirmado para Realizado: O profissional registra o atendimento como concluído.
  - De Confirmado para Cancelado: O paciente ou recepção cancela o agendamento após confirmação.
  - De Realizado para Cancelado: O atendimento é cancelado após ser registrado (ex: erro ou desistência de última hora).
  - De Cancelado para Pendente: O agendamento é reativado após um cancelamento (ex: erro ou mudança de planos).

## Diagrama de Classes Conceituais (Domínio)

Diferente do diagrama de classes de projeto, o diagrama conceitual foca em representar as entidades do domínio e seus relacionamentos de forma abstrata, sem detalhes de implementação. Seguindo o padrão de projeto SOLID, as classes são organizadas para refletir a lógica de negócio e as regras do domínio, facilitando a evolução do sistema ao longo do desenvolvimento.

### Estrutura das Entidades (Domain Layer)

Abaixo, represento como essas classes seriam estruturadas logicamente:

```prisma
// schema.prisma

datasource db {
  provider = "postgresql" // Ou o banco de sua preferência (mysql, sqlserver)
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}

model User {
  id        String   @id @default(uuid())
  email     String   @unique
  password  String   // Hash da senha (BCrypt)
  isActive  Boolean  @default(true)
  
  // Relacionamento OBRIGATÓRIO com Professional (1:1)
  // Isso permite que Admin, Recepcionista ou Médico tenham um login
  professional   Professional @relation(fields: [professionalId], references: [id])
  professionalId String       @unique

  // Relacionamento opcional com o perfil de paciente
  // Isso permite que o paciente também tenha acesso ao portal/app
  patient        Patient?      @relation(fields: [patientId], references: [id])
  patientId      String?       @unique

  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}

model Patient {
  id           String        @id @default(uuid())
  name         String
  contact      String
  // Relação inversa opcional
  user         User?
  appointments Appointment[] // 1:N Relationship
  createdAt    DateTime      @default(now())
  updatedAt    DateTime      @updatedAt
}

model Professional {
  id             String            @id @default(uuid())
  name           String
  // Opcional para profissionais sem conselho de classe (ex: Assistentes)
  licenseNumber  String?           @unique // Equivalent to "registroProfissional"
  // Define o papel do profissional no sistema
  role           ProfessionalRole  @default(PRACTITIONER)
  specialty      String?
  
  // Relação inversa obrigatória
  user           User
  services       Service[]         // Relationship N:N (Many professionals can do the same service)
  appointments   Appointment[]
  createdAt      DateTime          @default(now())
  updatedAt      DateTime          @updatedAt
}

model Service {
  id               String          @id @default(uuid())
  description      String          // Ex: "Consultation", "Exam" 
  durationMinutes  Int
  price            Decimal         @db.Decimal(10, 2)
  professionals    Professional[]  // M:N Relationship
  appointments     Appointment[]
  createdAt        DateTime         @default(now())
  updatedAt        DateTime         @updatedAt
}

model Appointment {
  id             String            @id @default(uuid())
  scheduledAt    DateTime          // Equivalent to "dataHora" 
  status         AppointmentStatus @default(PENDING)
  
  // Relationships
  patient        Patient           @relation(fields: [patientId], references: [id])
  patientId      String
  
  professional   Professional      @relation(fields: [professionalId], references: [id])
  professionalId String
  
  service        Service           @relation(fields: [serviceId], references: [id])
  serviceId      String

  createdAt      DateTime          @default(now())
  updatedAt      DateTime          @updatedAt
}

enum AppointmentStatus {
  PENDING
  CONFIRMED
  COMPLETED
  CANCELLED
}

enum ProfessionalRole {
  PRACTITIONER    // Médico, Fisioterapeuta, etc.
  NURSE           // Enfermeira
  ASSISTANT       // Assistente de instrumentação
  ADMINISTRATOR   // Administrador da clínica
  RECEPTIONIST    // Recepcionista
}
```
