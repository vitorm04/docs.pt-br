---
title: "Define o seu aplicativo de multi-contêiner com docker compose.yml"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Define o seu aplicativo de multi-contêiner com docker compose.yml"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c5d4d2c9fb9fbb595f6f6ea195247474f353a32f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Define o seu aplicativo de multi-contêiner com docker compose.yml 

Neste guia, o [docker compose.yml](https://docs.docker.com/compose/compose-file/) arquivo foi apresentado na seção [etapa 4. Definir os serviços no docker compose.yml ao compilar um aplicativo de multi-contêiner de Docker](#step4_define_svcs_in_docker_compose_yml). No entanto, existem outras maneiras de usar os arquivos de docker-compose que vale a pena explorar mais detalhadamente.

Por exemplo, você pode descrever explicitamente como você deseja implantar seu aplicativo de multi-contêiner no arquivo compose.yml docker. Opcionalmente, você também pode descrever como você vai criar imagens personalizadas do Docker. (As imagens do Docker personalizados também podem ser criadas com a CLI do Docker.)

Basicamente, você define cada um dos contêineres que você deseja implantar além de certas características para cada implantação de contêiner. Uma vez que um arquivo de descrição do multi-contêiner implantação, você pode implantar a solução completa em uma única ação orquestrada pelo [compor docker backup](https://docs.docker.com/compose/overview/) comando CLI, ou você pode implantá-lo transparente do Visual Studio. Caso contrário, você precisa usar a CLI do Docker para implantar por container em várias etapas, usando o comando docker run na linha de comando. Portanto, cada serviço definido no docker compose.yml deve especificar exatamente uma imagem ou de compilação. Outras chaves são opcionais e são análogos às sua contrapartes de linha de comando de execução de docker.

O código a seguir YAML é a definição de um arquivo de possíveis global mas único docker-compose.yml para o exemplo eShopOnContainers. Isso não é o arquivo real docker-compose eShopOnContainers. Em vez disso, é uma versão simplificada e consolidada em um único arquivo, que não é a melhor maneira de trabalhar com o docker-compor arquivos, como será explicado posteriormente.

```yml
version: '2'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

A chave de raiz no arquivo é services. Sob essa chave é definir os serviços que você deseja implantar e executar quando você executar o docker-compor o comando ou quando você implanta no Visual Studio usando esse arquivo compose.yml docker. Nesse caso, o arquivo de docker compose.yml tem vários serviços definidos, conforme descrito na lista a seguir.

-   webmvc contêiner, incluindo o aplicativo MVC do ASP.NET Core consumindo microservices do lado do servidor C\#

-   Catalog.API contêiner, incluindo o API da Web do catálogo ASP.NET Core microsserviço

-   Ordering.API contêiner, incluindo o ordenação de API de Web do ASP.NET Core microsserviço

-   SQL.Data contêiner executando o SQL Server para Linux, mantendo os bancos de dados microservices

-   basket.API contêiner com o API da Web do carrinho ASP.NET Core microsserviço

-   basket.Data contêiner executando o serviço de cache do REDIS, com o banco de dados de compras como um cache REDIS

### <a name="a-simple-web-service-api-container"></a>Um contêiner de API do serviço Web simples

Concentrando-se em um único contêiner, o contêiner-microsserviço catalog.api tem uma definição simples:

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=catalog.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

Esse serviço em contêineres tem a seguinte configuração básica:

-   Ele se baseia a imagem eshop/catalog.api personalizado. Para simplificar, não há nenhuma compilação: definição no arquivo de chave. Isso significa que a imagem deve foram previamente criados (com o build do docker) ou ter sido baixado (com o comando do docker pull) de qualquer registro de Docker.

-   Define uma variável de ambiente denominada ConnectionString com a cadeia de caracteres de conexão a ser usada pelo Entity Framework para acessar a instância do SQL Server que contém o modelo de dados de catálogo. Nesse caso, o mesmo contêiner de SQL Server está mantendo vários bancos de dados. Portanto, você precisa menos memória no computador de desenvolvimento para Docker. No entanto, você também pode implantar um contêiner do SQL Server para cada banco de dados de microsserviço.

-   O nome do SQL Server é sql.data, que é o mesmo nome usado para o contêiner que está executando a instância do SQL Server para Linux. Isso é prático; poder usar essa resolução de nome (interna para o host do Docker) resolverá o endereço de rede, você não precisa saber o IP interno para os contêineres que você está acessando de outros contêineres.

Como a cadeia de caracteres de conexão é definida por uma variável de ambiente, você pode definir essa variável por meio de um mecanismo diferente e em um horário diferente. Por exemplo, você pode definir uma cadeia de caracteres de conexão diferente durante a implantação em produção, os hosts final ou através de seus pipelines de CI/CD no VSTS ou sistema DevOps preferencial.

-   Expõe a porta 80 para acesso interno ao serviço catalog.api dentro do host do Docker. O host atualmente é uma VM do Linux, porque ele se baseia em uma imagem do Docker para Linux, mas você pode configurar o contêiner para executar uma imagem do Windows em vez disso.

-   Ele encaminha a exposto a porta 80 no contêiner para a porta 5101 na máquina de host do Docker (VM Linux).

-   Vincula o serviço da web para o serviço de sql.data (a instância do SQL Server para o banco de dados do Linux em execução em um contêiner). Quando você especificar essa dependência, o contêiner catalog.api não será iniciado até que o contêiner sql.data já foi iniciado; Isso é importante porque catalog.api deve ter o banco de dados do SQL Server e executado pela primeira vez. No entanto, esse tipo de dependência do contêiner não é suficiente em muitos casos, porque Docker verifica apenas no nível do contêiner. Às vezes, o serviço (no SQL Server neste caso) talvez ainda não esteja pronto, portanto, é aconselhável para implementar a lógica de repetição com retirada exponencial em seu cliente microservices. Dessa forma, se um contêiner de dependência não está pronto para um curto período de tempo, o aplicativo ainda será resiliente.

-   Ele é configurado para permitir o acesso a servidores externos: adicionais\_hosts configuração permite que você acesse os servidores externos ou máquinas fora do host do Docker (ou seja, fora da VM do Linux que é um desenvolvimento Docker padrão de host), como um SQL local Instância de servidor em seu PC de desenvolvimento.

Também existem outras configurações mais avançadas de docker compose.yml que discutiremos nas seções a seguir.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Usando o docker-compor arquivos para vários ambientes de destino

Os arquivos de docker compose.yml são arquivos de definição e podem ser usados por várias infraestruturas entendem esse formato. A ferramenta mais simples é o docker-compor o comando, mas outras ferramentas como orchestrators (por exemplo, Docker Swarm) também entender esse arquivo.

Portanto, usando o docker-compor o comando que você pode direcionar os cenários principais a seguir.

#### <a name="development-environments"></a>Ambientes de desenvolvimento

Ao desenvolver aplicativos, é importante poder executar um aplicativo em um ambiente de desenvolvimento isolado. Você pode usar o comando CLI para criar esse ambiente ou use o Visual Studio que usa compor docker nos bastidores de compor docker.

O arquivo compose.yml docker permite que você configure e documentar todas as dependências do seu aplicativo serviço (outros serviços, cache, bancos de dados, filas, etc.). Usando o comando CLI de compor docker, você pode criar e iniciar um ou mais contêineres para cada dependência com um único comando (docker-compor backup).

Docker compose.yml são arquivos de configuração interpretados pelo mecanismo do Docker, mas também servem como arquivos de documentação conveniente sobre a composição de seu aplicativo de contêiner vários.

#### <a name="testing-environments"></a>Ambientes de teste

Uma parte importante de qualquer implantação contínua (CD) ou o processo de integração contínua (CI) são os testes de unidade e testes de integração. Esses testes automatizados exigem um ambiente isolado, portanto, eles não são afetados por usuários ou qualquer outra alteração nos dados do aplicativo.

Com o Docker Compose, você pode criar e destruir o ambiente isolado facilmente em alguns comandos do seu prompt de comando ou scripts, como os comandos a seguir:

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>Implantações de produção

Você também pode usar redigir para implantar em um mecanismo de Docker remoto. Um caso comum é implantar uma única instância de host do Docker (como uma produção VM ou servidor provisionados com [Docker máquina](https://docs.docker.com/machine/overview/)). Mas ele também pode ser um inteiro [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, porque clusters também são compatíveis com os arquivos de docker compose.yml.

Se você estiver usando qualquer orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), você precisará adicionar configurações de instalação e metadados como os de docker compose.yml, mas no formato exigido pelo orquestrador de.

Em qualquer caso, compor a docker é um formato conveniente de ferramenta e os metadados para fluxos de trabalho de desenvolvimento, teste e produção, embora o fluxo de trabalho de produção pode variar o orquestrador que você está usando.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Usando vários docker-compor arquivos para lidar com vários ambientes

Durante o direcionamento ambientes diferentes, você deve usar várias compor arquivos. Isso permite criar diversas variantes de configuração, dependendo do ambiente.

#### <a name="overriding-the-base-docker-compose-file"></a>Substituindo o arquivo de base docker-compose

Você pode usar um arquivo único docker-compose.yml como nos exemplos simplificados mostrados nas seções anteriores. No entanto, isso não é recomendável para a maioria dos aplicativos.

Por padrão, redação lê dois arquivos, um compose.yml docker e um arquivo de docker-compose.override.yml opcional. Conforme mostrado na Figura 8-11, quando você estiver usando o Visual Studio e habilitar o suporte do Docker, Visual Studio também cria os arquivos mais alguns arquivos adicionais usados para depuração.

![](./media/image12.png)

**Figura 8-11**. compor docker de arquivos no Visual Studio de 2017

Você pode editar os arquivos de docker-compose com um editor, como o código do Visual Studio ou Sublime e executar o aplicativo com o docker-compor até o comando.

Por convenção, o arquivo de docker compose.yml contém sua configuração base e outras configurações estáticas. Isso significa que a configuração do serviço não deve ser alterada dependendo do ambiente de implantação que você tiver como alvo.

O arquivo de docker compose.override.yml, como o nome sugere, contém configurações que substituem as configurações básicas, como configuração depende do ambiente de implantação. Você também pode ter vários arquivos de substituição com nomes diferentes. Os arquivos de substituição geralmente contêm informações adicionais exigidas pelo aplicativo mas específico em um ambiente de ou para uma implantação.

#### <a name="targeting-multiple-environments"></a>Direcionamento de vários ambientes

Um caso de uso típico é quando você define vários compor arquivos para que você pode direcionar a vários ambientes, como produção, teste, desenvolvimento ou CI. Para dar suporte a essas diferenças, você pode dividir a configuração de redação em vários arquivos, conforme mostrado na Figura 8-12.

![](./media/image13.png)

**Figura 8-12**. Docker-compor vários a arquivos de substituição de valores no arquivo de base de compose.yml de docker

Você inicia com o arquivo de base de compose.yml de docker. Esse arquivo de base deve conter as definições de configuração de base ou estático que não são alterados dependendo do ambiente. Por exemplo, o eShopOnContainers tem o seguinte arquivo de docker compose.yml como o arquivo de base.

```yml
#docker-compose.yml (Base)
version: '2'

services:
  basket.api:
    image: eshop/basket.api
    build:
    context: ./src/Services/Basket/Basket.API
    dockerfile: Dockerfile
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api
    build:
    context: ./src/Services/Catalog/Catalog.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  identity.api:
    image: eshop/identity.api
    build:
    context: ./src/Services/Identity/Identity.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    build:
    context: ./src/Services/Ordering/Ordering.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  webspa:
    image: eshop/webspa
    build:
    context: ./src/Web/WebSPA
    dockerfile: Dockerfile
    depends_on:
      - identity.api
      - basket.api

  webmvc:
    image: eshop/webmvc
    build:
    context: ./src/Web/WebMVC
    dockerfile: Dockerfile
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api

  sql.data:
    image: microsoft/mssql-server-linux
    basket.data:
    image: redis
    expose:
      - "6379"
    rabbitmq:
    image: rabbitmq
    ports:
      - "5672:5672"

  webstatus:
    image: eshop/webstatus
    build:
    context: ./src/Web/WebStatus
    dockerfile: Dockerfile
```

Os valores no arquivo de base de compose.yml de docker não devem alterar devido a ambientes de implantação de destino diferente.

Se você se concentre na definição do serviço webmvc, por exemplo, você pode ver como essa informação é muito semelhante a não importa qual o ambiente que você pode ser direcionado. Você tem as seguintes informações:

-   O nome do serviço: webmvc.

-   Imagem personalizada do contêiner: eshop/webmvc.

-   O comando para criar a imagem personalizada do Docker, que indica qual Dockerfile a ser usado.

-   Dependências em outros serviços, para que este contêiner não inicia até que os outros contêineres de dependência foram iniciados.

Você pode ter uma configuração adicional, mas o ponto importante é que no arquivo de base de compose.yml de docker, você apenas deseja definir as informações que é comuns em ambientes. Em seguida, no docker compose.override.yml ou arquivos semelhantes para produção ou preparo, você deve colocar configuração é específica para cada ambiente.

Normalmente, o docker-compose.override.yml é usado para o seu ambiente de desenvolvimento, como no exemplo a seguir do eShopOnContainers:

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '2'

services:
# Simplified number of services here:
  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:5101
      - ConnectionString=Server=sql.data; Database=Microsoft.eShopOnContainers.Services.CatalogDb; User Id=sa;Password=Pass@word
      - ExternalCatalogBaseUrl=http://localhost:5101
    ports:
      - "5101:5101"

  identity.api:
    environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:5105
    - SpaClient=http://localhost:5104
    - ConnectionStrings__DefaultConnection = Server=sql.data;Database=Microsoft.eShopOnContainers.Service.IdentityDb;User Id=sa;Password=Pass@word
    - MvcClient=http://localhost:5100
    ports:
      - "5105:5105"

  webspa:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:5104
      - CatalogUrl=http://localhost:5101
      - OrderingUrl=http://localhost:5102
      - IdentityUrl=http://localhost:5105
      - BasketUrl=http:// localhost:5103
    ports:
      - "5104:5104"

  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

Neste exemplo, a configuração de substituição de desenvolvimento expõe algumas portas para o host, define variáveis de ambiente com URLs de redirecionamento e especifica as cadeias de caracteres de conexão para o ambiente de desenvolvimento. Essas configurações são todos apenas para o ambiente de desenvolvimento.

Quando você executa compor docker backup (ou iniciá-lo do Visual Studio), o comando lê as substituições automaticamente como se ele foi mesclando os dois arquivos.

Suponha que você deseja que o outro arquivo de redação para o ambiente de produção, com valores de configuração diferentes. Você pode criar outro arquivo de substituição, como a seguir. (Este arquivo pode ser armazenado em um repositório Git diferente ou gerenciado e protegido por uma equipe diferente.)

```yml
#docker-compose.prod.yml (Extended config for PRODUCTION env.)
version: '2'

services:
  # Simplified number of services here:
  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ASPNETCORE_URLS=http://0.0.0.0:5101
      - ConnectionString=Server=sql.data; Database = Microsoft.eShopOnContainers.Services.CatalogDb; User Id=sa;Password=Prod@Pass
      - ExternalCatalogBaseUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5101
    ports:
      - "5101:5101"

  identity.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ASPNETCORE_URLS=http://0.0.0.0:5105
      - SpaClient=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5104
      - ConnectionStrings__DefaultConnection = Server=sql.data;Database=Microsoft.eShopOnContainers.Service.IdentityDb;User Id=sa;Password=Pass@word
      - MvcClient=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5100
    ports:
      - "5105:5105"

  webspa:
    environment:
      - ASPNETCORE_ENVIRONMENT= Production
      - ASPNETCORE_URLS=http://0.0.0.0:5104
      - CatalogUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5101
      - OrderingUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5102
      - IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
      - BasketUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5103
    ports:
      - "5104:5104"

  sql.data:
    environment:
      - SA_PASSWORD=Prod@Pass
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Como implantar um arquivo de substituição específica

Para usar vários arquivos de substituição, ou um arquivo de substituição com um nome diferente, você pode usar a opção -f com o comando docker-compor e especificar os arquivos. Compor mesclagens arquivos na ordem em que elas são especificadas na linha de comando. O exemplo a seguir mostra como implantar com arquivos de substituição.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Usando variáveis de ambiente no docker-compor arquivos

É conveniente, especialmente em ambientes de produção, para poder obter informações de configuração de variáveis de ambiente, como nós temos mostrado nos exemplos anteriores. Fazer referência a uma variável de ambiente em seus arquivos docker-compose usando a sintaxe \${meu\_VAR}. A seguinte linha de um arquivo de docker compose.prod.yml mostra como referenciar o valor de uma variável de ambiente.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Variáveis de ambiente são criadas e inicializadas de maneiras diferentes, dependendo do seu ambiente de host (Linux, Windows, cluster de nuvem, etc.). No entanto, uma abordagem conveniente é usar um arquivo de .env. Os arquivos docker-compose suportam declarando variáveis de ambiente padrão no arquivo .env. Esses valores das variáveis de ambiente são os valores padrão. Mas elas podem ser substituídas pelos valores que você possa ter definido em cada um de seus ambientes (sistema operacional do host ou variáveis de ambiente do cluster). Coloque esse arquivo .env na pasta em que o compõem docker comando é executado em.

O exemplo a seguir mostra um arquivo de .env como o [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) arquivo para o aplicativo eShopOnContainers.

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Compor docker espera cada linha em um arquivo .env para estar no formato &lt;variável&gt;=&lt;valor&gt;.

Observe que os valores definidos no ambiente de tempo de execução sempre substituam os valores definidos no arquivo .env. De maneira semelhante, os valores passados por meio de argumentos de linha de comando também substituem os valores padrão definidos no arquivo .env.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Visão geral do Docker compor**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Vários arquivos de redação**
    [*https://docs.docker.com/compose/extends/\#arquivos compor vários*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Criando imagens do Docker do ASP.NET Core de otimização

Se você está explorando o Docker e o .NET Core em fontes na Internet, você encontrará Dockerfiles que demonstram a simplicidade de criação de uma imagem do Docker, copiando a fonte em um contêiner. Esses exemplos sugerem que, por meio de uma configuração simple, você pode ter uma imagem do Docker com o ambiente que acompanha seu aplicativo. O exemplo a seguir mostra um Dockerfile simple neste modo.

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

Um Dockerfile como isso funciona. No entanto, você pode otimizar substancialmente suas imagens, especialmente as imagens de produção.

No contêiner e microservices modelo, você está iniciando constantemente contêineres. O modo como o uso de contêineres não reinicia um contêiner em suspensão, como o contêiner está descartável. Orchestrators (como o Docker Swarm, Kubernetes, DCOS ou Azure Service Fabric) simplesmente criarem novas instâncias de imagens. Isso significa que você precisa otimizar pré-compilação do aplicativo quando ele é criado para que o processo de instanciação será mais rápido. Quando o contêiner é iniciado, ele deve estar pronto para executar. Você não deve restaurar e compilação em tempo de execução, usando dotnet dotnet e restauração criar comandos a partir do dotnet CLI que, como você pode ver em várias postagens de blog sobre .NET Core e o Docker.

A equipe do .NET está executando um trabalho importante para tornar o .NET Core e ASP.NET Core uma estrutura otimizada de contêiner. Não somente o .NET Core é uma estrutura leve com um espaço de memória pequenos; a equipe tem voltada para o desempenho de inicialização e produzido algumas imagens Docker otimizadas, como o [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) imagem disponível no [Hub do Docker](https://hub.docker.com/r/microsoft/aspnetcore/), em comparação com o regular [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) ou [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) imagens. O [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) imagem fornece configuração automática de aspnetcore\_urls para a porta 80 e cache de assemblies; pre-ngend essas duas configurações resultam em inicialização mais rápida.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Criando otimização de imagens do Docker com o ASP.NET Core**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>Criar o aplicativo de um contêiner de compilação (CI)

Outro benefício de Docker é que você pode criar o aplicativo a partir de um contêiner pré-configurados, conforme mostrado na Figura 8-13, portanto você não precisa criar uma máquina de compilação ou a VM para criar seu aplicativo. Você pode usar ou esse contêiner de compilação de teste executando-o em sua máquina de desenvolvimento. Mas o que é ainda mais interessante é que você pode usar o mesmo contêiner de compilação do seu pipeline de CI (integração contínua).

![](./media/image14.png)

**Figura 8-13**. Componentes de criação de bits de .NET de um contêiner

Para este cenário, fornecemos o [aspnetcore/microsoft-compilação](https://hub.docker.com/r/microsoft/aspnetcore-build/) imagem, que você pode usar para compilar e criar o ASP.NET Core aplicativos. A saída é colocada em uma imagem com base no [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) imagem, que é uma imagem de tempo de execução otimizado, conforme observada anteriormente.

A imagem de compilação aspnetcore contém tudo o que você precisa para compilar um aplicativo ASP.NET Core, incluindo .NET Core, o SDK do ASP.NET, npm, Bower, Gulp, etc.

Precisamos essas dependências no momento da compilação. Mas não queremos executar esses recursos com o aplicativo em tempo de execução, porque isso tornaria a imagem desnecessariamente grande. No aplicativo eShopOnContainers, você pode criar o aplicativo de um contêiner, executando apenas o seguinte docker-compor comando.

```
  docker-compose -f docker-compose.ci.build.yml up
```

Figura 8-14 mostra este comando executado na linha de comando.

![](./media/image15.png)

**Figura 8-14.** Criar seu aplicativo .NET de um contêiner

Como você pode ver, o contêiner que está sendo executado é a compilação de ci\_1 contêiner. Isso se baseia a imagem aspnetcore compilação para que ela pode compilar e criar seu aplicativo inteiro de dentro do contêiner em vez de seu PC. Que é por que na verdade é criar e compilar projetos .NET Core no Linux, porque esse contêiner está em execução no host Linux Docker padrão.

O [docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) arquivo de imagem (parte da eShopOnContainers) contém o código a seguir. Você pode ver que ele inicia um contêiner de compilação usando o [aspnetcore/microsoft-compilação](https://hub.docker.com/r/microsoft/aspnetcore-build/) imagem.

```yml
version: '2'
  services:
    ci-build:
      image: microsoft/aspnetcore-build:1.0-1.1
      volumes:
        - .:/src
      working_dir: /src
      command: /bin/bash -c "pushd ./src/Web/WebSPA && npm rebuild node-sass && pushd ./../../.. && dotnet restore ./eShopOnContainers-ServicesAndWebApps.sln && dotnet publish ./eShopOnContainers-ServicesAndWebApps.sln -c Release -o ./obj/Docker/publish"
```

* Começando com **.NET Core 2.0**, `dotnet restore` comando é executado automaticamente quando o `dotnet publish` comando é executado.

Depois que o contêiner de compilação está em execução, ele executa a restauração de dotnet do SDK do .NET e dotnet publicar comandos em relação a todos os projetos na solução para compilar os bits de .NET. Nesse caso, pois eShopOnContainers também tem um SPA com base em TypeScript e Angular para o código do cliente, ele também precisa verificar dependências de JavaScript com npm, mas essa ação não está relacionada aos bits de .NET.

O dotnet publicar compilações de comando e publica a saída compilada dentro da pasta de cada projeto para o. pasta de /obj/Docker/Publish, conforme mostrado na Figura 8-15.

![](./media/image16.png)

**Figura 8-15.** Comando de publicar arquivos binários gerados pelo dotnet

#### <a name="creating-the-docker-images-from-the-cli"></a>Criar as imagens do Docker da CLI

Depois que a saída do aplicativo é publicada para as pastas relacionadas (dentro de cada projeto), a próxima etapa é criar as imagens do Docker. Para fazer isso, você usa a compilação docker-compose e docker-compor a comandos, conforme mostrado na Figura 8-16.

![](./media/image17.png)

**Figura 8-16.** Criação de imagens do Docker e os contêineres em execução

Na Figura 8-17, você pode ver como o docker-compose criar execução do comando.

![](./media/image18.png)

**Figura 8-17**. Criação de imagens do Docker com o docker-compor o comando de compilação

A diferença entre o docker-compose criar e compor docker backup comandos é que compõem docker compilações e inicia as imagens.

Quando você usa o Visual Studio, todas essas etapas são executadas nos bastidores. O Visual Studio compila seu aplicativo .NET, cria as imagens do Docker e implanta os contêineres no host do Docker. O Visual Studio oferece recursos adicionais, como a capacidade de depurar seus contêineres em execução no Docker, diretamente do Visual Studio.

O takeway geral aqui é que é capaz de criar seu aplicativo o mesmo propósito seu pipeline de CI/CD deve compilá-lo — de um contêiner em vez de em uma máquina local. Depois de ter as imagens criadas, em seguida, você apenas precisa executar as imagens do Docker usando o docker-compor o comando.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Criação de bits de um contêiner: Configurando a solução eShopOnContainers em um ambiente Windows CLI (dotnet CLI, CLI do Docker e o código do VS)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/ 03.-Setting-the-eShopOnContainers-Solution-up-in-a-Windows-CLI-Environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[Anterior] (dados-controlada por-crud-microservice.md) [Avançar] (container.md de servidor de banco de dados)
