# Criar um CRUD para a API Restful
- **Tema**: Fundamentos de Nest (API Restful)
- **Subtema**: Fundamentos - Criar um CRUD (create, retrieve, update, delete)

## Objetivos
- Criar um novo projeto javascript para uma API Restful usando o script [nest](https://nestjs.com/)


## Sumário
1. [Baixar o projeto inicial](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#1-baixar-o-projeto-inicial)
2. [Instalar as bibliotecas](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#2-instalar-as-bibliotecas)
3. [Criar CRUD](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#3-criar-crud)
4. [Modificar a entidade](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#4-modificar-a-entidade)
5. [Modificar o DTO de Criação](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#5-modificar-o-dto-de-cria%C3%A7%C3%A3o)
6. [Configurar o acesso ao SQLite](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#6-configurar-o-acesso-ao-sqlite)
7. [Programar para criar nova tarefa com o endpoint /tarefas e método POST](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#7-programar-para-criar-nova-tarefa-com-o-endpoint-tarefas-e-m%C3%A9todo-post)
8. [Programar para recuperar todas as tarefas com o endpoint /tarefas e método GET](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#8-programar-para-recuperar-todas-as-tarefas-com-o-endpoint-tarefas-e-m%C3%A9todo-get)
9. [Programar para recuperar uma tarefa com o endpoint /tarefas/:id e método GET](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#9-programar-para-recuperar-uma-tarefa-com-o-endpoint-tarefasid-e-m%C3%A9todo-get)
10. [Programar para apagar uma tarefa com o endpoint /tarefas/:id e método DELETE](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#9-programar-para-recuperar-uma-tarefa-com-o-endpoint-tarefasid-e-m%C3%A9todo-get)
11. [Programar para atualizar o texto de uma tarefa com o endpoint /tarefas/:id e o método PUT](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#11-programar-para-atualizar-o-texto-de-uma-tarefa-com-o-endpoint-tarefasid-e-o-m%C3%A9todo-put)
12. [Programar para finalizar uma tarefa com o endpoint /tarefas/:id/finalizar e o método PUT](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#12-programar-para-finalizar-uma-tarefa-com-o-endpoint-tarefasidfinalizar-e-o-m%C3%A9todo-put)
13. [Programar para finalizar uma tarefa com o endpoint /tarefas/:id/abrir e o método PUT](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/02-crud.md#13-programar-para-finalizar-uma-tarefa-com-o-endpoint-tarefasidabrir-e-o-m%C3%A9todo-put)

## Links
- [Criando o primeiro CRUD com NestJS](https://www.treinaweb.com.br/blog/criando-o-primeiro-crud-com-nestjs)
- Typescript
  - Anotações [decoradores](https://www.typescriptlang.org/docs/handbook/decorators.html#decorators)
  - [Genéricos](https://www.typescriptlang.org/docs/handbook/2/generics.html)
- TypeORM
  - [Opção para declarar entidades](https://typeorm.io/entities#column-options)



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
1. Abrir um segundo terminal.
2. Executar o comando `nest` para gerar código `npx nest generate resource tarefas --no-spec`
3. Observar no primeiro terminal se atualizou _endpoints_

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

**terminal de monitoramento da API**
```console
[11:33:53] File change detected. Starting incremental compilation...

[11:33:53] Found 0 errors. Watching for file changes.

[Nest] 15876  - 31/07/2023, 11:33:54     LOG [NestFactory] Starting Nest application...
[Nest] 15876  - 31/07/2023, 11:33:54     LOG [InstanceLoader] AppModule dependencies initialized +10ms
[Nest] 15876  - 31/07/2023, 11:33:54     LOG [InstanceLoader] TarefasModule dependencies initialized +0ms
[Nest] 15876  - 31/07/2023, 11:33:54     LOG [RoutesResolver] AppController {/}: +9ms
[Nest] 15876  - 31/07/2023, 11:33:54     LOG [RouterExplorer] Mapped {/, GET} route +2ms
[Nest] 15876  - 31/07/2023, 11:33:54     LOG [RoutesResolver] TarefasController {/tarefas}: +0ms
[Nest] 15876  - 31/07/2023, 11:33:54     LOG [RouterExplorer] Mapped {/tarefas, POST} route +1ms
[Nest] 15876  - 31/07/2023, 11:33:54     LOG [RouterExplorer] Mapped {/tarefas, GET} route +0ms
[Nest] 15876  - 31/07/2023, 11:33:54     LOG [RouterExplorer] Mapped {/tarefas/:id, GET} route +1ms
[Nest] 15876  - 31/07/2023, 11:33:54     LOG [RouterExplorer] Mapped {/tarefas/:id, PATCH} route +0ms
[Nest] 15876  - 31/07/2023, 11:33:54     LOG [RouterExplorer] Mapped {/tarefas/:id, DELETE} route +0ms
[Nest] 15876  - 31/07/2023, 11:33:54     LOG [NestApplication] Nest application successfully started +6ms

```



# 4. Modificar a entidade
1. Editar o arquivo `./src/tarefas/entities/tarefa.entity.ts`
2. Adicione os atributos e suas anotações na classe `Tarefa`

arquivo `./src/tarefas/entities/tarefa.entity.ts`
```typescript
import { Column, Entity, PrimaryGeneratedColumn } from 'typeorm';

@Entity()
export class Tarefa {
  @PrimaryGeneratedColumn('increment')
  id: number;

  @Column()
  titulo: string;

  @Column({ default: false })
  feito: boolean;
}

```



# 5. Modificar o DTO de Criação
1. Editar o arquivo `./src/tarefas/dto/create-tarefa.dto.ts`
2. Adicione os atributos ao DTO `Tarefa`

arquivo `./src/tarefas/dto/create-tarefa.dto.ts`
```typescript
export class CreateTarefaDto {
  titulo: string;
}

```


# 6. Configurar o acesso ao SQLite
1. Criar o arquivo `./src/ormconfig.ts` para configurar o acesso ao mecanismo de repositório.
2. Modificar o arquivo `./src/app.module.ts` para usar a configuração de acesso ao repositório.
3. Verificar a saída do primeiro terminal que excuta o terminal.

arquivo `./src/ormconfig.ts`
```typescript
import { DataSourceOptions } from 'typeorm';

export const config: DataSourceOptions = {
  type: 'sqlite',
  database: '.db/database.sqlite',
  synchronize: true,
  dropSchema: true,
  entities: [__dirname + '/**/entities/*.entity{.ts,.js}'],
};

```

arquivo `./src/app.module.ts`
```typescript
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';
import { TarefasModule } from './tarefas/tarefas.module';
import { TypeOrmModule } from '@nestjs/typeorm';
import { config } from './ormconfig';

@Module({
  imports: [TarefasModule, TypeOrmModule.forRoot(config)],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}

```

```console
[17:40:02] File change detected. Starting incremental compilation...

[17:40:04] Found 0 errors. Watching for file changes.

[Nest] 22524  - 31/07/2023, 17:40:05     LOG [NestFactory] Starting Nest application...
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [InstanceLoader] TypeOrmModule dependencies initialized +99ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [InstanceLoader] AppModule dependencies initialized +1ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [InstanceLoader] TarefasModule dependencies initialized +0ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [InstanceLoader] TypeOrmCoreModule dependencies initialized +137ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [RoutesResolver] AppController {/}: +12ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [RouterExplorer] Mapped {/, GET} route +2ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [RoutesResolver] TarefasController {/tarefas}: +0ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [RouterExplorer] Mapped {/tarefas, POST} route +1ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [RouterExplorer] Mapped {/tarefas, GET} route +1ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [RouterExplorer] Mapped {/tarefas/:id, GET} route +0ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [RouterExplorer] Mapped {/tarefas/:id, PATCH} route +0ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [RouterExplorer] Mapped {/tarefas/:id, DELETE} route +1ms
[Nest] 22524  - 31/07/2023, 17:40:05     LOG [NestApplication] Nest application successfully started +2ms

```


# 7. Programar para criar nova tarefa com o endpoint /tarefas e método POST
1. Acessar o endpoint `http://localhost:3000/tarefas` com o método POST. O retorno esperado é o texto `This action adds a new tarefa`.
2. Modificar o arquivo `./src/tarefas/tarefa.module.ts`, para configurar o repositório com a entidade `Tarefa`.
3. Modificar o arquivo `./src/tarefas/tarefa.service.ts`, para ter acesso ao repositório e ter acesso a persistência.
4. 

arquivo `./src/tarefas/tarefa.module.ts`
```typescript
import { Module } from '@nestjs/common';
import { TarefasService } from './tarefas.service';
import { TarefasController } from './tarefas.controller';
import { TypeOrmModule } from '@nestjs/typeorm';
import { Tarefa } from './entities/tarefa.entity';

@Module({
  imports: [TypeOrmModule.forFeature([Tarefa])],
  controllers: [TarefasController],
  providers: [TarefasService],
})
export class TarefasModule {}

```

arquivo `./src/tarefas/tarefa.module.ts`
```typescript

```

# 8. Programar para recuperar todas as tarefas com o endpoint /tarefas e método GET



# 9. Programar para recuperar uma tarefa com o endpoint /tarefas/:id e método GET




# 10. Programar para apagar uma tarefa com o endpoint /tarefas/:id e método DELETE




# 11. Programar para atualizar o texto de uma tarefa com o endpoint /tarefas/:id e o método PUT




# 12. Programar para finalizar uma tarefa com o endpoint /tarefas/:id/finalizar e o método PUT




# 13. Programar para finalizar uma tarefa com o endpoint /tarefas/:id/abrir e o método PUT

