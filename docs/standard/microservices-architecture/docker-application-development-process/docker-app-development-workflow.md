---
title: Fluxo de trabalho de desenvolvimento para aplicativos do Docker
description: Entenda os detalhes do fluxo de trabalho para o desenvolvimento de aplicativos baseados no Docker. Comece o passo a passo e obtenha alguns detalhes para otimizar Dockerfiles e concluir com o fluxo de trabalho simplificado disponível ao usar o Visual Studio.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: d494dba829d8065e2bc1424bc9bcc11e265fbcc0
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921085"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="0374c-104">Fluxo de trabalho de desenvolvimento para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="0374c-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="0374c-105">O ciclo de vida de desenvolvimento de aplicativo começa em seu computador, como desenvolvedor, onde você pode codificar o aplicativo usando sua linguagem preferida e testá-lo localmente.</span><span class="sxs-lookup"><span data-stu-id="0374c-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="0374c-106">Com esse fluxo de trabalho, não importa a linguagem, a estrutura e a plataforma escolhidas, você está sempre desenvolvendo e testando contêineres do Docker, mas localmente.</span><span class="sxs-lookup"><span data-stu-id="0374c-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="0374c-107">Cada contêiner (uma instância de uma imagem do Docker) inclui os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="0374c-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="0374c-108">Uma seleção de sistema operacional, por exemplo, uma distribuição do Linux, o Windows Nano Server ou o Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="0374c-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="0374c-109">Arquivos adicionados durante o desenvolvimento, por exemplo, os binários e o código-fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0374c-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="0374c-110">Informações de configuração, como configurações de ambiente e dependências.</span><span class="sxs-lookup"><span data-stu-id="0374c-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="0374c-111">Fluxo de trabalho para o desenvolvimento de aplicativos baseados em contêiner do Docker</span><span class="sxs-lookup"><span data-stu-id="0374c-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="0374c-112">Esta seção descreve o fluxo de trabalho de desenvolvimento do *loop interno* de aplicativos baseados em contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="0374c-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="0374c-113">O fluxo de trabalho de loop interno significa que ele não está considerando o fluxo de trabalho de DevOps mais amplo, que pode incluir até implantação de produção e apenas se concentra no trabalho de desenvolvimento realizado no computador do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="0374c-113">The inner-loop workflow means it's not considering the broader DevOps workflow, that can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="0374c-114">As etapas iniciais para configurar o ambiente não são incluídas, pois elas são executadas apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="0374c-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="0374c-115">Um aplicativo é composto de seus próprios serviços e de bibliotecas adicionais (dependências).</span><span class="sxs-lookup"><span data-stu-id="0374c-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="0374c-116">A figura 5-1 a seguir ilustra as etapas básicas que são normalmente realizadas para criar um aplicativo do Docker.</span><span class="sxs-lookup"><span data-stu-id="0374c-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![<span data-ttu-id="0374c-117">O processo de desenvolvimento de aplicativos do Docker: 1 – Codificar o aplicativo, 2 – Escrever Dockerfiles, 3 – Criar imagens definidas nos Dockerfiles, 4 – (opcional) Criar serviços no arquivo docker-compose.yml, 5 – Executar o contêiner ou o aplicativo docker-compose, 6 – Testar o aplicativo ou os microsserviços, 7 – Enviar por push para o repositório e repetir.</span><span class="sxs-lookup"><span data-stu-id="0374c-117">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span> ](./media/image1.png)

**<span data-ttu-id="0374c-118">Figura 5-1.</span><span class="sxs-lookup"><span data-stu-id="0374c-118">Figure 5-1.</span></span>** <span data-ttu-id="0374c-119">Fluxo de trabalho passo a passo para o desenvolvimento de aplicativos do Docker em contêineres</span><span class="sxs-lookup"><span data-stu-id="0374c-119">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="0374c-120">Nesta seção, todo esse processo é detalhado e cada etapa principal é explicada com base em um ambiente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0374c-120">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="0374c-121">Ao usar uma abordagem de desenvolvimento de editor/CLI (por exemplo, o Visual Studio Code com a CLI do Docker no macOS ou no Windows), você precisará conhecer cada etapa e, na maioria das vezes, com mais detalhes do que ao usar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0374c-121">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="0374c-122">Para obter mais informações sobre como trabalhar em um ambiente de CLI, confira o livro eletrônico [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/) (Ciclo de vida do aplicativo do Docker em contêineres com ferramentas e plataformas da Microsoft).</span><span class="sxs-lookup"><span data-stu-id="0374c-122">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="0374c-123">Quando você usar o Visual Studio 2017, muitas dessas etapas serão feitas para você, melhorando significativamente sua produtividade.</span><span class="sxs-lookup"><span data-stu-id="0374c-123">When you're using Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="0374c-124">Isso se aplica principalmente quando você usa o Visual Studio 2017 e tem aplicativos de vários contêineres como destino.</span><span class="sxs-lookup"><span data-stu-id="0374c-124">This is especially true when you're using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="0374c-125">Por exemplo, com apenas um clique do mouse, o Visual Studio adiciona o Dockerfile e o arquivo docker-compose.yml aos seus projetos com a configuração correta para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0374c-125">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="0374c-126">Ao executar o aplicativo no Visual Studio, ele cria a imagem do Docker e executa o aplicativo de vários contêineres diretamente no Docker; e até mesmo permite que você depure vários contêineres de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="0374c-126">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="0374c-127">Esses recursos vão acelerar sua velocidade de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0374c-127">These features will boost your development speed.</span></span>

<span data-ttu-id="0374c-128">No entanto, apenas porque o Visual Studio automatiza essas etapas não significa que você não precisa saber o que está acontecendo nos bastidores com o Docker.</span><span class="sxs-lookup"><span data-stu-id="0374c-128">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="0374c-129">Portanto, as diretrizes a seguir detalham cada etapa.</span><span class="sxs-lookup"><span data-stu-id="0374c-129">Therefore, the following guidance details every step.</span></span>

