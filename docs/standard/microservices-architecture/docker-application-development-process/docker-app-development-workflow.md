---
title: Fluxo de trabalho de desenvolvimento para aplicativos do Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Fluxo de trabalho de desenvolvimento para aplicativos do Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/05/2018
ms.openlocfilehash: 00cffde7e7eb548f755b60f64aa596210b570d07
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297511"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="3924a-103">Fluxo de trabalho de desenvolvimento para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="3924a-103">Development workflow for Docker apps</span></span>

<span data-ttu-id="3924a-104">O ciclo de vida de desenvolvimento do aplicativo inicia-se no computador de cada desenvolvedor, em que o desenvolvedor codifica o aplicativo usando a linguagem de sua preferência, testando-o localmente.</span><span class="sxs-lookup"><span data-stu-id="3924a-104">The application development life cycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="3924a-105">Independentemente da linguagem, da estrutura e da plataforma escolhidas pelo desenvolvedor, com esse fluxo de trabalho, ele estará sempre desenvolvendo e testando contêineres do Docker, fazendo-o, entretanto, localmente.</span><span class="sxs-lookup"><span data-stu-id="3924a-105">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="3924a-106">Cada contêiner (uma instância de uma imagem do Docker) inclui os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="3924a-106">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="3924a-107">Uma seleção do sistema operacional (por exemplo, uma distribuição do Linux, o Windows Nano Server ou o Windows Server Core).</span><span class="sxs-lookup"><span data-stu-id="3924a-107">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

- <span data-ttu-id="3924a-108">Arquivos adicionados pelo desenvolvedor (binários do aplicativo, etc.).</span><span class="sxs-lookup"><span data-stu-id="3924a-108">Files added by the developer (application binaries, etc.).</span></span>

- <span data-ttu-id="3924a-109">Informações de configuração (configurações de ambiente e dependências).</span><span class="sxs-lookup"><span data-stu-id="3924a-109">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="3924a-110">Fluxo de trabalho para o desenvolvimento de aplicativos baseados em contêiner do Docker</span><span class="sxs-lookup"><span data-stu-id="3924a-110">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="3924a-111">Esta seção descreve o fluxo de trabalho de desenvolvimento do *loop interno* de aplicativos baseados em contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-111">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="3924a-112">O fluxo de trabalho de loop interno não leva em conta o fluxo de trabalho de DevOps mais amplo, mas concentra-se apenas no trabalho de desenvolvimento realizado no computador do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="3924a-112">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="3924a-113">As etapas iniciais para configurar o ambiente não estão incluídas, pois elas são realizadas apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="3924a-113">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="3924a-114">Um aplicativo é composto de seus próprios serviços e de bibliotecas adicionais (dependências).</span><span class="sxs-lookup"><span data-stu-id="3924a-114">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="3924a-115">A figura 5-1 a seguir ilustra as etapas básicas que são normalmente realizadas para criar um aplicativo do Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-115">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![Fluxo de trabalho passo a passo para o desenvolvimento do gráfico de aplicativos do Docker em contêineres](./media/image1.png)

<span data-ttu-id="3924a-117">**Figura 5-1.**</span><span class="sxs-lookup"><span data-stu-id="3924a-117">**Figure 5-1.**</span></span> <span data-ttu-id="3924a-118">Fluxo de trabalho passo a passo para o desenvolvimento de aplicativos do Docker em contêineres</span><span class="sxs-lookup"><span data-stu-id="3924a-118">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="3924a-119">Neste guia, todo esse processo será detalhado e cada etapa principal será explicada com base em um ambiente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3924a-119">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="3924a-120">Ao usar uma abordagem de desenvolvimento de editor/CLI (por exemplo, Visual Studio Code com CLI do Docker no macOS ou no Windows), você precisará conhecer cada etapa e, na maioria das vezes, com mais detalhes do que ao usar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3924a-120">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="3924a-121">Para obter mais informações sobre como trabalhar em um ambiente de CLI, confira o livro eletrônico [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/) (Ciclo de vida do aplicativo do Docker em contêineres com ferramentas e plataformas da Microsoft).</span><span class="sxs-lookup"><span data-stu-id="3924a-121">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="3924a-122">Quando você usar o Visual Studio, muitas dessas etapas serão feitas para você, melhorando significativamente sua produtividade.</span><span class="sxs-lookup"><span data-stu-id="3924a-122">When you're using Visual Studio, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="3924a-123">Isso é especialmente verdadeiro quando você usa o Visual Studio 2017 e tem aplicativos de vários contêineres como destino.</span><span class="sxs-lookup"><span data-stu-id="3924a-123">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="3924a-124">Por exemplo, com apenas um clique do mouse, o Visual Studio adiciona os arquivos *Dockerfile* e *docker-compose.yml* aos projetos com a configuração correta para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3924a-124">For instance, with just one mouse click, Visual Studio adds the *Dockerfile* and *docker-compose.yml* files to your projects with the configuration for your application.</span></span> <span data-ttu-id="3924a-125">Quando você executa o aplicativo no Visual Studio, ele cria a imagem do Docker e executa o aplicativo de vários contêineres diretamente no Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-125">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker.</span></span> <span data-ttu-id="3924a-126">Ele até mesmo permite que você depure vários contêineres de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="3924a-126">It even allows you to debug several containers at once.</span></span> <span data-ttu-id="3924a-127">Essas funcionalidades aceleram sua velocidade de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3924a-127">These features boost your development speed.</span></span>

<span data-ttu-id="3924a-128">Na diretriz a seguir, explicaremos o que está acontecendo com o Docker "nos bastidores".</span><span class="sxs-lookup"><span data-stu-id="3924a-128">In the guidance that follows, we explain what's happening "under the covers" with Docker.</span></span>

