---
title: Definindo o aplicativo de vários contêineres com o docker-compose.yml
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Definindo o aplicativo de vários contêineres com o docker-compose.yml
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: 0c4eda54fbb1f48095d52fa798ea839eb509a636
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42754723"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="dfd09-103">Definindo o aplicativo de vários contêineres com o docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="dfd09-103">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="dfd09-104">Neste guia, o arquivo [docker-compose.yml](https://docs.docker.com/compose/compose-file/) foi apresentado na seção [Etapa 4. Definir os serviços no docker-compose.yml ao compilar um aplicativo de vários contêineres do Docker](#step4_define_svcs_in_docker_compose_yml).</span><span class="sxs-lookup"><span data-stu-id="dfd09-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="dfd09-105">No entanto, há outras maneiras de usar os arquivos docker-compose e vale a pena explorá-las com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="dfd09-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="dfd09-106">Por exemplo, você pode descrever explicitamente como deseja implantar o aplicativo de vários contêineres no arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="dfd09-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="dfd09-107">Opcionalmente, você também pode descrever como vai criar as imagens personalizadas do Docker.</span><span class="sxs-lookup"><span data-stu-id="dfd09-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="dfd09-108">(As imagens personalizadas do Docker também podem ser criadas com a CLI do Docker).</span><span class="sxs-lookup"><span data-stu-id="dfd09-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="dfd09-109">Basicamente, você define cada um dos contêineres que deseja implantar, além de determinadas características para cada implantação de contêiner.</span><span class="sxs-lookup"><span data-stu-id="dfd09-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="dfd09-110">Com um arquivo de descrição de implantação de vários contêineres pronto, você poderá implantar toda a solução por meio de uma única ação orquestrada pelo comando da CLI [docker-compose up](https://docs.docker.com/compose/overview/) ou poderá implantá-la de forma transparente no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dfd09-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="dfd09-111">Caso contrário, você teria que usar a CLI do Docker para implantar contêiner por contêiner, em várias etapas, usando o comando docker run na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="dfd09-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="dfd09-112">Portanto, cada serviço definido no docker-compose.yml deve especificar exatamente uma imagem ou build.</span><span class="sxs-lookup"><span data-stu-id="dfd09-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="dfd09-113">As outras chaves são opcionais e são semelhantes aos correspondentes do docker run na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="dfd09-113">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="dfd09-114">O código YAML a seguir é a definição de um arquivo docker-compose.yml possivelmente global, mas único, do exemplo eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="dfd09-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="dfd09-115">Esse não é o verdadeiro arquivo docker-compose do eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="dfd09-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="dfd09-116">Em vez disso, ele é uma versão simplificada e consolidada em um único arquivo, o que não é a melhor maneira de se trabalhar com arquivos docker-compose, como será explicado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="dfd09-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="dfd09-117">A chave de raiz desse arquivo é services.</span><span class="sxs-lookup"><span data-stu-id="dfd09-117">The root key in this file is services.</span></span> <span data-ttu-id="dfd09-118">Sob essa chave você define os serviços que você deseja implantar e executar, com o comando docker-compose up, ou ao implantar no Visual Studio usando esse arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="dfd09-118">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="dfd09-119">Nesse caso, o arquivo docker-compose.yml tem vários serviços definidos, conforme descrito na lista a seguir.</span><span class="sxs-lookup"><span data-stu-id="dfd09-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="dfd09-120">Contêiner webmvc, incluindo o aplicativo MVC do ASP.NET Core que consome os microsserviços do C\# do lado do servidor</span><span class="sxs-lookup"><span data-stu-id="dfd09-120">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="dfd09-121">Contêiner catalog.api, incluindo o microsserviço da API Web do Catálogo do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dfd09-121">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="dfd09-122">Contêiner ordering.api, incluindo o microsserviço da API Web de Pedidos do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dfd09-122">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="dfd09-123">Contêiner sql.data, que executa o SQL Server para Linux, mantendo os bancos de dados de microsserviços</span><span class="sxs-lookup"><span data-stu-id="dfd09-123">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="dfd09-124">Contêiner basket.api, com o microsserviço Carrinho de compras da API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dfd09-124">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="dfd09-125">Contêiner basket.data, que executa o Serviço de Cache Redis, com o banco de dados de carrinho de compras como um Cache Redis</span><span class="sxs-lookup"><span data-stu-id="dfd09-125">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="dfd09-126">Um contêiner de API de serviço Web simples</span><span class="sxs-lookup"><span data-stu-id="dfd09-126">A simple Web Service API container</span></span>