![1 – Codificar o aplicativo](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="0374c-131">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="0374c-131">Step 1.</span></span> <span data-ttu-id="0374c-132">Iniciar a codificação e a criação do aplicativo inicial ou da linha de base do serviço</span><span class="sxs-lookup"><span data-stu-id="0374c-132">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="0374c-133">O desenvolvimento de um aplicativo do Docker é semelhante à forma como você desenvolve um aplicativo sem Docker.</span><span class="sxs-lookup"><span data-stu-id="0374c-133">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="0374c-134">A diferença é que, durante o desenvolvimento para o Docker, você está implantando e testando o aplicativo ou os serviços executando-os em contêineres do Docker em seu ambiente local (seja em uma VM do Linux configurada pelo Docker ou diretamente no Windows quando está usando contêineres do Windows).</span><span class="sxs-lookup"><span data-stu-id="0374c-134">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="0374c-135">Configurar seu ambiente local com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0374c-135">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="0374c-136">Para começar, instale o [Docker CE (Community Edition)](https://docs.docker.com/docker-for-windows/) para Windows, conforme explicado nas instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="0374c-136">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="0374c-137">Introdução ao Docker CE for Windows</span><span class="sxs-lookup"><span data-stu-id="0374c-137">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="0374c-138">Além disso, você precisa do Visual Studio 2017 versão 15.7 ou posterior com a carga de trabalho **Desenvolvimento multiplataforma do .NET Core** instalada, conforme mostrado na Figura 5-2.</span><span class="sxs-lookup"><span data-stu-id="0374c-138">In addition, you need Visual Studio 2017 version 15.7 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![Seleção de carga de trabalho de desenvolvimento multiplataforma do .NET Core durante a instalação do Visual Studio.](./media/image3.png)

<span data-ttu-id="0374c-140">**Figura 5-2**.</span><span class="sxs-lookup"><span data-stu-id="0374c-140">**Figure 5-2**.</span></span> <span data-ttu-id="0374c-141">Selecionando a carga de trabalho **Desenvolvimento multiplataforma do .NET Core** durante a instalação do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0374c-141">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="0374c-142">Você pode iniciar a codificação do aplicativo no .NET simples (normalmente no .NET Core, se estiver planejando usar contêineres) mesmo antes de habilitar o Docker no aplicativo e antes da implantação e dos testes no Docker.</span><span class="sxs-lookup"><span data-stu-id="0374c-142">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="0374c-143">No entanto, é recomendável que você comece a trabalhar no Docker assim que possível, porque que esse será o ambiente real e os problemas poderão ser descobertos o mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="0374c-143">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="0374c-144">Isso é recomendável porque o Visual Studio facilita tanto o trabalho com o Docker parecendo, até mesmo, transparente — o melhor exemplo ao depurar aplicativos de vários contêineres do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0374c-144">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0374c-145">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="0374c-145">Additional resources</span></span>

- <span data-ttu-id="0374c-146">**Introdução ao Docker CE for Windows** \\</span><span class="sxs-lookup"><span data-stu-id="0374c-146">**Get started with Docker CE for Windows** \\</span></span>
  [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)

- <span data-ttu-id="0374c-147">**Visual Studio 2017** \\</span><span class="sxs-lookup"><span data-stu-id="0374c-147">**Visual Studio 2017** \\</span></span>
  [https://visualstudio.microsoft.com/downloads/](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![2 – Escrever Dockerfiles](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="0374c-149">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="0374c-149">Step 2.</span></span> <span data-ttu-id="0374c-150">Criar um Dockerfile relacionado a uma imagem base existente do .NET</span><span class="sxs-lookup"><span data-stu-id="0374c-150">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="0374c-151">Você precisa de um Dockerfile para cada imagem personalizada que você deseja criar. Você também precisará de um Dockerfile para cada contêiner a ser implantado automaticamente, por meio do Visual Studio, ou implantado manualmente, usando a CLI do Docker (comandos docker run e docker-compose).</span><span class="sxs-lookup"><span data-stu-id="0374c-151">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="0374c-152">Se seu aplicativo contém um único serviço personalizado, é necessário um único Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="0374c-152">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="0374c-153">Se seu aplicativo contém vários serviços (como em uma arquitetura de microsserviços), é necessário um Dockerfile para cada serviço.</span><span class="sxs-lookup"><span data-stu-id="0374c-153">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="0374c-154">O Dockerfile é colocado na pasta raiz do seu aplicativo ou serviço.</span><span class="sxs-lookup"><span data-stu-id="0374c-154">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="0374c-155">Ele contém os comandos que indicam ao Docker como configurar e executar seu aplicativo ou serviço em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="0374c-155">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="0374c-156">Você pode criar manualmente um Dockerfile por meio de código e adicioná-lo ao seu projeto junto com as dependências do .NET.</span><span class="sxs-lookup"><span data-stu-id="0374c-156">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="0374c-157">Com o Visual Studio e suas ferramentas para Docker, esta tarefa requer apenas alguns cliques do mouse.</span><span class="sxs-lookup"><span data-stu-id="0374c-157">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="0374c-158">Quando você cria um projeto no Visual Studio 2017, há uma opção chamada **Habilitar suporte a contêiner (Docker)**, conforme mostrado na Figura 5-3.</span><span class="sxs-lookup"><span data-stu-id="0374c-158">When you create a new project in Visual Studio 2017, there's an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![Habilitar a caixa de seleção de suporte ao Docker ao criar um projeto ASP.NET Core no Visual Studio 2017](./media/image5.png)

<span data-ttu-id="0374c-160">**Figura 5-3**.</span><span class="sxs-lookup"><span data-stu-id="0374c-160">**Figure 5-3**.</span></span> <span data-ttu-id="0374c-161">Habilitando o suporte ao Docker ao criar um projeto ASP.NET Core no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0374c-161">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2017</span></span>

<span data-ttu-id="0374c-162">Você também pode habilitar o suporte ao Docker em um projeto de aplicativo Web ASP.NET Core existente clicando com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecionando **Adicionar** > **Suporte ao Docker**, conforme mostrado na Figura 5-4.</span><span class="sxs-lookup"><span data-stu-id="0374c-162">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![Adicionar a opção de menu de suporte ao Docker no Visual Studio](./media/image6.png)

<span data-ttu-id="0374c-164">**Figura 5-4**.</span><span class="sxs-lookup"><span data-stu-id="0374c-164">**Figure 5-4**.</span></span> <span data-ttu-id="0374c-165">Habilitando o suporte do Docker em um projeto existente do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0374c-165">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="0374c-166">Essa ação adiciona um *Dockerfile* ao projeto com a configuração necessária e só está disponível em projetos ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0374c-166">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="0374c-167">De maneira semelhante, o Visual Studio também pode adicionar um arquivo docker-compose.yml a toda a solução com a opção **Adicionar > Suporte ao orquestrador de contêineres**.</span><span class="sxs-lookup"><span data-stu-id="0374c-167">In a similar fashion, Visual Studio can also add a docker-compose.yml file for the whole solution with the option **Add > Container Orchestrator Support**.</span></span> <span data-ttu-id="0374c-168">Na etapa 4, exploraremos essa opção com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="0374c-168">In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="0374c-169">Usando uma imagem do Docker do .NET oficial existente</span><span class="sxs-lookup"><span data-stu-id="0374c-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="0374c-170">Geralmente, você cria uma imagem personalizada para o contêiner usando uma imagem base que você pode obter de um repositório oficial, como o Registro do [Docker Hub](https://hub.docker.com/).</span><span class="sxs-lookup"><span data-stu-id="0374c-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="0374c-171">É exatamente isso o que acontece nos bastidores quando você habilita o suporte do Docker no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0374c-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="0374c-172">O Dockerfile usará uma imagem `aspnetcore` existente.</span><span class="sxs-lookup"><span data-stu-id="0374c-172">Your Dockerfile will use an existing `aspnetcore` image.</span></span>

<span data-ttu-id="0374c-173">Anteriormente, explicamos quais imagens do Docker e quais repositórios você poderia usar, dependendo da estrutura e do sistema operacional que você escolheu.</span><span class="sxs-lookup"><span data-stu-id="0374c-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="0374c-174">Por exemplo, se você quiser usar o ASP.NET Core (Linux ou Windows), a imagem a ser usada será `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="0374c-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="0374c-175">Assim, basta especificar qual imagem base do Docker será usada para o seu contêiner.</span><span class="sxs-lookup"><span data-stu-id="0374c-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="0374c-176">Você pode fazer isso adicionando `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` ao seu Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="0374c-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` to your Dockerfile.</span></span> <span data-ttu-id="0374c-177">Isso será realizado automaticamente pelo Visual Studio, mas se você precisar atualizar a versão, será esse valor que você atualizará.</span><span class="sxs-lookup"><span data-stu-id="0374c-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="0374c-178">O uso de um repositório de imagem oficial do .NET do Hub do Docker com um número de versão garante que os mesmos recursos de linguagem estejam disponíveis em todos os computadores (incluindo desenvolvimento, teste e produção).</span><span class="sxs-lookup"><span data-stu-id="0374c-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="0374c-179">O exemplo a seguir mostra um Dockerfile de exemplo para um contêiner do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0374c-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="0374c-180">Nesse caso, a imagem é baseada na versão 2.2 da imagem oficial do Docker do ASP.NET Core (de várias arquiteturas para o Linux e o Windows).</span><span class="sxs-lookup"><span data-stu-id="0374c-180">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="0374c-181">Essa é a configuração `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="0374c-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="0374c-182">(Para obter mais informações sobre essa imagem base, confira a página [Imagem do Docker do .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).) No Dockerfile, você também precisará instruir o Docker a escutar na porta TCP que você usará em tempo de execução (nesse caso, a porta 80, conforme definido com a configuração EXPOSE).</span><span class="sxs-lookup"><span data-stu-id="0374c-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="0374c-183">Você pode especificar mais definições de configurações no Dockerfile, dependendo da linguagem e da estrutura usadas.</span><span class="sxs-lookup"><span data-stu-id="0374c-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="0374c-184">Por exemplo, a linha ENTRYPOINT com `["dotnet", "MySingleContainerWebApp.dll"]` diz ao Docker para executar um aplicativo do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0374c-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="0374c-185">Se você estiver usando o SDK e a CLI do .NET Core (CLI do dotnet) para compilar e executar o aplicativo do .NET, essa configuração será diferente.</span><span class="sxs-lookup"><span data-stu-id="0374c-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="0374c-186">O essencial é que a linha ENTRYPOINT e outras configurações serão diferentes dependendo da linguagem e da plataforma que você escolher para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0374c-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0374c-187">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="0374c-187">Additional resources</span></span>

- <span data-ttu-id="0374c-188">**Criando imagens do Docker para aplicativos do .NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="0374c-188">**Building Docker Images for .NET Core Applications** \\</span></span>
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

- <span data-ttu-id="0374c-189">**Criar sua própria imagem**.</span><span class="sxs-lookup"><span data-stu-id="0374c-189">**Build your own image**.</span></span> <span data-ttu-id="0374c-190">Na documentação oficial do Docker.\\</span><span class="sxs-lookup"><span data-stu-id="0374c-190">In the official Docker documentation.\\</span></span>
  [https://docs.docker.com/engine/tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/)

- <span data-ttu-id="0374c-191">**Staying up-to-date with .NET Container Images** \ (Permanecendo atualizado com as imagens de contêiner do .NET)</span><span class="sxs-lookup"><span data-stu-id="0374c-191">**Staying up-to-date with .NET Container Images** \\</span></span>
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="0374c-192">**Using .NET and Docker Together – DockerCon 2018 Update** \ (Usando o .NET e o Docker juntos – DockerCon atualização de 2018)</span><span class="sxs-lookup"><span data-stu-id="0374c-192">**Using .NET and Docker Together - DockerCon 2018 Update** \\</span></span>
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="0374c-193">Usando repositórios de imagens para várias arquiteturas</span><span class="sxs-lookup"><span data-stu-id="0374c-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="0374c-194">Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="0374c-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="0374c-195">Esse recurso permite que fornecedores, como a Microsoft (criadores de imagem base), criem um único repositório para abranger várias plataformas (ou seja, Linux e Windows).</span><span class="sxs-lookup"><span data-stu-id="0374c-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="0374c-196">Por exemplo, o repositório [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/), disponível no registro do Hub do Docker, é compatível com Linux e Windows Nano Server usando o mesmo nome de repositório.</span><span class="sxs-lookup"><span data-stu-id="0374c-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="0374c-197">Ao especificar uma marcação, você direciona a uma plataforma que é explícita, como nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="0374c-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  <span data-ttu-id="0374c-198">Destinos: .NET Core 2.2 somente em tempo de execução no Linux</span><span class="sxs-lookup"><span data-stu-id="0374c-198">Targets: .NET Core 2.2 runtime-only on Linux</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  <span data-ttu-id="0374c-199">Destinos: .NET Core 2.2 somente em tempo de execução no Windows Nano Server</span><span class="sxs-lookup"><span data-stu-id="0374c-199">Targets: .NET Core 2.2 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="0374c-200">Mas, se você especificar o mesmo nome de imagem, mesmo com a mesma marca, as imagens para várias arquiteturas (como a imagem `aspnetcore`) usarão a versão do Linux ou do Windows, dependendo do sistema operacional do host do Docker em que você esteja implantando, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0374c-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnetcore` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  <span data-ttu-id="0374c-201">Várias arquiteturas: .NET Core 2.2 somente em tempo de execução no Linux ou no Windows Nano Server, dependendo do sistema operacional do host do Docker</span><span class="sxs-lookup"><span data-stu-id="0374c-201">Multi-arch: .NET Core 2.2 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="0374c-202">Dessa forma, ao efetuar pull de uma imagem de um host do Windows, será efetuado o pull da variante do Windows e, ao efetuar pull do mesmo nome de imagem de um host do Linux, será efetuado pull da variante do Linux.</span><span class="sxs-lookup"><span data-stu-id="0374c-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="0374c-203">Builds de vários estágios no Dockerfile</span><span class="sxs-lookup"><span data-stu-id="0374c-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="0374c-204">O Dockerfile é semelhante a um script em lotes.</span><span class="sxs-lookup"><span data-stu-id="0374c-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="0374c-205">Como o que você faria se tivesse que configurar o computador da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="0374c-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="0374c-206">Ele começa com uma imagem base que define o contexto inicial, como o sistema de arquivos de inicialização, que se baseia no sistema operacional do host.</span><span class="sxs-lookup"><span data-stu-id="0374c-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="0374c-207">Ele não é um sistema operacional, mas você pode imaginá-lo como se fosse "o sistema operacional” dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="0374c-207">It's not an OS, but you can think of if like "the" OS inside the container.</span></span>

<span data-ttu-id="0374c-208">A execução de cada linha de comando cria uma camada no sistema de arquivos com as alterações em relação à anterior, para que, quando combinadas, produzam o sistema de arquivos resultante.</span><span class="sxs-lookup"><span data-stu-id="0374c-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="0374c-209">Como cada nova camada é baseada na anterior e o tamanho da imagem resultante aumenta com cada comando, as imagens poderão ficar muito grandes se precisarem incluir, por exemplo, o SDK necessário para criar e publicar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0374c-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="0374c-210">É nesse ponto que os builds de vários estágios (do Docker 17.05 e superior) entram em cena para fazer a mágica.</span><span class="sxs-lookup"><span data-stu-id="0374c-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="0374c-211">A ideia central é que você pode separar o processo de execução do Dockerfile em estágios, em que um estágio é uma imagem inicial seguida por um ou mais comandos, e o último estágio determina o tamanho da imagem final.</span><span class="sxs-lookup"><span data-stu-id="0374c-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="0374c-212">Resumindo, os builds de vários estágios permitem dividir a criação em "fases" diferentes e, em seguida, montar a imagem final usando somente os diretórios relevantes dos estágios intermediários.</span><span class="sxs-lookup"><span data-stu-id="0374c-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="0374c-213">A estratégia geral para usar esse recurso é:</span><span class="sxs-lookup"><span data-stu-id="0374c-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="0374c-214">usar uma imagem base do SDK (não importa quão grande), com todos os componentes necessários para criar e publicar o aplicativo em uma pasta e, em seguida,</span><span class="sxs-lookup"><span data-stu-id="0374c-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="0374c-215">usar uma imagem base pequena, somente em tempo de execução e copiar a pasta de publicação do estágio anterior para produzir uma pequena imagem final.</span><span class="sxs-lookup"><span data-stu-id="0374c-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="0374c-216">Provavelmente a melhor maneira de entender os vários estágios é percorrer um Dockerfile detalhadamente, linha por linha, então, vamos começar com o Dockerfile inicial criado pelo Visual Studio ao adicionar o suporte ao Docker a um projeto e entraremos em algumas otimizações mais tarde.</span><span class="sxs-lookup"><span data-stu-id="0374c-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="0374c-217">O Dockerfile inicial pode ser como este:</span><span class="sxs-lookup"><span data-stu-id="0374c-217">The initial Dockerfile might look something like this:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks … 
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -0 /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

<span data-ttu-id="0374c-218">E estes são os detalhes, linha por linha:</span><span class="sxs-lookup"><span data-stu-id="0374c-218">And these are the details, line by line:</span></span>

1.  <span data-ttu-id="0374c-219">Inicie um estágio com uma imagem base "pequena" somente em tempo de execução, chamando-a de **base** para referência.</span><span class="sxs-lookup"><span data-stu-id="0374c-219">Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>
2.  <span data-ttu-id="0374c-220">Crie o diretório **/app** na imagem.</span><span class="sxs-lookup"><span data-stu-id="0374c-220">Create **/app** directory in the image.</span></span>
3.  <span data-ttu-id="0374c-221">Exponha a porta **80**.</span><span class="sxs-lookup"><span data-stu-id="0374c-221">Expose port **80**.</span></span>
<!-- skip -->
5.  <span data-ttu-id="0374c-222">Inicie um novo estágio com imagem "grande" para build/publicação, chamando-a de **build** para referência.</span><span class="sxs-lookup"><span data-stu-id="0374c-222">Begin a new stage with "large" image for building/publishing, call it **build** for reference.</span></span>
6.  <span data-ttu-id="0374c-223">Crie o diretório **/src** na imagem.</span><span class="sxs-lookup"><span data-stu-id="0374c-223">Create directory **/src** in the image.</span></span>
7.  <span data-ttu-id="0374c-224">Até a linha 16, copie os arquivos de projetos **.csproj** referenciados, para poder restaurar os pacotes mais tarde.</span><span class="sxs-lookup"><span data-stu-id="0374c-224">Up to line 16, copy referenced projects **.csproj** files, to be able to restore packages later.</span></span>
<!-- skip -->
17. <span data-ttu-id="0374c-225">Restaure os pacotes do projeto **Catalog.API** e os projetos referenciados.</span><span class="sxs-lookup"><span data-stu-id="0374c-225">Restore packages for the **Catalog.API** project and the referenced projects.</span></span>
18. <span data-ttu-id="0374c-226">Copie **toda a árvores de diretórios da solução** (exceto os arquivos/diretórios incluídos no arquivo **.dockerignore**) para o diretório **/src** na imagem.</span><span class="sxs-lookup"><span data-stu-id="0374c-226">Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) from to the **/src** directory in the image.</span></span>
19. <span data-ttu-id="0374c-227">Altere a pasta atual para o projeto **Catalog.API**.</span><span class="sxs-lookup"><span data-stu-id="0374c-227">Change current folder to **Catalog.API** project.</span></span>
20. <span data-ttu-id="0374c-228">Compile o projeto (e outras dependências do projeto) e emita a saída no diretório **/app** na imagem.</span><span class="sxs-lookup"><span data-stu-id="0374c-228">Build project (and other project dependencies) and output to **/app** directory in the image.</span></span>
<!-- skip -->
22. <span data-ttu-id="0374c-229">Comece um novo estágio continuando do build, chamando-o de **publicar** para referência.</span><span class="sxs-lookup"><span data-stu-id="0374c-229">Begin a new stage continuing from build, call it **publish** for reference.</span></span>
23. <span data-ttu-id="0374c-230">Publique o projeto (e as dependências) e emita a saída para o diretório **/app** na imagem.</span><span class="sxs-lookup"><span data-stu-id="0374c-230">Publish project (and dependencies) and output to **/app** directory in the image.</span></span>
<!-- skip -->
25. <span data-ttu-id="0374c-231">Comece um novo estágio continuando da **base** e chame-o de **final**</span><span class="sxs-lookup"><span data-stu-id="0374c-231">Begin a new stage continuing from **base** and call it **final**</span></span>
26. <span data-ttu-id="0374c-232">Altere o diretório atual para **/app**</span><span class="sxs-lookup"><span data-stu-id="0374c-232">Change current directory to **/app**</span></span>
27. <span data-ttu-id="0374c-233">Copie o diretório **/app** do estágio **publicar** no diretório atual</span><span class="sxs-lookup"><span data-stu-id="0374c-233">Copy the **/app** directory from stage **publish** to the current directory</span></span>
28. <span data-ttu-id="0374c-234">Defina o comando a ser executado quando o contêiner for iniciado.</span><span class="sxs-lookup"><span data-stu-id="0374c-234">Define the command to run when the container is started.</span></span>

<span data-ttu-id="0374c-235">Agora vamos explorar algumas otimizações para melhorar o desempenho de todo o processo que, no caso do eShopOnContainers, significa cerca de 22 minutos ou mais para criar a solução completa em contêineres do Linux.</span><span class="sxs-lookup"><span data-stu-id="0374c-235">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="0374c-236">Você aproveitará o recurso de cache de camada do Docker, que é bastante simples: se a imagem base e os comandos forem iguais a outros já executados, ele poderá usar apenas a camada resultante sem precisar executar os comandos, economizando tempo.</span><span class="sxs-lookup"><span data-stu-id="0374c-236">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="0374c-237">Portanto, vamos nos concentrar no estágio **build**. As linhas 5 a 6 são basicamente as mesmas, mas as linhas 7 a 17 são diferentes para cada serviço do eShopOnContainers, portanto precisam ser executadas todas as vezes, no entanto, se você tiver alterado as linhas 7 a 16 para:</span><span class="sxs-lookup"><span data-stu-id="0374c-237">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```
COPY . .
```

<span data-ttu-id="0374c-238">Ele seria igual para cada serviço, ele poderia copiar toda a solução e criar uma camada maior, mas:</span><span class="sxs-lookup"><span data-stu-id="0374c-238">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1) <span data-ttu-id="0374c-239">o processo de cópia seria executado somente na primeira vez (e durante a recriação, se algum arquivo fosse alterado) e usaria o cache para todos os outros serviços e</span><span class="sxs-lookup"><span data-stu-id="0374c-239">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2) <span data-ttu-id="0374c-240">como a imagem maior ocorre em um estágio intermediário, ela não afeta o tamanho da imagem final.</span><span class="sxs-lookup"><span data-stu-id="0374c-240">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="0374c-241">A próxima otimização significativa envolve o comando `restore` executado na linha 17, que também é diferente para cada serviço do eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0374c-241">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="0374c-242">Se você alterar essa linha para apenas:</span><span class="sxs-lookup"><span data-stu-id="0374c-242">If you change that line to just:</span></span>

