---
title: "Definindo o aplicativo de vários contêineres com o docker-compose.yml"
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Definindo o aplicativo de vários contêineres com o docker-compose.yml"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c4fed5c7ba5c2048d103f22bd2b463c143013280
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Definindo o aplicativo de vários contêineres com o docker-compose.yml 

Neste guia, o arquivo [docker-compose.yml](https://docs.docker.com/compose/compose-file/) foi apresentado na seção [Etapa 4. Definir os serviços no docker-compose.yml ao compilar um aplicativo de vários contêineres do Docker](#step4_define_svcs_in_docker_compose_yml). No entanto, há outras maneiras de usar os arquivos docker-compose e vale a pena explorá-las com mais detalhes.

Por exemplo, você pode descrever explicitamente como deseja implantar o aplicativo de vários contêineres no arquivo docker-compose.yml. Opcionalmente, você também pode descrever como vai criar as imagens personalizadas do Docker. (As imagens personalizadas do Docker também podem ser criadas com a CLI do Docker).

Basicamente, você define cada um dos contêineres que deseja implantar, além de determinadas características para cada implantação de contêiner. Com um arquivo de descrição de implantação de vários contêineres pronto, você poderá implantar toda a solução por meio de uma única ação orquestrada pelo comando da CLI [docker-compose up](https://docs.docker.com/compose/overview/) ou poderá implantá-la de forma transparente no Visual Studio. Caso contrário, você teria que usar a CLI do Docker para implantar contêiner por contêiner, em várias etapas, usando o comando docker run na linha de comando. Portanto, cada serviço definido no docker-compose.yml deve especificar exatamente uma imagem ou build. As outras chaves são opcionais e são semelhantes aos correspondentes do docker run na linha de comando.

O código YAML a seguir é a definição de um arquivo docker-compose.yml possivelmente global, mas único, do exemplo eShopOnContainers. Esse não é o verdadeiro arquivo docker-compose do eShopOnContainers. Em vez disso, ele é uma versão simplificada e consolidada em um único arquivo, o que não é a melhor maneira de se trabalhar com arquivos docker-compose, como será explicado posteriormente.

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

A chave de raiz desse arquivo é services. Sob essa chave você define os serviços que você deseja implantar e executar, com o comando docker-compose up, ou ao implantar no Visual Studio usando esse arquivo docker-compose.yml. Nesse caso, o arquivo docker-compose.yml tem vários serviços definidos, conforme descrito na lista a seguir.

-   Contêiner webmvc, incluindo o aplicativo MVC do ASP.NET Core que consome os microsserviços do C\# do lado do servidor

-   Contêiner catalog.api, incluindo o microsserviço da API Web do Catálogo do ASP.NET Core

-   Contêiner ordering.api, incluindo o microsserviço da API Web de Pedidos do ASP.NET Core

-   Contêiner sql.data, que executa o SQL Server para Linux, mantendo os bancos de dados de microsserviços

-   Contêiner basket.api, com o microsserviço Carrinho de compras da API Web do ASP.NET Core

-   Contêiner basket.data, que executa o Serviço de Cache Redis, com o banco de dados de carrinho de compras como um Cache Redis

### <a name="a-simple-web-service-api-container"></a>Um contêiner de API de serviço Web simples

Concentrando-se em um único contêiner, o microsserviço de contêiner catalog.api tem uma definição simples:

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

Esse serviço em contêiner tem a seguinte configuração básica:

-   Ele se baseia na imagem eshop/catalog.api personalizada. Por questões de simplicidade, não há nenhuma definição de chave build: no arquivo. Isso significa que a imagem deverá ser previamente compilada (com docker build) ou ser baixada (com o comando docker pull) de qualquer registro do Docker.

-   Ele define uma variável de ambiente denominada ConnectionString, com a cadeia de conexão a ser usada pelo Entity Framework para acessar a instância do SQL Server que contém o modelo de dados de catálogo. Nesse caso, o mesmo contêiner do SQL Server está mantendo vários bancos de dados. Dessa forma, você precisará de menos memória no computador de desenvolvimento do Docker. No entanto, você também poderia implantar um contêiner do SQL Server para cada banco de dados de microsserviço.

-   O nome do SQL Server é sql.data, que é o mesmo nome usado pelo contêiner que está executando a Instância do SQL Server para Linux. Isso é conveniente: a possibilidade de usar essa resolução de nome (interna ao host do Docker) resolverá o endereço de rede, então você não precisará saber o IP interno dos contêineres que está acessando de outros contêineres.

Como a cadeia de conexão é definida por uma variável de ambiente, você pode definir essa variável por meio de um mecanismo diferente e em outro momento. Por exemplo, você pode definir uma cadeia de conexão diferente durante a implantação em produção nos hosts finais ou fazer isso através dos pipelines de CI/CD no VSTS ou no sistema de DevOps de sua preferência.

-   Ele expõe a porta 80 para acesso interno ao serviço catalog.api dentro do host do Docker. Atualmente o host é uma VM do Linux, porque ele se baseia em uma imagem do Docker para Linux, mas você também pode configurar o contêiner para ser executado em uma imagem do Windows.

-   Ele encaminha a porta 80, exposta no contêiner, para a porta 5101 no computador host do Docker (a VM do Linux).

-   Ele vincula o serviço Web ao serviço sql.data (a instância do SQL Server para o banco de dados do Linux em execução em um contêiner). Ao especificar essa dependência, o contêiner catalog.api não será iniciado até que o contêiner sql.data seja iniciado. Isso é importante porque o catalog.api precisa que o banco de dados do SQL Server esteja em execução. No entanto, esse tipo de dependência de contêiner não é suficiente em muitos casos, porque o Docker verifica apenas no nível de contêiner. Às vezes, o serviço (o SQL Server, neste caso) poderá ainda não estar pronto, portanto, é aconselhável implementar uma lógica de repetição com retirada exponencial no microsserviço cliente. Dessa forma, se um contêiner de dependência não estiver pronto durante um breve período de tempo, o aplicativo continuará resiliente.

-   Ele é configurado para permitir o acesso a servidores externos: a configuração extra\_hosts permite que você acesse servidores externos ou computadores fora do host do Docker (ou seja, fora da VM do Linux padrão, que é um host do Docker para desenvolvimento), como uma Instância do SQL Server local em seu computador de desenvolvimento.

Também há outras configurações mais avançadas do docker-compose.yml que discutiremos nas próximas seções.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Usando arquivos docker-compose para destinar-se a vários ambientes

Os arquivos docker-compose.yml são arquivos de definição e podem ser usados por várias infraestruturas que entendem esse formato. A ferramenta mais simples é o comando docker-compose, mas outras ferramentas, como orquestradores (por exemplo, o Docker Swarm), também entendem esse arquivo.

Portanto, ao usar o comando docker-compose você pode ter os seguintes principais cenários como destino.

#### <a name="development-environments"></a>Ambientes de desenvolvimento

Ao desenvolver aplicativos, é importante ser capaz de executar um aplicativo em um ambiente de desenvolvimento isolado. Você pode usar o comando de CLI docker-compose para criar esse ambiente ou usar o Visual Studio, que usa o docker-compose nos bastidores.

O arquivo docker-compose.yml permite que você configure e documente todas as dependências de serviço do seu aplicativo (outros serviços, cache, bancos de dados, filas, etc.). Ao usar o comando de CLI docker-compose, você pode criar e iniciar um ou mais contêineres para cada dependência com um único comando (docker-compose up).

Os docker-compose.yml são arquivos de configuração interpretados pelo mecanismo do Docker, mas também servem como arquivos de documentação convenientes, com informações sobre a composição de seu aplicativo para vários contêineres.

#### <a name="testing-environments"></a>Ambientes de teste

Uma parte importante de qualquer processo de CD (implantação contínua) ou CI (integração contínua) são os testes de unidade e testes de integração. Esses testes automatizados exigem um ambiente isolado para que não sejam afetados por usuários ou qualquer outra alteração nos dados do aplicativo.

Com o Docker Compose, você pode criar e destruir esse ambiente isolado facilmente por meio de alguns comandos no prompt de comando ou por meio de scripts, como os comandos a seguir:

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>Implantações de produção

Você também pode usar o Compose para implantar em um mecanismo remoto do Docker. Um caso comum é a implantação em uma única instância de host do Docker (como uma VM ou servidor de produção, provisionados com o [Docker Machine](https://docs.docker.com/machine/overview/)). Mas também poderia ser em um cluster [Docker Swarm](https://docs.docker.com/swarm/overview/) inteiro, porque os clusters também são compatíveis com os arquivos docker-compose.yml.

Se estiver usando qualquer outro orquestrador (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), você precisará adicionar configurações de instalação e metadados, como aqueles no docker-compose.yml, mas no formato exigido pelo outro orquestrador.

De qualquer maneira, o docker-compose é uma ferramenta conveniente e um formato de metadados para fluxos de trabalho de desenvolvimento, teste e produção, embora o fluxo de trabalho de produção possa variar no orquestrador que você está usando.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Usando vários arquivos docker-compose para lidar com diversos ambientes

Ao destinar-se a ambientes diferentes, você deve usar vários arquivos compose. Isso permite que você crie diversas variantes de configuração, dependendo do ambiente.

#### <a name="overriding-the-base-docker-compose-file"></a>Substituindo o arquivo base docker-compose

Você pode usar um único arquivo docker-compose.yml, como nos exemplos simplificados mostrados nas seções anteriores. No entanto, isso não é recomendável para a maioria dos aplicativos.

Por padrão, o Compose lê dois arquivos, um docker-compose.yml e um arquivo docker-compose.override.yml opcional. Conforme mostrado na Figura 8-11, quando você está usando o Visual Studio e habilitando o suporte do Docker, o Visual Studio também cria outro arquivo yml, o docker-compose.ci.build, para que você use nos pipelines de CI/CD, como no VSTS.

![](./media/image12.png)

**Figura 8-11**. Arquivos docker-compose no Visual Studio 2017

Você pode editar os arquivos docker-compose com qualquer editor, como o Visual Studio Code ou o Sublime, e executar o aplicativo com o comando docker-compose up.

Por convenção, o arquivo docker-compose.yml contém sua configuração base e outras configurações estáticas. Isso significa que a configuração do serviço não deve ser alterada de acordo com o ambiente de implantação que você tem como destino.

O arquivo docker-compose.override.yml, como o próprio nome sugere, contém definições de configuração que substituem a configuração base, como a configuração que depende do ambiente de implantação. Você também pode ter vários arquivos de substituição com nomes diferentes. Os arquivos de substituição geralmente contêm informações adicionais, exigidas pelo aplicativo, bem como as informações específicas de um ambiente ou uma implantação.

#### <a name="targeting-multiple-environments"></a>Destinando-se a vários ambientes

Um caso de uso típico é aquele em que você define vários arquivos compose para destinar-se a vários ambientes, como de produção, de preparo, de CI ou de desenvolvimento. Para dar suporte a essas diferenças, você pode dividir a configuração do Compose em vários arquivos, conforme mostrado na Figura 8-12.

![](./media/image13.png)

**Figura 8-12**. Vários arquivos docker-compose substituindo valores no arquivo base docker-compose.yml

Você inicia com o arquivo base docker-compose.yml. Esse arquivo base deve conter as definições de configuração base ou estáticas que não se alteram de acordo com o ambiente. Por exemplo, o eShopOnContainers tem o seguinte arquivo docker-compose.yml como o arquivo base.

```yml
#docker-compose.yml (Base)
version: '3'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: ./src/Services/Basket/Basket.API
      dockerfile: Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: ./src/Services/Catalog/Catalog.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: ./src/Services/Marketing/Marketing.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: ./src/Web/WebMVC
      dockerfile: Dockerfile    
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api
      - marketing.api

  sql.data:
    image: microsoft/mssql-server-linux:2017-latest

  nosql.data:
    image: mongo

  basket.data:
    image: redis
      
  rabbitmq:
    image: rabbitmq:3-management

```

Os valores do arquivo base docker-compose.yml não devem se alterar devido aos diferentes ambientes de implantação de destino.

Se você se concentrar na definição do serviço webmvc, por exemplo, verá como essa informação é muito semelhante independentemente do ambiente ao qual você se destina. Você tem as seguintes informações:

-   O nome do serviço: webmvc.

-   A imagem personalizada do contêiner: eshop/webmvc.

-   O comando para compilar a imagem personalizada do Docker, que indica qual Dockerfile usar.

-   As dependências de outros serviços, para que este contêiner não se inicie até que os outros contêineres de dependência sejam iniciados.

Você pode ter outras configurações, mas o ponto importante é que, no arquivo base docker-compose.yml, é necessário definir apenas as informações que são comuns entre ambientes. Então, no docker-compose.override.yml ou em arquivos semelhantes de produção ou de preparo, você deve colocar a configuração específica para cada ambiente.

Normalmente, o docker-compose.override.yml é usado para o ambiente de desenvolvimento, como no exemplo a seguir, do eShopOnContainers:

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3'

services: 
# Simplified number of services here: 
      
  basket.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basket.data}
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}      
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5101/api/v1/catalog/items/[0]/pic/}   
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}         
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}          
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
      - LocationsUrl=http://locations.api
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://marketing.api                                                    
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc     
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - MSSQL_SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
      - MSSQL_PID=Developer
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
  basket.data:
    ports:
      - "6379:6379"      
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

