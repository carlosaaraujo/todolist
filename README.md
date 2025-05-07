# ToDo List API

API REST para gerenciamento de tarefas (ToDo List), desenvolvida em Java com Spring Boot.

## Funcionalidades

- Cadastro de usuários com senha criptografada (BCrypt)
- Autenticação básica (Basic Auth) para operações de tarefas
- CRUD de tarefas, associadas a usuários
- Validações de datas e permissões
- Banco de dados em memória (H2) para desenvolvimento/testes

## Estrutura do Projeto

```
src/
 ├── main/
 │    ├── java/br/com/carlosaaraujo/todolist/
 │    │     ├── TodolistApplication.java
 │    │     ├── errors/ExceptionHandlerController.java
 │    │     ├── filter/FilterTaskAuth.java
 │    │     ├── task/
 │    │     │     ├── TaskController.java
 │    │     │     ├── TaskModel.java
 │    │     │     └── ITaskRepository.java
 │    │     ├── user/
 │    │     │     ├── UserController.java
 │    │     │     ├── UserModel.java
 │    │     │     └── IUserRepository.java
 │    │     └── utils/Utils.java
 │    └── resources/
 │          ├── application.properties
 │          ├── static/
 │          └── templates/
 └── test/
      └── java/br/com/carlosaaraujo/todolist/TodolistApplicationTests.java
```

## Requisitos

- Java 17+
- Maven 3.9+
- (Opcional) Docker

## Como executar

### Usando Maven

```sh
./mvnw spring-boot:run
```

A aplicação estará disponível em: [http://localhost:8080](http://localhost:8080)

### Usando Docker

```sh
docker build -t todolist .
docker run -p 8080:8080 todolist
```

## Endpoints principais

### Usuários

- `POST /users/`  
  Cria um novo usuário.  
  **Body:**  
  ```json
  {
    "username": "usuario",
    "name": "Nome do Usuário",
    "password": "senha"
  }
  ```

### Tarefas (requer autenticação Basic Auth)

- `POST /tasks/`  
  Cria uma tarefa.

- `GET /tasks/`  
  Lista tarefas do usuário autenticado.

- `PUT /tasks/{id}`  
  Atualiza uma tarefa do usuário autenticado.

## Autenticação

Para acessar os endpoints de tarefas, utilize o cabeçalho HTTP:

```
Authorization: Basic base64(username:password)
```

## Banco de Dados

- H2 em memória (acessível em `/h2-console` durante execução)
- Configurações em `src/main/resources/application.properties`



---
