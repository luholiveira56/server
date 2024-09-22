# Projeto in.orbit

> 💡 **Definição**: Controle de metas pessoais.
> 💡 **Funcionamento**: Ao abrir o aplicativo irá mostrar que não tem nenhuma meta cadastrada.
    Clicando em *Cadastrar Meta* irá mostrar um menu lateral para indicar *Qual atividade/meta* irá querer cumprir e *Quantas vezes na semana* irá querer cumprir.
    Quanto mais vezes selecionar as atividades/metas da semana mais vezes irá precisar cumprir na semana para atingir objetivo de 100%.
    Na sequencia será mostrado uma visualização semanal no topo como 05 a 12 de Agosto, seguido por uma barra de progresso com tantas metas completadas:
    Quando não tiver atividades/metas completadas irá mostrar uma lista que deverá completar, então ao clicar em alguma irá registrar que completou a meta.
    QUando tiver atividades/metas completadas irá mostrar na lista da semana que completou junto com o nome da meta e o horario, então conforme a quantidade de vezes selecionada para cumprir como *Acordar Cedo 2x na semana* e ter cumprir ontem e hoje, irá mostrar o nome da meta visualmente desabilitada não precisando completar mais, com isso, a barra de progresso fica totalmente corelacionada com o *Numero de vezes que tem que completar as metas X Quantas metas ja completou*. 
> 💡 **Foco do Projeto**: 1º - Back-end: SQL.
                          2º - Front-end: - CSS + Dados e Formularios (Como fazer o consumo da API)

# Construir Back-end

 - Aplicação: Node.js
 - Tecnologias: Fastify, Zod, Docker Compose, Drizzle ORM
 - Criação: Schema e Seed do Banco de Dados
 - Features do projeto: Metas, Metas Pendentes e Complementar Metas.
 - Ferramenta: Biome

# Configuração

 - Typescript: no arquivo *tsconfig.json* criado pelo comando *npx tsc --init* quando não suber o que incluir,
 buscar no google *tsconfig bases* e acessar o github e encontrar pela versão do *Node* usado clicar no package e copia a estrutura no *The tsconfig.json*
 - Para acessar o link http://localhost:3333/ rodar o comando *npm run dev* 

# Fases da resolução de um problema

Caso o erro abaixo aconteça na tentativa de:

 - rodar no terminal o comando: npx drizzle-kit studio
 - acessar a url https://local.drizzle.studio e não carregar as tabelas
 - nem retornar status 200 no Postman ao clicar no Send no http://localhost:3333/

<!-- AggregateError [ECONNREFUSED]: 
    at internalConnectMultiple (node:net:1118:18)
    at afterConnectMultiple (node:net:1685:7)
    at TCPConnectWrap.callbackTrampoline (node:internal/async_hooks:130:17) {
  code: 'ECONNREFUSED',
  [errors]: [
    Error: connect ECONNREFUSED ::1:5432
        at createConnectionError (node:net:1648:14)
        at afterConnectMultiple (node:net:1678:16)
        at TCPConnectWrap.callbackTrampoline (node:internal/async_hooks:130:17) {
      errno: -4078,
      code: 'ECONNREFUSED',
      syscall: 'connect',
      address: '::1',
      port: 5432
    },
    Error: connect ECONNREFUSED 127.0.0.1:5432
        at createConnectionError (node:net:1648:14)
        at afterConnectMultiple (node:net:1678:16)
        at TCPConnectWrap.callbackTrampoline (node:internal/async_hooks:130:17) {
      errno: -4078,
      code: 'ECONNREFUSED',
      syscall: 'connect',
      address: '127.0.0.1',
      port: 5432
    }
  ]
} -->

Rodar no terminal do projeto Server referente ao arquivo docker-compose.yml o comando:

 - docker compose up -d (irá fazer o processo de rodar o banco de dados baixando a imagem do bitnami/postgresql e rodar ela localmente)
 - docker ps (irá mostrar o banco rodando)
 - docker ps -a (caso o banco não esteja rodando usar esse comando para encontrar o CONTAINER e pegar o ID)
 - docker logs CONTAINER ID (mostrará todos os logs e o ultimo deverá ser do exemplo, informando que está rodando, caso contrario poderá ser alguma configuração errada. exemplo: 2024-09-16 01:28:27.847 GMT [1] LOG:  database system is ready to accept connections)
 - comando para rodar o servidor: npm run dev

Caso seja inserido um botão na aplicação para navegar nas semanas, para verificar se o usuario completou 100% das metas na semana anterior:

 - implementar SQL personalizado utilizando WITH Queries (Common Table Expressions).
 - permite escrever queries auxiliares para serem usadas em uma querie maior, com a ideia de repartir uma querie muito complexa em varios pedaços em queries mais simples/menores, mas sendo executadas ao mesmo tempo numa instrução ao banco de dados.