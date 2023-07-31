# Criar um projeto novo, executar e ver rotas (endpoints)
- **Tema**: Fundamentos de Nest (API Restful)
- **Subtema**: Fundamentos - Criar um novo projeto

## Objetivos
- Criar um novo projeto javascript para uma API Restful usando o script [nest](https://nestjs.com/)


## Sumário
1. [Criar um projeto novo](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/01-novo_projeto.md#1-criar-um-projeto-novo)
2. [Executar a API Restful](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/01-novo_projeto.md#2-executar-a-api-restful)
3. [Testar a API Restful](https://github.com/infoweb-pos/notas_de_aula-nest/blob/main/fundamentos/01-novo_projeto.md#3-testar-a-api-restful)


# 1. Criar um projeto novo
1. Instalar o `node`, e `vs code`
2. Abrir o terminal de comandos
3. Executar o comando `npx @nestjs/cli new api`

```console
$ npx @nestjs/cli new api
Need to install the following packages:
  @nestjs/cli@10.1.11
Ok to proceed? (y) y
⚡  We will scaffold your app in a few seconds..

? Which package manager would you ❤️  to use? 
❯ npm 
  yarn 
  pnpm 

? Which package manager would you ❤️  to use? npm
CREATE projeto/.eslintrc.js (663 bytes)
CREATE projeto/.prettierrc (51 bytes)
CREATE projeto/README.md (3340 bytes)
CREATE projeto/nest-cli.json (171 bytes)
CREATE projeto/package.json (1952 bytes)
CREATE projeto/tsconfig.build.json (97 bytes)
CREATE projeto/tsconfig.json (546 bytes)
CREATE projeto/src/app.controller.spec.ts (617 bytes)
CREATE projeto/src/app.controller.ts (274 bytes)
CREATE projeto/src/app.module.ts (249 bytes)
CREATE projeto/src/app.service.ts (142 bytes)
CREATE projeto/src/main.ts (208 bytes)
CREATE projeto/test/app.e2e-spec.ts (630 bytes)
CREATE projeto/test/jest-e2e.json (183 bytes)

✔ Installation in progress... ☕

🚀  Successfully created project projeto
👉  Get started with the following commands:

$ cd apinpm 
$ npm run start

                                         
                          Thanks for installing Nest 🙏
                 Please consider donating to our open collective
                        to help us maintain this package.
                                         
                                         
               🍷  Donate: https://opencollective.com/nest

$ 
```

# 2. Executar a API Restful
1. Ainda no mesmo terminal, entar na pasta (diretório) `cd api`
2. Executar a API Restful `npm run start:dev`

```console
$ cd api
[api] $ npm run start:dev

[08:21:25] Starting compilation in watch mode...

[08:21:28] Found 0 errors. Watching for file changes.

[Nest] 129393  - 31/07/2023, 08:21:28     LOG [NestFactory] Starting Nest application...
[Nest] 129393  - 31/07/2023, 08:21:28     LOG [InstanceLoader] AppModule dependencies initialized +15ms
[Nest] 129393  - 31/07/2023, 08:21:28     LOG [RoutesResolver] AppController {/}: +26ms
[Nest] 129393  - 31/07/2023, 08:21:28     LOG [RouterExplorer] Mapped {/, GET} route +4ms
[Nest] 129393  - 31/07/2023, 08:21:28     LOG [NestApplication] Nest application successfully started +8ms


```

# 3. Testar a API Restful
1. Abrir outro terminal
2. Executar o comando `curl --verbose localhost:3000`
3. Modificar o retorno do endpoint `\`
4. Executar novamente o comando `curl --verbose localhost:3000`

```console
[api] $ curl --verbose localhost:3000
*   Trying 127.0.0.1:3000...
* Connected to localhost (127.0.0.1) port 3000 (#0)
> GET / HTTP/1.1
> Host: localhost:3000
> User-Agent: curl/8.0.1
> Accept: */*
> 
< HTTP/1.1 200 OK
< X-Powered-By: Express
< Content-Type: text/html; charset=utf-8
< Content-Length: 12
< ETag: W/"c-Lve95gjOVATpfV8EL5X4nxwjKHE"
< Date: Mon, 31 Jul 2023 11:21:51 GMT
< Connection: keep-alive
< Keep-Alive: timeout=5
< 
* Connection #0 to host localhost left intact
Hello World!

[api] $ curl --verbose localhost:3000
*   Trying 127.0.0.1:3000...
* Connected to localhost (127.0.0.1) port 3000 (#0)
> GET / HTTP/1.1
> Host: localhost:3000
> User-Agent: curl/8.0.1
> Accept: */*
> 
< HTTP/1.1 200 OK
< X-Powered-By: Express
< Content-Type: application/json; charset=utf-8
< Content-Length: 46
< ETag: W/"2e-iFQ3MlL8UOhhq9nI72jwtS/Fiyg"
< Date: Mon, 31 Jul 2023 11:26:15 GMT
< Connection: keep-alive
< Keep-Alive: timeout=5
< 
* Connection #0 to host localhost left intact
{"estado":"ok","mensagem":"API Retuful no ar"}

[api] $ 
```
