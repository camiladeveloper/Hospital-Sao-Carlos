# Hospital-Sao-Carlos

# 🏥 Sistema de Gestão de Agendamentos Médicos — Hospital São Carlos

## 📋 Descrição do Projeto
O **Sistema de Agendamentos Médicos do Hospital São Carlos** é uma aplicação completa desenvolvida com **Java Spring Boot, JPA/Hibernate, MySQL e JavaScript**, cujo objetivo é facilitar o **gerenciamento de consultas médicas** por recepcionistas e médicos.  

O sistema permite **cadastrar pacientes, médicos e consultas**, **alterar o status de atendimento** e **visualizar um painel dinâmico de agendamentos**.

---

## ⚙️ Tecnologias Utilizadas

### 🧠 Backend
- Java 17+
- Spring Boot
  - Spring Web
  - Spring Data JPA
  - Spring Validation
- Hibernate
- MySQL
- Maven
- Swagger / OpenAPI (para documentação da API)

### 🎨 Frontend
- HTML5
- CSS3
- JavaScript (fetch API)
- Bootstrap (opcional)

### 🧾 Outras Ferramentas
- Git / GitHub
- Diagrama ER
- IDE: Eclipse / VS Code

---

## 🧱 Arquitetura do Sistema

O projeto segue o padrão **Camadas MVC (Model-View-Controller)**:

Controller → Service → Repository → Database


📌 **Camadas principais:**
- **Model (Entidades)**: Paciente, Consulta, Médico, Especialidade, Status, Funcionário.  
- **Repository**: Interfaces que estendem `JpaRepository`.
- **Service**: Contém a lógica de negócio (regras de status, filtros, etc).
- **Controller**: Expõe endpoints REST para consumo pelo front-end.

---

## 🗄️ Modelagem de Dados

### Entidades Principais
- **Paciente**
  - id, nome, cpf, telefone, dataNascimento, endereço
- **Consulta**
  - id, dataHora, paciente, médico, especialidade, status, criadoPor
- **Médico**
  - id, nome, crm, especialidade, telefone
- **Especialidade**
  - id, nome
- **StatusAtendimento**
  - id, nome (Agendada, Aguardando, Em Atendimento, Concluída, Cancelada)
- **Funcionário**
  - id, nome, cpf, cargo, telefone

📎 O diagrama completo está no diretório `/docs/diagrama-ER.png`.

---

## 🚀 Como Executar o Projeto

### 🔧 Pré-requisitos
- JDK 17+
- Maven 3.8+
- MySQL 8.0+
- Git

### ⚙️ Configuração do Banco de Dados

Crie o banco:
`CREATE DATABASE hospital_sao_carlos;`

Edite o arquivo src/main/resources/application.properties:

`spring.datasource.url=jdbc:mysql://localhost:3306/hospital_sao_carlos
spring.datasource.username=root
spring.datasource.password=senha
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true`

####▶️ Executando a Aplicação

1 - Clone o repositório:
`git clone https://github.com/seu-usuario/hospital-sao-carlos.git`

2 - Acesse o diretório:
`cd hospital-sao-carlos`

3 - Execute com Maven:
`mvn spring-boot:run`

4 - Acesse a API:
`http://localhost:8080`

🔗 Endpoints Principais
| Método   | Endpoint                       | Descrição                      |
| -------- | ------------------------------ | ------------------------------ |
| `GET`    | `/consultas`                   | Lista todas as consultas       |
| `GET`    | `/consultas?status=Aguardando` | Filtra por status              |
| `GET`    | `/consultas?data=2025-10-10`   | Filtra por data                |
| `POST`   | `/consultas`                   | Cadastra nova consulta         |
| `PUT`    | `/consultas/{id}`              | Atualiza dados da consulta     |
| `PATCH`  | `/consultas/{id}/status`       | Altera o status de atendimento |
| `DELETE` | `/consultas/{id}`              | Cancela uma consulta           |
| `GET`    | `/pacientes`                   | Lista pacientes                |
| `POST`   | `/pacientes`                   | Cadastra paciente              |
| `GET`    | `/especialidades`              | Lista especialidades médicas   |

Após iniciar o projeto, acesse:
http://localhost:8080/

🖥️ Frontend

O frontend é uma interface simples em HTML + JS que consome a API REST.

📍 Principais páginas:

- /frontend/index.html → Painel de Consultas

- /frontend/novo-agendamento.html → Cadastro de nova consulta

- /frontend/pacientes.html → Cadastro e listagem de pacientes

Funcionalidades:

- Exibe consultas em tabela dinâmica.

- Filtra por data e status.

- Botões de ação:

  - Check-in: muda status para "Aguardando"

  - Finalizar: muda para "Concluída"

  - Cancelar: muda para "Cancelada"

🧠 Regras de Negócio

- Uma consulta deve estar vinculada a um paciente e a um médico.

- Não pode haver duas consultas no mesmo horário para o mesmo médico.

- O status de atendimento segue o fluxo:

  Agendada → Aguardando → Em Atendimento → Concluída / Cancelada

- Todos os campos obrigatórios devem ser validados antes do cadastro.

🧪 Testes

- Testes unitários com Spring Boot Test.


diagrama-ER.png → Diagrama do banco

arquitetura.png → Camadas da aplicação

manual-usuario.pdf → Manual do painel de consultas

requisitos.md → Lista de requisitos implementados

👥 Autores

Hospital São Carlos – Projeto Final do Curso Java com Spring Boot
Desenvolvido por: Camila Ribeiro Rodrigues
Instrutor: Carlos Eduardo
Ano: 2025