<span data-ttu-id="dfd09-127">Concentrando-se em um único contêiner, o microsserviço de contêiner catalog.api tem uma definição simples:</span><span class="sxs-lookup"><span data-stu-id="dfd09-127">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="dfd09-128">Esse serviço em contêiner tem a seguinte configuração básica:</span><span class="sxs-lookup"><span data-stu-id="dfd09-128">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="dfd09-129">Ele se baseia na imagem eshop/catalog.api personalizada.</span><span class="sxs-lookup"><span data-stu-id="dfd09-129">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="dfd09-130">Por questões de simplicidade, não há nenhuma definição de chave build: no arquivo.</span><span class="sxs-lookup"><span data-stu-id="dfd09-130">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="dfd09-131">Isso significa que a imagem deverá ser previamente compilada (com docker build) ou ser baixada (com o comando docker pull) de qualquer registro do Docker.</span><span class="sxs-lookup"><span data-stu-id="dfd09-131">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="dfd09-132">Ele define uma variável de ambiente denominada ConnectionString, com a cadeia de conexão a ser usada pelo Entity Framework para acessar a instância do SQL Server que contém o modelo de dados de catálogo.</span><span class="sxs-lookup"><span data-stu-id="dfd09-132">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="dfd09-133">Nesse caso, o mesmo contêiner do SQL Server está mantendo vários bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="dfd09-133">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="dfd09-134">Dessa forma, você precisará de menos memória no computador de desenvolvimento do Docker.</span><span class="sxs-lookup"><span data-stu-id="dfd09-134">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="dfd09-135">No entanto, você também poderia implantar um contêiner do SQL Server para cada banco de dados de microsserviço.</span><span class="sxs-lookup"><span data-stu-id="dfd09-135">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="dfd09-136">O nome do SQL Server é sql.data, que é o mesmo nome usado pelo contêiner que está executando a Instância do SQL Server para Linux.</span><span class="sxs-lookup"><span data-stu-id="dfd09-136">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="dfd09-137">Isso é conveniente: a possibilidade de usar essa resolução de nome (interna ao host do Docker) resolverá o endereço de rede, então você não precisará saber o IP interno dos contêineres que está acessando de outros contêineres.</span><span class="sxs-lookup"><span data-stu-id="dfd09-137">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="dfd09-138">Como a cadeia de conexão é definida por uma variável de ambiente, você pode definir essa variável por meio de um mecanismo diferente e em outro momento.</span><span class="sxs-lookup"><span data-stu-id="dfd09-138">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="dfd09-139">Por exemplo, você pode definir uma cadeia de conexão diferente durante a implantação em produção nos hosts finais ou fazer isso através dos pipelines de CI/CD no VSTS ou no sistema de DevOps de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="dfd09-139">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in VSTS or your preferred DevOps system.</span></span>

-   <span data-ttu-id="dfd09-140">Ele expõe a porta 80 para acesso interno ao serviço catalog.api dentro do host do Docker.</span><span class="sxs-lookup"><span data-stu-id="dfd09-140">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="dfd09-141">Atualmente o host é uma VM do Linux, porque ele se baseia em uma imagem do Docker para Linux, mas você também pode configurar o contêiner para ser executado em uma imagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="dfd09-141">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="dfd09-142">Ele encaminha a porta 80, exposta no contêiner, para a porta 5101 no computador host do Docker (a VM do Linux).</span><span class="sxs-lookup"><span data-stu-id="dfd09-142">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="dfd09-143">Ele vincula o serviço Web ao serviço sql.data (a instância do SQL Server para o banco de dados do Linux em execução em um contêiner).</span><span class="sxs-lookup"><span data-stu-id="dfd09-143">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="dfd09-144">Ao especificar essa dependência, o contêiner catalog.api não será iniciado até que o contêiner sql.data seja iniciado. Isso é importante porque o catalog.api precisa que o banco de dados do SQL Server esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="dfd09-144">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="dfd09-145">No entanto, esse tipo de dependência de contêiner não é suficiente em muitos casos, porque o Docker verifica apenas no nível de contêiner.</span><span class="sxs-lookup"><span data-stu-id="dfd09-145">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="dfd09-146">Às vezes, o serviço (o SQL Server, neste caso) poderá ainda não estar pronto, portanto, é aconselhável implementar uma lógica de repetição com retirada exponencial no microsserviço cliente.</span><span class="sxs-lookup"><span data-stu-id="dfd09-146">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="dfd09-147">Dessa forma, se um contêiner de dependência não estiver pronto durante um breve período de tempo, o aplicativo continuará resiliente.</span><span class="sxs-lookup"><span data-stu-id="dfd09-147">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="dfd09-148">Ele é configurado para permitir o acesso a servidores externos: a configuração extra\_hosts permite que você acesse servidores externos ou computadores fora do host do Docker (ou seja, fora da VM do Linux padrão, que é um host do Docker para desenvolvimento), como uma Instância do SQL Server local em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="dfd09-148">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="dfd09-149">Também há outras configurações mais avançadas do docker-compose.yml que discutiremos nas próximas seções.</span><span class="sxs-lookup"><span data-stu-id="dfd09-149">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="dfd09-150">Usando arquivos docker-compose para destinar-se a vários ambientes</span><span class="sxs-lookup"><span data-stu-id="dfd09-150">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="dfd09-151">Os arquivos docker-compose.yml são arquivos de definição e podem ser usados por várias infraestruturas que entendem esse formato.</span><span class="sxs-lookup"><span data-stu-id="dfd09-151">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="dfd09-152">A ferramenta mais simples é o comando docker-compose, mas outras ferramentas, como orquestradores (por exemplo, o Docker Swarm), também entendem esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="dfd09-152">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="dfd09-153">Portanto, ao usar o comando docker-compose você pode ter os seguintes principais cenários como destino.</span><span class="sxs-lookup"><span data-stu-id="dfd09-153">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="dfd09-154">Ambientes de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="dfd09-154">Development environments</span></span>

