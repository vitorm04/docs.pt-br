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
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="3d8c2-104">Define o seu aplicativo de multi-contêiner com docker compose.yml</span><span class="sxs-lookup"><span data-stu-id="3d8c2-104">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="3d8c2-105">Neste guia, o [docker compose.yml](https://docs.docker.com/compose/compose-file/) arquivo foi apresentado na seção [etapa 4. Definir os serviços no docker compose.yml ao compilar um aplicativo de multi-contêiner de Docker](#step4_define_svcs_in_docker_compose_yml).</span><span class="sxs-lookup"><span data-stu-id="3d8c2-105">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="3d8c2-106">No entanto, existem outras maneiras de usar os arquivos de docker-compose que vale a pena explorar mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-106">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="3d8c2-107">Por exemplo, você pode descrever explicitamente como você deseja implantar seu aplicativo de multi-contêiner no arquivo compose.yml docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-107">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="3d8c2-108">Opcionalmente, você também pode descrever como você vai criar imagens personalizadas do Docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-108">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="3d8c2-109">(As imagens do Docker personalizados também podem ser criadas com a CLI do Docker.)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-109">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="3d8c2-110">Basicamente, você define cada um dos contêineres que você deseja implantar além de certas características para cada implantação de contêiner.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-110">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="3d8c2-111">Uma vez que um arquivo de descrição do multi-contêiner implantação, você pode implantar a solução completa em uma única ação orquestrada pelo [compor docker backup](https://docs.docker.com/compose/overview/) comando CLI, ou você pode implantá-lo transparente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-111">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="3d8c2-112">Caso contrário, você precisa usar a CLI do Docker para implantar por container em várias etapas, usando o comando docker run na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-112">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="3d8c2-113">Portanto, cada serviço definido no docker compose.yml deve especificar exatamente uma imagem ou de compilação.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-113">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="3d8c2-114">Outras chaves são opcionais e são análogos às sua contrapartes de linha de comando de execução de docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-114">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="3d8c2-115">O código a seguir YAML é a definição de um arquivo de possíveis global mas único docker-compose.yml para o exemplo eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-115">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="3d8c2-116">Isso não é o arquivo real docker-compose eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-116">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="3d8c2-117">Em vez disso, é uma versão simplificada e consolidada em um único arquivo, que não é a melhor maneira de trabalhar com o docker-compor arquivos, como será explicado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-117">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="3d8c2-118">A chave de raiz no arquivo é services.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-118">The root key in this file is services.</span></span> <span data-ttu-id="3d8c2-119">Sob essa chave é definir os serviços que você deseja implantar e executar quando você executar o docker-compor o comando ou quando você implanta no Visual Studio usando esse arquivo compose.yml docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-119">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="3d8c2-120">Nesse caso, o arquivo de docker compose.yml tem vários serviços definidos, conforme descrito na lista a seguir.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-120">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="3d8c2-121">webmvc contêiner, incluindo o aplicativo MVC do ASP.NET Core consumindo microservices do lado do servidor C\#</span><span class="sxs-lookup"><span data-stu-id="3d8c2-121">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="3d8c2-122">Catalog.API contêiner, incluindo o API da Web do catálogo ASP.NET Core microsserviço</span><span class="sxs-lookup"><span data-stu-id="3d8c2-122">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="3d8c2-123">Ordering.API contêiner, incluindo o ordenação de API de Web do ASP.NET Core microsserviço</span><span class="sxs-lookup"><span data-stu-id="3d8c2-123">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="3d8c2-124">SQL.Data contêiner executando o SQL Server para Linux, mantendo os bancos de dados microservices</span><span class="sxs-lookup"><span data-stu-id="3d8c2-124">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="3d8c2-125">basket.API contêiner com o API da Web do carrinho ASP.NET Core microsserviço</span><span class="sxs-lookup"><span data-stu-id="3d8c2-125">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="3d8c2-126">basket.Data contêiner executando o serviço de cache do REDIS, com o banco de dados de compras como um cache REDIS</span><span class="sxs-lookup"><span data-stu-id="3d8c2-126">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="3d8c2-127">Um contêiner de API do serviço Web simples</span><span class="sxs-lookup"><span data-stu-id="3d8c2-127">A simple Web Service API container</span></span>

<span data-ttu-id="3d8c2-128">Concentrando-se em um único contêiner, o contêiner-microsserviço catalog.api tem uma definição simples:</span><span class="sxs-lookup"><span data-stu-id="3d8c2-128">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="3d8c2-129">Esse serviço em contêineres tem a seguinte configuração básica:</span><span class="sxs-lookup"><span data-stu-id="3d8c2-129">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="3d8c2-130">Ele se baseia a imagem eshop/catalog.api personalizado.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-130">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="3d8c2-131">Para simplificar, não há nenhuma compilação: definição no arquivo de chave.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-131">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="3d8c2-132">Isso significa que a imagem deve foram previamente criados (com o build do docker) ou ter sido baixado (com o comando do docker pull) de qualquer registro de Docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-132">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="3d8c2-133">Define uma variável de ambiente denominada ConnectionString com a cadeia de caracteres de conexão a ser usada pelo Entity Framework para acessar a instância do SQL Server que contém o modelo de dados de catálogo.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-133">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="3d8c2-134">Nesse caso, o mesmo contêiner de SQL Server está mantendo vários bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-134">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="3d8c2-135">Portanto, você precisa menos memória no computador de desenvolvimento para Docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-135">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="3d8c2-136">No entanto, você também pode implantar um contêiner do SQL Server para cada banco de dados de microsserviço.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-136">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="3d8c2-137">O nome do SQL Server é sql.data, que é o mesmo nome usado para o contêiner que está executando a instância do SQL Server para Linux.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-137">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="3d8c2-138">Isso é prático; poder usar essa resolução de nome (interna para o host do Docker) resolverá o endereço de rede, você não precisa saber o IP interno para os contêineres que você está acessando de outros contêineres.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-138">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="3d8c2-139">Como a cadeia de caracteres de conexão é definida por uma variável de ambiente, você pode definir essa variável por meio de um mecanismo diferente e em um horário diferente.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-139">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="3d8c2-140">Por exemplo, você pode definir uma cadeia de caracteres de conexão diferente durante a implantação em produção, os hosts final ou através de seus pipelines de CI/CD no VSTS ou sistema DevOps preferencial.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-140">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in VSTS or your preferred DevOps system.</span></span>

-   <span data-ttu-id="3d8c2-141">Expõe a porta 80 para acesso interno ao serviço catalog.api dentro do host do Docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-141">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="3d8c2-142">O host atualmente é uma VM do Linux, porque ele se baseia em uma imagem do Docker para Linux, mas você pode configurar o contêiner para executar uma imagem do Windows em vez disso.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-142">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="3d8c2-143">Ele encaminha a exposto a porta 80 no contêiner para a porta 5101 na máquina de host do Docker (VM Linux).</span><span class="sxs-lookup"><span data-stu-id="3d8c2-143">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="3d8c2-144">Vincula o serviço da web para o serviço de sql.data (a instância do SQL Server para o banco de dados do Linux em execução em um contêiner).</span><span class="sxs-lookup"><span data-stu-id="3d8c2-144">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="3d8c2-145">Quando você especificar essa dependência, o contêiner catalog.api não será iniciado até que o contêiner sql.data já foi iniciado; Isso é importante porque catalog.api deve ter o banco de dados do SQL Server e executado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-145">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="3d8c2-146">No entanto, esse tipo de dependência do contêiner não é suficiente em muitos casos, porque Docker verifica apenas no nível do contêiner.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-146">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="3d8c2-147">Às vezes, o serviço (no SQL Server neste caso) talvez ainda não esteja pronto, portanto, é aconselhável para implementar a lógica de repetição com retirada exponencial em seu cliente microservices.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-147">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="3d8c2-148">Dessa forma, se um contêiner de dependência não está pronto para um curto período de tempo, o aplicativo ainda será resiliente.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-148">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="3d8c2-149">Ele é configurado para permitir o acesso a servidores externos: adicionais\_hosts configuração permite que você acesse os servidores externos ou máquinas fora do host do Docker (ou seja, fora da VM do Linux que é um desenvolvimento Docker padrão de host), como um SQL local Instância de servidor em seu PC de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-149">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="3d8c2-150">Também existem outras configurações mais avançadas de docker compose.yml que discutiremos nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-150">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="3d8c2-151">Usando o docker-compor arquivos para vários ambientes de destino</span><span class="sxs-lookup"><span data-stu-id="3d8c2-151">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="3d8c2-152">Os arquivos de docker compose.yml são arquivos de definição e podem ser usados por várias infraestruturas entendem esse formato.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-152">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="3d8c2-153">A ferramenta mais simples é o docker-compor o comando, mas outras ferramentas como orchestrators (por exemplo, Docker Swarm) também entender esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-153">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="3d8c2-154">Portanto, usando o docker-compor o comando que você pode direcionar os cenários principais a seguir.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-154">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="3d8c2-155">Ambientes de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="3d8c2-155">Development environments</span></span>

<span data-ttu-id="3d8c2-156">Ao desenvolver aplicativos, é importante poder executar um aplicativo em um ambiente de desenvolvimento isolado.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-156">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="3d8c2-157">Você pode usar o comando CLI para criar esse ambiente ou use o Visual Studio que usa compor docker nos bastidores de compor docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-157">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="3d8c2-158">O arquivo compose.yml docker permite que você configure e documentar todas as dependências do seu aplicativo serviço (outros serviços, cache, bancos de dados, filas, etc.).</span><span class="sxs-lookup"><span data-stu-id="3d8c2-158">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="3d8c2-159">Usando o comando CLI de compor docker, você pode criar e iniciar um ou mais contêineres para cada dependência com um único comando (docker-compor backup).</span><span class="sxs-lookup"><span data-stu-id="3d8c2-159">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="3d8c2-160">Docker compose.yml são arquivos de configuração interpretados pelo mecanismo do Docker, mas também servem como arquivos de documentação conveniente sobre a composição de seu aplicativo de contêiner vários.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-160">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="3d8c2-161">Ambientes de teste</span><span class="sxs-lookup"><span data-stu-id="3d8c2-161">Testing environments</span></span>

<span data-ttu-id="3d8c2-162">Uma parte importante de qualquer implantação contínua (CD) ou o processo de integração contínua (CI) são os testes de unidade e testes de integração.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-162">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="3d8c2-163">Esses testes automatizados exigem um ambiente isolado, portanto, eles não são afetados por usuários ou qualquer outra alteração nos dados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-163">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="3d8c2-164">Com o Docker Compose, você pode criar e destruir o ambiente isolado facilmente em alguns comandos do seu prompt de comando ou scripts, como os comandos a seguir:</span><span class="sxs-lookup"><span data-stu-id="3d8c2-164">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="3d8c2-165">Implantações de produção</span><span class="sxs-lookup"><span data-stu-id="3d8c2-165">Production deployments</span></span>

<span data-ttu-id="3d8c2-166">Você também pode usar redigir para implantar em um mecanismo de Docker remoto.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-166">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="3d8c2-167">Um caso comum é implantar uma única instância de host do Docker (como uma produção VM ou servidor provisionados com [Docker máquina](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="3d8c2-167">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="3d8c2-168">Mas ele também pode ser um inteiro [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, porque clusters também são compatíveis com os arquivos de docker compose.yml.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-168">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="3d8c2-169">Se você estiver usando qualquer orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), você precisará adicionar configurações de instalação e metadados como os de docker compose.yml, mas no formato exigido pelo orquestrador de.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-169">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="3d8c2-170">Em qualquer caso, compor a docker é um formato conveniente de ferramenta e os metadados para fluxos de trabalho de desenvolvimento, teste e produção, embora o fluxo de trabalho de produção pode variar o orquestrador que você está usando.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-170">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="3d8c2-171">Usando vários docker-compor arquivos para lidar com vários ambientes</span><span class="sxs-lookup"><span data-stu-id="3d8c2-171">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="3d8c2-172">Durante o direcionamento ambientes diferentes, você deve usar várias compor arquivos.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-172">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="3d8c2-173">Isso permite criar diversas variantes de configuração, dependendo do ambiente.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-173">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="3d8c2-174">Substituindo o arquivo de base docker-compose</span><span class="sxs-lookup"><span data-stu-id="3d8c2-174">Overriding the base docker-compose file</span></span>