Neste exemplo, a configuração de substituição de desenvolvimento expõe algumas portas para o host, define variáveis de ambiente com URLs de redirecionamento e especifica cadeias de conexão para o ambiente de desenvolvimento. Todas essas configurações são apenas para o ambiente de desenvolvimento.

Quando você executa `docker-compose up` (ou o inicia no Visual Studio), o comando lerá as substituições automaticamente como se estivesse mesclando os dois arquivos.

Suponha que você deseja outro arquivo do Compose para o ambiente de produção, com valores de configuração, de portas ou de cadeias de conexão diferentes. Você pode criar outro arquivo de substituição, como um arquivo chamado `docker-compose.prod.yml`, com diferentes configurações e variáveis de ambiente.  Esse arquivo poderá ser armazenado em outro repositório GIT ou gerenciado e protegido por uma equipe diferente.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Como implantar com um arquivo de substituição específico

Para usar vários arquivos de substituição, ou um arquivo de substituição com um nome diferente, use a opção -f com o comando docker-compose e especifique os arquivos. O Compose mescla os arquivos na ordem em que eles são especificados na linha de comando. O exemplo a seguir mostra como implantar com arquivos de substituição.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Usando variáveis de ambiente em arquivos docker-compose

É conveniente, especialmente em ambientes de produção, ter a possibilidade de obter informações de configuração de variáveis de ambiente, como mostramos em exemplos anteriores. Faça referência a uma variável de ambiente em arquivos docker-compose, usando a sintaxe \${MY\_VAR}. A seguinte linha de um arquivo docker-compose.prod.yml mostra como referenciar o valor de uma variável de ambiente.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