```console
RUN dotnet restore
```

<span data-ttu-id="0374c-243">Isso restauraria os pacotes de toda a solução, mas, novamente, isso seria feito apenas uma vez, em vez de 15 vezes com a estratégia atual.</span><span class="sxs-lookup"><span data-stu-id="0374c-243">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="0374c-244">No entanto, `dotnet restore` só será executado se houver um único arquivo de projeto ou de solução na pasta, portanto, isso é um pouco mais complicado e a maneira de resolvê-lo, sem entrar em muitos detalhes, é esta:</span><span class="sxs-lookup"><span data-stu-id="0374c-244">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1) <span data-ttu-id="0374c-245">adicione as seguintes linhas ao **.dockerignore**:</span><span class="sxs-lookup"><span data-stu-id="0374c-245">Add the following lines to **.dockerignore**:</span></span>

   - `*.sln`<span data-ttu-id="0374c-246">, para ignorar todos os arquivos de solução na árvore da pasta principal</span><span class="sxs-lookup"><span data-stu-id="0374c-246">, to ignore all solution files in the main folder tree</span></span>

   - `!eShopOnContainers-ServicesAndWebApps.sln`<span data-ttu-id="0374c-247">, para incluir apenas esse arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="0374c-247">, to include only this solution file.</span></span>

