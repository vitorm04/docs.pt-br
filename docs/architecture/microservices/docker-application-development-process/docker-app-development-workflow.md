---
title: Fluxo de trabalho de desenvolvimento para aplicativos do Docker
description: Entenda os detalhes do fluxo de trabalho para o desenvolvimento de aplicativos baseados no Docker. Comece o passo a passo e obtenha alguns detalhes para otimizar Dockerfiles e concluir com o fluxo de trabalho simplificado disponível ao usar o Visual Studio.
ms.date: 01/30/2020
ms.openlocfilehash: 2f380c840e186c345f9222aa6b0cf1097a74874e
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389193"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="d37f7-104">Fluxo de trabalho de desenvolvimento para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="d37f7-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="d37f7-105">O ciclo de vida de desenvolvimento de aplicativo começa em seu computador, como desenvolvedor, onde você pode codificar o aplicativo usando sua linguagem preferida e testá-lo localmente.</span><span class="sxs-lookup"><span data-stu-id="d37f7-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="d37f7-106">Com esse fluxo de trabalho, não importa a linguagem, a estrutura e a plataforma escolhidas, você está sempre desenvolvendo e testando contêineres do Docker, mas localmente.</span><span class="sxs-lookup"><span data-stu-id="d37f7-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="d37f7-107">Cada contêiner (uma instância de uma imagem do Docker) inclui os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="d37f7-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="d37f7-108">Uma seleção de sistema operacional, por exemplo, uma distribuição do Linux, o Windows Nano Server ou o Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="d37f7-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="d37f7-109">Arquivos adicionados durante o desenvolvimento, por exemplo, os binários e o código-fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d37f7-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="d37f7-110">Informações de configuração, como configurações de ambiente e dependências.</span><span class="sxs-lookup"><span data-stu-id="d37f7-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="d37f7-111">Fluxo de trabalho para o desenvolvimento de aplicativos baseados em contêiner do Docker</span><span class="sxs-lookup"><span data-stu-id="d37f7-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="d37f7-112">Esta seção descreve o fluxo de trabalho de desenvolvimento do *loop interno* de aplicativos baseados em contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="d37f7-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="d37f7-113">O fluxo de trabalho de loop interno significa que não está considerando o fluxo de trabalho de DevOps mais amplo, que pode incluir até a implantação da produção, e apenas se concentra no trabalho de desenvolvimento feito no computador do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="d37f7-113">The inner-loop workflow means it's not considering the broader DevOps workflow, which can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="d37f7-114">As etapas iniciais para configurar o ambiente não são incluídas, pois elas são executadas apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="d37f7-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="d37f7-115">Um aplicativo é composto de seus próprios serviços e de bibliotecas adicionais (dependências).</span><span class="sxs-lookup"><span data-stu-id="d37f7-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="d37f7-116">A figura 5-1 a seguir ilustra as etapas básicas que são normalmente realizadas para criar um aplicativo do Docker.</span><span class="sxs-lookup"><span data-stu-id="d37f7-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Diagrama mostrando os 7 passos necessários para criar um aplicativo contêiner.":::
<span data-ttu-id="d37f7-118">O processo de desenvolvimento dos aplicativos Docker: 1 - Código seu App, 2 - Write Dockerfile/s, 3 - Criar imagens definidas em Dockerfile/s, 4 - (opcional) Compor serviços no arquivo docker-compose.yml, 5 - Executar contêiner ou docker-compose app, 6 - Teste seu aplicativo ou microsserviços, 7 - Empurre para repo e repita.</span><span class="sxs-lookup"><span data-stu-id="d37f7-118">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="d37f7-119">**Figura 5-1.**</span><span class="sxs-lookup"><span data-stu-id="d37f7-119">**Figure 5-1.**</span></span> <span data-ttu-id="d37f7-120">Fluxo de trabalho passo a passo para o desenvolvimento de aplicativos do Docker em contêineres</span><span class="sxs-lookup"><span data-stu-id="d37f7-120">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="d37f7-121">Nesta seção, todo esse processo é detalhado e cada etapa principal é explicada com base em um ambiente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d37f7-121">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="d37f7-122">Ao usar uma abordagem de desenvolvimento de editor/CLI (por exemplo, o Visual Studio Code com a CLI do Docker no macOS ou no Windows), você precisará conhecer cada etapa e, na maioria das vezes, com mais detalhes do que ao usar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d37f7-122">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="d37f7-123">Para obter mais informações sobre como trabalhar em um ambiente de CLI, confira o livro eletrônico [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/) (Ciclo de vida do aplicativo do Docker em contêineres com ferramentas e plataformas da Microsoft).</span><span class="sxs-lookup"><span data-stu-id="d37f7-123">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="d37f7-124">Quando você está usando o Visual Studio 2019, muitas dessas etapas são tratadas para você, o que melhora drasticamente sua produtividade.</span><span class="sxs-lookup"><span data-stu-id="d37f7-124">When you're using Visual Studio 2019, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="d37f7-125">Isso é especialmente verdade quando você está usando o Visual Studio 2019 e mirando aplicativos de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="d37f7-125">This is especially true when you're using Visual Studio 2019 and targeting multi-container applications.</span></span> <span data-ttu-id="d37f7-126">Por exemplo, com apenas um clique `Dockerfile` no `docker-compose.yml` mouse, o Visual Studio adiciona o arquivo e o arquivo aos seus projetos com a configuração para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d37f7-126">For instance, with just one mouse click, Visual Studio adds the `Dockerfile` and `docker-compose.yml` file to your projects with the configuration for your application.</span></span> <span data-ttu-id="d37f7-127">Ao executar o aplicativo no Visual Studio, ele cria a imagem do Docker e executa o aplicativo de vários contêineres diretamente no Docker; e até mesmo permite que você depure vários contêineres de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="d37f7-127">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="d37f7-128">Esses recursos vão acelerar sua velocidade de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d37f7-128">These features will boost your development speed.</span></span>

<span data-ttu-id="d37f7-129">No entanto, apenas porque o Visual Studio automatiza essas etapas não significa que você não precisa saber o que está acontecendo nos bastidores com o Docker.</span><span class="sxs-lookup"><span data-stu-id="d37f7-129">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="d37f7-130">Portanto, as diretrizes a seguir detalham cada etapa.</span><span class="sxs-lookup"><span data-stu-id="d37f7-130">Therefore, the following guidance details every step.</span></span>