As variáveis de ambiente são criadas e inicializadas de diferentes maneiras, dependendo do ambiente de host (Linux, Windows, cluster de nuvem, etc.). Entretanto, uma abordagem conveniente é usar um arquivo .env. Os arquivos docker-compose são compatíveis com a declaração de variáveis de ambiente padrão no arquivo .env. Esses valores das variáveis de ambiente são os valores padrão. Mas elas podem ser substituídas pelos valores que você definiu em cada um dos ambientes (sistema operacional de host ou variáveis de ambiente do cluster). Coloque esse arquivo .env na pasta em que o comando docker-compose é executado.

O exemplo a seguir mostra um arquivo .env parecido com o [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) do aplicativo eShopOnContainers.

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

O docker-compose espera que cada linha de um arquivo .env esteja no formato &lt;variável&gt;=&lt;valor&gt;.

Observe que os valores definidos no ambiente do tempo de execução sempre substituem os valores definidos no arquivo .env. De maneira semelhante, os valores passados por meio de argumentos de linha de comando também substituem os valores padrão definidos no arquivo .env.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Visão geral do Docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Vários arquivos Compose**
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Criando imagens do Docker do ASP.NET Core otimizadas

Se estiver explorando o Docker e o .NET Core em fontes na Internet, você encontrará Dockerfiles que demonstram a simplicidade da criação de uma imagem do Docker por meio da cópia da fonte em um contêiner. Esses exemplos sugerem que, ao usar uma configuração simples, você pode ter uma imagem do Docker com o ambiente empacotado com seu aplicativo. O exemplo a seguir mostra um Dockerfile simples neste sentido.

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