2) <span data-ttu-id="0374c-248">inclua o argumento `/ignoreprojectextensions:.dcproj` em `dotnet restore`, para que ele também ignore o projeto docker-compose e só restaure os pacotes da solução eShopOnContainers-ServicesAndWebApps.</span><span class="sxs-lookup"><span data-stu-id="0374c-248">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="0374c-249">Para a otimização final, acontece que a linha 20 é redundante e a linha 23 também compila o aplicativo e vem, naturalmente, logo após a linha 20, o que gera outro comando demorado.</span><span class="sxs-lookup"><span data-stu-id="0374c-249">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="0374c-250">O arquivo resultante é:</span><span class="sxs-lookup"><span data-stu-id="0374c-250">The resulting file is then:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="0374c-251">Criação da imagem base do zero</span><span class="sxs-lookup"><span data-stu-id="0374c-251">Creating your base image from scratch</span></span>

<span data-ttu-id="0374c-252">Você pode criar sua própria imagem base do Docker do zero.</span><span class="sxs-lookup"><span data-stu-id="0374c-252">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="0374c-253">Esse cenário não é recomendável para um iniciante no Docker, mas se você desejar definir os bits específicos da sua própria imagem base, isso será possível.</span><span class="sxs-lookup"><span data-stu-id="0374c-253">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0374c-254">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="0374c-254">Additional resources</span></span>

