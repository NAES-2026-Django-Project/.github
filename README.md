# 🚀 Mini-Jira: Sistema de Gestão de Projetos e Outsourcing

Este projeto foi desenvolvido como trabalho prático para a disciplina de **Novas Aplicações em Engenharia de Software**. O objetivo é gerenciar o ciclo de vida de projetos de desenvolvimento, desde a criação de equipes até o acompanhamento de tarefas via quadros Kanban, utilizando uma arquitetura desacoplada (Decoupled Architecture).

## 📌 Escopo do Projeto

O sistema permite que administradores gerenciem recursos humanos (usuários e equipes), enquanto gerentes e desenvolvedores colaboram em projetos específicos através de uma interface intuitiva e regras de negócio rigorosas.

### 🔑 Níveis de Acesso (Roles)

  * **Admin:** Controle total sobre usuários, equipes e parametrizações globais.
  * **Manager:** Responsável pela criação de projetos, quadros Kanban e gestão de sua equipe vinculada.
  * **Developer:** Focado na execução de tarefas e registro de logs de atividade.

### ⚙️ Funcionalidades Principais

  * **Gestão de Equipes:** Vínculo estrito de 1 Manager para N Developers.
  * **Gestão de Projetos:** Criação de projetos com obrigatoriedade de alocação de 1 Manager e exatamente 4 Developers pertencentes à equipe do gestor.
  * **Kanban Board:** Interface interativa com suporte a *Drag and Drop* para movimentação de tarefas entre colunas (To Do, Doing, Done).
  * **Task Logging:** Histórico detalhado de progresso em cada tarefa.
  * **Autenticação Stateless:** Segurança via JWT (JSON Web Token).

-----

## 🛠 Stacks de Desenvolvimento

O projeto utiliza tecnologias modernas de mercado para garantir escalabilidade e performance.

### **Backend (API)**

  * **Python 3.12+** & **Django 5.0**
  * **Django REST Framework (DRF):** Construção de endpoints robustos.
  * **SimpleJWT:** Implementação de autenticação stateless.
  * **PostgreSQL:** Banco de dados relacional para produção (ou SQLite para desenvolvimento).

### **Frontend (SPA)**

  * **Angular 17+:** Framework principal para uma experiência de usuário fluida.
  * **Bootstrap 5:** Estilização responsiva e componentes de interface.
  * **Angular CDK (Drag and Drop):** Manipulação visual das tarefas no Kanban.
  * **RxJS:** Gerenciamento de estados e chamadas assíncronas.

-----

## 📊 Modelagem de Dados (MER)

O banco de dados foi estruturado seguindo os princípios da 3ª Forma Normal, garantindo integridade referencial:

  * `user_profile`: Extensão do usuário Django com o campo `role`.
  * `team`: Agrupamento de desenvolvedores sob a liderança de um manager.
  * `project`: Entidade central que vincula a equipe ao cliente e prazos.
  * `kanban_board`: Divisão lógica de fluxo de trabalho dentro de um projeto.
  * `task`: Unidades de trabalho com atribuição individual.
  * `task_log`: Registros temporais de atividades.

-----

## 📐 Regras de Negócio Implementadas (Destaques)

1.  **Regra de Alocação:** Um projeto só pode ser salvo se houver exatamente 4 desenvolvedores selecionados e se todos eles pertencerem à equipe do gerente responsável pelo projeto.
2.  **Privacidade de Dados:** Desenvolvedores só visualizam projetos e tarefas nos quais estão explicitamente vinculados.
3.  **Movimentação de Status:** A movimentação de uma tarefa no Kanban valida se o usuário atual possui permissão de edição naquele projeto específico.

-----