![Etapa 1 – Codificar o gráfico do aplicativo](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="3924a-130">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="3924a-130">Step 1.</span></span> <span data-ttu-id="3924a-131">Iniciar a codificação e a criação do aplicativo inicial ou da linha de base do serviço</span><span class="sxs-lookup"><span data-stu-id="3924a-131">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="3924a-132">O desenvolvimento de um aplicativo do Docker é semelhante à forma como você desenvolve um aplicativo sem Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-132">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="3924a-133">A diferença é que, durante o desenvolvimento para o Docker, você está implantando e testando o aplicativo ou os serviços executando-os dentro de contêineres do Docker em seu ambiente local.</span><span class="sxs-lookup"><span data-stu-id="3924a-133">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="3924a-134">O contêiner pode ser do Linux ou do Windows.</span><span class="sxs-lookup"><span data-stu-id="3924a-134">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="3924a-135">Configurar seu ambiente local com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3924a-135">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="3924a-136">Para começar, instale o [Docker CE (Community Edition)](https://www.docker.com/community-edition) para Windows, conforme explicado nas instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="3924a-136">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="3924a-137">Introdução ao Docker CE para Windows</span><span class="sxs-lookup"><span data-stu-id="3924a-137">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="3924a-138">Além disso, você precisa do Visual Studio 2017 com a carga de trabalho **Desenvolvimento multiplataforma do .NET Core** instalada, conforme mostrado na Figura 5-2.</span><span class="sxs-lookup"><span data-stu-id="3924a-138">In addition, you need Visual Studio 2017 with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="3924a-139">**Figura 5-2**.</span><span class="sxs-lookup"><span data-stu-id="3924a-139">**Figure 5-2**.</span></span> <span data-ttu-id="3924a-140">Selecionando a carga de trabalho **.NET Core e Docker** durante a instalação do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3924a-140">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="3924a-141">Você pode iniciar a codificação do seu aplicativo no .NET simples (normalmente no .NET Core, se você estiver planejando usar contêineres) mesmo antes de habilitar o Docker em seu aplicativo e antes da implantação e do teste no Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-141">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="3924a-142">No entanto, é recomendável que você comece a trabalhar no Docker assim que possível, porque que esse será o ambiente real e os problemas poderão ser descobertos o mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="3924a-142">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="3924a-143">Isso é recomendável porque o Visual Studio facilita tanto o trabalho com o Docker que ele parece quase transparente – o melhor exemplo ao depurar aplicativos de vários contêineres no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3924a-143">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent — the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3924a-144">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3924a-144">Additional resources</span></span>

- <span data-ttu-id="3924a-145">**Introdução ao Docker CE para Windows**</span><span class="sxs-lookup"><span data-stu-id="3924a-145">**Get started with Docker CE for Windows**</span></span>

   [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

- <span data-ttu-id="3924a-146">**Visual Studio 2017**</span><span class="sxs-lookup"><span data-stu-id="3924a-146">**Visual Studio 2017**</span></span>

   [*https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![Etapa 2 – Escrever o gráfico de Dockerfiles](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="3924a-148">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="3924a-148">Step 2.</span></span> <span data-ttu-id="3924a-149">Criar um Dockerfile relacionado a uma imagem base existente do .NET</span><span class="sxs-lookup"><span data-stu-id="3924a-149">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="3924a-150">Você precisa de um Dockerfile para cada imagem personalizada que deseja criar. Também precisa de um Dockerfile para cada contêiner a ser implantado, seja automaticamente por meio do Visual Studio ou manualmente usando a CLI do Docker (comandos docker run e docker-compose).</span><span class="sxs-lookup"><span data-stu-id="3924a-150">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="3924a-151">Se seu aplicativo contém um único serviço personalizado, é necessário um único Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="3924a-151">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="3924a-152">Se seu aplicativo contém vários serviços (como em uma arquitetura de microsserviços), é necessário um Dockerfile para cada serviço.</span><span class="sxs-lookup"><span data-stu-id="3924a-152">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="3924a-153">O Dockerfile é colocado na pasta raiz do seu aplicativo ou serviço.</span><span class="sxs-lookup"><span data-stu-id="3924a-153">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="3924a-154">Ele contém os comandos que indicam ao Docker como configurar e executar seu aplicativo ou serviço em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="3924a-154">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="3924a-155">Você pode criar manualmente um Dockerfile por meio de código e adicioná-lo ao seu projeto junto com as dependências do .NET.</span><span class="sxs-lookup"><span data-stu-id="3924a-155">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="3924a-156">Com as Ferramentas do Visual Studio para Docker, essa tarefa exige apenas alguns cliques do mouse.</span><span class="sxs-lookup"><span data-stu-id="3924a-156">With Visual Studio Tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="3924a-157">Quando você cria um projeto no Visual Studio 2017, há uma opção chamada **Habilitar Suporte do Docker**, conforme mostrado na Figura 5-3.</span><span class="sxs-lookup"><span data-stu-id="3924a-157">When you create a new project in Visual Studio 2017, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![Habilitando o suporte do Docker ao criar um novo projeto no Visual Studio 2017](./media/image5.png)

<span data-ttu-id="3924a-159">**Figura 5-3**.</span><span class="sxs-lookup"><span data-stu-id="3924a-159">**Figure 5-3**.</span></span> <span data-ttu-id="3924a-160">Habilitando o suporte do Docker ao criar um novo projeto no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3924a-160">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="3924a-161">Você também pode habilitar o suporte ao Docker em um projeto de aplicativo Web .NET Core existente clicando com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecionando **Adicionar** > **Suporte ao Docker**, conforme mostrado na Figura 5-4.</span><span class="sxs-lookup"><span data-stu-id="3924a-161">You can also enable Docker support on an existing .NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![Adicionar a opção de menu de suporte ao Docker no Visual Studio](./media/add-docker-support.png)

<span data-ttu-id="3924a-163">**Figura 5-4**.</span><span class="sxs-lookup"><span data-stu-id="3924a-163">**Figure 5-4**.</span></span> <span data-ttu-id="3924a-164">Habilitando o suporte do Docker em um projeto existente do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3924a-164">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="3924a-165">Essa ação adiciona um *Dockerfile* ao projeto com a configuração necessária e só está disponível em projetos de aplicativo Web .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3924a-165">This action adds a *Dockerfile* to the project with the required configuration, and is only available on .NET Core web app projects.</span></span>

<span data-ttu-id="3924a-166">Para adicionar um arquivo *docker-compose.yml* a toda a solução, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecione **Adicionar** > **Suporte ao Orquestrador de Contêineres**, conforme mostrado na Figura 5-5.</span><span class="sxs-lookup"><span data-stu-id="3924a-166">To add a *docker-compose.yml* file for the whole solution, right-click on the project in **Solution Explorer** and select **Add** > **Container Orchestrator Support**, as shown in Figure 5-5.</span></span>

![Adicionar a opção de menu de suporte ao orquestrador de contêineres no Visual Studio](./media/add-container-orchestrator-support.png)

<span data-ttu-id="3924a-168">**Figura 5-5**.</span><span class="sxs-lookup"><span data-stu-id="3924a-168">**Figure 5-5**.</span></span> <span data-ttu-id="3924a-169">Adicionando o suporte ao orquestrador de contêineres a um projeto existente no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="3924a-169">Adding container orchestrator support to an existing project in Visual Studio 2017.</span></span>

<span data-ttu-id="3924a-170">Nas seções a seguir, descrevemos as informações que vão em cada um desses arquivos.</span><span class="sxs-lookup"><span data-stu-id="3924a-170">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="3924a-171">O Visual Studio realiza esse trabalho para você, mas é útil entender o que vai dentro de um Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="3924a-171">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="3924a-172">Opção a: criação de um projeto usando uma imagem do Docker oficial existente do .NET</span><span class="sxs-lookup"><span data-stu-id="3924a-172">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="3924a-173">Geralmente, você cria uma imagem personalizada para seu contêiner sobre uma imagem base que você pode obter de um repositório oficial, no registro do [Hub do Docker](https://hub.docker.com/).</span><span class="sxs-lookup"><span data-stu-id="3924a-173">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="3924a-174">É exatamente isso o que acontece nos bastidores quando você habilita o suporte do Docker no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3924a-174">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="3924a-175">O Dockerfile usa uma imagem aspnetcore existente.</span><span class="sxs-lookup"><span data-stu-id="3924a-175">The Dockerfile uses an existing aspnetcore image.</span></span>

<span data-ttu-id="3924a-176">Anteriormente, explicamos quais imagens do Docker e quais repositórios você poderia usar, dependendo da estrutura e do sistema operacional que você escolheu.</span><span class="sxs-lookup"><span data-stu-id="3924a-176">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="3924a-177">Por exemplo, se você quer usar o ASP.NET Core (Linux ou Windows), a imagem a ser usada é microsoft/aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="3924a-177">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="3924a-178">Assim, basta especificar qual imagem base do Docker será usada para o seu contêiner.</span><span class="sxs-lookup"><span data-stu-id="3924a-178">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="3924a-179">Isso é feito com a adição de FROM microsoft/aspnetcore:2.0 ao seu Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="3924a-179">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="3924a-180">Isso é realizado automaticamente pelo Visual Studio, mas se você precisar atualizar a versão, atualize esse valor.</span><span class="sxs-lookup"><span data-stu-id="3924a-180">This is automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="3924a-181">O uso de um repositório de imagem oficial do .NET do Hub do Docker com um número de versão garante que os mesmos recursos de linguagem estejam disponíveis em todos os computadores (incluindo desenvolvimento, teste e produção).</span><span class="sxs-lookup"><span data-stu-id="3924a-181">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="3924a-182">O exemplo a seguir mostra um Dockerfile de exemplo para um contêiner do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3924a-182">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0

ARG source

WORKDIR /app

EXPOSE 80

COPY ${source:-obj/Docker/publish} .

ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="3924a-183">Nesse caso, o contêiner é baseado na versão 2.0 da imagem do Docker do ASP.NET Core oficial (de várias arquiteturas, para Linux e Windows).</span><span class="sxs-lookup"><span data-stu-id="3924a-183">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="3924a-184">Essa é a configuração `FROM microsoft/aspnetcore:2.0`.</span><span class="sxs-lookup"><span data-stu-id="3924a-184">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="3924a-185">(Para obter mais informações sobre essa imagem base, confira a página [Imagem do Docker do ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) e a página [Imagem do Docker do .NET Core](https://hub.docker.com/r/microsoft/dotnet/).) No Dockerfile, você também precisará instruir o Docker a escutar na porta TCP que você usará em tempo de execução (nesse caso, a porta 80, conforme definido com a configuração EXPOSE).</span><span class="sxs-lookup"><span data-stu-id="3924a-185">(For more information about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="3924a-186">Você pode especificar mais configurações no Dockerfile, dependendo da linguagem e da estrutura que você está usando.</span><span class="sxs-lookup"><span data-stu-id="3924a-186">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="3924a-187">Por exemplo, a linha ENTRYPOINT, com \["dotnet", "MySingleContainerWebApp.dll"\], informa ao Docker para executar um aplicativo do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3924a-187">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="3924a-188">Se você estiver usando o SDK e a CLI do .NET Core (CLI do dotnet) para compilar e executar o aplicativo do .NET, essa configuração será diferente.</span><span class="sxs-lookup"><span data-stu-id="3924a-188">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="3924a-189">O essencial é que a linha ENTRYPOINT e outras configurações serão diferentes dependendo da linguagem e da plataforma que você escolher para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3924a-189">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3924a-190">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3924a-190">Additional resources</span></span>

- <span data-ttu-id="3924a-191">**Criando Imagens do Docker para .NET Core Applications**</span><span class="sxs-lookup"><span data-stu-id="3924a-191">**Building Docker Images for .NET Core Applications**</span></span>

   [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

- <span data-ttu-id="3924a-192">**Criar sua própria imagem**.</span><span class="sxs-lookup"><span data-stu-id="3924a-192">**Build your own image**.</span></span> <span data-ttu-id="3924a-193">Na documentação oficial do Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-193">In the official Docker documentation.</span></span>

   [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="3924a-194">Usando repositórios de imagens para várias arquiteturas</span><span class="sxs-lookup"><span data-stu-id="3924a-194">Using multi-arch image repositories</span></span>

<span data-ttu-id="3924a-195">Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="3924a-195">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="3924a-196">Esse recurso permite que fornecedores, como a Microsoft (criadores de imagem base), criem um único repositório para abranger várias plataformas (ou seja, Linux e Windows).</span><span class="sxs-lookup"><span data-stu-id="3924a-196">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="3924a-197">Por exemplo, o repositório [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/), disponível no registro do Hub do Docker, é compatível com Linux e Windows Nano Server usando o mesmo nome de repositório.</span><span class="sxs-lookup"><span data-stu-id="3924a-197">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="3924a-198">Ao especificar uma marcação, você direciona a uma plataforma que é explícita, como nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="3924a-198">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- <span data-ttu-id="3924a-199">**microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="3924a-199">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

- <span data-ttu-id="3924a-200">**microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="3924a-200">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="3924a-201">Mas (e essa é uma novidade desde meados de 2017) se você especificar o mesmo nome de imagem e até a mesma marcação, as novas imagens de várias arquiteturas (como a imagem aspnetcore, que dá suporte a várias arquiteturas) usarão a versão do Windows ou do Linux, dependendo do sistema operacional host do Docker que você está implantando, conforme mostrado no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="3924a-201">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image, which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

- <span data-ttu-id="3924a-202">**microsoft/aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="3924a-202">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="3924a-203">Dessa forma, ao efetuar pull de uma imagem de um host do Windows, será efetuado o pull da variante do Windows e, ao efetuar pull do mesmo nome de imagem de um host do Linux, será efetuado pull da variante do Linux.</span><span class="sxs-lookup"><span data-stu-id="3924a-203">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="3924a-204">Opção B: criação da imagem base do zero</span><span class="sxs-lookup"><span data-stu-id="3924a-204">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="3924a-205">Você pode criar sua própria imagem base do Docker do zero.</span><span class="sxs-lookup"><span data-stu-id="3924a-205">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="3924a-206">Esse cenário não é recomendável para um iniciante no Docker, mas se você desejar definir os bits específicos da sua própria imagem base, isso será possível.</span><span class="sxs-lookup"><span data-stu-id="3924a-206">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3924a-207">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3924a-207">Additional resources</span></span>

- <span data-ttu-id="3924a-208">**Imagens do .NET Core para várias arquiteturas**.</span><span class="sxs-lookup"><span data-stu-id="3924a-208">**Multi-arch .NET Core images**.</span></span>

   https://github.com/dotnet/announcements/issues/14

- <span data-ttu-id="3924a-209">**Criar uma imagem base**.</span><span class="sxs-lookup"><span data-stu-id="3924a-209">**Create a base image**.</span></span> <span data-ttu-id="3924a-210">Documentação oficial do Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-210">Official Docker documentation.</span></span>

   [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![Etapa 3 – Criar um gráfico de imagens](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="3924a-212">Etapa 3.</span><span class="sxs-lookup"><span data-stu-id="3924a-212">Step 3.</span></span> <span data-ttu-id="3924a-213">Criar imagens personalizadas do Docker e inserir seu aplicativo ou serviço nelas</span><span class="sxs-lookup"><span data-stu-id="3924a-213">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="3924a-214">Para cada serviço do seu aplicativo, você precisa criar uma imagem relacionada.</span><span class="sxs-lookup"><span data-stu-id="3924a-214">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="3924a-215">Se seu aplicativo é composto de um único serviço ou aplicativo Web, você precisa apenas de uma única imagem.</span><span class="sxs-lookup"><span data-stu-id="3924a-215">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="3924a-216">As imagens do Docker são criadas automaticamente para você no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3924a-216">The Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="3924a-217">As etapas a seguir são necessárias apenas para o fluxo de trabalho de editor/CLI e são explicadas com a finalidade de esclarecer o que acontece nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="3924a-217">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="3924a-218">Você, como desenvolvedor, precisa desenvolver e testar localmente até enviar um recurso concluído por push ou mudar para o sistema de controle do código-fonte (por exemplo, para o GitHub).</span><span class="sxs-lookup"><span data-stu-id="3924a-218">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="3924a-219">Isso significa que você precisa criar as imagens do Docker e implantar contêineres em um host do Docker local (VM do Windows ou Linux) e executar, testar e depurar nesses contêineres locais.</span><span class="sxs-lookup"><span data-stu-id="3924a-219">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="3924a-220">Para criar uma imagem personalizada no ambiente local usando a CLI do Docker e o Dockerfile, use o comando docker build, como na Figura 5-5.</span><span class="sxs-lookup"><span data-stu-id="3924a-220">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Criando uma imagem personalizada do Docker](./media/image8.png)

<span data-ttu-id="3924a-222">**Figura 5-5**.</span><span class="sxs-lookup"><span data-stu-id="3924a-222">**Figure 5-5**.</span></span> <span data-ttu-id="3924a-223">Criando uma imagem personalizada do Docker</span><span class="sxs-lookup"><span data-stu-id="3924a-223">Creating a custom Docker image</span></span>

<span data-ttu-id="3924a-224">Opcionalmente, em vez de executar diretamente o comando docker build na pasta do projeto, você pode, primeiro, gerar uma pasta implantável com as bibliotecas e os binários do .NET necessários, executando dotnet publish e, em seguida, usar o comando docker build.</span><span class="sxs-lookup"><span data-stu-id="3924a-224">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="3924a-225">Isso criará uma imagem do Docker com o nome **cesardl/netcore-webapi-microservice-docker:first**.</span><span class="sxs-lookup"><span data-stu-id="3924a-225">This will create a Docker image with the name **cesardl/netcore-webapi-microservice-docker:first**.</span></span> <span data-ttu-id="3924a-226">Nesse caso, :first é uma marcação que representa uma versão específica.</span><span class="sxs-lookup"><span data-stu-id="3924a-226">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="3924a-227">Você poderá repetir esta etapa para cada imagem personalizada que tiver que criar para o seu aplicativo composto do Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-227">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="3924a-228">Quando um aplicativo é composto de diversos contêineres (ou seja, é um aplicativo de vários contêineres), você também pode usar o comando docker-compose up --build para compilar todas as imagens relacionadas com um único comando, usando os metadados expostos nos arquivos docker-compose.yml relacionados.</span><span class="sxs-lookup"><span data-stu-id="3924a-228">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="3924a-229">Você pode encontrar as imagens existentes no seu repositório local usando o comando docker images, conforme mostrado na Figura 5-6.</span><span class="sxs-lookup"><span data-stu-id="3924a-229">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Exibindo imagens existentes usando o comando docker images](./media/image9.png)

<span data-ttu-id="3924a-231">**Figura 5-6.**</span><span class="sxs-lookup"><span data-stu-id="3924a-231">**Figure 5-6.**</span></span> <span data-ttu-id="3924a-232">Exibição de imagens existentes usando o comando docker images</span><span class="sxs-lookup"><span data-stu-id="3924a-232">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="3924a-233">Criação de imagens do Docker com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3924a-233">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="3924a-234">Ao usar o Visual Studio para criar um projeto com suporte ao Docker, você não cria explicitamente uma imagem.</span><span class="sxs-lookup"><span data-stu-id="3924a-234">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="3924a-235">Em vez disso, a imagem é criada para você quando você pressiona **F5** para executar o aplicativo ou o serviço convertido para Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-235">Instead, the image is created for you when you press **F5** to run the dockerized application or service.</span></span> <span data-ttu-id="3924a-236">Esta etapa é automática no Visual Studio e você não verá ela ocorrer, mas é importante que você saiba o que está acontecendo nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="3924a-236">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![Etapa 4 – definir o gráfico de serviços](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="3924a-238">Etapa 4.</span><span class="sxs-lookup"><span data-stu-id="3924a-238">Step 4.</span></span> <span data-ttu-id="3924a-239">Definir os serviços no docker-compose.yml ao compilar um aplicativo de vários contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="3924a-239">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="3924a-240">O arquivo [docker-compose.yml](https://docs.docker.com/compose/compose-file/) permite que você defina um conjunto de serviços relacionados para que sejam implantados como um aplicativo composto com comandos de implantação.</span><span class="sxs-lookup"><span data-stu-id="3924a-240">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="3924a-241">Para usar um arquivo docker-compose.yml, você precisa criar o arquivo na pasta principal ou raiz da sua solução, com conteúdo semelhante ao do exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3924a-241">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="3924a-242">Esse arquivo docker-compose.yml é uma versão simplificada e mesclada.</span><span class="sxs-lookup"><span data-stu-id="3924a-242">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="3924a-243">Ele contém dados de configuração estática para cada contêiner (como o nome da imagem personalizada), o que é sempre aplicável, além das informações de configuração que dependerão do ambiente de implantação, como a cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="3924a-243">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="3924a-244">Nas próximas seções, você aprenderá como dividir a configuração do docker-compose.yml em vários arquivos e valores de substituição de docker-compose, dependendo do ambiente e do tipo de execução (depuração ou lançamento).</span><span class="sxs-lookup"><span data-stu-id="3924a-244">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="3924a-245">O arquivo docker-compose.yml de exemplo define quatro serviços: o serviço webmvc (um aplicativo Web), dois microsserviços (catalog.api e ordering.api) e um contêiner de fonte de dados, sql.data, com base no SQL Server para Linux, em execução como um contêiner.</span><span class="sxs-lookup"><span data-stu-id="3924a-245">The docker-compose.yml file example defines four services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="3924a-246">Cada serviço é implantado como um contêiner, assim, é necessário uma imagem do Docker para cada serviço.</span><span class="sxs-lookup"><span data-stu-id="3924a-246">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="3924a-247">O arquivo docker-compose.yml não apenas especifica quais contêineres estão sendo usados, mas também como eles são configurados individualmente.</span><span class="sxs-lookup"><span data-stu-id="3924a-247">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="3924a-248">Por exemplo, a definição de contêiner do webmvc, no arquivo .yml:</span><span class="sxs-lookup"><span data-stu-id="3924a-248">For instance, the webmvc container definition in the .yml file:</span></span>

- <span data-ttu-id="3924a-249">Usa uma imagem eshop/web:latest pré-compilada.</span><span class="sxs-lookup"><span data-stu-id="3924a-249">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="3924a-250">Entretanto, você também poderia definir a imagem para ser compilada como parte da execução do docker-compose, com uma configuração adicional baseada em uma seção build: no arquivo docker-compose.</span><span class="sxs-lookup"><span data-stu-id="3924a-250">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="3924a-251">Inicializa duas variáveis de ambiente (CatalogUrl e OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="3924a-251">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="3924a-252">Encaminha a porta 80, exposta no contêiner, para a porta 80 externa, no computador host.</span><span class="sxs-lookup"><span data-stu-id="3924a-252">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="3924a-253">Vincula o aplicativo Web ao serviço de catálogo e pedidos com a configuração depends\_on.</span><span class="sxs-lookup"><span data-stu-id="3924a-253">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="3924a-254">Isso faz com que o serviço aguarde até que esses serviços sejam iniciados.</span><span class="sxs-lookup"><span data-stu-id="3924a-254">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="3924a-255">Vamos abordar novamente o arquivo docker-compose.yml em uma seção posterior, ao explicar como implementar microsserviços e aplicativos de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="3924a-255">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="3924a-256">Trabalhando com o docker-compose.yml no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3924a-256">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="3924a-257">Quando você adiciona o suporte ao orquestrador de contêineres a um projeto de aplicativo Web, conforme mostrado na Figura 5-7, o Visual Studio adiciona uma seção de serviço (projeto) à solução que contém um arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="3924a-257">When you add container orchestrator support to a web app project, as shown in Figure 5-7, Visual Studio adds a service section (project) to the solution that contains a docker-compose.yml file.</span></span> <span data-ttu-id="3924a-258">Essa é uma maneira fácil de iniciar a composição de uma solução de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="3924a-258">This is an easy way to start composing a multiple-container solution.</span></span>

![Adicionar o item de menu de suporte ao orquestrador de contêineres no Visual Studio](./media/add-container-orchestrator-support.png)

<span data-ttu-id="3924a-260">**Figura 5-7**.</span><span class="sxs-lookup"><span data-stu-id="3924a-260">**Figure 5-7**.</span></span> <span data-ttu-id="3924a-261">Adicionar suporte do Docker no Visual Studio 2017 ao clicar com o botão direito do mouse em um projeto do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3924a-261">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="3924a-262">A adição de suporte ao orquestrador de contêineres adiciona o Dockerfile ao projeto (caso ainda não exista).</span><span class="sxs-lookup"><span data-stu-id="3924a-262">Adding container orchestrator support adds the Dockerfile to your project (if it doesn't already exist).</span></span> <span data-ttu-id="3924a-263">Ele também adiciona informações de configuração a um arquivo docker-compose.yml global no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="3924a-263">It also adds configuration information to a global docker-compose.yml file at the solution level.</span></span> <span data-ttu-id="3924a-264">Você verá um novo nó de projeto (o arquivo de projeto *docker-compose.dcproj*) no **Gerenciador de Soluções** que contém o arquivo docker-compose.yml, conforme mostrado na Figura 5-8.</span><span class="sxs-lookup"><span data-stu-id="3924a-264">You'll see a new project node (the *docker-compose.dcproj* project file) in **Solution Explorer** that contains the docker-compose.yml file, as shown in Figure 5-8.</span></span>

![Nó de docker-compose no Gerenciador de Soluções](./media/docker-compose-files.png)

<span data-ttu-id="3924a-266">**Figura 5-8**.</span><span class="sxs-lookup"><span data-stu-id="3924a-266">**Figure 5-8**.</span></span> <span data-ttu-id="3924a-267">O nó de árvore **docker-compose** adicionado no Gerenciador de Soluções do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3924a-267">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="3924a-268">Depois, você pode abrir o arquivo docker-compose.yml e atualizá-lo com outras funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="3924a-268">You can then open the docker-compose.yml file and update it with additional features.</span></span>

<span data-ttu-id="3924a-269">Você pode implantar um aplicativo de vários contêineres com um único arquivo docker-compose.yml usando o comando `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="3924a-269">You can deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span>

![Etapa 5 – Executar o gráfico do aplicativo](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="3924a-271">Etapa 5.</span><span class="sxs-lookup"><span data-stu-id="3924a-271">Step 5.</span></span> <span data-ttu-id="3924a-272">Compilar e executar seu aplicativo do Docker</span><span class="sxs-lookup"><span data-stu-id="3924a-272">Build and run your Docker application</span></span>

<span data-ttu-id="3924a-273">Se seu aplicativo tem apenas um contêiner, você pode executá-lo implantando-o no host do Docker (VM ou servidor físico).</span><span class="sxs-lookup"><span data-stu-id="3924a-273">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="3924a-274">No entanto, se o aplicativo contém vários serviços, você pode implantá-lo como um aplicativo composto usando um único comando de CLI (docker-compose up) ou com o Visual Studio, que usará esse mesmo comando nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="3924a-274">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="3924a-275">Vamos examinar as diferentes opções.</span><span class="sxs-lookup"><span data-stu-id="3924a-275">Let’s look at the different options.</span></span>

### <a name="option-a-run-a-single-container-app"></a><span data-ttu-id="3924a-276">Opção A: executar um aplicativo de contêiner único</span><span class="sxs-lookup"><span data-stu-id="3924a-276">Option A: Run a single-container app</span></span>

#### <a name="docker-cli"></a><span data-ttu-id="3924a-277">CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="3924a-277">Docker CLI</span></span>

<span data-ttu-id="3924a-278">Você pode executar um contêiner do Docker usando o comando docker run, como na Figura 5-9:</span><span class="sxs-lookup"><span data-stu-id="3924a-278">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![Executando um contêiner do Docker usando o comando docker run](./media/image13.png)

<span data-ttu-id="3924a-280">**Figura 5-9**.</span><span class="sxs-lookup"><span data-stu-id="3924a-280">**Figure 5-9**.</span></span> <span data-ttu-id="3924a-281">Executando um contêiner do Docker usando o comando docker run</span><span class="sxs-lookup"><span data-stu-id="3924a-281">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="3924a-282">Nesse caso, o comando associa a porta interna 5000 do contêiner à porta 80 do computador host.</span><span class="sxs-lookup"><span data-stu-id="3924a-282">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="3924a-283">Isso significa que o host está escutando na porta 80 e encaminhando para a porta 5000 no contêiner.</span><span class="sxs-lookup"><span data-stu-id="3924a-283">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

#### <a name="visual-studio"></a><span data-ttu-id="3924a-284">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3924a-284">Visual Studio</span></span>

<span data-ttu-id="3924a-285">Caso ainda não tenha adicionado o suporte ao orquestrador de contêineres, você também poderá executar um aplicativo de contêiner único no Visual Studio pressionando **F5**.</span><span class="sxs-lookup"><span data-stu-id="3924a-285">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **F5**.</span></span> <span data-ttu-id="3924a-286">O contêiner é executado localmente usando o docker run.</span><span class="sxs-lookup"><span data-stu-id="3924a-286">The container runs locally using docker run.</span></span>

### <a name="option-b-run-a-multi-container-app"></a><span data-ttu-id="3924a-287">Opção B: executar um aplicativo de vários contêineres</span><span class="sxs-lookup"><span data-stu-id="3924a-287">Option B: Run a multi-container app</span></span>

<span data-ttu-id="3924a-288">Na maioria dos cenários empresariais, um aplicativo do Docker será ser composto de vários serviços, o que significa que você precisará executar um aplicativo de vários contêineres, conforme mostrado na Figura 5-10.</span><span class="sxs-lookup"><span data-stu-id="3924a-288">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Gráfico mostrando a VM com contêineres do Docker implantados](./media/image14.png)

<span data-ttu-id="3924a-290">**Figura 5-10**.</span><span class="sxs-lookup"><span data-stu-id="3924a-290">**Figure 5-10**.</span></span> <span data-ttu-id="3924a-291">VM com contêineres do Docker implantados</span><span class="sxs-lookup"><span data-stu-id="3924a-291">VM with Docker containers deployed</span></span>

#### <a name="docker-cli"></a><span data-ttu-id="3924a-292">CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="3924a-292">Docker CLI</span></span>

<span data-ttu-id="3924a-293">Para executar um aplicativo de vários contêineres com a CLI do Docker, você pode executar o comando docker-compose up.</span><span class="sxs-lookup"><span data-stu-id="3924a-293">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="3924a-294">Esse comando usa o arquivo docker-compose.yml, que você tem no nível da solução, para implantar um aplicativo de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="3924a-294">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="3924a-295">A figura 5-11 mostra os resultados da execução do comando no diretório principal do projeto, que contém o arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="3924a-295">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![Resultados de exemplo ao executar o comando docker-compose up](./media/image15.png)

<span data-ttu-id="3924a-297">**Figura 5-11**.</span><span class="sxs-lookup"><span data-stu-id="3924a-297">**Figure 5-11**.</span></span> <span data-ttu-id="3924a-298">Resultados de exemplo ao executar o comando docker-compose up</span><span class="sxs-lookup"><span data-stu-id="3924a-298">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="3924a-299">Depois que o comando docker-compose up é executado, o aplicativo e os contêineres relacionados são implantados no host do Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-299">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host.</span></span>

#### <a name="visual-studio"></a><span data-ttu-id="3924a-300">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3924a-300">Visual Studio</span></span>

<span data-ttu-id="3924a-301">A execução de um aplicativo de vários contêineres com o Visual Studio 2017 é simples.</span><span class="sxs-lookup"><span data-stu-id="3924a-301">Running a multi-container application using Visual Studio 2017 is simple.</span></span> <span data-ttu-id="3924a-302">Você não somente pode executar o aplicativo de vários contêineres, mas também depurar todos os respectivos contêineres diretamente no Visual Studio, definindo pontos de interrupção regulares.</span><span class="sxs-lookup"><span data-stu-id="3924a-302">Not only can you run the multi-container application, but you're able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="3924a-303">Conforme mencionado anteriormente, sempre que você adiciona o suporte ao orquestrador de contêineres a um projeto em uma solução, esse projeto é configurado no arquivo docker-compose.yml global (nível da solução), o que permite que você execute ou depure toda a solução de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="3924a-303">As mentioned before, each time you add container orchestrator support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="3924a-304">O Visual Studio iniciará um contêiner para cada projeto que tenha o suporte habilitado para a solução do Docker e executará todas as etapas internas para você (dotnet publish, docker build, etc.).</span><span class="sxs-lookup"><span data-stu-id="3924a-304">Visual Studio will start one container for each project that has Docker solution support enabled and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="3924a-305">O ponto importante aqui é que, conforme mostrado na Figura 5-12, há um comando adicional do **Docker** no Visual Studio 2017 para a ação da tecla **F5**.</span><span class="sxs-lookup"><span data-stu-id="3924a-305">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there's an additional **Docker** command for the **F5** key action.</span></span> <span data-ttu-id="3924a-306">Essa opção permite que você execute ou depure um aplicativo de vários contêineres executando todos os contêineres que estão definidos nos arquivos docker-compose.yml no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="3924a-306">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="3924a-307">A capacidade de depurar soluções de vários contêineres significa que você poderá definir vários pontos de interrupção, cada ponto de interrupção em um projeto (contêiner) diferente e que, durante a depuração no Visual Studio, você vai parar nos pontos de interrupção definidos em diferentes projetos e em execução em diferentes contêineres.</span><span class="sxs-lookup"><span data-stu-id="3924a-307">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Executando aplicativos de vários contêineres no Visual Studio 2017](./media/image16.png)

<span data-ttu-id="3924a-309">**Figura 5-12**.</span><span class="sxs-lookup"><span data-stu-id="3924a-309">**Figure 5-12**.</span></span> <span data-ttu-id="3924a-310">Executando aplicativos de vários contêineres no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3924a-310">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3924a-311">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3924a-311">Additional resources</span></span>

-  <span data-ttu-id="3924a-312">**Implantar um contêiner ASP.NET em um host remoto do Docker**</span><span class="sxs-lookup"><span data-stu-id="3924a-312">**Deploy an ASP.NET container to a remote Docker host**</span></span>

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="3924a-313">Uma observação sobre teste e implantação com orquestradores</span><span class="sxs-lookup"><span data-stu-id="3924a-313">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="3924a-314">Os comandos docker-compose up e docker run (ou a execução e a depuração dos contêineres no Visual Studio) são adequados para o teste de contêineres no ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3924a-314">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="3924a-315">Mas você não deve usar essa abordagem se tiver como destino os clusters e orquestradores do Docker, como Docker Swarm, Mesosphere DC/OS ou Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3924a-315">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="3924a-316">Se estiver usando um cluster como [modo Docker Swarm](https://docs.docker.com/engine/swarm/) (disponível no Docker CE para Windows e Mac desde a versão 1.12), você precisará implantar e testar com comandos adicionais, como [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/), para serviços únicos.</span><span class="sxs-lookup"><span data-stu-id="3924a-316">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="3924a-317">Se estiver implantando um aplicativo composto por vários contêineres, você usará [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) e [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) para implantar o aplicativo composto como uma *pilha*.</span><span class="sxs-lookup"><span data-stu-id="3924a-317">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="3924a-318">Para obter mais informações, consulte a postagem no blog [Introducing Experimental Distributed Application Bundles (Apresentando pacotes de aplicativos experimentais distribuídos)](https://blog.docker.com/2016/06/docker-app-bundle/) na documentação do Docker,</span><span class="sxs-lookup"><span data-stu-id="3924a-318">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="3924a-319">no site do Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-319">on the Docker site.</span></span>

<span data-ttu-id="3924a-320">Para [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) e [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/) você também teria que usar outros scripts e comandos de implantação.</span><span class="sxs-lookup"><span data-stu-id="3924a-320">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![Etapa 6 – Gráfico](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="3924a-322">Etapa 6.</span><span class="sxs-lookup"><span data-stu-id="3924a-322">Step 6.</span></span> <span data-ttu-id="3924a-323">Testar seu aplicativo do Docker usando o host local do Docker</span><span class="sxs-lookup"><span data-stu-id="3924a-323">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="3924a-324">Esta etapa varia de acordo com o que seu aplicativo está fazendo.</span><span class="sxs-lookup"><span data-stu-id="3924a-324">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="3924a-325">Em um aplicativo Web .NET Core simples implantado como um único contêiner ou serviço, você pode acessar o serviço abrindo um navegador no host do Docker e navegando até o site, conforme mostrado na Figura 5-13.</span><span class="sxs-lookup"><span data-stu-id="3924a-325">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="3924a-326">(Se a configuração do Dockerfile mapear o contêiner para uma porta no host que seja diferente de 80, inclua a porta do host na URL).</span><span class="sxs-lookup"><span data-stu-id="3924a-326">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Exemplo de teste do seu aplicativo do Docker localmente usando localhost](./media/image18.png)

<span data-ttu-id="3924a-328">**Figura 5-13**.</span><span class="sxs-lookup"><span data-stu-id="3924a-328">**Figure 5-13**.</span></span> <span data-ttu-id="3924a-329">Exemplo de teste do seu aplicativo do Docker localmente usando localhost</span><span class="sxs-lookup"><span data-stu-id="3924a-329">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="3924a-330">Se o localhost não estiver apontando para o IP do host do Docker (por padrão, ao usar o Docker CE, ele deveria fazê-lo), use o endereço IP da placa de rede do seu computador para navegar até o serviço.</span><span class="sxs-lookup"><span data-stu-id="3924a-330">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="3924a-331">Essa URL no navegador usa a porta 80 para o exemplo de contêiner específico que está sendo abordado.</span><span class="sxs-lookup"><span data-stu-id="3924a-331">This URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="3924a-332">No entanto, internamente as solicitações estão sendo redirecionadas para a porta 5000, pois é assim que ele foi implantado com o comando docker run, conforme explicado em uma etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="3924a-332">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="3924a-333">Você também pode testar o aplicativo usando o comando curl no terminal, conforme mostrado na Figura 5-14.</span><span class="sxs-lookup"><span data-stu-id="3924a-333">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="3924a-334">Em uma instalação do Docker no Windows, o IP padrão do Host do Docker é sempre 10.0.75.1, além do endereço IP do seu computador.</span><span class="sxs-lookup"><span data-stu-id="3924a-334">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![Exemplo de teste do seu aplicativo do Docker localmente usando curl](./media/image19.png)

<span data-ttu-id="3924a-336">**Figura 5-14**.</span><span class="sxs-lookup"><span data-stu-id="3924a-336">**Figure 5-14**.</span></span> <span data-ttu-id="3924a-337">Exemplo de teste do seu aplicativo do Docker localmente usando curl</span><span class="sxs-lookup"><span data-stu-id="3924a-337">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="3924a-338">Testando e depurando contêineres com o Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3924a-338">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="3924a-339">Ao executar e depurar contêineres com o Visual Studio 2017, você depura o aplicativo do .NET de maneira muito parecida como você faria ao executar sem contêineres.</span><span class="sxs-lookup"><span data-stu-id="3924a-339">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="3924a-340">Testando e depurando sem o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3924a-340">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="3924a-341">Se você estiver desenvolvendo por meio da abordagem de editor/CLI, a depuração de contêineres será mais difícil e será necessário fazer a depuração por meio da geração de rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="3924a-341">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3924a-342">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3924a-342">Additional resources</span></span>

- <span data-ttu-id="3924a-343">**Depurando aplicativos em um contêiner local do Docker**</span><span class="sxs-lookup"><span data-stu-id="3924a-343">**Debugging apps in a local Docker container**</span></span>

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- <span data-ttu-id="3924a-344">**Steve Lasker. Compilar, depurar, implantar aplicativos do ASP.NET Core com o Docker.**</span><span class="sxs-lookup"><span data-stu-id="3924a-344">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="3924a-345">Vídeo.</span><span class="sxs-lookup"><span data-stu-id="3924a-345">Video.</span></span>

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="3924a-346">Fluxo de trabalho simplificado ao desenvolver contêineres com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3924a-346">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="3924a-347">Efetivamente, o fluxo de trabalho ao usar o Visual Studio é muito mais simples do que ao usar a abordagem de editor/CLI.</span><span class="sxs-lookup"><span data-stu-id="3924a-347">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="3924a-348">A maioria das etapas necessárias pelo Docker, relacionadas ao Dockerfile e aos arquivos docker-compose.yml, são ocultas ou simplificadas pelo Visual Studio, conforme mostrado na Figura 5-15.</span><span class="sxs-lookup"><span data-stu-id="3924a-348">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![Fluxo de trabalho simplificado ao desenvolver com o Visual Studio](./media/image20.png)

<span data-ttu-id="3924a-350">**Figura 5-15**.</span><span class="sxs-lookup"><span data-stu-id="3924a-350">**Figure 5-15**.</span></span> <span data-ttu-id="3924a-351">Fluxo de trabalho simplificado ao desenvolver com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3924a-351">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="3924a-352">Além disso, será necessário executar a etapa 2 (adicionar suporte do Docker aos seus projetos) apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="3924a-352">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="3924a-353">Portanto, o fluxo de trabalho é semelhante às suas tarefas de desenvolvimento regulares, quando utiliza o .NET para qualquer outro desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3924a-353">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="3924a-354">É necessário saber o que está acontecendo nos bastidores (o processo de build da imagem, quais imagens base você está usando, implantação de contêineres, etc.) e, às vezes, você também precisará editar o Dockerfile ou o arquivo docker-compose.yml para personalizar comportamentos.</span><span class="sxs-lookup"><span data-stu-id="3924a-354">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="3924a-355">Mas a maior parte do trabalho é bastante simplificada com o uso do Visual Studio, o que o torna muito mais produtivo.</span><span class="sxs-lookup"><span data-stu-id="3924a-355">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3924a-356">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3924a-356">Additional resources</span></span>

- <span data-ttu-id="3924a-357">**Steve Lasker. Desenvolvimento do Docker no .NET com o Visual Studio 2017**</span><span class="sxs-lookup"><span data-stu-id="3924a-357">**Steve Lasker. .NET Docker Development with Visual Studio 2017**</span></span>

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

- <span data-ttu-id="3924a-358">**Jeffrey T. Fritz. Colocar um aplicativo .NET Core em um contêiner com as novas Ferramentas do Docker para Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="3924a-358">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**</span></span>

   [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="3924a-359">Usando comandos do PowerShell em um DockerFile para configurar contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="3924a-359">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="3924a-360">Os [contêineres do Windows](/virtualization/windowscontainers/about/) permitem converter seus aplicativos existentes do Windows em imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker.</span><span class="sxs-lookup"><span data-stu-id="3924a-360">[Windows Containers](/virtualization/windowscontainers/about/) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="3924a-361">Para usar contêineres do Windows, você executa comandos do PowerShell no Dockerfile, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3924a-361">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore

LABEL Description="IIS" Vendor="Microsoft" Version="10"

RUN powershell -Command Add-WindowsFeature Web-Server

CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="3924a-362">Nesse caso, estamos usando uma imagem base do Windows Server Core (a configuração FROM) e instalando IIS com um comando do PowerShell (a configuração RUN).</span><span class="sxs-lookup"><span data-stu-id="3924a-362">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="3924a-363">Da mesma forma, você também pode usar comandos do PowerShell para configurar outros componentes, como ASP.NET 4.x, .NET 4.6 ou qualquer outro software do Windows.</span><span class="sxs-lookup"><span data-stu-id="3924a-363">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="3924a-364">Por exemplo, o seguinte comando, em um Dockerfile, configura o ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="3924a-364">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="3924a-365">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3924a-365">Additional resources</span></span>

- <span data-ttu-id="3924a-366">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="3924a-366">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="3924a-367">Comandos do PowerShell de exemplo para executar em Dockerfiles e incluir recursos do Windows.</span><span class="sxs-lookup"><span data-stu-id="3924a-367">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>

   [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="3924a-368">[Anterior](index.md)
[Próximo](../net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="3924a-368">[Previous](index.md)
[Next](../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>