Um Dockerfile como esse funcionará. No entanto, você pode otimizar substancialmente suas imagens, especialmente as imagens de produção.

No modelo de contêiner e microsserviços, você está constantemente iniciando contêineres. O modo comum de uso de contêineres não reinicia um contêiner em suspensão porque o contêiner é descartável. Orquestradores, como Docker Swarm, Kubernetes, DCOS ou Azure Service Fabric, simplesmente criam novas instâncias de imagens. Isso significa que você precisará otimizar por meio da pré-compilação do aplicativo quando ele for criado, fazendo com que o processo de instanciação seja mais rápido. Quando o contêiner é iniciado, ele deve estar pronto para executar. Você não deve restaurar e compilar em tempo de execução, usando os comandos dotnet restore e dotnet build na CLI do dotnet, como você pode ver em várias postagens de blog sobre o .NET Core e o Docker.

A equipe do .NET está realizando um trabalho importante para tornar o .NET Core e o ASP.NET Core uma estrutura otimizada para contêineres. O .NET Core não é apenas uma estrutura leve com um volume de memória pequeno; a equipe tem se concentrado no desempenho de inicialização e produzido algumas imagens de Docker otimizadas, como a imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/), disponível no [Hub do Docker](https://hub.docker.com/r/microsoft/aspnetcore/), em comparação com as imagens [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) ou [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) regulares. A imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) fornece configuração automática de aspnetcore\_urls para a porta 80 e o cache de assemblies pré criado; essas duas configurações resultam em inicialização mais rápida.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Building Optimized Docker Images with ASP.NET Core (Criando imagens do Docker otimizadas com o ASP.NET Core)**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>Compilando o aplicativo em um contêiner de build (CI)

Outro benefício do Docker é que você pode compilar o aplicativo em um contêiner pré-configurado, conforme mostrado na Figura 8-13, evitando a necessidade de criar um computador de build ou uma VM para compilar o aplicativo. Você pode usar ou testar esse contêiner de build executando-o em seu computador de desenvolvimento. E o que é ainda mais interessante é que você pode usar o mesmo contêiner de build em seu pipeline de CI (integração contínua).

![](./media/image14.png)

**Figura 8-13**. Contêiner de build do Docker compilando os binários de .NET 

Para este cenário, fornecemos a imagem [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/), que você pode usar para compilar e criar os aplicativos do ASP.NET Core. A saída é colocada em uma imagem baseada na imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/), que é uma imagem de tempo de execução otimizado, conforme observado anteriormente.