- <span data-ttu-id="0374c-255">**Imagens do .NET Core para várias arquiteturas**.\\</span><span class="sxs-lookup"><span data-stu-id="0374c-255">**Multi-arch .NET Core images**.\\</span></span>
  [https://github.com/dotnet/announcements/issues/14](https://github.com/dotnet/announcements/issues/14)

- <span data-ttu-id="0374c-256">**Criar uma imagem base**.</span><span class="sxs-lookup"><span data-stu-id="0374c-256">**Create a base image**.</span></span> <span data-ttu-id="0374c-257">Documentação oficial do Docker.\\</span><span class="sxs-lookup"><span data-stu-id="0374c-257">Official Docker documentation.\\</span></span>
  [https://docs.docker.com/engine/userguide/eng-image/baseimages/](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![3 – Criar imagens definidas em Dockerfiles](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="0374c-259">Etapa 3.</span><span class="sxs-lookup"><span data-stu-id="0374c-259">Step 3.</span></span> <span data-ttu-id="0374c-260">Criar imagens personalizadas do Docker e inserir seu aplicativo ou serviço nelas</span><span class="sxs-lookup"><span data-stu-id="0374c-260">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="0374c-261">Para cada serviço do seu aplicativo, você precisa criar uma imagem relacionada.</span><span class="sxs-lookup"><span data-stu-id="0374c-261">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="0374c-262">Se seu aplicativo é composto de um único serviço ou aplicativo Web, você precisa apenas de uma única imagem.</span><span class="sxs-lookup"><span data-stu-id="0374c-262">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="0374c-263">Observe que as imagens do Docker são criadas automaticamente para você no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0374c-263">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="0374c-264">As etapas a seguir são necessárias apenas para o fluxo de trabalho de editor/CLI e são explicadas com a finalidade de esclarecer o que acontece nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="0374c-264">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="0374c-265">Você, como desenvolvedor, precisa desenvolver e testar localmente até enviar um recurso concluído por push ou mudar para o sistema de controle do código-fonte (por exemplo, para o GitHub).</span><span class="sxs-lookup"><span data-stu-id="0374c-265">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="0374c-266">Isso significa que você precisa criar as imagens do Docker e implantar contêineres em um host do Docker local (VM do Windows ou Linux) e executar, testar e depurar nesses contêineres locais.</span><span class="sxs-lookup"><span data-stu-id="0374c-266">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="0374c-267">Para criar uma imagem personalizada no seu ambiente local, usando a CLI do Docker e o Dockerfile, você pode usar o comando docker build, como na Figura 5-5.</span><span class="sxs-lookup"><span data-stu-id="0374c-267">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Tela de progresso da criação de uma imagem do Docker](./media/image8.png)

<span data-ttu-id="0374c-269">**Figura 5-5**.</span><span class="sxs-lookup"><span data-stu-id="0374c-269">**Figure 5-5**.</span></span> <span data-ttu-id="0374c-270">Criando uma imagem personalizada do Docker</span><span class="sxs-lookup"><span data-stu-id="0374c-270">Creating a custom Docker image</span></span>

<span data-ttu-id="0374c-271">Opcionalmente, em vez de executar diretamente o comando docker build na pasta do projeto, você pode, primeiro, gerar uma pasta implantável com as bibliotecas e os binários do .NET necessários, executando `dotnet publish` e, em seguida, usar o comando `docker build`.</span><span class="sxs-lookup"><span data-stu-id="0374c-271">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="0374c-272">Isso criará uma imagem do Docker com o nome `cesardl/netcore-webapi-microservice-docker:first`.</span><span class="sxs-lookup"><span data-stu-id="0374c-272">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="0374c-273">Nesse caso, :first é uma marcação que representa uma versão específica.</span><span class="sxs-lookup"><span data-stu-id="0374c-273">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="0374c-274">Você poderá repetir esta etapa para cada imagem personalizada que tiver que criar para o seu aplicativo composto do Docker.</span><span class="sxs-lookup"><span data-stu-id="0374c-274">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="0374c-275">Quando um aplicativo é composto de vários contêineres (ou seja, ele é um aplicativo multicontêineres), você também pode usar o comando `docker-compose up --build` para compilar todas as imagens relacionadas com um único comando usando os metadados expostos nos arquivos docker-compose.yml relacionados.</span><span class="sxs-lookup"><span data-stu-id="0374c-275">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="0374c-276">Você pode encontrar as imagens existentes no seu repositório local usando o comando docker images, conforme mostrado na Figura 5-6.</span><span class="sxs-lookup"><span data-stu-id="0374c-276">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Exibição de tela da lista de imagens do comando docker images](./media/image9.png)

**<span data-ttu-id="0374c-278">Figura 5-6.</span><span class="sxs-lookup"><span data-stu-id="0374c-278">Figure 5-6.</span></span>** <span data-ttu-id="0374c-279">Exibição de imagens existentes usando o comando docker images</span><span class="sxs-lookup"><span data-stu-id="0374c-279">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="0374c-280">Criação de imagens do Docker com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0374c-280">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="0374c-281">Ao usar o Visual Studio para criar um projeto com suporte ao Docker, você não cria explicitamente uma imagem.</span><span class="sxs-lookup"><span data-stu-id="0374c-281">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="0374c-282">Em vez disso, a imagem é criada quando você pressiona **F5** (ou **Ctrl+F5**) para executar o aplicativo ou o serviço convertido para Docker.</span><span class="sxs-lookup"><span data-stu-id="0374c-282">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="0374c-283">Esta etapa é automática no Visual Studio e você não verá ela ocorrer, mas é importante que você saiba o que está acontecendo nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="0374c-283">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![4 – (opcional) Criar serviços no arquivo docker-compose.yml](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="0374c-285">Etapa 4.</span><span class="sxs-lookup"><span data-stu-id="0374c-285">Step 4.</span></span> <span data-ttu-id="0374c-286">Definir os serviços no docker-compose.yml ao compilar um aplicativo de vários contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="0374c-286">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="0374c-287">O arquivo [docker-compose.yml](https://docs.docker.com/compose/compose-file/) permite que você defina um conjunto de serviços relacionados para que sejam implantados como um aplicativo composto com comandos de implantação.</span><span class="sxs-lookup"><span data-stu-id="0374c-287">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="0374c-288">Ele também configura as relações de dependência e a configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0374c-288">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="0374c-289">Para usar um arquivo docker-compose.yml, você precisa criar o arquivo na pasta principal ou raiz da sua solução, com conteúdo semelhante ao do exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0374c-289">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

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
      - ConnectionString=Server=sql.data;Port=1433;Database=CatalogDB;…
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

<span data-ttu-id="0374c-290">Esse arquivo docker-compose.yml é uma versão simplificada e mesclada.</span><span class="sxs-lookup"><span data-stu-id="0374c-290">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="0374c-291">Ele contém dados de configuração estáticos para cada contêiner (como o nome da imagem personalizada), o que é sempre necessário, além das informações de configuração que poderão depender do ambiente de implantação, como a cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="0374c-291">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="0374c-292">Nas próximas seções, você aprenderá como dividir a configuração do docker-compose.yml em vários arquivos docker-compose e substituir valores dependendo do ambiente e do tipo de execução (depuração ou lançamento).</span><span class="sxs-lookup"><span data-stu-id="0374c-292">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="0374c-293">O arquivo docker-compose.yml de exemplo define quatro serviços: o serviço `webmvc` (um aplicativo Web), dois microsserviços (`ordering.api` e `basket.api`) e um contêiner de fonte de dados, `sql.data`, com base no SQL Server para Linux, em execução como um contêiner.</span><span class="sxs-lookup"><span data-stu-id="0374c-293">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering.api` and `basket.api`), and one data source container, `sql.data`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="0374c-294">Cada serviço será implantado como um contêiner, portanto, uma imagem do Docker é necessária para cada um.</span><span class="sxs-lookup"><span data-stu-id="0374c-294">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="0374c-295">O arquivo docker-compose.yml não apenas especifica quais contêineres estão sendo usados, mas também como eles são configurados individualmente.</span><span class="sxs-lookup"><span data-stu-id="0374c-295">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="0374c-296">Por exemplo, a definição de contêiner `webmvc` no arquivo .yml:</span><span class="sxs-lookup"><span data-stu-id="0374c-296">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="0374c-297">usa uma imagem `eshop/web:latest` predefinida.</span><span class="sxs-lookup"><span data-stu-id="0374c-297">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="0374c-298">Entretanto, você também poderia definir a imagem para ser compilada como parte da execução do docker-compose, com uma configuração adicional baseada em uma seção build: no arquivo docker-compose.</span><span class="sxs-lookup"><span data-stu-id="0374c-298">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="0374c-299">Inicializa duas variáveis de ambiente (CatalogUrl e OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="0374c-299">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="0374c-300">Encaminha a porta 80, exposta no contêiner, para a porta 80 externa, no computador host.</span><span class="sxs-lookup"><span data-stu-id="0374c-300">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="0374c-301">vincula o aplicativo Web ao catálogo e ao serviço de pedidos com a configuração depends_on.</span><span class="sxs-lookup"><span data-stu-id="0374c-301">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="0374c-302">Isso faz com que o serviço aguarde até que esses serviços sejam iniciados.</span><span class="sxs-lookup"><span data-stu-id="0374c-302">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="0374c-303">Vamos abordar novamente o arquivo docker-compose.yml em uma seção posterior, ao explicar como implementar microsserviços e aplicativos de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="0374c-303">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="0374c-304">Trabalhando com o docker-compose.yml no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0374c-304">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="0374c-305">Além de adicionar um Dockerfile a um projeto, como já mencionado, o Visual Studio 2017 (do 15.8 em diante) pode adicionar o suporte ao orquestrador do Docker Compose em uma solução.</span><span class="sxs-lookup"><span data-stu-id="0374c-305">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="0374c-306">Quando você adiciona o suporte ao orquestrador de contêineres, conforme mostrado na Figura 5-7, pela primeira vez, o Visual Studio cria o Dockerfile para o projeto e cria um projeto (seção de serviço) na solução com vários arquivos `docker-compose*.yml` globais e, em seguida, adiciona o projeto nesses arquivos.</span><span class="sxs-lookup"><span data-stu-id="0374c-306">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="0374c-307">Depois, você pode abrir os arquivos docker-compose.yml e atualizá-los com mais recursos.</span><span class="sxs-lookup"><span data-stu-id="0374c-307">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="0374c-308">Você precisa repetir essa forma de operação para cada projeto que deseja incluir no arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="0374c-308">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="0374c-309">No momento da redação deste artigo, o Visual Studio é compatível com os orquestradores do Docker Compose e do Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="0374c-309">At the time of this writing, Visual Studio supports Docker Compose and Service Fabric orchestrators.</span></span>

![Opção do menu de contexto para adicionar o suporte ao orquestrador a um projeto ASP.NET Core](./media/image21.png)

<span data-ttu-id="0374c-311">**Figura 5-7**.</span><span class="sxs-lookup"><span data-stu-id="0374c-311">**Figure 5-7**.</span></span> <span data-ttu-id="0374c-312">Adicionar suporte do Docker no Visual Studio 2017 ao clicar com o botão direito do mouse em um projeto do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0374c-312">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="0374c-313">Depois de adicionar suporte ao orquestrador à solução no Visual Studio, você também verá um novo nó (no arquivo de projeto `docker-compose.dcproj`) no Gerenciador de Soluções contendo os arquivos docker-compose.yml adicionados, conforme mostrado na Figura 5-8.</span><span class="sxs-lookup"><span data-stu-id="0374c-313">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Nó de docker-compose no Gerenciador de Soluções](./media/image11.png)

<span data-ttu-id="0374c-315">**Figura 5-8**.</span><span class="sxs-lookup"><span data-stu-id="0374c-315">**Figure 5-8**.</span></span> <span data-ttu-id="0374c-316">O nó de árvore **docker-compose** adicionado no Gerenciador de Soluções do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0374c-316">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="0374c-317">Você pode implantar um aplicativo de vários contêineres com um único arquivo docker-compose.yml usando o comando `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="0374c-317">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="0374c-318">No entanto, o Visual Studio adiciona um grupo desses arquivos, para que você possa substituir os valores de acordo com o ambiente (desenvolvimento ou produção) e o tipo de execução (lançamento ou depuração).</span><span class="sxs-lookup"><span data-stu-id="0374c-318">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="0374c-319">Essa funcionalidade será explicada nas seções posteriores.</span><span class="sxs-lookup"><span data-stu-id="0374c-319">This capability will be explained in later sections.</span></span>

![5 – Executar contêineres ou aplicativo compostos](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="0374c-321">Etapa 5.</span><span class="sxs-lookup"><span data-stu-id="0374c-321">Step 5.</span></span> <span data-ttu-id="0374c-322">Compilar e executar seu aplicativo do Docker</span><span class="sxs-lookup"><span data-stu-id="0374c-322">Build and run your Docker application</span></span>

<span data-ttu-id="0374c-323">Se seu aplicativo tem apenas um contêiner, você pode executá-lo implantando-o no host do Docker (VM ou servidor físico).</span><span class="sxs-lookup"><span data-stu-id="0374c-323">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="0374c-324">No entanto, se seu aplicativo contém vários serviços, você pode implantá-lo como um aplicativo composto, usando um único comando de CLI (docker-compose up), ou com o Visual Studio, que usará esse mesmo comando nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="0374c-324">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="0374c-325">Vamos examinar as diferentes opções.</span><span class="sxs-lookup"><span data-stu-id="0374c-325">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="0374c-326">Opção A: executar um aplicativo de contêiner único</span><span class="sxs-lookup"><span data-stu-id="0374c-326">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="0374c-327">Usando a CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="0374c-327">Using Docker CLI</span></span>

<span data-ttu-id="0374c-328">Você pode executar um contêiner do Docker usando o comando `docker run`, conforme mostrado na Figura 5-9:</span><span class="sxs-lookup"><span data-stu-id="0374c-328">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="0374c-329">O comando acima criará uma instância de contêiner da imagem especificada, cada vez que for executado.</span><span class="sxs-lookup"><span data-stu-id="0374c-329">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="0374c-330">Você pode usar o parâmetro `--name` para dar um nome ao contêiner e, em seguida, usar `docker start {name}` (ou usar a ID do contêiner ou o nome automático) para executar uma instância de contêiner existente.</span><span class="sxs-lookup"><span data-stu-id="0374c-330">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container id or automatic name) to run an existing container instance.</span></span>

![Exibição de tela durante a execução de um contêiner do Docker usando o comando docker run](./media/image13.png)

<span data-ttu-id="0374c-332">**Figura 5-9**.</span><span class="sxs-lookup"><span data-stu-id="0374c-332">**Figure 5-9**.</span></span> <span data-ttu-id="0374c-333">Executando um contêiner do Docker usando o comando docker run</span><span class="sxs-lookup"><span data-stu-id="0374c-333">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="0374c-334">Nesse caso, o comando associa a porta interna 5000 do contêiner à porta 80 do computador host.</span><span class="sxs-lookup"><span data-stu-id="0374c-334">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="0374c-335">Isso significa que o host está escutando na porta 80 e encaminhando para a porta 5000 no contêiner.</span><span class="sxs-lookup"><span data-stu-id="0374c-335">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="0374c-336">O hash mostrado é a ID do contêiner e também recebe um nome legível aleatório quando a opção `--name` não é usada.</span><span class="sxs-lookup"><span data-stu-id="0374c-336">The hash shown is the container id and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="0374c-337">Usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0374c-337">Using Visual Studio</span></span>

<span data-ttu-id="0374c-338">Se ainda não adicionou o suporte ao orquestrador de contêineres, você também poderá executar um aplicativo de contêiner único no Visual Studio pressionando **Ctrl+F5** e usar **F5** para depurar o aplicativo dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="0374c-338">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="0374c-339">O contêiner é executado localmente usando o docker run.</span><span class="sxs-lookup"><span data-stu-id="0374c-339">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="0374c-340">Opção B: executar um aplicativo de vários contêineres</span><span class="sxs-lookup"><span data-stu-id="0374c-340">Option B: Running a multi-container application</span></span>

<span data-ttu-id="0374c-341">Na maioria dos cenários empresariais, um aplicativo do Docker será ser composto de vários serviços, o que significa que você precisará executar um aplicativo de vários contêineres, conforme mostrado na Figura 5-10.</span><span class="sxs-lookup"><span data-stu-id="0374c-341">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![VM com vários contêineres do Docker](./media/image14.png)

<span data-ttu-id="0374c-343">**Figura 5-10**.</span><span class="sxs-lookup"><span data-stu-id="0374c-343">**Figure 5-10**.</span></span> <span data-ttu-id="0374c-344">VM com contêineres do Docker implantados</span><span class="sxs-lookup"><span data-stu-id="0374c-344">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="0374c-345">Usando a CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="0374c-345">Using Docker CLI</span></span>

<span data-ttu-id="0374c-346">Para executar um aplicativo de vários contêineres com a CLI do Docker, use o comando `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="0374c-346">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="0374c-347">Esse comando usa o arquivo **docker-compose.yml**, que existe no nível da solução, para implantar um aplicativo de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="0374c-347">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="0374c-348">A figura 5-11 mostra os resultados da execução do comando no diretório principal da solução, que contém o arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="0374c-348">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Exibição da tela ao executar o comando docker-compose up](./media/image15.png)

<span data-ttu-id="0374c-350">**Figura 5-11**.</span><span class="sxs-lookup"><span data-stu-id="0374c-350">**Figure 5-11**.</span></span> <span data-ttu-id="0374c-351">Resultados de exemplo ao executar o comando docker-compose up</span><span class="sxs-lookup"><span data-stu-id="0374c-351">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="0374c-352">Depois que o comando docker-compose up é executado, o aplicativo e os contêineres relacionados são implantados no host do Docker, como é mostrado na Figura 5-10.</span><span class="sxs-lookup"><span data-stu-id="0374c-352">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="0374c-353">Usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0374c-353">Using Visual Studio</span></span>

<span data-ttu-id="0374c-354">A execução de um aplicativo de vários contêineres com o Visual Studio 2017 é muito simples.</span><span class="sxs-lookup"><span data-stu-id="0374c-354">Running a multi-container application using Visual Studio 2017 can't get any simpler.</span></span> <span data-ttu-id="0374c-355">Basta pressionar **Ctrl+F5** para executar ou **F5** para depuração, como de costume, configurando o projeto **docker-compose** como o projeto de inicialização.</span><span class="sxs-lookup"><span data-stu-id="0374c-355">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="0374c-356">O Visual Studio trata de toda a configuração necessária, portanto, você pode criar pontos de interrupção, como de costume, e depurar os processos que acabam se tornando independentes em execução em "servidores remotos".</span><span class="sxs-lookup"><span data-stu-id="0374c-356">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", just like that.</span></span>

<span data-ttu-id="0374c-357">Conforme mencionado anteriormente, sempre que você adiciona suporte à solução do Docker a um projeto de uma solução, esse projeto é configurado no arquivo global (nível da solução) docker-compose.yml, o que permite que você execute ou depure toda a solução de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="0374c-357">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="0374c-358">O Visual Studio iniciará um contêiner para cada projeto que tenha suporte habilitado à solução do Docker e executará todas as etapas internas para você (dotnet publish, docker build, etc.).</span><span class="sxs-lookup"><span data-stu-id="0374c-358">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="0374c-359">Se você quiser dar uma olhada na parte chata do trabalho, confira o arquivo:</span><span class="sxs-lookup"><span data-stu-id="0374c-359">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="0374c-360">O ponto importante aqui é que, conforme mostrado na Figura 5-12, há um comando adicional do **Docker**, no Visual Studio 2017, para a ação da tecla F5.</span><span class="sxs-lookup"><span data-stu-id="0374c-360">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="0374c-361">Essa opção permite que você execute ou depure um aplicativo de vários contêineres executando todos os contêineres que estão definidos nos arquivos docker-compose.yml no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="0374c-361">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="0374c-362">A capacidade de depurar soluções de vários contêineres significa que você poderá definir vários pontos de interrupção, cada ponto de interrupção em um projeto (contêiner) diferente e que, durante a depuração no Visual Studio, você vai parar nos pontos de interrupção definidos em diferentes projetos e em execução em diferentes contêineres.</span><span class="sxs-lookup"><span data-stu-id="0374c-362">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Barra de ferramentas de depuração do Visual Studio executando o projeto docker-compose](./media/image16.png)

<span data-ttu-id="0374c-364">**Figura 5-12**.</span><span class="sxs-lookup"><span data-stu-id="0374c-364">**Figure 5-12**.</span></span> <span data-ttu-id="0374c-365">Executando aplicativos de vários contêineres no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0374c-365">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0374c-366">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="0374c-366">Additional resources</span></span>

- <span data-ttu-id="0374c-367">**Implantar um contêiner ASP.NET em um host remoto do Docker** \\</span><span class="sxs-lookup"><span data-stu-id="0374c-367">**Deploy an ASP.NET container to a remote Docker host** \\</span></span>
  [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="0374c-368">Uma observação sobre teste e implantação com orquestradores</span><span class="sxs-lookup"><span data-stu-id="0374c-368">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="0374c-369">Os comandos docker-compose up e docker run (ou executar e depurar os contêineres no Visual Studio) são adequados para contêineres de teste em seu ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0374c-369">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="0374c-370">Mas você não deve usar essa abordagem para implantações de produção, com orquestradores de destino como [Kubernetes](https://kubernetes.io/) ou [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="0374c-370">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="0374c-371">Se você estiver usando o Kubernetes, use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) para organizar os contêineres e [serviços](https://kubernetes.io/docs/concepts/services-networking/service/) para colocá-los em rede.</span><span class="sxs-lookup"><span data-stu-id="0374c-371">If you're using Kubernetes you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="0374c-372">Você também pode usar [implantações](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) para organizar a criação e a modificação de pods.</span><span class="sxs-lookup"><span data-stu-id="0374c-372">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![6 – Testar o aplicativo ou os microsserviços](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="0374c-374">Etapa 6.</span><span class="sxs-lookup"><span data-stu-id="0374c-374">Step 6.</span></span> <span data-ttu-id="0374c-375">Testar seu aplicativo do Docker usando o host local do Docker</span><span class="sxs-lookup"><span data-stu-id="0374c-375">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="0374c-376">Esta etapa varia de acordo com o que seu aplicativo está fazendo.</span><span class="sxs-lookup"><span data-stu-id="0374c-376">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="0374c-377">Em um aplicativo Web .NET Core simples implantado como um único contêiner ou serviço, você pode acessar o serviço abrindo um navegador no host do Docker e navegando até o site, conforme mostrado na Figura 5-13.</span><span class="sxs-lookup"><span data-stu-id="0374c-377">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="0374c-378">(Se a configuração do Dockerfile mapear o contêiner para uma porta no host que seja diferente de 80, inclua a porta do host na URL).</span><span class="sxs-lookup"><span data-stu-id="0374c-378">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Exibição do navegador de uma resposta do ponto de extremidade da API](./media/image18.png)

<span data-ttu-id="0374c-380">**Figura 5-13**.</span><span class="sxs-lookup"><span data-stu-id="0374c-380">**Figure 5-13**.</span></span> <span data-ttu-id="0374c-381">Exemplo de teste do seu aplicativo do Docker localmente usando localhost</span><span class="sxs-lookup"><span data-stu-id="0374c-381">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="0374c-382">Se o localhost não estiver apontando para o IP do host do Docker (por padrão, obrigatório ao usar o Docker CE), use o endereço IP da placa de rede do computador para navegar até o serviço.</span><span class="sxs-lookup"><span data-stu-id="0374c-382">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="0374c-383">Observe que a URL no navegador usa a porta 80 para o exemplo de contêiner específico que está sendo discutido.</span><span class="sxs-lookup"><span data-stu-id="0374c-383">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="0374c-384">No entanto, internamente as solicitações estão sendo redirecionadas para a porta 5000, pois é assim que ele foi implantado com o comando docker run, conforme explicado em uma etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="0374c-384">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="0374c-385">Você também pode testar o aplicativo usando o comando curl no terminal, conforme mostrado na Figura 5-14.</span><span class="sxs-lookup"><span data-stu-id="0374c-385">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="0374c-386">Em uma instalação do Docker no Windows, o IP padrão do host do Docker é sempre 10.0.75.1, além do endereço IP real do computador.</span><span class="sxs-lookup"><span data-stu-id="0374c-386">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Exibição de tela de uma resposta do ponto de extremidade da API com o curl](./media/image19.png)

<span data-ttu-id="0374c-388">**Figura 5-14**.</span><span class="sxs-lookup"><span data-stu-id="0374c-388">**Figure 5-14**.</span></span> <span data-ttu-id="0374c-389">Exemplo de teste do seu aplicativo do Docker localmente usando curl</span><span class="sxs-lookup"><span data-stu-id="0374c-389">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="0374c-390">Testando e depurando contêineres com o Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0374c-390">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="0374c-391">Ao executar e depurar contêineres com o Visual Studio 2017, você depura o aplicativo do .NET de maneira muito parecida como você faria ao executar sem contêineres.</span><span class="sxs-lookup"><span data-stu-id="0374c-391">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="0374c-392">Testando e depurando sem o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0374c-392">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="0374c-393">Se você estiver desenvolvendo por meio da abordagem de editor/CLI, a depuração de contêineres será mais difícil e será melhor fazer a depuração com a geração de rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="0374c-393">If you're developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0374c-394">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="0374c-394">Additional resources</span></span>

- <span data-ttu-id="0374c-395">**Depurando aplicativos em um contêiner do Docker local** \\</span><span class="sxs-lookup"><span data-stu-id="0374c-395">**Debugging apps in a local Docker container** \\</span></span>
  [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- **<span data-ttu-id="0374c-396">Steve Lasker.</span><span class="sxs-lookup"><span data-stu-id="0374c-396">Steve Lasker.</span></span> <span data-ttu-id="0374c-397">Compilar, depurar, implantar aplicativos ASP.NET Core com o Docker.</span><span class="sxs-lookup"><span data-stu-id="0374c-397">Build, Debug, Deploy ASP.NET Core Apps with Docker.</span></span>** <span data-ttu-id="0374c-398">Vídeo.</span><span class="sxs-lookup"><span data-stu-id="0374c-398">Video.</span></span> \
  [https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="0374c-399">Fluxo de trabalho simplificado ao desenvolver contêineres com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0374c-399">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="0374c-400">Efetivamente, o fluxo de trabalho ao usar o Visual Studio é muito mais simples do que ao usar a abordagem de editor/CLI.</span><span class="sxs-lookup"><span data-stu-id="0374c-400">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="0374c-401">A maioria das etapas necessárias pelo Docker, relacionadas ao Dockerfile e aos arquivos docker-compose.yml, são ocultas ou simplificadas pelo Visual Studio, conforme mostrado na Figura 5-15.</span><span class="sxs-lookup"><span data-stu-id="0374c-401">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![Fluxo de trabalho de desenvolvimento de contêiner simplificado com o Visual Studio: 1 – Codificar o aplicativo, 2 – Adicionar o suporte ao Docker aos projetos (uma única vez), 3 – Executar o contêiner ou o aplicativo docker-compose, 4 – Testar o aplicativo ou os microsserviços, 5 – Enviar por push para o repositório e repetir.](./media/image20.png)

<span data-ttu-id="0374c-403">**Figura 5-15**.</span><span class="sxs-lookup"><span data-stu-id="0374c-403">**Figure 5-15**.</span></span> <span data-ttu-id="0374c-404">Fluxo de trabalho simplificado ao desenvolver com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0374c-404">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="0374c-405">Além disso, será necessário executar a etapa 2 (adicionar suporte do Docker aos seus projetos) apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="0374c-405">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="0374c-406">Portanto, o fluxo de trabalho é semelhante às suas tarefas de desenvolvimento regulares, quando utiliza o .NET para qualquer outro desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0374c-406">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="0374c-407">É necessário saber o que está acontecendo nos bastidores (o processo de build da imagem, quais imagens base você está usando, a implantação de contêineres, etc.) e, às vezes, você também precisará editar o Dockerfile ou o arquivo docker-compose.yml para personalizar comportamentos.</span><span class="sxs-lookup"><span data-stu-id="0374c-407">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="0374c-408">Mas a maior parte do trabalho é bastante simplificada com o uso do Visual Studio, o que o torna muito mais produtivo.</span><span class="sxs-lookup"><span data-stu-id="0374c-408">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0374c-409">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="0374c-409">Additional resources</span></span>

- <span data-ttu-id="0374c-410">**Steve Lasker. .NET Docker Development with Visual Studio 2017** \ (Desenvolvimento do Docker no .NET com o Visual Studio 2017)</span><span class="sxs-lookup"><span data-stu-id="0374c-410">**Steve Lasker. .NET Docker Development with Visual Studio 2017** \\</span></span>
  [https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="0374c-411">Usando comandos do PowerShell em um DockerFile para configurar contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="0374c-411">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="0374c-412">Os [contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) permitem converter seus aplicativos existentes do Windows em imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker.</span><span class="sxs-lookup"><span data-stu-id="0374c-412">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="0374c-413">Para usar contêineres do Windows, você executa comandos do PowerShell no Dockerfile, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0374c-413">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="0374c-414">Nesse caso, estamos usando uma imagem base do Windows Server Core (a configuração FROM) e instalando IIS com um comando do PowerShell (a configuração RUN).</span><span class="sxs-lookup"><span data-stu-id="0374c-414">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="0374c-415">Da mesma forma, você também pode usar comandos do PowerShell para configurar outros componentes, como ASP.NET 4.x, .NET 4.6 ou qualquer outro software do Windows.</span><span class="sxs-lookup"><span data-stu-id="0374c-415">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="0374c-416">Por exemplo, o seguinte comando, em um Dockerfile, configura o ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="0374c-416">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="0374c-417">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="0374c-417">Additional resources</span></span>

- **<span data-ttu-id="0374c-418">aspnet-docker/Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="0374c-418">aspnet-docker/Dockerfile.</span></span>** <span data-ttu-id="0374c-419">Comandos do PowerShell de exemplo a serem executados em Dockerfiles para incluir recursos do Windows.\\</span><span class="sxs-lookup"><span data-stu-id="0374c-419">Example PowerShell commands to run from dockerfiles to include Windows features.\\</span></span>
  [https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile](https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile)

>[!div class="step-by-step"]
><span data-ttu-id="0374c-420">[Anterior](index.md)
>[Próximo](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="0374c-420">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
