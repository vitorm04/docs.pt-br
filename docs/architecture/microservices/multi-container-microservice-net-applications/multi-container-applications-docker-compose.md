---
title: Definindo o aplicativo de vários contêineres com o docker-compose.yml
description: Como especificar a composição de microsserviços para um aplicativo de vários contêineres com o docker-compose.yml.
ms.date: 10/02/2018
ms.openlocfilehash: 02db27feb1320d8b9c6823b8f9ef51c2ddf9791c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737099"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Definindo o aplicativo de vários contêineres com o docker-compose.yml

Neste guia, o arquivo [Docker-Compose. yml](https://docs.docker.com/compose/compose-file/) foi introduzido na seção [etapa 4. Defina seus serviços em Docker-Compose. yml ao criar um aplicativo Docker com vários contêineres](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application). No entanto, há outras maneiras de usar os arquivos docker-compose e vale a pena explorá-las com mais detalhes.

Por exemplo, você pode descrever explicitamente como deseja implantar o aplicativo de vários contêineres no arquivo docker-compose.yml. Opcionalmente, você também pode descrever como vai criar as imagens personalizadas do Docker. (As imagens personalizadas do Docker também podem ser criadas com a CLI do Docker).

Basicamente, você define cada um dos contêineres que deseja implantar, além de determinadas características para cada implantação de contêiner. Com um arquivo de descrição de implantação de vários contêineres pronto, você poderá implantar toda a solução por meio de uma única ação orquestrada pelo comando da CLI [docker-compose up](https://docs.docker.com/compose/overview/) ou poderá implantá-la de forma transparente no Visual Studio. Caso contrário, você precisará usar a CLI do Docker para implantar contêiner por contêiner, em várias etapas, usando o comando `docker run` na linha de comando. Portanto, cada serviço definido no docker-compose.yml deve especificar exatamente uma imagem ou build. As outras chaves são opcionais e são semelhantes aos correspondentes de `docker run` na linha de comando.

O código YAML a seguir é a definição de um arquivo docker-compose.yml possivelmente global, mas único, do exemplo eShopOnContainers. Esse não é o verdadeiro arquivo docker-compose do eShopOnContainers. Em vez disso, ele é uma versão simplificada e consolidada em um único arquivo, o que não é a melhor maneira de se trabalhar com arquivos docker-compose, como será explicado posteriormente.

```yml
version: '3.4'

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

A chave de raiz desse arquivo é services. Sob essa chave, você define os serviços que deseja implantar e executar ao executar o comando `docker-compose up` ou ao implantar por meio do Visual Studio usando esse arquivo docker-compose.yml. Nesse caso, o arquivo docker-compose.yml tem vários serviços definidos, conforme descrito na tabela a seguir.

| Nome do serviço | Descrição |
|--------------|-------------|
| webmvc       | Contêiner, incluindo o aplicativo MVC ASP.NET Core, que consome os microsserviços do C\# do lado do servidor|
| catalog.api  | Contêiner, incluindo o microsserviço de API Web do ASP.NET Core de Catálogo |
| ordering.api | Contêiner, incluindo o microsserviço de API Web do ASP.NET Core de Pedidos |
| sql.data     | Contêiner que executa o SQL Server para Linux armazenando os bancos de dados de microsserviços |
| basket.api   | Contêiner com o microsserviço de API Web do ASP.NET Core de Cesta |
| basket.data  | Contêiner que executa o serviço de Cache Redis, com o banco de dados da cesta como um Cache Redis |

### <a name="a-simple-web-service-api-container"></a>Um contêiner de API de serviço Web simples

Concentrando-se em um único contêiner, o microsserviço de contêiner catalog.api tem uma definição simples:

```yml
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
```

Esse serviço em contêiner tem a seguinte configuração básica:

- Ele se baseia na imagem eshop/catalog.api personalizada. Por questões de simplicidade, não há nenhuma definição de chave build: no arquivo. Isso significa que a imagem precisa ser previamente compilada (com docker build) ou ser baixada (com o comando docker pull) de qualquer registro do Docker.

- Ele define uma variável de ambiente denominada ConnectionString, com a cadeia de conexão a ser usada pelo Entity Framework para acessar a instância do SQL Server que contém o modelo de dados de catálogo. Nesse caso, o mesmo contêiner do SQL Server está mantendo vários bancos de dados. Dessa forma, você precisará de menos memória no computador de desenvolvimento do Docker. No entanto, você também poderia implantar um contêiner do SQL Server para cada banco de dados de microsserviço.

- O nome do SQL Server é sql.data, que é o mesmo nome usado pelo contêiner que está executando a Instância do SQL Server para Linux. Isso é conveniente: a possibilidade de usar essa resolução de nome (interna ao host do Docker) resolverá o endereço de rede, então você não precisará saber o IP interno dos contêineres que está acessando de outros contêineres.

Como a cadeia de conexão é definida por uma variável de ambiente, você pode definir essa variável por meio de um mecanismo diferente e em outro momento. Por exemplo, você pode definir uma cadeia de conexão diferente durante a implantação em produção nos hosts finais ou fazer isso através dos pipelines de CI/CD no Azure DevOps Services ou no sistema de DevOps de sua preferência.

- Ele expõe a porta 80 para acesso interno ao serviço catalog.api dentro do host do Docker. Atualmente o host é uma VM do Linux, porque ele se baseia em uma imagem do Docker para Linux, mas você também pode configurar o contêiner para ser executado em uma imagem do Windows.

- Ele encaminha a porta 80, exposta no contêiner, para a porta 5101 no computador host do Docker (a VM do Linux).

- Ele vincula o serviço Web ao serviço sql.data (a instância do SQL Server para o banco de dados do Linux em execução em um contêiner). Ao especificar essa dependência, o contêiner catalog.api não será iniciado até que o contêiner sql.data seja iniciado. Isso é importante porque o catalog.api precisa que o banco de dados do SQL Server esteja em execução. No entanto, esse tipo de dependência de contêiner não é suficiente em muitos casos, porque o Docker verifica apenas no nível de contêiner. Às vezes, o serviço (o SQL Server, neste caso) poderá ainda não estar pronto, portanto, é aconselhável implementar uma lógica de repetição com retirada exponencial no microsserviço cliente. Dessa forma, se um contêiner de dependência não estiver pronto durante um breve período de tempo, o aplicativo continuará resiliente.

- Ele é configurado para permitir o acesso a servidores externos: a configuração extra\_hosts permite que você acesse servidores externos ou computadores fora do host do Docker (ou seja, fora da VM do Linux padrão, que é um host do Docker para desenvolvimento), como uma Instância do SQL Server local em seu computador de desenvolvimento.

Também há outras configurações mais avançadas do docker-compose.yml que discutiremos nas próximas seções.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Usando arquivos docker-compose para destinar-se a vários ambientes

Os arquivos docker-compose.yml são arquivos de definição e podem ser usados por várias infraestruturas que entendem esse formato. A ferramenta mais simples é o comando docker-compose.

Portanto, ao usar o comando docker-compose você pode ter os seguintes principais cenários como destino.

#### <a name="development-environments"></a>Ambientes de desenvolvimento

Ao desenvolver aplicativos, é importante ser capaz de executar um aplicativo em um ambiente de desenvolvimento isolado. Você pode usar o comando de CLI docker-compose para criar esse ambiente ou usar o Visual Studio, que usa o docker-compose nos bastidores.

O arquivo docker-compose.yml permite que você configure e documente todas as dependências de serviço do seu aplicativo (outros serviços, cache, bancos de dados, filas, etc.). Usando o comando da CLI docker-compose, você pode criar e iniciar um ou mais contêineres para cada dependência com um único comando (docker-compose up).

Os docker-compose.yml são arquivos de configuração interpretados pelo mecanismo do Docker, mas também servem como arquivos de documentação convenientes, com informações sobre a composição de seu aplicativo para vários contêineres.

#### <a name="testing-environments"></a>Ambientes de teste

Uma parte importante de qualquer processo de CD (implantação contínua) ou CI (integração contínua) são os testes de unidade e testes de integração. Esses testes automatizados exigem um ambiente isolado para que não sejam afetados por usuários ou qualquer outra alteração nos dados do aplicativo.

Com o Docker Compose, você pode criar e destruir esse ambiente isolado facilmente por meio de alguns comandos no prompt de comando ou por meio de scripts, como os comandos a seguir:

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a>Implantações de produção

Você também pode usar o Compose para implantar em um mecanismo remoto do Docker. Um caso comum é a implantação em uma única instância de host do Docker (como uma VM ou servidor de produção, provisionados com o [Docker Machine](https://docs.docker.com/machine/overview/)).

Se estiver usando qualquer outro orquestrador (Azure Service Fabric, Kubernetes, etc.), precisará adicionar definições de configuração de instalação e metadados, como aquelas em docker-compose.yml, mas no formato exigido pelo outro orquestrador.

De qualquer maneira, o docker-compose é uma ferramenta conveniente e um formato de metadados para fluxos de trabalho de desenvolvimento, teste e produção, embora o fluxo de trabalho de produção possa variar no orquestrador que você está usando.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Usando vários arquivos docker-compose para lidar com diversos ambientes

Ao destinar-se a ambientes diferentes, você deve usar vários arquivos compose. Isso permite que você crie diversas variantes de configuração, dependendo do ambiente.

#### <a name="overriding-the-base-docker-compose-file"></a>Substituindo o arquivo base docker-compose

Você pode usar um único arquivo docker-compose.yml, como nos exemplos simplificados mostrados nas seções anteriores. No entanto, isso não é recomendável para a maioria dos aplicativos.

Por padrão, o Compose lê dois arquivos, um docker-compose.yml e um arquivo docker-compose.override.yml opcional. Conforme mostrado na Figura 6-11, quando você estiver usando o Visual Studio e habilitar o suporte ao Docker, o Visual Studio também criará um arquivo docker-compose.vs.debug.g.yml adicional para depurar o aplicativo. Dê uma olhada nesse arquivo na pasta obj\\Docker\\ da pasta da solução principal.

![Captura de tela dos arquivos em um projeto do Docker Compose.](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

**Figura 6-11**. Arquivos docker-compose no Visual Studio 2017

estrutura do arquivo de projeto do **Docker-Compose** :

* *. dockerignore* -usado para ignorar arquivos
* *Docker-Compose. yml* -usado para compor microserviços
* *Docker-Compose. Override. yml* -usado para configurar o ambiente de microserviços

Edite os arquivos docker-compose com qualquer editor, como o Visual Studio Code ou o Sublime, e execute o aplicativo com o comando docker-compose up.

Por convenção, o arquivo docker-compose.yml contém sua configuração base e outras configurações estáticas. Isso significa que a configuração do serviço não deve ser alterada de acordo com o ambiente de implantação que você tem como destino.

O arquivo docker-compose.override.yml, como o próprio nome sugere, contém definições de configuração que substituem a configuração base, como a configuração que depende do ambiente de implantação. Você também pode ter vários arquivos de substituição com nomes diferentes. Os arquivos de substituição geralmente contêm informações adicionais, exigidas pelo aplicativo, bem como as informações específicas de um ambiente ou uma implantação.

#### <a name="targeting-multiple-environments"></a>Destinando-se a vários ambientes

Um caso de uso típico é aquele em que você define vários arquivos compose para destinar-se a vários ambientes, como de produção, de preparo, de CI ou de desenvolvimento. Para dar suporte a essas diferenças, você pode dividir a configuração do Compose em vários arquivos, conforme mostrado na Figura 6-12.

![Diagrama de três arquivos Docker-Compose definidos para substituir o arquivo base.](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

**Figura 6-12**. Vários arquivos docker-compose substituindo valores no arquivo base docker-compose.yml

Você pode combinar vários arquivos Docker-Compose*. yml para lidar com ambientes diferentes. Você inicia com o arquivo base docker-compose.yml. Esse arquivo base deve conter as definições de configuração base ou estáticas que não se alteram de acordo com o ambiente. Por exemplo, o eShopOnContainers tem o arquivo docker-compose.yml a seguir (simplificado com menos serviços) como o arquivo base.

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
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

- O nome do serviço: webmvc.

- A imagem personalizada do contêiner: eshop/webmvc.

- O comando para compilar a imagem personalizada do Docker, que indica qual Dockerfile usar.

- As dependências de outros serviços, para que este contêiner não se inicie até que os outros contêineres de dependência sejam iniciados.

Você pode ter outras configurações, mas o ponto importante é que, no arquivo base docker-compose.yml, é necessário definir apenas as informações que são comuns entre ambientes. Então, no docker-compose.override.yml ou em arquivos semelhantes de produção ou de preparo, você deve colocar a configuração específica para cada ambiente.

Normalmente, o docker-compose.override.yml é usado para o ambiente de desenvolvimento, como no exemplo a seguir, do eShopOnContainers:

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

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
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}
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
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
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

Quando você executa `docker-compose up` (ou o inicia no Visual Studio), o comando lerá as substituições automaticamente como se estivesse mesclando os dois arquivos.

Suponha que você deseja outro arquivo do Compose para o ambiente de produção, com valores de configuração, de portas ou de cadeias de conexão diferentes. Você pode criar outro arquivo de substituição, como um arquivo chamado `docker-compose.prod.yml`, com diferentes configurações e variáveis de ambiente. Esse arquivo poderá ser armazenado em outro repositório GIT ou gerenciado e protegido por uma equipe diferente.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Como implantar com um arquivo de substituição específico

Para usar vários arquivos de substituição, ou um arquivo de substituição com um nome diferente, use a opção -f com o comando docker-compose e especifique os arquivos. O Compose mescla os arquivos na ordem em que eles são especificados na linha de comando. O exemplo a seguir mostra como implantar com arquivos de substituição.

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Usando variáveis de ambiente em arquivos docker-compose

É conveniente, especialmente em ambientes de produção, ter a possibilidade de obter informações de configuração de variáveis de ambiente, como mostramos em exemplos anteriores. Referencie uma variável de ambiente nos arquivos docker-compose usando a sintaxe ${MY\_VAR}. A seguinte linha de um arquivo docker-compose.prod.yml mostra como referenciar o valor de uma variável de ambiente.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

As variáveis de ambiente são criadas e inicializadas de diferentes maneiras, dependendo do ambiente de host (Linux, Windows, cluster de nuvem, etc.). Entretanto, uma abordagem conveniente é usar um arquivo .env. Os arquivos docker-compose são compatíveis com a declaração de variáveis de ambiente padrão no arquivo .env. Esses valores das variáveis de ambiente são os valores padrão. Mas elas podem ser substituídas pelos valores que você definiu em cada um dos ambientes (sistema operacional de host ou variáveis de ambiente do cluster). Coloque esse arquivo .env na pasta em que o comando docker-compose é executado.

O exemplo a seguir mostra um arquivo .env parecido com o [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) do aplicativo eShopOnContainers.

```env
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

O docker-compose espera que cada linha de um arquivo .env esteja no formato \<variável\>=\<valor\>.

Observe que os valores definidos no ambiente do runtime sempre substituem os valores definidos no arquivo .env. De maneira semelhante, os valores passados por meio de argumentos de linha de comando também substituem os valores padrão definidos no arquivo .env.

#### <a name="additional-resources"></a>Recursos adicionais

- **Visão geral do Docker Compose** \
    <https://docs.docker.com/compose/overview/>

- **Vários arquivos Compose** \
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Criando imagens do Docker do ASP.NET Core otimizadas

Se estiver explorando o Docker e o .NET Core em fontes na Internet, você encontrará Dockerfiles que demonstram a simplicidade da criação de uma imagem do Docker por meio da cópia da fonte em um contêiner. Esses exemplos sugerem que, ao usar uma configuração simples, você pode ter uma imagem do Docker com o ambiente empacotado com seu aplicativo. O exemplo a seguir mostra um Dockerfile simples neste sentido.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:2.2
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

Um Dockerfile como esse funcionará. No entanto, você pode otimizar substancialmente suas imagens, especialmente as imagens de produção.

No modelo de contêiner e microsserviços, você está constantemente iniciando contêineres. O modo comum de uso de contêineres não reinicia um contêiner em suspensão porque o contêiner é descartável. Orquestradores (como o Kubernetes e o Azure Service Fabric) simplesmente criam instâncias de imagens. Isso significa que você precisará otimizar por meio da pré-compilação do aplicativo quando ele for criado, fazendo com que o processo de instanciação seja mais rápido. Quando o contêiner é iniciado, ele deve estar pronto para executar. Você não deve restaurar nem compilar em tempo de execução usando os comandos `dotnet restore` e `dotnet build` na CLI do dotnet, como visto em várias postagens no blog sobre o .NET Core e o Docker.

A equipe do .NET está realizando um trabalho importante para tornar o .NET Core e o ASP.NET Core uma estrutura otimizada para contêineres. O .NET Core não é apenas uma estrutura leve com um volume de memória pequeno; a equipe se concentrou em imagens do Docker otimizadas para três cenários principais e as publicou no Registro no Hub do Docker em *dotnet/core*, começando na versão 2.1:

1. **Desenvolvimento**: em que a prioridade é a capacidade de iterar e depurar rapidamente as alterações, e onde o tamanho é secundário.

2. **Build**: a prioridade é compilar o aplicativo e inclui os binários e outras dependências para otimizar os binários.

3. **Produção**: onde o foco é a implantação rápida e a inicialização de contêineres, portanto, essas imagens são limitadas aos binários e ao conteúdo necessário para executar o aplicativo.

Para conseguir isso, a equipe do .NET fornece quatro variantes básicas em [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (no Hub do Docker):

1. **sdk**: para cenários de desenvolvimento e build
1. **aspnet**: para cenários de produção do ASP.NET
1. **runtime**: para cenários de produção do .NET
1. **runtime-deps**: para cenários de produção de [aplicativos autossuficientes](../../../core/deploying/index.md#self-contained-deployments-scd).

Para uma inicialização mais rápida, as imagens de runtime também definem automaticamente aspnetcore\_urls para a porta 80 e usam o Ngen para criar um cache de imagens nativas de assemblies.

#### <a name="additional-resources"></a>Recursos adicionais

- **Criando imagens otimizadas do Docker com o ASP.NET Core**  
  <https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/>

- **Criando Imagens do Docker para .NET Core Applications**  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> [Anterior](data-driven-crud-microservice.md)
> [Próximo](database-server-container.md)