<span data-ttu-id="3d8c2-175">Você pode usar um arquivo único docker-compose.yml como nos exemplos simplificados mostrados nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-175">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="3d8c2-176">No entanto, isso não é recomendável para a maioria dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-176">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="3d8c2-177">Por padrão, redação lê dois arquivos, um compose.yml docker e um arquivo de docker-compose.override.yml opcional.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-177">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="3d8c2-178">Conforme mostrado na Figura 8-11, quando você estiver usando o Visual Studio e habilitar o suporte do Docker, Visual Studio também cria os arquivos mais alguns arquivos adicionais usados para depuração.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-178">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates those files plus some additional files used for debugging.</span></span>

![](./media/image12.png)

<span data-ttu-id="3d8c2-179">**Figura 8-11**.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-179">**Figure 8-11**.</span></span> <span data-ttu-id="3d8c2-180">compor docker de arquivos no Visual Studio de 2017</span><span class="sxs-lookup"><span data-stu-id="3d8c2-180">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="3d8c2-181">Você pode editar os arquivos de docker-compose com um editor, como o código do Visual Studio ou Sublime e executar o aplicativo com o docker-compor até o comando.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-181">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="3d8c2-182">Por convenção, o arquivo de docker compose.yml contém sua configuração base e outras configurações estáticas.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-182">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="3d8c2-183">Isso significa que a configuração do serviço não deve ser alterada dependendo do ambiente de implantação que você tiver como alvo.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-183">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="3d8c2-184">O arquivo de docker compose.override.yml, como o nome sugere, contém configurações que substituem as configurações básicas, como configuração depende do ambiente de implantação.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-184">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="3d8c2-185">Você também pode ter vários arquivos de substituição com nomes diferentes.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-185">You can have multiple override files with different names also.</span></span> <span data-ttu-id="3d8c2-186">Os arquivos de substituição geralmente contêm informações adicionais exigidas pelo aplicativo mas específico em um ambiente de ou para uma implantação.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-186">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="3d8c2-187">Direcionamento de vários ambientes</span><span class="sxs-lookup"><span data-stu-id="3d8c2-187">Targeting multiple environments</span></span>