<span data-ttu-id="dfd09-155">Ao desenvolver aplicativos, é importante ser capaz de executar um aplicativo em um ambiente de desenvolvimento isolado.</span><span class="sxs-lookup"><span data-stu-id="dfd09-155">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="dfd09-156">Você pode usar o comando de CLI docker-compose para criar esse ambiente ou usar o Visual Studio, que usa o docker-compose nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="dfd09-156">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="dfd09-157">O arquivo docker-compose.yml permite que você configure e documente todas as dependências de serviço do seu aplicativo (outros serviços, cache, bancos de dados, filas, etc.).</span><span class="sxs-lookup"><span data-stu-id="dfd09-157">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="dfd09-158">Ao usar o comando de CLI docker-compose, você pode criar e iniciar um ou mais contêineres para cada dependência com um único comando (docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="dfd09-158">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="dfd09-159">Os docker-compose.yml são arquivos de configuração interpretados pelo mecanismo do Docker, mas também servem como arquivos de documentação convenientes, com informações sobre a composição de seu aplicativo para vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="dfd09-159">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="dfd09-160">Ambientes de teste</span><span class="sxs-lookup"><span data-stu-id="dfd09-160">Testing environments</span></span>

<span data-ttu-id="dfd09-161">Uma parte importante de qualquer processo de CD (implantação contínua) ou CI (integração contínua) são os testes de unidade e testes de integração.</span><span class="sxs-lookup"><span data-stu-id="dfd09-161">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="dfd09-162">Esses testes automatizados exigem um ambiente isolado para que não sejam afetados por usuários ou qualquer outra alteração nos dados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dfd09-162">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="dfd09-163">Com o Docker Compose, você pode criar e destruir esse ambiente isolado facilmente por meio de alguns comandos no prompt de comando ou por meio de scripts, como os comandos a seguir:</span><span class="sxs-lookup"><span data-stu-id="dfd09-163">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="dfd09-164">Implantações de produção</span><span class="sxs-lookup"><span data-stu-id="dfd09-164">Production deployments</span></span>

<span data-ttu-id="dfd09-165">Você também pode usar o Compose para implantar em um mecanismo remoto do Docker.</span><span class="sxs-lookup"><span data-stu-id="dfd09-165">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="dfd09-166">Um caso comum é a implantação em uma única instância de host do Docker (como uma VM ou servidor de produção, provisionados com o [Docker Machine](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="dfd09-166">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="dfd09-167">Mas também poderia ser em um cluster [Docker Swarm](https://docs.docker.com/swarm/overview/) inteiro, porque os clusters também são compatíveis com os arquivos docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="dfd09-167">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="dfd09-168">Se estiver usando qualquer outro orquestrador (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), você precisará adicionar configurações de instalação e metadados, como aqueles no docker-compose.yml, mas no formato exigido pelo outro orquestrador.</span><span class="sxs-lookup"><span data-stu-id="dfd09-168">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="dfd09-169">De qualquer maneira, o docker-compose é uma ferramenta conveniente e um formato de metadados para fluxos de trabalho de desenvolvimento, teste e produção, embora o fluxo de trabalho de produção possa variar no orquestrador que você está usando.</span><span class="sxs-lookup"><span data-stu-id="dfd09-169">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="dfd09-170">Usando vários arquivos docker-compose para lidar com diversos ambientes</span><span class="sxs-lookup"><span data-stu-id="dfd09-170">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="dfd09-171">Ao destinar-se a ambientes diferentes, você deve usar vários arquivos compose.</span><span class="sxs-lookup"><span data-stu-id="dfd09-171">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="dfd09-172">Isso permite que você crie diversas variantes de configuração, dependendo do ambiente.</span><span class="sxs-lookup"><span data-stu-id="dfd09-172">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="dfd09-173">Substituindo o arquivo base docker-compose</span><span class="sxs-lookup"><span data-stu-id="dfd09-173">Overriding the base docker-compose file</span></span>

<span data-ttu-id="dfd09-174">Você pode usar um único arquivo docker-compose.yml, como nos exemplos simplificados mostrados nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="dfd09-174">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="dfd09-175">No entanto, isso não é recomendável para a maioria dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="dfd09-175">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="dfd09-176">Por padrão, o Compose lê dois arquivos, um docker-compose.yml e um arquivo docker-compose.override.yml opcional.</span><span class="sxs-lookup"><span data-stu-id="dfd09-176">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="dfd09-177">Conforme mostrado na Figura 8-11, quando você está usando o Visual Studio e habilitando o suporte do Docker, o Visual Studio também cria outro arquivo yml, o docker-compose.ci.build, para que você use nos pipelines de CI/CD, como no VSTS.</span><span class="sxs-lookup"><span data-stu-id="dfd09-177">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.ci.build,yml file for you to use from your CI/CD pipelines like in VSTS.</span></span>

![](./media/image12.png)

<span data-ttu-id="dfd09-178">**Figura 8-11**.</span><span class="sxs-lookup"><span data-stu-id="dfd09-178">**Figure 8-11**.</span></span> <span data-ttu-id="dfd09-179">Arquivos docker-compose no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="dfd09-179">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="dfd09-180">Você pode editar os arquivos docker-compose com qualquer editor, como o Visual Studio Code ou o Sublime, e executar o aplicativo com o comando docker-compose up.</span><span class="sxs-lookup"><span data-stu-id="dfd09-180">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="dfd09-181">Por convenção, o arquivo docker-compose.yml contém sua configuração base e outras configurações estáticas.</span><span class="sxs-lookup"><span data-stu-id="dfd09-181">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="dfd09-182">Isso significa que a configuração do serviço não deve ser alterada de acordo com o ambiente de implantação que você tem como destino.</span><span class="sxs-lookup"><span data-stu-id="dfd09-182">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="dfd09-183">O arquivo docker-compose.override.yml, como o próprio nome sugere, contém definições de configuração que substituem a configuração base, como a configuração que depende do ambiente de implantação.</span><span class="sxs-lookup"><span data-stu-id="dfd09-183">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="dfd09-184">Você também pode ter vários arquivos de substituição com nomes diferentes.</span><span class="sxs-lookup"><span data-stu-id="dfd09-184">You can have multiple override files with different names also.</span></span> <span data-ttu-id="dfd09-185">Os arquivos de substituição geralmente contêm informações adicionais, exigidas pelo aplicativo, bem como as informações específicas de um ambiente ou uma implantação.</span><span class="sxs-lookup"><span data-stu-id="dfd09-185">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="dfd09-186">Destinando-se a vários ambientes</span><span class="sxs-lookup"><span data-stu-id="dfd09-186">Targeting multiple environments</span></span>

<span data-ttu-id="dfd09-187">Um caso de uso típico é aquele em que você define vários arquivos compose para destinar-se a vários ambientes, como de produção, de preparo, de CI ou de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="dfd09-187">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="dfd09-188">Para dar suporte a essas diferenças, você pode dividir a configuração do Compose em vários arquivos, conforme mostrado na Figura 8-12.</span><span class="sxs-lookup"><span data-stu-id="dfd09-188">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="dfd09-189">**Figura 8-12**.</span><span class="sxs-lookup"><span data-stu-id="dfd09-189">**Figure 8-12**.</span></span> <span data-ttu-id="dfd09-190">Vários arquivos docker-compose substituindo valores no arquivo base docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="dfd09-190">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="dfd09-191">Você inicia com o arquivo base docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="dfd09-191">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="dfd09-192">Esse arquivo base deve conter as definições de configuração base ou estáticas que não se alteram de acordo com o ambiente.</span><span class="sxs-lookup"><span data-stu-id="dfd09-192">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="dfd09-193">Por exemplo, o eShopOnContainers tem o seguinte arquivo docker-compose.yml como o arquivo base.</span><span class="sxs-lookup"><span data-stu-id="dfd09-193">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

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

<span data-ttu-id="dfd09-194">Os valores do arquivo base docker-compose.yml não devem se alterar devido aos diferentes ambientes de implantação de destino.</span><span class="sxs-lookup"><span data-stu-id="dfd09-194">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="dfd09-195">Se você se concentrar na definição do serviço webmvc, por exemplo, verá como essa informação é muito semelhante independentemente do ambiente ao qual você se destina.</span><span class="sxs-lookup"><span data-stu-id="dfd09-195">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="dfd09-196">Você tem as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="dfd09-196">You have the following information:</span></span>

-   <span data-ttu-id="dfd09-197">O nome do serviço: webmvc.</span><span class="sxs-lookup"><span data-stu-id="dfd09-197">The service name: webmvc.</span></span>

-   <span data-ttu-id="dfd09-198">A imagem personalizada do contêiner: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="dfd09-198">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="dfd09-199">O comando para compilar a imagem personalizada do Docker, que indica qual Dockerfile usar.</span><span class="sxs-lookup"><span data-stu-id="dfd09-199">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="dfd09-200">As dependências de outros serviços, para que este contêiner não se inicie até que os outros contêineres de dependência sejam iniciados.</span><span class="sxs-lookup"><span data-stu-id="dfd09-200">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="dfd09-201">Você pode ter outras configurações, mas o ponto importante é que, no arquivo base docker-compose.yml, é necessário definir apenas as informações que são comuns entre ambientes.</span><span class="sxs-lookup"><span data-stu-id="dfd09-201">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="dfd09-202">Então, no docker-compose.override.yml ou em arquivos semelhantes de produção ou de preparo, você deve colocar a configuração específica para cada ambiente.</span><span class="sxs-lookup"><span data-stu-id="dfd09-202">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="dfd09-203">Normalmente, o docker-compose.override.yml é usado para o ambiente de desenvolvimento, como no exemplo a seguir, do eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="dfd09-203">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

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

<span data-ttu-id="dfd09-204">Neste exemplo, a configuração de substituição de desenvolvimento expõe algumas portas para o host, define variáveis de ambiente com URLs de redirecionamento e especifica cadeias de conexão para o ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="dfd09-204">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="dfd09-205">Todas essas configurações são apenas para o ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="dfd09-205">These settings are all just for the development environment.</span></span>

<span data-ttu-id="dfd09-206">Quando você executa `docker-compose up` (ou o inicia no Visual Studio), o comando lerá as substituições automaticamente como se estivesse mesclando os dois arquivos.</span><span class="sxs-lookup"><span data-stu-id="dfd09-206">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="dfd09-207">Suponha que você deseja outro arquivo do Compose para o ambiente de produção, com valores de configuração, de portas ou de cadeias de conexão diferentes.</span><span class="sxs-lookup"><span data-stu-id="dfd09-207">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="dfd09-208">Você pode criar outro arquivo de substituição, como um arquivo chamado `docker-compose.prod.yml`, com diferentes configurações e variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="dfd09-208">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="dfd09-209">Esse arquivo poderá ser armazenado em outro repositório GIT ou gerenciado e protegido por uma equipe diferente.</span><span class="sxs-lookup"><span data-stu-id="dfd09-209">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="dfd09-210">Como implantar com um arquivo de substituição específico</span><span class="sxs-lookup"><span data-stu-id="dfd09-210">How to deploy with a specific override file</span></span>

<span data-ttu-id="dfd09-211">Para usar vários arquivos de substituição, ou um arquivo de substituição com um nome diferente, use a opção -f com o comando docker-compose e especifique os arquivos.</span><span class="sxs-lookup"><span data-stu-id="dfd09-211">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="dfd09-212">O Compose mescla os arquivos na ordem em que eles são especificados na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="dfd09-212">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="dfd09-213">O exemplo a seguir mostra como implantar com arquivos de substituição.</span><span class="sxs-lookup"><span data-stu-id="dfd09-213">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="dfd09-214">Usando variáveis de ambiente em arquivos docker-compose</span><span class="sxs-lookup"><span data-stu-id="dfd09-214">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="dfd09-215">É conveniente, especialmente em ambientes de produção, ter a possibilidade de obter informações de configuração de variáveis de ambiente, como mostramos em exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="dfd09-215">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="dfd09-216">Faça referência a uma variável de ambiente em arquivos docker-compose, usando a sintaxe \${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="dfd09-216">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="dfd09-217">A seguinte linha de um arquivo docker-compose.prod.yml mostra como referenciar o valor de uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="dfd09-217">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="dfd09-218">As variáveis de ambiente são criadas e inicializadas de diferentes maneiras, dependendo do ambiente de host (Linux, Windows, cluster de nuvem, etc.).</span><span class="sxs-lookup"><span data-stu-id="dfd09-218">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="dfd09-219">Entretanto, uma abordagem conveniente é usar um arquivo .env.</span><span class="sxs-lookup"><span data-stu-id="dfd09-219">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="dfd09-220">Os arquivos docker-compose são compatíveis com a declaração de variáveis de ambiente padrão no arquivo .env.</span><span class="sxs-lookup"><span data-stu-id="dfd09-220">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="dfd09-221">Esses valores das variáveis de ambiente são os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="dfd09-221">These values for the environment variables are the default values.</span></span> <span data-ttu-id="dfd09-222">Mas elas podem ser substituídas pelos valores que você definiu em cada um dos ambientes (sistema operacional de host ou variáveis de ambiente do cluster).</span><span class="sxs-lookup"><span data-stu-id="dfd09-222">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="dfd09-223">Coloque esse arquivo .env na pasta em que o comando docker-compose é executado.</span><span class="sxs-lookup"><span data-stu-id="dfd09-223">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="dfd09-224">O exemplo a seguir mostra um arquivo .env parecido com o [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) do aplicativo eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="dfd09-224">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="dfd09-225">O docker-compose espera que cada linha de um arquivo .env esteja no formato &lt;variável&gt;=&lt;valor&gt;.</span><span class="sxs-lookup"><span data-stu-id="dfd09-225">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="dfd09-226">Observe que os valores definidos no ambiente do tempo de execução sempre substituem os valores definidos no arquivo .env.</span><span class="sxs-lookup"><span data-stu-id="dfd09-226">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="dfd09-227">De maneira semelhante, os valores passados por meio de argumentos de linha de comando também substituem os valores padrão definidos no arquivo .env.</span><span class="sxs-lookup"><span data-stu-id="dfd09-227">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="dfd09-228">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="dfd09-228">Additional resources</span></span>

-   <span data-ttu-id="dfd09-229">**Visão geral do Docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="dfd09-229">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="dfd09-230">**Vários arquivos Compose**
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="dfd09-230">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="dfd09-231">Criando imagens do Docker do ASP.NET Core otimizadas</span><span class="sxs-lookup"><span data-stu-id="dfd09-231">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="dfd09-232">Se estiver explorando o Docker e o .NET Core em fontes na Internet, você encontrará Dockerfiles que demonstram a simplicidade da criação de uma imagem do Docker por meio da cópia da fonte em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="dfd09-232">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="dfd09-233">Esses exemplos sugerem que, ao usar uma configuração simples, você pode ter uma imagem do Docker com o ambiente empacotado com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dfd09-233">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="dfd09-234">O exemplo a seguir mostra um Dockerfile simples neste sentido.</span><span class="sxs-lookup"><span data-stu-id="dfd09-234">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="dfd09-235">Um Dockerfile como esse funcionará.</span><span class="sxs-lookup"><span data-stu-id="dfd09-235">A Dockerfile like this will work.</span></span> <span data-ttu-id="dfd09-236">No entanto, você pode otimizar substancialmente suas imagens, especialmente as imagens de produção.</span><span class="sxs-lookup"><span data-stu-id="dfd09-236">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="dfd09-237">No modelo de contêiner e microsserviços, você está constantemente iniciando contêineres.</span><span class="sxs-lookup"><span data-stu-id="dfd09-237">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="dfd09-238">O modo comum de uso de contêineres não reinicia um contêiner em suspensão porque o contêiner é descartável.</span><span class="sxs-lookup"><span data-stu-id="dfd09-238">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="dfd09-239">Orquestradores, como Docker Swarm, Kubernetes, DCOS ou Azure Service Fabric, simplesmente criam novas instâncias de imagens.</span><span class="sxs-lookup"><span data-stu-id="dfd09-239">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="dfd09-240">Isso significa que você precisará otimizar por meio da pré-compilação do aplicativo quando ele for criado, fazendo com que o processo de instanciação seja mais rápido.</span><span class="sxs-lookup"><span data-stu-id="dfd09-240">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="dfd09-241">Quando o contêiner é iniciado, ele deve estar pronto para executar.</span><span class="sxs-lookup"><span data-stu-id="dfd09-241">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="dfd09-242">Você não deve restaurar e compilar em tempo de execução, usando os comandos dotnet restore e dotnet build na CLI do dotnet, como você pode ver em várias postagens de blog sobre o .NET Core e o Docker.</span><span class="sxs-lookup"><span data-stu-id="dfd09-242">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="dfd09-243">A equipe do .NET está realizando um trabalho importante para tornar o .NET Core e o ASP.NET Core uma estrutura otimizada para contêineres.</span><span class="sxs-lookup"><span data-stu-id="dfd09-243">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="dfd09-244">O .NET Core não é apenas uma estrutura leve com um volume de memória pequeno; a equipe tem se concentrado no desempenho de inicialização e produzido algumas imagens de Docker otimizadas, como a imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/), disponível no [Hub do Docker](https://hub.docker.com/r/microsoft/aspnetcore/), em comparação com as imagens [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) ou [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) regulares.</span><span class="sxs-lookup"><span data-stu-id="dfd09-244">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="dfd09-245">A imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) fornece configuração automática de aspnetcore\_urls para a porta 80 e o cache de assemblies pré criado; essas duas configurações resultam em inicialização mais rápida.</span><span class="sxs-lookup"><span data-stu-id="dfd09-245">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="dfd09-246">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="dfd09-246">Additional resources</span></span>

-   <span data-ttu-id="dfd09-247">**Criando imagens otimizadas do Docker com o ASP.NET Core**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="dfd09-247">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="dfd09-248">Compilando o aplicativo em um contêiner de build (CI)</span><span class="sxs-lookup"><span data-stu-id="dfd09-248">Building the application from a build (CI) container</span></span>

<span data-ttu-id="dfd09-249">Outro benefício do Docker é que você pode compilar o aplicativo em um contêiner pré-configurado, conforme mostrado na Figura 8-13, evitando a necessidade de criar um computador de build ou uma VM para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dfd09-249">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="dfd09-250">Você pode usar ou testar esse contêiner de build executando-o em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="dfd09-250">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="dfd09-251">E o que é ainda mais interessante é que você pode usar o mesmo contêiner de build em seu pipeline de CI (integração contínua).</span><span class="sxs-lookup"><span data-stu-id="dfd09-251">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="dfd09-252">**Figura 8-13**.</span><span class="sxs-lookup"><span data-stu-id="dfd09-252">**Figure 8-13**.</span></span> <span data-ttu-id="dfd09-253">Contêiner de build do Docker compilando os binários de .NET</span><span class="sxs-lookup"><span data-stu-id="dfd09-253">Docker build-container compiling your .NET binaries</span></span> 

<span data-ttu-id="dfd09-254">Para este cenário, fornecemos a imagem [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/), que você pode usar para compilar e criar os aplicativos do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfd09-254">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="dfd09-255">A saída é colocada em uma imagem baseada na imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/), que é uma imagem de tempo de execução otimizado, conforme observado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="dfd09-255">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="dfd09-256">A imagem aspnetcore-build contém tudo o que você precisa para compilar um aplicativo do ASP.NET Core, incluindo o .NET Core, o SDK do ASP.NET, o npm, o Bower, o Gulp, etc.</span><span class="sxs-lookup"><span data-stu-id="dfd09-256">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="dfd09-257">Essas dependências são necessárias no momento do build.</span><span class="sxs-lookup"><span data-stu-id="dfd09-257">We need these dependencies at build time.</span></span> <span data-ttu-id="dfd09-258">No entanto, não queremos levá-las com o aplicativo em tempo de execução, porque isso tornaria a imagem desnecessariamente grande.</span><span class="sxs-lookup"><span data-stu-id="dfd09-258">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="dfd09-259">No aplicativo eShopOnContainers, você pode compilar o aplicativo em um contêiner simplesmente por meio da execução do seguinte comando docker-compose.</span><span class="sxs-lookup"><span data-stu-id="dfd09-259">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="dfd09-260">A figura 8-14 mostra este comando em execução na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="dfd09-260">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="dfd09-261">**Figura 8-14.**</span><span class="sxs-lookup"><span data-stu-id="dfd09-261">**Figure 8-14.**</span></span> <span data-ttu-id="dfd09-262">Compilando seu aplicativo do .NET em um contêiner</span><span class="sxs-lookup"><span data-stu-id="dfd09-262">Building your .NET application from a container</span></span>

<span data-ttu-id="dfd09-263">Como você pode ver, o contêiner que está sendo executado é o contêiner ci-build\_1.</span><span class="sxs-lookup"><span data-stu-id="dfd09-263">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="dfd09-264">Ele se baseia na imagem aspnetcore-build para que possa compilar e criar o aplicativo inteiro de dentro do contêiner em vez de fazê-lo em seu computador.</span><span class="sxs-lookup"><span data-stu-id="dfd09-264">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="dfd09-265">É por isso que, na verdade, ele está criando e compilando os projetos do .NET Core no Linux, porque esse contêiner está em execução no host Linux do Docker padrão.</span><span class="sxs-lookup"><span data-stu-id="dfd09-265">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="dfd09-266">O arquivo [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) dessa imagem (parte do eShopOnContainers) contém o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="dfd09-266">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="dfd09-267">Veja que ele inicia um contêiner de build usando a imagem [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/).</span><span class="sxs-lookup"><span data-stu-id="dfd09-267">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

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

* <span data-ttu-id="dfd09-268">Começando com o **.NET Core 2.0**, o comando `dotnet restore` é executado automaticamente quando o comando `dotnet publish` é executado.</span><span class="sxs-lookup"><span data-stu-id="dfd09-268">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="dfd09-269">Após o contêiner de build estar em funcionamento, ele executará os comandos dotnet restore e dotnet publish do SDK do .NET em todos os projetos da solução, a fim de compilar os bits do .NET.</span><span class="sxs-lookup"><span data-stu-id="dfd09-269">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="dfd09-270">Nesse caso, como o eShopOnContainers também tem um SPA com base em TypeScript e Angular para o código do cliente, ele também precisa verificar as dependências de JavaScript com o npm, mas essa ação não está relacionada com os bits do .NET.</span><span class="sxs-lookup"><span data-stu-id="dfd09-270">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="dfd09-271">O comando dotnet publish compila e publica a saída compilada dentro da pasta de cada projeto na pasta ../obj/Docker/publish, conforme mostrado na Figura 8-15.</span><span class="sxs-lookup"><span data-stu-id="dfd09-271">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="dfd09-272">**Figura 8-15.**</span><span class="sxs-lookup"><span data-stu-id="dfd09-272">**Figure 8-15.**</span></span> <span data-ttu-id="dfd09-273">Arquivos binários gerados pelo comando dotnet publish</span><span class="sxs-lookup"><span data-stu-id="dfd09-273">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="dfd09-274">Criando as imagens do Docker por meio da CLI</span><span class="sxs-lookup"><span data-stu-id="dfd09-274">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="dfd09-275">Depois que a saída do aplicativo é publicada nas pastas relacionadas (dentro de cada projeto), a próxima etapa é criar as imagens do Docker.</span><span class="sxs-lookup"><span data-stu-id="dfd09-275">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="dfd09-276">Para fazer isso, você usa os comandos docker-compose build e docker-compose up, conforme mostrado na Figura 8-16.</span><span class="sxs-lookup"><span data-stu-id="dfd09-276">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="dfd09-277">**Figura 8-16.**</span><span class="sxs-lookup"><span data-stu-id="dfd09-277">**Figure 8-16.**</span></span> <span data-ttu-id="dfd09-278">Criando imagens do Docker e executando os contêineres</span><span class="sxs-lookup"><span data-stu-id="dfd09-278">Building Docker images and running the containers</span></span>

<span data-ttu-id="dfd09-279">Na Figura 8-17, você pode ver como o comando docker-compose build é executado.</span><span class="sxs-lookup"><span data-stu-id="dfd09-279">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="dfd09-280">**Figura 8-17**.</span><span class="sxs-lookup"><span data-stu-id="dfd09-280">**Figure 8-17**.</span></span> <span data-ttu-id="dfd09-281">Criando as imagens do Docker com o comando docker-compose build</span><span class="sxs-lookup"><span data-stu-id="dfd09-281">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="dfd09-282">A diferença entre os comandos docker-compose build e docker-compose up é que o docker-compose up compila e inicia as imagens.</span><span class="sxs-lookup"><span data-stu-id="dfd09-282">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="dfd09-283">Quando você usa o Visual Studio, todas essas etapas são realizadas nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="dfd09-283">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="dfd09-284">O Visual Studio compila seu aplicativo do .NET, cria as imagens do Docker e implanta os contêineres no host do Docker.</span><span class="sxs-lookup"><span data-stu-id="dfd09-284">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="dfd09-285">O Visual Studio oferece recursos adicionais, como a capacidade de depurar seus contêineres em execução no Docker diretamente no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dfd09-285">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="dfd09-286">A conclusão geral aqui é que você pode compilar seu aplicativo da mesma maneira que o pipeline de CI/CD deveria fazê-lo — em um contêiner em vez de um computador local.</span><span class="sxs-lookup"><span data-stu-id="dfd09-286">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="dfd09-287">Depois que as imagens são criadas, você só precisa executar as imagens do Docker usando o comando docker-compose up.</span><span class="sxs-lookup"><span data-stu-id="dfd09-287">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="dfd09-288">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="dfd09-288">Additional resources</span></span>

-   <span data-ttu-id="dfd09-289">**Criando bits com base em um contêiner: configurando a solução eShopOnContainers em um ambiente da CLI do Windows (CLI do dotnet, CLI do Docker e VS Code)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="dfd09-289">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="dfd09-290">[Anterior](data-driven-crud-microservice.md)
[Próximo](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="dfd09-290">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