![Imagem para o Passo 1.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="d37f7-132">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="d37f7-132">Step 1.</span></span> <span data-ttu-id="d37f7-133">Iniciar a codificação e a criação do aplicativo inicial ou da linha de base do serviço</span><span class="sxs-lookup"><span data-stu-id="d37f7-133">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="d37f7-134">O desenvolvimento de um aplicativo do Docker é semelhante à forma como você desenvolve um aplicativo sem Docker.</span><span class="sxs-lookup"><span data-stu-id="d37f7-134">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="d37f7-135">A diferença é que, durante o desenvolvimento para o Docker, você está implantando e testando o aplicativo ou os serviços executando-os em contêineres do Docker em seu ambiente local (seja em uma VM do Linux configurada pelo Docker ou diretamente no Windows quando está usando contêineres do Windows).</span><span class="sxs-lookup"><span data-stu-id="d37f7-135">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="d37f7-136">Configurar seu ambiente local com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d37f7-136">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="d37f7-137">Para começar, instale o [Docker CE (Community Edition)](https://docs.docker.com/docker-for-windows/) para Windows, conforme explicado nas instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="d37f7-137">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="d37f7-138">Introdução ao Docker CE for Windows</span><span class="sxs-lookup"><span data-stu-id="d37f7-138">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="d37f7-139">Além disso, você precisa do Visual Studio 2019 versão 16.4 ou posterior, com a carga de trabalho **de desenvolvimento multiplataforma .NET Core** instalada, como mostrado na Figura 5-2.</span><span class="sxs-lookup"><span data-stu-id="d37f7-139">In addition, you need Visual Studio 2019 version 16.4 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![Captura de tela da seleção de desenvolvimento multiplataforma .NET Core.](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

<span data-ttu-id="d37f7-141">**Figura 5-2**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-141">**Figure 5-2**.</span></span> <span data-ttu-id="d37f7-142">Selecionando a carga de trabalho **de desenvolvimento multiplataforma .NET Core** durante a configuração do Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="d37f7-142">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2019 setup</span></span>

<span data-ttu-id="d37f7-143">Você pode iniciar a codificação do aplicativo no .NET simples (normalmente no .NET Core, se estiver planejando usar contêineres) mesmo antes de habilitar o Docker no aplicativo e antes da implantação e dos testes no Docker.</span><span class="sxs-lookup"><span data-stu-id="d37f7-143">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="d37f7-144">No entanto, é recomendável que você comece a trabalhar no Docker assim que possível, porque que esse será o ambiente real e os problemas poderão ser descobertos o mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="d37f7-144">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="d37f7-145">Isso é recomendável porque o Visual Studio facilita tanto o trabalho com o Docker parecendo, até mesmo, transparente — o melhor exemplo ao depurar aplicativos de vários contêineres do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d37f7-145">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d37f7-146">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="d37f7-146">Additional resources</span></span>

- <span data-ttu-id="d37f7-147">**Comece com o Docker CE para Windows** </span><span class="sxs-lookup"><span data-stu-id="d37f7-147">**Get started with Docker CE for Windows** </span></span>\
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="d37f7-148">**Visual Studio 2019** </span><span class="sxs-lookup"><span data-stu-id="d37f7-148">**Visual Studio 2019** </span></span>\
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![Imagem para o passo 2.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="d37f7-150">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="d37f7-150">Step 2.</span></span> <span data-ttu-id="d37f7-151">Criar um Dockerfile relacionado a uma imagem base existente do .NET</span><span class="sxs-lookup"><span data-stu-id="d37f7-151">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="d37f7-152">Você precisa de um Dockerfile para cada imagem personalizada que você deseja criar. Você também precisará de um Dockerfile para cada contêiner a ser implantado automaticamente, por meio do Visual Studio, ou implantado manualmente, usando a CLI do Docker (comandos docker run e docker-compose).</span><span class="sxs-lookup"><span data-stu-id="d37f7-152">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="d37f7-153">Se seu aplicativo contém um único serviço personalizado, é necessário um único Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d37f7-153">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="d37f7-154">Se seu aplicativo contém vários serviços (como em uma arquitetura de microsserviços), é necessário um Dockerfile para cada serviço.</span><span class="sxs-lookup"><span data-stu-id="d37f7-154">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="d37f7-155">O Dockerfile é colocado na pasta raiz do seu aplicativo ou serviço.</span><span class="sxs-lookup"><span data-stu-id="d37f7-155">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="d37f7-156">Ele contém os comandos que indicam ao Docker como configurar e executar seu aplicativo ou serviço em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="d37f7-156">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="d37f7-157">Você pode criar manualmente um Dockerfile por meio de código e adicioná-lo ao seu projeto junto com as dependências do .NET.</span><span class="sxs-lookup"><span data-stu-id="d37f7-157">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="d37f7-158">Com o Visual Studio e suas ferramentas para Docker, esta tarefa requer apenas alguns cliques do mouse.</span><span class="sxs-lookup"><span data-stu-id="d37f7-158">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="d37f7-159">Quando você cria um novo projeto no Visual Studio 2019, há uma opção chamada **Enable Docker Support**, como mostrado na Figura 5-3.</span><span class="sxs-lookup"><span data-stu-id="d37f7-159">When you create a new project in Visual Studio 2019, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![Captura de tela mostrando a caixa de seleção De suporte do Docker.](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

<span data-ttu-id="d37f7-161">**Figura 5-3**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-161">**Figure 5-3**.</span></span> <span data-ttu-id="d37f7-162">Habilitando o suporte ao Docker ao criar um novo projeto ASP.NET Core no Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="d37f7-162">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2019</span></span>

<span data-ttu-id="d37f7-163">Você também pode habilitar o suporte ao Docker em um projeto de aplicativo web ASP.NET Core existente clicando com o botão direito do mouse no projeto no **Solution Explorer** e selecionando **Adicionar** > **suporte ao Docker...**, como mostrado na Figura 5-4.</span><span class="sxs-lookup"><span data-stu-id="d37f7-163">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support...**, as shown in Figure 5-4.</span></span>

![Captura de tela mostrando a opção Suporte ao Docker no menu Adicionar.](./media/docker-app-development-workflow/add-docker-support-option.png)

<span data-ttu-id="d37f7-165">**Figura 5-4**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-165">**Figure 5-4**.</span></span> <span data-ttu-id="d37f7-166">Habilitando o suporte ao Docker em um projeto existente do Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="d37f7-166">Enabling Docker support in an existing Visual Studio 2019 project</span></span>

<span data-ttu-id="d37f7-167">Essa ação adiciona um *Dockerfile* ao projeto com a configuração necessária e só está disponível em projetos ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d37f7-167">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="d37f7-168">Da mesma forma, o Visual `docker-compose.yml` Studio também pode adicionar um arquivo para toda a solução com a opção **Adicionar > suporte ao Orquestrador de Contêineres...**. Na etapa 4, vamos explorar essa opção com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="d37f7-168">In a similar fashion, Visual Studio can also add a `docker-compose.yml` file for the whole solution with the option **Add > Container Orchestrator Support...**. In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="d37f7-169">Usando uma imagem do Docker do .NET oficial existente</span><span class="sxs-lookup"><span data-stu-id="d37f7-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="d37f7-170">Geralmente, você cria uma imagem personalizada para o contêiner usando uma imagem base que você pode obter de um repositório oficial, como o Registro do [Docker Hub](https://hub.docker.com/).</span><span class="sxs-lookup"><span data-stu-id="d37f7-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="d37f7-171">É exatamente isso o que acontece nos bastidores quando você habilita o suporte do Docker no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d37f7-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="d37f7-172">O Dockerfile usará uma imagem `dotnet/core/aspnet` existente.</span><span class="sxs-lookup"><span data-stu-id="d37f7-172">Your Dockerfile will use an existing `dotnet/core/aspnet` image.</span></span>

<span data-ttu-id="d37f7-173">Anteriormente, explicamos quais imagens do Docker e quais repositórios você poderia usar, dependendo da estrutura e do sistema operacional que você escolheu.</span><span class="sxs-lookup"><span data-stu-id="d37f7-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="d37f7-174">Por exemplo, se você quiser usar o ASP.NET Core (Linux ou Windows), a imagem a ser usada será `mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span><span class="sxs-lookup"><span data-stu-id="d37f7-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="d37f7-175">Assim, basta especificar qual imagem base do Docker será usada para o seu contêiner.</span><span class="sxs-lookup"><span data-stu-id="d37f7-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="d37f7-176">Você pode fazer isso adicionando `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` ao seu Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d37f7-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` to your Dockerfile.</span></span> <span data-ttu-id="d37f7-177">Isso será realizado automaticamente pelo Visual Studio, mas se você precisar atualizar a versão, será esse valor que você atualizará.</span><span class="sxs-lookup"><span data-stu-id="d37f7-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="d37f7-178">O uso de um repositório de imagem oficial do .NET do Hub do Docker com um número de versão garante que os mesmos recursos de linguagem estejam disponíveis em todos os computadores (incluindo desenvolvimento, teste e produção).</span><span class="sxs-lookup"><span data-stu-id="d37f7-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="d37f7-179">O exemplo a seguir mostra um Dockerfile de exemplo para um contêiner do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d37f7-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="d37f7-180">Neste caso, a imagem é baseada na versão 3.1 da imagem oficial do ASP.NET Core Docker (multi-arch para Linux e Windows).</span><span class="sxs-lookup"><span data-stu-id="d37f7-180">In this case, the image is based on version 3.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="d37f7-181">Essa é a configuração `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span><span class="sxs-lookup"><span data-stu-id="d37f7-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="d37f7-182">(Para obter mais informações sobre essa imagem base, consulte a página [.NET Core Docker Image.)](https://hub.docker.com/_/microsoft-dotnet-core/) No arquivo Docker, você também precisa instruir o Docker a ouvir a porta TCP que você usará em tempo de execução (neste caso, a porta 80, conforme configurado com a configuração EXPOSE).</span><span class="sxs-lookup"><span data-stu-id="d37f7-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="d37f7-183">Você pode especificar mais definições de configurações no Dockerfile, dependendo da linguagem e da estrutura usadas.</span><span class="sxs-lookup"><span data-stu-id="d37f7-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="d37f7-184">Por exemplo, a linha ENTRYPOINT com `["dotnet", "MySingleContainerWebApp.dll"]` diz ao Docker para executar um aplicativo do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d37f7-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="d37f7-185">Se você estiver usando o SDK e a CLI do .NET Core (CLI do dotnet) para compilar e executar o aplicativo do .NET, essa configuração será diferente.</span><span class="sxs-lookup"><span data-stu-id="d37f7-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="d37f7-186">O essencial é que a linha ENTRYPOINT e outras configurações serão diferentes dependendo da linguagem e da plataforma que você escolher para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d37f7-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d37f7-187">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="d37f7-187">Additional resources</span></span>

- <span data-ttu-id="d37f7-188">**Construindo imagens docker para aplicativos .NET Core** </span><span class="sxs-lookup"><span data-stu-id="d37f7-188">**Building Docker Images for .NET Core Applications** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- <span data-ttu-id="d37f7-189">**Criar sua própria imagem**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-189">**Build your own image**.</span></span> <span data-ttu-id="d37f7-190">Na documentação oficial do Docker.</span><span class="sxs-lookup"><span data-stu-id="d37f7-190">In the official Docker documentation.</span></span>\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="d37f7-191">**Manter-se atualizado com imagens de contêiner .NET** </span><span class="sxs-lookup"><span data-stu-id="d37f7-191">**Staying up-to-date with .NET Container Images** </span></span>\
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="d37f7-192">**Usando .NET e Docker Together - DockerCon 2018 Update** </span><span class="sxs-lookup"><span data-stu-id="d37f7-192">**Using .NET and Docker Together - DockerCon 2018 Update** </span></span>\
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="d37f7-193">Usando repositórios de imagens para várias arquiteturas</span><span class="sxs-lookup"><span data-stu-id="d37f7-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="d37f7-194">Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="d37f7-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="d37f7-195">Esse recurso permite que fornecedores, como a Microsoft (criadores de imagem base), criem um único repositório para abranger várias plataformas (ou seja, Linux e Windows).</span><span class="sxs-lookup"><span data-stu-id="d37f7-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="d37f7-196">Por exemplo, o repositório [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/), disponível no registro do Hub do Docker, é compatível com Linux e Windows Nano Server usando o mesmo nome de repositório.</span><span class="sxs-lookup"><span data-stu-id="d37f7-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="d37f7-197">Ao especificar uma marcação, você direciona a uma plataforma que é explícita, como nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="d37f7-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim` \
  <span data-ttu-id="d37f7-198">Alvos: .NET Core 3.1 somente em execução no Linux</span><span class="sxs-lookup"><span data-stu-id="d37f7-198">Targets: .NET Core 3.1 runtime-only on Linux</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1909` \
  <span data-ttu-id="d37f7-199">Alvos: .NET Core 3.1 somente em execução no Windows Nano Server</span><span class="sxs-lookup"><span data-stu-id="d37f7-199">Targets: .NET Core 3.1 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="d37f7-200">Mas, se você especificar o mesmo nome de imagem, mesmo com a mesma marca, as imagens para várias arquiteturas (como a imagem `aspnet`) usarão a versão do Linux ou do Windows, dependendo do sistema operacional do host do Docker em que você esteja implantando, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d37f7-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnet` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1` \
  <span data-ttu-id="d37f7-201">Multi-arch: .NET Core 3.1 somente em tempo de execução no Linux ou Windows Nano Server, dependendo do sistema operacional host Docker</span><span class="sxs-lookup"><span data-stu-id="d37f7-201">Multi-arch: .NET Core 3.1 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="d37f7-202">Dessa forma, ao efetuar pull de uma imagem de um host do Windows, será efetuado o pull da variante do Windows e, ao efetuar pull do mesmo nome de imagem de um host do Linux, será efetuado pull da variante do Linux.</span><span class="sxs-lookup"><span data-stu-id="d37f7-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="d37f7-203">Builds de vários estágios no Dockerfile</span><span class="sxs-lookup"><span data-stu-id="d37f7-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="d37f7-204">O Dockerfile é semelhante a um script em lotes.</span><span class="sxs-lookup"><span data-stu-id="d37f7-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="d37f7-205">Como o que você faria se tivesse que configurar o computador da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d37f7-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="d37f7-206">Ele começa com uma imagem base que define o contexto inicial, como o sistema de arquivos de inicialização, que se baseia no sistema operacional do host.</span><span class="sxs-lookup"><span data-stu-id="d37f7-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="d37f7-207">Não é um sistema operacional, mas você pode pensar nele como "o" sistema operacional dentro do recipiente.</span><span class="sxs-lookup"><span data-stu-id="d37f7-207">It's not an OS, but you can think of it like "the" OS inside the container.</span></span>

<span data-ttu-id="d37f7-208">A execução de cada linha de comando cria uma camada no sistema de arquivos com as alterações em relação à anterior, para que, quando combinadas, produzam o sistema de arquivos resultante.</span><span class="sxs-lookup"><span data-stu-id="d37f7-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="d37f7-209">Como cada nova camada é baseada na anterior e o tamanho da imagem resultante aumenta com cada comando, as imagens poderão ficar muito grandes se precisarem incluir, por exemplo, o SDK necessário para criar e publicar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d37f7-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="d37f7-210">É nesse ponto que os builds de vários estágios (do Docker 17.05 e superior) entram em cena para fazer a mágica.</span><span class="sxs-lookup"><span data-stu-id="d37f7-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="d37f7-211">A ideia central é que você pode separar o processo de execução do Dockerfile em estágios, em que um estágio é uma imagem inicial seguida por um ou mais comandos, e o último estágio determina o tamanho da imagem final.</span><span class="sxs-lookup"><span data-stu-id="d37f7-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="d37f7-212">Resumindo, os builds de vários estágios permitem dividir a criação em "fases" diferentes e, em seguida, montar a imagem final usando somente os diretórios relevantes dos estágios intermediários.</span><span class="sxs-lookup"><span data-stu-id="d37f7-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="d37f7-213">A estratégia geral para usar esse recurso é:</span><span class="sxs-lookup"><span data-stu-id="d37f7-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="d37f7-214">usar uma imagem base do SDK (não importa quão grande), com todos os componentes necessários para criar e publicar o aplicativo em uma pasta e, em seguida,</span><span class="sxs-lookup"><span data-stu-id="d37f7-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="d37f7-215">usar uma imagem base pequena, somente em runtime e copiar a pasta de publicação do estágio anterior para produzir uma pequena imagem final.</span><span class="sxs-lookup"><span data-stu-id="d37f7-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="d37f7-216">Provavelmente a melhor maneira de entender os vários estágios é percorrer um Dockerfile detalhadamente, linha por linha, então, vamos começar com o Dockerfile inicial criado pelo Visual Studio ao adicionar o suporte ao Docker a um projeto e entraremos em algumas otimizações mais tarde.</span><span class="sxs-lookup"><span data-stu-id="d37f7-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="d37f7-217">O Dockerfile inicial pode ser como este:</span><span class="sxs-lookup"><span data-stu-id="d37f7-217">The initial Dockerfile might look something like this:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
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
20  RUN dotnet build Catalog.API.csproj -c Release -o /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -o /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app .
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

<span data-ttu-id="d37f7-218">E estes são os detalhes, linha por linha:</span><span class="sxs-lookup"><span data-stu-id="d37f7-218">And these are the details, line by line:</span></span>

- <span data-ttu-id="d37f7-219">**linha #1:** Inicie um estágio com uma imagem base "pequena" somente em tempo de execução, **chame-a de base** para referência.</span><span class="sxs-lookup"><span data-stu-id="d37f7-219">**Line #1:** Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>

- <span data-ttu-id="d37f7-220">**linha #2:** Crie o **diretório /app** na imagem.</span><span class="sxs-lookup"><span data-stu-id="d37f7-220">**Line #2:** Create the **/app** directory in the image.</span></span>

- <span data-ttu-id="d37f7-221">**Linha #3:** Expor a porta **80**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-221">**Line #3:** Expose port **80**.</span></span>

- <span data-ttu-id="d37f7-222">**linha #5:** Inicie uma nova etapa com a imagem "grande" para construção/publicação.</span><span class="sxs-lookup"><span data-stu-id="d37f7-222">**Line #5:** Begin a new stage with the "large" image for building/publishing.</span></span> <span data-ttu-id="d37f7-223">Chame de **construção** para referência.</span><span class="sxs-lookup"><span data-stu-id="d37f7-223">Call it **build** for reference.</span></span>

- <span data-ttu-id="d37f7-224">**Linha #6:** Criar diretório **/src** na imagem.</span><span class="sxs-lookup"><span data-stu-id="d37f7-224">**Line #6:** Create directory **/src** in the image.</span></span>

- <span data-ttu-id="d37f7-225">**Linha #7:** Até a linha 16, copie arquivos do projeto **.csproj** para poder restaurar pacotes mais tarde.</span><span class="sxs-lookup"><span data-stu-id="d37f7-225">**Line #7:** Up to line 16, copy referenced **.csproj** project files to be able to restore packages later.</span></span>

- <span data-ttu-id="d37f7-226">**linha #17:** Restaurar pacotes para o projeto **Catalog.API** e os projetos referenciados.</span><span class="sxs-lookup"><span data-stu-id="d37f7-226">**Line #17:** Restore packages for the **Catalog.API** project and the referenced projects.</span></span>

- <span data-ttu-id="d37f7-227">**Linha #18:** Copie **todas as árvore suinológicas para a solução** (exceto os arquivos/diretórios incluídos no arquivo **.dockerignore)** para o diretório **/src** na imagem.</span><span class="sxs-lookup"><span data-stu-id="d37f7-227">**Line #18:** Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) to the **/src** directory in the image.</span></span>

- <span data-ttu-id="d37f7-228">**Linha #19:** Alterar a pasta atual para o projeto **Catalog.API.**</span><span class="sxs-lookup"><span data-stu-id="d37f7-228">**Line #19:** Change the current folder to the **Catalog.API** project.</span></span>

- <span data-ttu-id="d37f7-229">**linha #20:** Construa o projeto (e outras dependências do projeto) e faça a saída para o diretório **/app** na imagem.</span><span class="sxs-lookup"><span data-stu-id="d37f7-229">**Line #20:** Build the project (and other project dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="d37f7-230">**Linha #22:** Comece uma nova etapa continuando a partir da construção.</span><span class="sxs-lookup"><span data-stu-id="d37f7-230">**Line #22:** Begin a new stage continuing from the build.</span></span> <span data-ttu-id="d37f7-231">**Chame-o publicar** para referência.</span><span class="sxs-lookup"><span data-stu-id="d37f7-231">Call it **publish** for reference.</span></span>

- <span data-ttu-id="d37f7-232">**Linha #23:** Publique o projeto (e dependências) e a saída para o diretório **/app** na imagem.</span><span class="sxs-lookup"><span data-stu-id="d37f7-232">**Line #23:** Publish the project (and dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="d37f7-233">**Linha #25:** Comece uma nova etapa continuando da **base** e chame de **final**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-233">**Line #25:** Begin a new stage continuing from **base** and call it **final**.</span></span>

- <span data-ttu-id="d37f7-234">**Linha #26:** Alterar o diretório atual para **/app**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-234">**Line #26:** Change the current directory to **/app**.</span></span>

- <span data-ttu-id="d37f7-235">**Linha #27:** Copie o **diretório /app** da **publicação** do estágio para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d37f7-235">**Line #27:** Copy the **/app** directory from stage **publish** to the current directory.</span></span>

- <span data-ttu-id="d37f7-236">**Linha #28:** Defina o comando a ser executado quando o contêiner for iniciado.</span><span class="sxs-lookup"><span data-stu-id="d37f7-236">**Line #28:** Define the command to run when the container is started.</span></span>

<span data-ttu-id="d37f7-237">Agora vamos explorar algumas otimizações para melhorar o desempenho de todo o processo que, no caso do eShopOnContainers, significa cerca de 22 minutos ou mais para criar a solução completa em contêineres do Linux.</span><span class="sxs-lookup"><span data-stu-id="d37f7-237">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="d37f7-238">Você aproveitará o recurso de cache de camada do Docker, que é bastante simples: se a imagem base e os comandos forem iguais a outros já executados, ele poderá usar apenas a camada resultante sem precisar executar os comandos, economizando tempo.</span><span class="sxs-lookup"><span data-stu-id="d37f7-238">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="d37f7-239">Portanto, vamos nos concentrar no estágio **build**. As linhas 5 a 6 são basicamente as mesmas, mas as linhas 7 a 17 são diferentes para cada serviço do eShopOnContainers, portanto precisam ser executadas todas as vezes, no entanto, se você tiver alterado as linhas 7 a 16 para:</span><span class="sxs-lookup"><span data-stu-id="d37f7-239">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```Dockerfile
COPY . .
```

<span data-ttu-id="d37f7-240">Ele seria igual para cada serviço, ele poderia copiar toda a solução e criar uma camada maior, mas:</span><span class="sxs-lookup"><span data-stu-id="d37f7-240">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1. <span data-ttu-id="d37f7-241">o processo de cópia seria executado somente na primeira vez (e durante a recriação, se algum arquivo fosse alterado) e usaria o cache para todos os outros serviços e</span><span class="sxs-lookup"><span data-stu-id="d37f7-241">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2. <span data-ttu-id="d37f7-242">como a imagem maior ocorre em um estágio intermediário, ela não afeta o tamanho da imagem final.</span><span class="sxs-lookup"><span data-stu-id="d37f7-242">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="d37f7-243">A próxima otimização significativa envolve o comando `restore` executado na linha 17, que também é diferente para cada serviço do eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="d37f7-243">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="d37f7-244">Se você alterar essa linha para apenas:</span><span class="sxs-lookup"><span data-stu-id="d37f7-244">If you change that line to just:</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="d37f7-245">Isso restauraria os pacotes de toda a solução, mas, novamente, isso seria feito apenas uma vez, em vez de 15 vezes com a estratégia atual.</span><span class="sxs-lookup"><span data-stu-id="d37f7-245">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="d37f7-246">No entanto, `dotnet restore` só será executado se houver um único arquivo de projeto ou de solução na pasta, portanto, isso é um pouco mais complicado e a maneira de resolvê-lo, sem entrar em muitos detalhes, é esta:</span><span class="sxs-lookup"><span data-stu-id="d37f7-246">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="d37f7-247">adicione as seguintes linhas ao **.dockerignore**:</span><span class="sxs-lookup"><span data-stu-id="d37f7-247">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="d37f7-248">`*.sln`, para ignorar todos os arquivos de solução na árvore da pasta principal</span><span class="sxs-lookup"><span data-stu-id="d37f7-248">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="d37f7-249">`!eShopOnContainers-ServicesAndWebApps.sln`, para incluir apenas esse arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="d37f7-249">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="d37f7-250">inclua o argumento `/ignoreprojectextensions:.dcproj` em `dotnet restore`, para que ele também ignore o projeto docker-compose e só restaure os pacotes da solução eShopOnContainers-ServicesAndWebApps.</span><span class="sxs-lookup"><span data-stu-id="d37f7-250">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="d37f7-251">Para a otimização final, acontece que a linha 20 é redundante e a linha 23 também compila o aplicativo e vem, naturalmente, logo após a linha 20, o que gera outro comando demorado.</span><span class="sxs-lookup"><span data-stu-id="d37f7-251">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="d37f7-252">O arquivo resultante é:</span><span class="sxs-lookup"><span data-stu-id="d37f7-252">The resulting file is then:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -o /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="d37f7-253">Criação da imagem base do zero</span><span class="sxs-lookup"><span data-stu-id="d37f7-253">Creating your base image from scratch</span></span>

<span data-ttu-id="d37f7-254">Você pode criar sua própria imagem base do Docker do zero.</span><span class="sxs-lookup"><span data-stu-id="d37f7-254">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="d37f7-255">Esse cenário não é recomendável para um iniciante no Docker, mas se você desejar definir os bits específicos da sua própria imagem base, isso será possível.</span><span class="sxs-lookup"><span data-stu-id="d37f7-255">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d37f7-256">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="d37f7-256">Additional resources</span></span>

- <span data-ttu-id="d37f7-257">**Imagens multi-arco .NET Core**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-257">**Multi-arch .NET Core images**.</span></span>\
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="d37f7-258">**Criar uma imagem base**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-258">**Create a base image**.</span></span> <span data-ttu-id="d37f7-259">Documentação oficial do Docker.</span><span class="sxs-lookup"><span data-stu-id="d37f7-259">Official Docker documentation.</span></span>\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Imagem para o passo 3.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="d37f7-261">Etapa 3.</span><span class="sxs-lookup"><span data-stu-id="d37f7-261">Step 3.</span></span> <span data-ttu-id="d37f7-262">Criar imagens personalizadas do Docker e inserir seu aplicativo ou serviço nelas</span><span class="sxs-lookup"><span data-stu-id="d37f7-262">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="d37f7-263">Para cada serviço do seu aplicativo, você precisa criar uma imagem relacionada.</span><span class="sxs-lookup"><span data-stu-id="d37f7-263">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="d37f7-264">Se seu aplicativo é composto de um único serviço ou aplicativo Web, você precisa apenas de uma única imagem.</span><span class="sxs-lookup"><span data-stu-id="d37f7-264">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="d37f7-265">Observe que as imagens do Docker são criadas automaticamente para você no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d37f7-265">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="d37f7-266">As etapas a seguir são necessárias apenas para o fluxo de trabalho de editor/CLI e são explicadas com a finalidade de esclarecer o que acontece nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="d37f7-266">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="d37f7-267">Você, como desenvolvedor, precisa desenvolver e testar localmente até enviar um recurso concluído por push ou mudar para o sistema de controle do código-fonte (por exemplo, para o GitHub).</span><span class="sxs-lookup"><span data-stu-id="d37f7-267">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="d37f7-268">Isso significa que você precisa criar as imagens do Docker e implantar contêineres em um host do Docker local (VM do Windows ou Linux) e executar, testar e depurar nesses contêineres locais.</span><span class="sxs-lookup"><span data-stu-id="d37f7-268">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="d37f7-269">Para criar uma imagem personalizada no seu ambiente local, usando a CLI do Docker e o Dockerfile, você pode usar o comando docker build, como na Figura 5-5.</span><span class="sxs-lookup"><span data-stu-id="d37f7-269">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Captura de tela mostrando a saída do console do comando de compilação docker.](./media/docker-app-development-workflow/run-docker-build-command.png)

<span data-ttu-id="d37f7-271">**Figura 5-5**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-271">**Figure 5-5**.</span></span> <span data-ttu-id="d37f7-272">Criando uma imagem personalizada do Docker</span><span class="sxs-lookup"><span data-stu-id="d37f7-272">Creating a custom Docker image</span></span>

<span data-ttu-id="d37f7-273">Opcionalmente, em vez de executar diretamente o comando docker build na pasta do projeto, você pode, primeiro, gerar uma pasta implantável com as bibliotecas e os binários do .NET necessários, executando `dotnet publish` e, em seguida, usar o comando `docker build`.</span><span class="sxs-lookup"><span data-stu-id="d37f7-273">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="d37f7-274">Isso criará uma imagem do Docker com o nome `cesardl/netcore-webapi-microservice-docker:first`.</span><span class="sxs-lookup"><span data-stu-id="d37f7-274">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="d37f7-275">Nesse caso, :first é uma marcação que representa uma versão específica.</span><span class="sxs-lookup"><span data-stu-id="d37f7-275">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="d37f7-276">Você poderá repetir esta etapa para cada imagem personalizada que tiver que criar para o seu aplicativo composto do Docker.</span><span class="sxs-lookup"><span data-stu-id="d37f7-276">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="d37f7-277">Quando um aplicativo é composto de vários contêineres (ou seja, ele é um aplicativo multicontêineres), você também pode usar o comando `docker-compose up --build` para compilar todas as imagens relacionadas com um único comando usando os metadados expostos nos arquivos docker-compose.yml relacionados.</span><span class="sxs-lookup"><span data-stu-id="d37f7-277">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="d37f7-278">Você pode encontrar as imagens existentes no seu repositório local usando o comando docker images, conforme mostrado na Figura 5-6.</span><span class="sxs-lookup"><span data-stu-id="d37f7-278">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Saída do console do comando docker images, mostrando as imagens existentes.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="d37f7-280">**Figura 5-6.**</span><span class="sxs-lookup"><span data-stu-id="d37f7-280">**Figure 5-6.**</span></span> <span data-ttu-id="d37f7-281">Exibição de imagens existentes usando o comando docker images</span><span class="sxs-lookup"><span data-stu-id="d37f7-281">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="d37f7-282">Criação de imagens do Docker com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d37f7-282">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="d37f7-283">Ao usar o Visual Studio para criar um projeto com suporte ao Docker, você não cria explicitamente uma imagem.</span><span class="sxs-lookup"><span data-stu-id="d37f7-283">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="d37f7-284">Em vez disso, a imagem é criada quando você pressiona **F5** (ou **Ctrl+F5**) para executar o aplicativo ou o serviço convertido para Docker.</span><span class="sxs-lookup"><span data-stu-id="d37f7-284">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="d37f7-285">Esta etapa é automática no Visual Studio e você não verá ela ocorrer, mas é importante que você saiba o que está acontecendo nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="d37f7-285">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![Imagem para o passo 4 opcional.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="d37f7-287">Etapa 4.</span><span class="sxs-lookup"><span data-stu-id="d37f7-287">Step 4.</span></span> <span data-ttu-id="d37f7-288">Definir os serviços no docker-compose.yml ao compilar um aplicativo de vários contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="d37f7-288">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="d37f7-289">O arquivo [docker-compose.yml](https://docs.docker.com/compose/compose-file/) permite que você defina um conjunto de serviços relacionados para que sejam implantados como um aplicativo composto com comandos de implantação.</span><span class="sxs-lookup"><span data-stu-id="d37f7-289">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="d37f7-290">Ele também configura as relações de dependência e a configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d37f7-290">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="d37f7-291">Para usar um arquivo docker-compose.yml, você precisa criar o arquivo na pasta principal ou raiz da sua solução, com conteúdo semelhante ao do exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d37f7-291">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
    ports:
      - "80:80"
    depends_on:
      - catalog-api
      - ordering-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sqldata

  sqldata:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="d37f7-292">Esse arquivo docker-compose.yml é uma versão simplificada e mesclada.</span><span class="sxs-lookup"><span data-stu-id="d37f7-292">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="d37f7-293">Ele contém dados de configuração estáticos para cada contêiner (como o nome da imagem personalizada), o que é sempre necessário, além das informações de configuração que poderão depender do ambiente de implantação, como a cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="d37f7-293">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="d37f7-294">Nas próximas seções, você aprenderá como dividir a configuração do docker-compose.yml em vários arquivos docker-compose e substituir valores dependendo do ambiente e do tipo de execução (depuração ou lançamento).</span><span class="sxs-lookup"><span data-stu-id="d37f7-294">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="d37f7-295">O arquivo docker-compose.yml de exemplo define quatro serviços: o serviço `webmvc` (um aplicativo Web), dois microsserviços (`ordering-api` e `basket-api`) e um contêiner de fonte de dados, `sqldata`, com base no SQL Server para Linux, em execução como um contêiner.</span><span class="sxs-lookup"><span data-stu-id="d37f7-295">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering-api` and `basket-api`), and one data source container, `sqldata`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="d37f7-296">Cada serviço será implantado como um contêiner, portanto, uma imagem do Docker é necessária para cada um.</span><span class="sxs-lookup"><span data-stu-id="d37f7-296">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="d37f7-297">O arquivo docker-compose.yml não apenas especifica quais contêineres estão sendo usados, mas também como eles são configurados individualmente.</span><span class="sxs-lookup"><span data-stu-id="d37f7-297">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="d37f7-298">Por exemplo, a definição de contêiner `webmvc` no arquivo .yml:</span><span class="sxs-lookup"><span data-stu-id="d37f7-298">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="d37f7-299">usa uma imagem `eshop/web:latest` predefinida.</span><span class="sxs-lookup"><span data-stu-id="d37f7-299">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="d37f7-300">Entretanto, você também poderia definir a imagem para ser compilada como parte da execução do docker-compose, com uma configuração adicional baseada em uma seção build: no arquivo docker-compose.</span><span class="sxs-lookup"><span data-stu-id="d37f7-300">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="d37f7-301">Inicializa duas variáveis de ambiente (CatalogUrl e OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="d37f7-301">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="d37f7-302">Encaminha a porta 80, exposta no contêiner, para a porta 80 externa, no computador host.</span><span class="sxs-lookup"><span data-stu-id="d37f7-302">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="d37f7-303">vincula o aplicativo Web ao catálogo e ao serviço de pedidos com a configuração depends_on.</span><span class="sxs-lookup"><span data-stu-id="d37f7-303">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="d37f7-304">Isso faz com que o serviço aguarde até que esses serviços sejam iniciados.</span><span class="sxs-lookup"><span data-stu-id="d37f7-304">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="d37f7-305">Vamos abordar novamente o arquivo docker-compose.yml em uma seção posterior, ao explicar como implementar microsserviços e aplicativos de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="d37f7-305">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a><span data-ttu-id="d37f7-306">Trabalhando com docker-compose.yml no Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="d37f7-306">Working with docker-compose.yml in Visual Studio 2019</span></span>

<span data-ttu-id="d37f7-307">Além de adicionar um Arquivo Docker a um projeto, como mencionamos antes, o Visual Studio 2017 (da versão 15.8 em) pode adicionar suporte orquestrador para Docker Compose a uma solução.</span><span class="sxs-lookup"><span data-stu-id="d37f7-307">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from version 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="d37f7-308">Quando você adiciona o suporte ao orquestrador de contêineres, conforme mostrado na Figura 5-7, pela primeira vez, o Visual Studio cria o Dockerfile para o projeto e cria um projeto (seção de serviço) na solução com vários arquivos `docker-compose*.yml` globais e, em seguida, adiciona o projeto nesses arquivos.</span><span class="sxs-lookup"><span data-stu-id="d37f7-308">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="d37f7-309">Depois, você pode abrir os arquivos docker-compose.yml e atualizá-los com mais recursos.</span><span class="sxs-lookup"><span data-stu-id="d37f7-309">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="d37f7-310">Você precisa repetir essa forma de operação para cada projeto que deseja incluir no arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="d37f7-310">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="d37f7-311">No momento desta escrita, o Visual Studio suporta **orquestradores Docker Compose** e **Kubernetes/Helm.**</span><span class="sxs-lookup"><span data-stu-id="d37f7-311">At the time of this writing, Visual Studio supports **Docker Compose** and **Kubernetes/Helm** orchestrators.</span></span>

![Captura de tela mostrando a opção Suporte ao Orquestrador de contêineres no menu de contexto do projeto.](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

<span data-ttu-id="d37f7-313">**Figura 5-7**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-313">**Figure 5-7**.</span></span> <span data-ttu-id="d37f7-314">Adicionando suporte ao Docker no Visual Studio 2019 clicando com o botão direito do mouse em um projeto ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d37f7-314">Adding Docker support in Visual Studio 2019 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="d37f7-315">Depois de adicionar suporte ao orquestrador à solução no Visual Studio, você também verá um novo nó (no arquivo de projeto `docker-compose.dcproj`) no Gerenciador de Soluções contendo os arquivos docker-compose.yml adicionados, conforme mostrado na Figura 5-8.</span><span class="sxs-lookup"><span data-stu-id="d37f7-315">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Captura de tela do nó de composição de docker no Solution Explorer.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

<span data-ttu-id="d37f7-317">**Figura 5-8**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-317">**Figure 5-8**.</span></span> <span data-ttu-id="d37f7-318">O nó de árvore **de composição docker** adicionado no Visual Studio 2019 Solution Explorer</span><span class="sxs-lookup"><span data-stu-id="d37f7-318">The **docker-compose** tree node added in Visual Studio 2019 Solution Explorer</span></span>

<span data-ttu-id="d37f7-319">Você pode implantar um aplicativo de vários contêineres com um único arquivo docker-compose.yml usando o comando `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="d37f7-319">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="d37f7-320">No entanto, o Visual Studio adiciona um grupo desses arquivos, para que você possa substituir os valores de acordo com o ambiente (desenvolvimento ou produção) e o tipo de execução (lançamento ou depuração).</span><span class="sxs-lookup"><span data-stu-id="d37f7-320">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="d37f7-321">Essa funcionalidade será explicada nas seções posteriores.</span><span class="sxs-lookup"><span data-stu-id="d37f7-321">This capability will be explained in later sections.</span></span>

![Imagem para o Passo 5.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="d37f7-323">Etapa 5.</span><span class="sxs-lookup"><span data-stu-id="d37f7-323">Step 5.</span></span> <span data-ttu-id="d37f7-324">Compilar e executar seu aplicativo do Docker</span><span class="sxs-lookup"><span data-stu-id="d37f7-324">Build and run your Docker application</span></span>

<span data-ttu-id="d37f7-325">Se seu aplicativo tem apenas um contêiner, você pode executá-lo implantando-o no host do Docker (VM ou servidor físico).</span><span class="sxs-lookup"><span data-stu-id="d37f7-325">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="d37f7-326">No entanto, se o aplicativo contiver vários serviços, você pode`docker-compose up)`implantá-lo como um aplicativo composto, usando um único comando CLI ( ou com o Visual Studio, que usará esse comando sob as capas.</span><span class="sxs-lookup"><span data-stu-id="d37f7-326">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (`docker-compose up)`, or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="d37f7-327">Vamos examinar as diferentes opções.</span><span class="sxs-lookup"><span data-stu-id="d37f7-327">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="d37f7-328">Opção A: Executando um aplicativo de contêiner único</span><span class="sxs-lookup"><span data-stu-id="d37f7-328">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="d37f7-329">Usando a CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="d37f7-329">Using Docker CLI</span></span>

<span data-ttu-id="d37f7-330">Você pode executar um contêiner do Docker usando o comando `docker run`, conforme mostrado na Figura 5-9:</span><span class="sxs-lookup"><span data-stu-id="d37f7-330">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="d37f7-331">O comando acima criará uma instância de contêiner da imagem especificada, cada vez que for executado.</span><span class="sxs-lookup"><span data-stu-id="d37f7-331">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="d37f7-332">Você pode `--name` usar o parâmetro para dar um `docker start {name}` nome ao contêiner e, em seguida, usar (ou usar o ID do contêiner ou nome automático) para executar uma instância de contêiner existente.</span><span class="sxs-lookup"><span data-stu-id="d37f7-332">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container ID or automatic name) to run an existing container instance.</span></span>

![Captura de tela executando um contêiner Docker usando o comando docker run.](./media/docker-app-development-workflow/use-docker-run-command.png)

<span data-ttu-id="d37f7-334">**Figura 5-9**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-334">**Figure 5-9**.</span></span> <span data-ttu-id="d37f7-335">Executando um contêiner do Docker usando o comando docker run</span><span class="sxs-lookup"><span data-stu-id="d37f7-335">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="d37f7-336">Nesse caso, o comando associa a porta interna 5000 do contêiner à porta 80 do computador host.</span><span class="sxs-lookup"><span data-stu-id="d37f7-336">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="d37f7-337">Isso significa que o host está escutando na porta 80 e encaminhando para a porta 5000 no contêiner.</span><span class="sxs-lookup"><span data-stu-id="d37f7-337">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="d37f7-338">O hash mostrado é o ID do contêiner e também é `--name` atribuído um nome legível aleatório se a opção não for usada.</span><span class="sxs-lookup"><span data-stu-id="d37f7-338">The hash shown is the container ID and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="d37f7-339">Como usar o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d37f7-339">Using Visual Studio</span></span>

<span data-ttu-id="d37f7-340">Se ainda não adicionou o suporte ao orquestrador de contêineres, você também poderá executar um aplicativo de contêiner único no Visual Studio pressionando **Ctrl+F5** e usar **F5** para depurar o aplicativo dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="d37f7-340">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="d37f7-341">O contêiner é executado localmente usando o docker run.</span><span class="sxs-lookup"><span data-stu-id="d37f7-341">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="d37f7-342">Opção B: executando um aplicativo de vários contêineres</span><span class="sxs-lookup"><span data-stu-id="d37f7-342">Option B: Running a multi-container application</span></span>

<span data-ttu-id="d37f7-343">Na maioria dos cenários empresariais, um aplicativo do Docker será ser composto de vários serviços, o que significa que você precisará executar um aplicativo de vários contêineres, conforme mostrado na Figura 5-10.</span><span class="sxs-lookup"><span data-stu-id="d37f7-343">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![VM com vários contêineres do Docker](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="d37f7-345">**Figura 5-10**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-345">**Figure 5-10**.</span></span> <span data-ttu-id="d37f7-346">VM com contêineres do Docker implantados</span><span class="sxs-lookup"><span data-stu-id="d37f7-346">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="d37f7-347">Usando a CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="d37f7-347">Using Docker CLI</span></span>

<span data-ttu-id="d37f7-348">Para executar um aplicativo de vários contêineres com a CLI do Docker, use o comando `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="d37f7-348">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="d37f7-349">Esse comando usa o arquivo **docker-compose.yml**, que existe no nível da solução, para implantar um aplicativo de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="d37f7-349">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="d37f7-350">A figura 5-11 mostra os resultados da execução do comando no diretório principal da solução, que contém o arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="d37f7-350">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Exibição da tela ao executar o comando docker-compose up](./media/docker-app-development-workflow/results-docker-compose-up.png)

<span data-ttu-id="d37f7-352">**Figura 5-11**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-352">**Figure 5-11**.</span></span> <span data-ttu-id="d37f7-353">Resultados de exemplo ao executar o comando docker-compose up</span><span class="sxs-lookup"><span data-stu-id="d37f7-353">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="d37f7-354">Depois que o comando docker-compose up é executado, o aplicativo e os contêineres relacionados são implantados no host do Docker, como é mostrado na Figura 5-10.</span><span class="sxs-lookup"><span data-stu-id="d37f7-354">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="d37f7-355">Como usar o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d37f7-355">Using Visual Studio</span></span>

<span data-ttu-id="d37f7-356">Executar um aplicativo de vários contêineres usando o Visual Studio 2019 não pode ficar mais simples.</span><span class="sxs-lookup"><span data-stu-id="d37f7-356">Running a multi-container application using Visual Studio 2019 can't get any simpler.</span></span> <span data-ttu-id="d37f7-357">Basta pressionar **Ctrl+F5** para executar ou **F5** para depuração, como de costume, configurando o projeto **docker-compose** como o projeto de inicialização.</span><span class="sxs-lookup"><span data-stu-id="d37f7-357">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="d37f7-358">O Visual Studio lida com toda a configuração necessária, para que você possa criar pontos de interrupção como de costume e depurar o que finalmente se tornam processos independentes em execução em "servidores remotos", com o depurador já conectado, assim mesmo.</span><span class="sxs-lookup"><span data-stu-id="d37f7-358">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", with the debugger already attached, just like that.</span></span>

<span data-ttu-id="d37f7-359">Conforme mencionado anteriormente, sempre que você adiciona suporte à solução do Docker a um projeto de uma solução, esse projeto é configurado no arquivo global (nível da solução) docker-compose.yml, o que permite que você execute ou depure toda a solução de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="d37f7-359">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="d37f7-360">O Visual Studio iniciará um contêiner para cada projeto que tenha suporte habilitado à solução do Docker e executará todas as etapas internas para você (dotnet publish, docker build, etc.).</span><span class="sxs-lookup"><span data-stu-id="d37f7-360">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="d37f7-361">Se você quiser dar uma olhada na parte chata do trabalho, confira o arquivo:</span><span class="sxs-lookup"><span data-stu-id="d37f7-361">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="d37f7-362">O ponto importante aqui é que, como mostrado na Figura 5-12, no Visual Studio 2019 há um comando **Docker** adicional para a ação chave F5.</span><span class="sxs-lookup"><span data-stu-id="d37f7-362">The important point here is that, as shown in Figure 5-12, in Visual Studio 2019 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="d37f7-363">Essa opção permite que você execute ou depure um aplicativo de vários contêineres executando todos os contêineres que estão definidos nos arquivos docker-compose.yml no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="d37f7-363">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="d37f7-364">A capacidade de depurar soluções de vários contêineres significa que você poderá definir vários pontos de interrupção, cada ponto de interrupção em um projeto (contêiner) diferente e que, durante a depuração no Visual Studio, você vai parar nos pontos de interrupção definidos em diferentes projetos e em execução em diferentes contêineres.</span><span class="sxs-lookup"><span data-stu-id="d37f7-364">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Captura de tela da barra de ferramentas de depuração executando um projeto de composição de docker.](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

<span data-ttu-id="d37f7-366">**Figura 5-12**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-366">**Figure 5-12**.</span></span> <span data-ttu-id="d37f7-367">Executando aplicativos multi-contêiner no Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="d37f7-367">Running multi-container apps in Visual Studio 2019</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d37f7-368">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="d37f7-368">Additional resources</span></span>

- <span data-ttu-id="d37f7-369">**Implantar um contêiner ASP.NET em um host Docker remoto** </span><span class="sxs-lookup"><span data-stu-id="d37f7-369">**Deploy an ASP.NET container to a remote Docker host** </span></span>\
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="d37f7-370">Uma observação sobre teste e implantação com orquestradores</span><span class="sxs-lookup"><span data-stu-id="d37f7-370">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="d37f7-371">Os comandos docker-compose up e docker run (ou executar e depurar os contêineres no Visual Studio) são adequados para contêineres de teste em seu ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d37f7-371">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="d37f7-372">Mas você não deve usar essa abordagem para implantações de produção, com orquestradores de destino como [Kubernetes](https://kubernetes.io/) ou [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="d37f7-372">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="d37f7-373">Se você estiver usando kubernetes, você tem que usar [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) para organizar contêineres e [serviços](https://kubernetes.io/docs/concepts/services-networking/service/) para rede-los.</span><span class="sxs-lookup"><span data-stu-id="d37f7-373">If you're using Kubernetes, you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="d37f7-374">Você também pode usar [implantações](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) para organizar a criação e a modificação de pods.</span><span class="sxs-lookup"><span data-stu-id="d37f7-374">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![Imagem para o Passo 6.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="d37f7-376">Etapa 6.</span><span class="sxs-lookup"><span data-stu-id="d37f7-376">Step 6.</span></span> <span data-ttu-id="d37f7-377">Testar seu aplicativo do Docker usando o host local do Docker</span><span class="sxs-lookup"><span data-stu-id="d37f7-377">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="d37f7-378">Esta etapa varia de acordo com o que seu aplicativo está fazendo.</span><span class="sxs-lookup"><span data-stu-id="d37f7-378">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="d37f7-379">Em um aplicativo Web .NET Core simples implantado como um único contêiner ou serviço, você pode acessar o serviço abrindo um navegador no host do Docker e navegando até o site, conforme mostrado na Figura 5-13.</span><span class="sxs-lookup"><span data-stu-id="d37f7-379">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="d37f7-380">(Se a configuração do Dockerfile mapear o contêiner para uma porta no host que seja diferente de 80, inclua a porta do host na URL).</span><span class="sxs-lookup"><span data-stu-id="d37f7-380">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Captura de tela da resposta do localhost/API/values.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="d37f7-382">**Figura 5-13**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-382">**Figure 5-13**.</span></span> <span data-ttu-id="d37f7-383">Exemplo de teste do seu aplicativo do Docker localmente usando localhost</span><span class="sxs-lookup"><span data-stu-id="d37f7-383">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="d37f7-384">Se o localhost não estiver apontando para o IP do host do Docker (por padrão, obrigatório ao usar o Docker CE), use o endereço IP da placa de rede do computador para navegar até o serviço.</span><span class="sxs-lookup"><span data-stu-id="d37f7-384">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="d37f7-385">Observe que a URL no navegador usa a porta 80 para o exemplo de contêiner específico que está sendo discutido.</span><span class="sxs-lookup"><span data-stu-id="d37f7-385">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="d37f7-386">No entanto, internamente as solicitações estão sendo redirecionadas para a porta 5000, pois é assim que ele foi implantado com o comando docker run, conforme explicado em uma etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="d37f7-386">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="d37f7-387">Você também pode testar o aplicativo usando o comando curl no terminal, conforme mostrado na Figura 5-14.</span><span class="sxs-lookup"><span data-stu-id="d37f7-387">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="d37f7-388">Em uma instalação do Docker no Windows, o IP padrão do host do Docker é sempre 10.0.75.1, além do endereço IP real do computador.</span><span class="sxs-lookup"><span data-stu-id="d37f7-388">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Saída do console http://10.0.75.1/API/values de obter o com cacho.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="d37f7-390">**Figura 5-14**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-390">**Figure 5-14**.</span></span> <span data-ttu-id="d37f7-391">Exemplo de teste do seu aplicativo do Docker localmente usando curl</span><span class="sxs-lookup"><span data-stu-id="d37f7-391">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a><span data-ttu-id="d37f7-392">Contêineres de teste e depuração com visual studio 2019</span><span class="sxs-lookup"><span data-stu-id="d37f7-392">Testing and debugging containers with Visual Studio 2019</span></span>

<span data-ttu-id="d37f7-393">Ao executar e depurar os contêineres com o Visual Studio 2019, você pode depurar o aplicativo .NET da mesma forma que faria ao rodar sem contêineres.</span><span class="sxs-lookup"><span data-stu-id="d37f7-393">When running and debugging the containers with Visual Studio 2019, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="d37f7-394">Testando e depurando sem o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d37f7-394">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="d37f7-395">Se você está desenvolvendo usando a abordagem editor/CLI, depurar contêineres é mais difícil e você provavelmente vai querer depurar gerando vestígios.</span><span class="sxs-lookup"><span data-stu-id="d37f7-395">If you're developing using the editor/CLI approach, debugging containers is more difficult and you'll probably want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d37f7-396">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="d37f7-396">Additional resources</span></span>

- <span data-ttu-id="d37f7-397">**Depuração de aplicativos em um contêiner Docker local** </span><span class="sxs-lookup"><span data-stu-id="d37f7-397">**Debugging apps in a local Docker container** </span></span>\
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="d37f7-398">**Steve Lasker. Criar, depurar, implantar ASP.NET principais aplicativos com o Docker.**</span><span class="sxs-lookup"><span data-stu-id="d37f7-398">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="d37f7-399">Vídeo.</span><span class="sxs-lookup"><span data-stu-id="d37f7-399">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="d37f7-400">Fluxo de trabalho simplificado ao desenvolver contêineres com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d37f7-400">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="d37f7-401">Efetivamente, o fluxo de trabalho ao usar o Visual Studio é muito mais simples do que ao usar a abordagem de editor/CLI.</span><span class="sxs-lookup"><span data-stu-id="d37f7-401">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="d37f7-402">A maioria das etapas necessárias pelo Docker, relacionadas ao Dockerfile e aos arquivos docker-compose.yml, são ocultas ou simplificadas pelo Visual Studio, conforme mostrado na Figura 5-15.</span><span class="sxs-lookup"><span data-stu-id="d37f7-402">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Diagrama mostrando os cinco passos simplificados necessários para criar um aplicativo.":::
<span data-ttu-id="d37f7-404">O processo de desenvolvimento dos aplicativos Docker: 1 - Código seu App, 2 - Write Dockerfile/s, 3 - Criar imagens definidas em Dockerfile/s, 4 - (opcional) Compor serviços no arquivo docker-compose.yml, 5 - Executar contêiner ou docker-compose app, 6 - Teste seu aplicativo ou microsserviços, 7 - Empurre para repo e repita.</span><span class="sxs-lookup"><span data-stu-id="d37f7-404">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="d37f7-405">**Figura 5-15**.</span><span class="sxs-lookup"><span data-stu-id="d37f7-405">**Figure 5-15**.</span></span> <span data-ttu-id="d37f7-406">Fluxo de trabalho simplificado ao desenvolver com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d37f7-406">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="d37f7-407">Além disso, será necessário executar a etapa 2 (adicionar suporte do Docker aos seus projetos) apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="d37f7-407">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="d37f7-408">Portanto, o fluxo de trabalho é semelhante às suas tarefas de desenvolvimento regulares, quando utiliza o .NET para qualquer outro desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d37f7-408">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="d37f7-409">É necessário saber o que está acontecendo nos bastidores (o processo de build da imagem, quais imagens base você está usando, a implantação de contêineres, etc.) e, às vezes, você também precisará editar o Dockerfile ou o arquivo docker-compose.yml para personalizar comportamentos.</span><span class="sxs-lookup"><span data-stu-id="d37f7-409">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="d37f7-410">Mas a maior parte do trabalho é bastante simplificada com o uso do Visual Studio, o que o torna muito mais produtivo.</span><span class="sxs-lookup"><span data-stu-id="d37f7-410">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d37f7-411">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="d37f7-411">Additional resources</span></span>

- <span data-ttu-id="d37f7-412">**Steve Lasker. .NET Docker Development com Visual Studio (2017)** </span><span class="sxs-lookup"><span data-stu-id="d37f7-412">**Steve Lasker. .NET Docker Development with Visual Studio (2017)** </span></span>\
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="d37f7-413">Usando comandos do PowerShell em um DockerFile para configurar contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="d37f7-413">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="d37f7-414">Os [contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) permitem converter seus aplicativos existentes do Windows em imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker.</span><span class="sxs-lookup"><span data-stu-id="d37f7-414">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="d37f7-415">Para usar contêineres do Windows, você executa comandos do PowerShell no Dockerfile, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d37f7-415">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="d37f7-416">Nesse caso, estamos usando uma imagem base do Windows Server Core (a configuração FROM) e instalando IIS com um comando do PowerShell (a configuração RUN).</span><span class="sxs-lookup"><span data-stu-id="d37f7-416">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="d37f7-417">Da mesma forma, você também pode usar comandos do PowerShell para configurar outros componentes, como ASP.NET 4.x, .NET 4.6 ou qualquer outro software do Windows.</span><span class="sxs-lookup"><span data-stu-id="d37f7-417">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="d37f7-418">Por exemplo, o seguinte comando, em um Dockerfile, configura o ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="d37f7-418">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="d37f7-419">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="d37f7-419">Additional resources</span></span>

- <span data-ttu-id="d37f7-420">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="d37f7-420">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="d37f7-421">Comandos do PowerShell de exemplo a serem executados em Dockerfiles para incluir recursos do Windows.</span><span class="sxs-lookup"><span data-stu-id="d37f7-421">Example PowerShell commands to run from dockerfiles to include Windows features.</span></span>\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="d37f7-422">[Próximo](index.md)
>[anterior](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="d37f7-422">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