<span data-ttu-id="3d8c2-188">Um caso de uso típico é quando você define vários compor arquivos para que você pode direcionar a vários ambientes, como produção, teste, desenvolvimento ou CI.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-188">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="3d8c2-189">Para dar suporte a essas diferenças, você pode dividir a configuração de redação em vários arquivos, conforme mostrado na Figura 8-12.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-189">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="3d8c2-190">**Figura 8-12**.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-190">**Figure 8-12**.</span></span> <span data-ttu-id="3d8c2-191">Docker-compor vários a arquivos de substituição de valores no arquivo de base de compose.yml de docker</span><span class="sxs-lookup"><span data-stu-id="3d8c2-191">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="3d8c2-192">Você inicia com o arquivo de base de compose.yml de docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-192">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="3d8c2-193">Esse arquivo de base deve conter as definições de configuração de base ou estático que não são alterados dependendo do ambiente.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-193">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="3d8c2-194">Por exemplo, o eShopOnContainers tem o seguinte arquivo de docker compose.yml como o arquivo de base.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-194">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

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

<span data-ttu-id="3d8c2-195">Os valores no arquivo de base de compose.yml de docker não devem alterar devido a ambientes de implantação de destino diferente.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-195">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="3d8c2-196">Se você se concentre na definição do serviço webmvc, por exemplo, você pode ver como essa informação é muito semelhante a não importa qual o ambiente que você pode ser direcionado.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-196">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="3d8c2-197">Você tem as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="3d8c2-197">You have the following information:</span></span>