A imagem aspnetcore-build contém tudo o que você precisa para compilar um aplicativo do ASP.NET Core, incluindo o .NET Core, o SDK do ASP.NET, o npm, o Bower, o Gulp, etc.

Essas dependências são necessárias no momento do build. No entanto, não queremos levá-las com o aplicativo em tempo de execução, porque isso tornaria a imagem desnecessariamente grande. No aplicativo eShopOnContainers, você pode compilar o aplicativo em um contêiner simplesmente por meio da execução do seguinte comando docker-compose.

```
  docker-compose -f docker-compose.ci.build.yml up
```

A figura 8-14 mostra este comando em execução na linha de comando.

![](./media/image15.png)

**Figura 8-14.** Compilando seu aplicativo do .NET em um contêiner

Como você pode ver, o contêiner que está sendo executado é o contêiner ci-build\_1. Ele se baseia na imagem aspnetcore-build para que possa compilar e criar o aplicativo inteiro de dentro do contêiner em vez de fazê-lo em seu computador. É por isso que, na verdade, ele está criando e compilando os projetos do .NET Core no Linux, porque esse contêiner está em execução no host Linux do Docker padrão.

O arquivo [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) dessa imagem (parte do eShopOnContainers) contém o seguinte código. Veja que ele inicia um contêiner de build usando a imagem [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/).

