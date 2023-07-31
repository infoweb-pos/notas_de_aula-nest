# Criar um CRUD para a API Restful
- **Tema**: Fundamentos de Nest (API Restful)
- **Subtema**: Fundamentos - Criar um CRUD (create, retrieve, update, delete)

## Objetivos
- Criar um novo projeto javascript para uma API Restful usando o script [nest](https://nestjs.com/)


## Sumário
1. Baixar o projeto inicial
2. Instalar as bibliotecas
3. Executar a API Restful
4. Criar CRUD
5. Modificar a entidade
6. Modificar o DTO 

## Links
- [Criando o primeiro CRUD com NestJS](https://www.treinaweb.com.br/blog/criando-o-primeiro-crud-com-nestjs)
- Typescript
  - Anotações [decoradores](https://www.typescriptlang.org/docs/handbook/decorators.html#decorators)
  - [Genéricos](https://www.typescriptlang.org/docs/handbook/2/generics.html)

# 1. Baixar o projeto inicial
1. Baixar o projeto [zip](https://github.com/infoweb-pos/2023-notas_de_aula-nest/archive/refs/tags/01-projeto-novo.zip).
2. Descompactar em uma pasta do seu computador.

# 2. Instalar as bibliotecas
1. Abrir o terminal do sistema ou do VS Code.
2. Abrir a pasta do projeto.
3. Instalar as bibliotecas [TypeORM](https://typeorm.io/) e [SQLite](https://www.sqlite.org/)
4. Executar a API Restful

```console
$ cd api

[api] $ npm i @nestjs/typeorm typeorm sqlite3

[api] $ npm run start:dev
[11:27:53] Starting compilation in watch mode...

[11:27:55] Found 0 errors. Watching for file changes.

[Nest] 14960  - 31/07/2023, 11:27:56     LOG [NestFactory] Starting Nest application...
[Nest] 14960  - 31/07/2023, 11:27:56     LOG [InstanceLoader] AppModule dependencies initialized +14ms
[Nest] 14960  - 31/07/2023, 11:27:56     LOG [RoutesResolver] AppController {/}: +18ms
[Nest] 14960  - 31/07/2023, 11:27:56     LOG [RouterExplorer] Mapped {/, GET} route +3ms
[Nest] 14960  - 31/07/2023, 11:27:56     LOG [NestApplication] Nest application successfully started +2ms


```

# 3. Criar CRUD
1. Ainda no terminal

```console
[api] $ npx nest generate resource tarefas --no-spec
? What transport layer do you use? (Use arrow keys)
❯ REST API 
  GraphQL (code first) 
  GraphQL (schema first) 
  Microservice (non-HTTP) 
  WebSockets 

? What transport layer do you use? REST API
? Would you like to generate CRUD entry points? (Y/n) y

? What transport layer do you use? REST API
? Would you like to generate CRUD entry points? Yes
CREATE src/tarefas/tarefas.controller.ts (936 bytes)
CREATE src/tarefas/tarefas.module.ts (261 bytes)
CREATE src/tarefas/tarefas.service.ts (637 bytes)
CREATE src/tarefas/dto/create-tarefa.dto.ts (32 bytes)
CREATE src/tarefas/dto/update-tarefa.dto.ts (177 bytes)
CREATE src/tarefas/entities/tarefa.entity.ts (23 bytes)
UPDATE package.json (2066 bytes)
UPDATE src/app.module.ts (320 bytes)
✔ Packages installed successfully.

[api] $ 
```