-   <span data-ttu-id="3d8c2-198">O nome do serviço: webmvc.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-198">The service name: webmvc.</span></span>

-   <span data-ttu-id="3d8c2-199">Imagem personalizada do contêiner: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-199">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="3d8c2-200">O comando para criar a imagem personalizada do Docker, que indica qual Dockerfile a ser usado.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-200">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="3d8c2-201">Dependências em outros serviços, para que este contêiner não inicia até que os outros contêineres de dependência foram iniciados.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-201">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="3d8c2-202">Você pode ter uma configuração adicional, mas o ponto importante é que no arquivo de base de compose.yml de docker, você apenas deseja definir as informações que é comuns em ambientes.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-202">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="3d8c2-203">Em seguida, no docker compose.override.yml ou arquivos semelhantes para produção ou preparo, você deve colocar configuração é específica para cada ambiente.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-203">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="3d8c2-204">Normalmente, o docker-compose.override.yml é usado para o seu ambiente de desenvolvimento, como no exemplo a seguir do eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="3d8c2-204">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

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

<span data-ttu-id="3d8c2-205">Neste exemplo, a configuração de substituição de desenvolvimento expõe algumas portas para o host, define variáveis de ambiente com URLs de redirecionamento e especifica as cadeias de caracteres de conexão para o ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-205">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="3d8c2-206">Essas configurações são todos apenas para o ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-206">These settings are all just for the development environment.</span></span>