```yml
version: '3'

services:

  ci-build:

    image: microsoft/aspnetcore-build:2.0

    volumes:
      - .:/src

    working_dir: /src

    command: /bin/bash -c "pushd ./src/Web/WebSPA && npm rebuild node-sass && popd && dotnet restore ./eShopOnContainers-ServicesAndWebApps.sln && dotnet publish ./eShopOnContainers-ServicesAndWebApps.sln -c Release -o ./obj/Docker/publish"

```

* Começando com o **.NET Core 2.0**, o comando `dotnet restore` é executado automaticamente quando o comando `dotnet publish` é executado.

Após o contêiner de build estar em funcionamento, ele executará os comandos dotnet restore e dotnet publish do SDK do .NET em todos os projetos da solução, a fim de compilar os bits do .NET. Nesse caso, como o eShopOnContainers também tem um SPA com base em TypeScript e Angular para o código do cliente, ele também precisa verificar as dependências de JavaScript com o npm, mas essa ação não está relacionada com os bits do .NET.

O comando dotnet publish compila e publica a saída compilada dentro da pasta de cada projeto na pasta ../obj/Docker/publish, conforme mostrado na Figura 8-15.

![](./media/image16.png)

**Figura 8-15.** Arquivos binários gerados pelo comando dotnet publish

#### <a name="creating-the-docker-images-from-the-cli"></a>Criando as imagens do Docker por meio da CLI

Depois que a saída do aplicativo é publicada nas pastas relacionadas (dentro de cada projeto), a próxima etapa é criar as imagens do Docker. Para fazer isso, você usa os comandos docker-compose build e docker-compose up, conforme mostrado na Figura 8-16.

![](./media/image17.png)

**Figura 8-16.** Criando imagens do Docker e executando os contêineres

Na Figura 8-17, você pode ver como o comando docker-compose build é executado.

![](./media/image18.png)

**Figura 8-17**. Criando as imagens do Docker com o comando docker-compose build

A diferença entre os comandos docker-compose build e docker-compose up é que o docker-compose up compila e inicia as imagens.

Quando você usa o Visual Studio, todas essas etapas são realizadas nos bastidores. O Visual Studio compila seu aplicativo do .NET, cria as imagens do Docker e implanta os contêineres no host do Docker. O Visual Studio oferece recursos adicionais, como a capacidade de depurar seus contêineres em execução no Docker diretamente no Visual Studio.

A conclusão geral aqui é que você pode compilar seu aplicativo da mesma maneira que o pipeline de CI/CD deveria fazê-lo — em um contêiner em vez de um computador local. Depois que as imagens são criadas, você só precisa executar as imagens do Docker usando o comando docker-compose up.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code) (Criação de bits em um contêiner: configurando a solução eShopOnContainers em um ambiente de CLI do Windows (CLI do dotnet, CLI do Docker e VS Code))**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[Anterior] (data-driven-crud-microservice.md) [Próximo] (database-server-container.md)