<span data-ttu-id="3d8c2-207">Quando você executa compor docker backup (ou iniciá-lo do Visual Studio), o comando lê as substituições automaticamente como se ele foi mesclando os dois arquivos.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-207">When you run docker-compose up (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="3d8c2-208">Suponha que você deseja que o outro arquivo de redação para o ambiente de produção, com valores de configuração diferentes.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-208">Suppose that you want another Compose file for the production environment, with different configuration values.</span></span> <span data-ttu-id="3d8c2-209">Você pode criar outro arquivo de substituição, como a seguir.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-209">You can create another override file, like the following.</span></span> <span data-ttu-id="3d8c2-210">(Este arquivo pode ser armazenado em um repositório Git diferente ou gerenciado e protegido por uma equipe diferente.)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-210">(This file might be stored in a different Git repo or managed and secured by a different team.)</span></span>

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

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="3d8c2-211">Como implantar um arquivo de substituição específica</span><span class="sxs-lookup"><span data-stu-id="3d8c2-211">How to deploy with a specific override file</span></span>

<span data-ttu-id="3d8c2-212">Para usar vários arquivos de substituição, ou um arquivo de substituição com um nome diferente, você pode usar a opção -f com o comando docker-compor e especificar os arquivos.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-212">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="3d8c2-213">Compor mesclagens arquivos na ordem em que elas são especificadas na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-213">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="3d8c2-214">O exemplo a seguir mostra como implantar com arquivos de substituição.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-214">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="3d8c2-215">Usando variáveis de ambiente no docker-compor arquivos</span><span class="sxs-lookup"><span data-stu-id="3d8c2-215">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="3d8c2-216">É conveniente, especialmente em ambientes de produção, para poder obter informações de configuração de variáveis de ambiente, como nós temos mostrado nos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-216">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="3d8c2-217">Fazer referência a uma variável de ambiente em seus arquivos docker-compose usando a sintaxe \${meu\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-217">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="3d8c2-218">A seguinte linha de um arquivo de docker compose.prod.yml mostra como referenciar o valor de uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-218">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="3d8c2-219">Variáveis de ambiente são criadas e inicializadas de maneiras diferentes, dependendo do seu ambiente de host (Linux, Windows, cluster de nuvem, etc.).</span><span class="sxs-lookup"><span data-stu-id="3d8c2-219">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="3d8c2-220">No entanto, uma abordagem conveniente é usar um arquivo de .env.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-220">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="3d8c2-221">Os arquivos docker-compose suportam declarando variáveis de ambiente padrão no arquivo .env.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-221">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="3d8c2-222">Esses valores das variáveis de ambiente são os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-222">These values for the environment variables are the default values.</span></span> <span data-ttu-id="3d8c2-223">Mas elas podem ser substituídas pelos valores que você possa ter definido em cada um de seus ambientes (sistema operacional do host ou variáveis de ambiente do cluster).</span><span class="sxs-lookup"><span data-stu-id="3d8c2-223">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="3d8c2-224">Coloque esse arquivo .env na pasta em que o compõem docker comando é executado em.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-224">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="3d8c2-225">O exemplo a seguir mostra um arquivo de .env como o [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) arquivo para o aplicativo eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-225">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="3d8c2-226">Compor docker espera cada linha em um arquivo .env para estar no formato &lt;variável&gt;=&lt;valor&gt;.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-226">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="3d8c2-227">Observe que os valores definidos no ambiente de tempo de execução sempre substituam os valores definidos no arquivo .env.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-227">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="3d8c2-228">De maneira semelhante, os valores passados por meio de argumentos de linha de comando também substituem os valores padrão definidos no arquivo .env.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-228">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3d8c2-229">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3d8c2-229">Additional resources</span></span>

-   <span data-ttu-id="3d8c2-230">**Visão geral do Docker compor**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-230">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="3d8c2-231">**Vários arquivos de redação**
    [*https://docs.docker.com/compose/extends/\#arquivos compor vários*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-231">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="3d8c2-232">Criando imagens do Docker do ASP.NET Core de otimização</span><span class="sxs-lookup"><span data-stu-id="3d8c2-232">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="3d8c2-233">Se você está explorando o Docker e o .NET Core em fontes na Internet, você encontrará Dockerfiles que demonstram a simplicidade de criação de uma imagem do Docker, copiando a fonte em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-233">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="3d8c2-234">Esses exemplos sugerem que, por meio de uma configuração simple, você pode ter uma imagem do Docker com o ambiente que acompanha seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-234">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="3d8c2-235">O exemplo a seguir mostra um Dockerfile simple neste modo.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-235">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="3d8c2-236">Um Dockerfile como isso funciona.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-236">A Dockerfile like this will work.</span></span> <span data-ttu-id="3d8c2-237">No entanto, você pode otimizar substancialmente suas imagens, especialmente as imagens de produção.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-237">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="3d8c2-238">No contêiner e microservices modelo, você está iniciando constantemente contêineres.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-238">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="3d8c2-239">O modo como o uso de contêineres não reinicia um contêiner em suspensão, como o contêiner está descartável.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-239">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="3d8c2-240">Orchestrators (como o Docker Swarm, Kubernetes, DCOS ou Azure Service Fabric) simplesmente criarem novas instâncias de imagens.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-240">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="3d8c2-241">Isso significa que você precisa otimizar pré-compilação do aplicativo quando ele é criado para que o processo de instanciação será mais rápido.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-241">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="3d8c2-242">Quando o contêiner é iniciado, ele deve estar pronto para executar.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-242">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="3d8c2-243">Você não deve restaurar e compilação em tempo de execução, usando dotnet dotnet e restauração criar comandos a partir do dotnet CLI que, como você pode ver em várias postagens de blog sobre .NET Core e o Docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-243">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="3d8c2-244">A equipe do .NET está executando um trabalho importante para tornar o .NET Core e ASP.NET Core uma estrutura otimizada de contêiner.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-244">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="3d8c2-245">Não somente o .NET Core é uma estrutura leve com um espaço de memória pequenos; a equipe tem voltada para o desempenho de inicialização e produzido algumas imagens Docker otimizadas, como o [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) imagem disponível no [Hub do Docker](https://hub.docker.com/r/microsoft/aspnetcore/), em comparação com o regular [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) ou [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) imagens.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-245">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="3d8c2-246">O [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) imagem fornece configuração automática de aspnetcore\_urls para a porta 80 e cache de assemblies; pre-ngend essas duas configurações resultam em inicialização mais rápida.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-246">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3d8c2-247">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3d8c2-247">Additional resources</span></span>

-   <span data-ttu-id="3d8c2-248">**Criando otimização de imagens do Docker com o ASP.NET Core**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-248">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="3d8c2-249">Criar o aplicativo de um contêiner de compilação (CI)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-249">Building the application from a build (CI) container</span></span>

<span data-ttu-id="3d8c2-250">Outro benefício de Docker é que você pode criar o aplicativo a partir de um contêiner pré-configurados, conforme mostrado na Figura 8-13, portanto você não precisa criar uma máquina de compilação ou a VM para criar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-250">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="3d8c2-251">Você pode usar ou esse contêiner de compilação de teste executando-o em sua máquina de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-251">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="3d8c2-252">Mas o que é ainda mais interessante é que você pode usar o mesmo contêiner de compilação do seu pipeline de CI (integração contínua).</span><span class="sxs-lookup"><span data-stu-id="3d8c2-252">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="3d8c2-253">**Figura 8-13**.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-253">**Figure 8-13**.</span></span> <span data-ttu-id="3d8c2-254">Componentes de criação de bits de .NET de um contêiner</span><span class="sxs-lookup"><span data-stu-id="3d8c2-254">Components building .NET bits from a container</span></span>

<span data-ttu-id="3d8c2-255">Para este cenário, fornecemos o [aspnetcore/microsoft-compilação](https://hub.docker.com/r/microsoft/aspnetcore-build/) imagem, que você pode usar para compilar e criar o ASP.NET Core aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-255">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="3d8c2-256">A saída é colocada em uma imagem com base no [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) imagem, que é uma imagem de tempo de execução otimizado, conforme observada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-256">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="3d8c2-257">A imagem de compilação aspnetcore contém tudo o que você precisa para compilar um aplicativo ASP.NET Core, incluindo .NET Core, o SDK do ASP.NET, npm, Bower, Gulp, etc.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-257">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="3d8c2-258">Precisamos essas dependências no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-258">We need these dependencies at build time.</span></span> <span data-ttu-id="3d8c2-259">Mas não queremos executar esses recursos com o aplicativo em tempo de execução, porque isso tornaria a imagem desnecessariamente grande.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-259">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="3d8c2-260">No aplicativo eShopOnContainers, você pode criar o aplicativo de um contêiner, executando apenas o seguinte docker-compor comando.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-260">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="3d8c2-261">Figura 8-14 mostra este comando executado na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-261">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="3d8c2-262">**Figura 8-14.**</span><span class="sxs-lookup"><span data-stu-id="3d8c2-262">**Figure 8-14.**</span></span> <span data-ttu-id="3d8c2-263">Criar seu aplicativo .NET de um contêiner</span><span class="sxs-lookup"><span data-stu-id="3d8c2-263">Building your .NET application from a container</span></span>

<span data-ttu-id="3d8c2-264">Como você pode ver, o contêiner que está sendo executado é a compilação de ci\_1 contêiner.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-264">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="3d8c2-265">Isso se baseia a imagem aspnetcore compilação para que ela pode compilar e criar seu aplicativo inteiro de dentro do contêiner em vez de seu PC.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-265">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="3d8c2-266">Que é por que na verdade é criar e compilar projetos .NET Core no Linux, porque esse contêiner está em execução no host Linux Docker padrão.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-266">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="3d8c2-267">O [docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) arquivo de imagem (parte da eShopOnContainers) contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-267">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="3d8c2-268">Você pode ver que ele inicia um contêiner de compilação usando o [aspnetcore/microsoft-compilação](https://hub.docker.com/r/microsoft/aspnetcore-build/) imagem.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-268">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

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

* <span data-ttu-id="3d8c2-269">Começando com **.NET Core 2.0**, `dotnet restore` comando é executado automaticamente quando o `dotnet publish` comando é executado.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-269">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="3d8c2-270">Depois que o contêiner de compilação está em execução, ele executa a restauração de dotnet do SDK do .NET e dotnet publicar comandos em relação a todos os projetos na solução para compilar os bits de .NET.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-270">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="3d8c2-271">Nesse caso, pois eShopOnContainers também tem um SPA com base em TypeScript e Angular para o código do cliente, ele também precisa verificar dependências de JavaScript com npm, mas essa ação não está relacionada aos bits de .NET.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-271">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="3d8c2-272">O dotnet publicar compilações de comando e publica a saída compilada dentro da pasta de cada projeto para o. pasta de /obj/Docker/Publish, conforme mostrado na Figura 8-15.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-272">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="3d8c2-273">**Figura 8-15.**</span><span class="sxs-lookup"><span data-stu-id="3d8c2-273">**Figure 8-15.**</span></span> <span data-ttu-id="3d8c2-274">Comando de publicar arquivos binários gerados pelo dotnet</span><span class="sxs-lookup"><span data-stu-id="3d8c2-274">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="3d8c2-275">Criar as imagens do Docker da CLI</span><span class="sxs-lookup"><span data-stu-id="3d8c2-275">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="3d8c2-276">Depois que a saída do aplicativo é publicada para as pastas relacionadas (dentro de cada projeto), a próxima etapa é criar as imagens do Docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-276">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="3d8c2-277">Para fazer isso, você usa a compilação docker-compose e docker-compor a comandos, conforme mostrado na Figura 8-16.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-277">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="3d8c2-278">**Figura 8-16.**</span><span class="sxs-lookup"><span data-stu-id="3d8c2-278">**Figure 8-16.**</span></span> <span data-ttu-id="3d8c2-279">Criação de imagens do Docker e os contêineres em execução</span><span class="sxs-lookup"><span data-stu-id="3d8c2-279">Building Docker images and running the containers</span></span>

<span data-ttu-id="3d8c2-280">Na Figura 8-17, você pode ver como o docker-compose criar execução do comando.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-280">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="3d8c2-281">**Figura 8-17**.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-281">**Figure 8-17**.</span></span> <span data-ttu-id="3d8c2-282">Criação de imagens do Docker com o docker-compor o comando de compilação</span><span class="sxs-lookup"><span data-stu-id="3d8c2-282">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="3d8c2-283">A diferença entre o docker-compose criar e compor docker backup comandos é que compõem docker compilações e inicia as imagens.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-283">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="3d8c2-284">Quando você usa o Visual Studio, todas essas etapas são executadas nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-284">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="3d8c2-285">O Visual Studio compila seu aplicativo .NET, cria as imagens do Docker e implanta os contêineres no host do Docker.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-285">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="3d8c2-286">O Visual Studio oferece recursos adicionais, como a capacidade de depurar seus contêineres em execução no Docker, diretamente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-286">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="3d8c2-287">O takeway geral aqui é que é capaz de criar seu aplicativo o mesmo propósito seu pipeline de CI/CD deve compilá-lo — de um contêiner em vez de em uma máquina local.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-287">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="3d8c2-288">Depois de ter as imagens criadas, em seguida, você apenas precisa executar as imagens do Docker usando o docker-compor o comando.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-288">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3d8c2-289">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3d8c2-289">Additional resources</span></span>

-   <span data-ttu-id="3d8c2-290">**Criação de bits de um contêiner: Configurando a solução eShopOnContainers em um ambiente Windows CLI (dotnet CLI, CLI do Docker e o código do VS)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/ 03.-Setting-the-eShopOnContainers-Solution-up-in-a-Windows-CLI-Environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="3d8c2-290">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="3d8c2-291">[Anterior] (dados-controlada por-crud-microservice.md) [Avançar] (container.md de servidor de banco de dados)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-291">[Previous] (data-driven-crud-microservice.md) [Next] (database-server-container.md)</span></span>
