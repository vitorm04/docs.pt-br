---
title: Fluxo de trabalho de desenvolvimento para aplicativos do Docker
description: Entenda os detalhes do fluxo de trabalho para o desenvolvimento de aplicativos baseados no Docker. Comece o passo a passo e obtenha alguns detalhes para otimizar Dockerfiles e concluir com o fluxo de trabalho simplificado disponível ao usar o Visual Studio.
ms.date: 01/07/2019
ms.openlocfilehash: 0c2789377bc388b8ac7373ee7fa46e3141f1b518
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "73740142"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="c262a-104">Fluxo de trabalho de desenvolvimento para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="c262a-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="c262a-105">O ciclo de vida de desenvolvimento de aplicativo começa em seu computador, como desenvolvedor, onde você pode codificar o aplicativo usando sua linguagem preferida e testá-lo localmente.</span><span class="sxs-lookup"><span data-stu-id="c262a-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="c262a-106">Com esse fluxo de trabalho, não importa a linguagem, a estrutura e a plataforma escolhidas, você está sempre desenvolvendo e testando contêineres do Docker, mas localmente.</span><span class="sxs-lookup"><span data-stu-id="c262a-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="c262a-107">Cada contêiner (uma instância de uma imagem do Docker) inclui os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="c262a-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="c262a-108">Uma seleção de sistema operacional, por exemplo, uma distribuição do Linux, o Windows Nano Server ou o Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="c262a-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="c262a-109">Arquivos adicionados durante o desenvolvimento, por exemplo, os binários e o código-fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c262a-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="c262a-110">Informações de configuração, como configurações de ambiente e dependências.</span><span class="sxs-lookup"><span data-stu-id="c262a-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="c262a-111">Fluxo de trabalho para o desenvolvimento de aplicativos baseados em contêiner do Docker</span><span class="sxs-lookup"><span data-stu-id="c262a-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="c262a-112">Esta seção descreve o fluxo de trabalho de desenvolvimento do *loop interno* de aplicativos baseados em contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="c262a-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="c262a-113">O fluxo de trabalho de loop interno significa que ele não está considerando o fluxo de trabalho de DevOps mais amplo, que pode incluir até a implantação de produção e só se concentra na tarefa de desenvolvimento feita no computador do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="c262a-113">The inner-loop workflow means it's not considering the broader DevOps workflow, which can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="c262a-114">As etapas iniciais para configurar o ambiente não são incluídas, pois elas são executadas apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="c262a-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="c262a-115">Um aplicativo é composto de seus próprios serviços e de bibliotecas adicionais (dependências).</span><span class="sxs-lookup"><span data-stu-id="c262a-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="c262a-116">A figura 5-1 a seguir ilustra as etapas básicas que são normalmente realizadas para criar um aplicativo do Docker.</span><span class="sxs-lookup"><span data-stu-id="c262a-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

<span data-ttu-id="c262a-117">:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Diagrama mostrando as 7 etapas necessárias para criar um aplicativo em contêineres.":::</span><span class="sxs-lookup"><span data-stu-id="c262a-117">:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram showing the 7 steps it takes to create a containerized app.":::</span></span>
<span data-ttu-id="c262a-118">O processo de desenvolvimento para aplicativos Docker: 1-codificar seu aplicativo, 2-gravar Dockerfile/s, 3-criar imagens definidas em Dockerfile/s, 4-(opcional) compor serviços no arquivo Docker-Compose. yml, 5-executar o contêiner ou o aplicativo Docker-Compose, 6-testar seu aplicativo ou seus microserviços, 7- Envie por push para o repositório e repita.</span><span class="sxs-lookup"><span data-stu-id="c262a-118">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="c262a-119">**Figura 5-1.**</span><span class="sxs-lookup"><span data-stu-id="c262a-119">**Figure 5-1.**</span></span> <span data-ttu-id="c262a-120">Fluxo de trabalho passo a passo para o desenvolvimento de aplicativos do Docker em contêineres</span><span class="sxs-lookup"><span data-stu-id="c262a-120">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="c262a-121">Nesta seção, todo esse processo é detalhado e cada etapa principal é explicada com base em um ambiente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c262a-121">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="c262a-122">Ao usar uma abordagem de desenvolvimento de editor/CLI (por exemplo, o Visual Studio Code com a CLI do Docker no macOS ou no Windows), você precisará conhecer cada etapa e, na maioria das vezes, com mais detalhes do que ao usar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c262a-122">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="c262a-123">Para obter mais informações sobre como trabalhar em um ambiente de CLI, confira o livro eletrônico [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/) (Ciclo de vida do aplicativo do Docker em contêineres com ferramentas e plataformas da Microsoft).</span><span class="sxs-lookup"><span data-stu-id="c262a-123">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="c262a-124">Quando você usar o Visual Studio 2017, muitas dessas etapas serão feitas para você, melhorando significativamente sua produtividade.</span><span class="sxs-lookup"><span data-stu-id="c262a-124">When you're using Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="c262a-125">Isso se aplica principalmente quando você usa o Visual Studio 2017 e tem aplicativos de vários contêineres como destino.</span><span class="sxs-lookup"><span data-stu-id="c262a-125">This is especially true when you're using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="c262a-126">Por exemplo, com apenas um clique do mouse, o Visual Studio adiciona o Dockerfile e o arquivo docker-compose.yml aos seus projetos com a configuração correta para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c262a-126">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="c262a-127">Ao executar o aplicativo no Visual Studio, ele cria a imagem do Docker e executa o aplicativo de vários contêineres diretamente no Docker; e até mesmo permite que você depure vários contêineres de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="c262a-127">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="c262a-128">Esses recursos vão acelerar sua velocidade de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="c262a-128">These features will boost your development speed.</span></span>

<span data-ttu-id="c262a-129">No entanto, apenas porque o Visual Studio automatiza essas etapas não significa que você não precisa saber o que está acontecendo nos bastidores com o Docker.</span><span class="sxs-lookup"><span data-stu-id="c262a-129">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="c262a-130">Portanto, as diretrizes a seguir detalham cada etapa.</span><span class="sxs-lookup"><span data-stu-id="c262a-130">Therefore, the following guidance details every step.</span></span>

![Imagem da etapa 1.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="c262a-132">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="c262a-132">Step 1.</span></span> <span data-ttu-id="c262a-133">Iniciar a codificação e a criação do aplicativo inicial ou da linha de base do serviço</span><span class="sxs-lookup"><span data-stu-id="c262a-133">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="c262a-134">O desenvolvimento de um aplicativo do Docker é semelhante à forma como você desenvolve um aplicativo sem Docker.</span><span class="sxs-lookup"><span data-stu-id="c262a-134">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="c262a-135">A diferença é que, durante o desenvolvimento para o Docker, você está implantando e testando o aplicativo ou os serviços executando-os em contêineres do Docker em seu ambiente local (seja em uma VM do Linux configurada pelo Docker ou diretamente no Windows quando está usando contêineres do Windows).</span><span class="sxs-lookup"><span data-stu-id="c262a-135">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="c262a-136">Configurar seu ambiente local com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c262a-136">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="c262a-137">Para começar, instale o [Docker CE (Community Edition)](https://docs.docker.com/docker-for-windows/) para Windows, conforme explicado nas instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="c262a-137">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="c262a-138">Introdução ao Docker CE para Windows</span><span class="sxs-lookup"><span data-stu-id="c262a-138">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="c262a-139">Além disso, você precisa do Visual Studio 2017 versão 15.7 ou posterior com a carga de trabalho **Desenvolvimento multiplataforma do .NET Core** instalada, conforme mostrado na Figura 5-2.</span><span class="sxs-lookup"><span data-stu-id="c262a-139">In addition, you need Visual Studio 2017 version 15.7 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![Captura de tela da seleção de desenvolvimento de plataforma cruzada do .NET Core.](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

<span data-ttu-id="c262a-141">**Figura 5-2**.</span><span class="sxs-lookup"><span data-stu-id="c262a-141">**Figure 5-2**.</span></span> <span data-ttu-id="c262a-142">Selecionando a carga de trabalho **Desenvolvimento multiplataforma do .NET Core** durante a instalação do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c262a-142">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="c262a-143">Você pode iniciar a codificação do aplicativo no .NET simples (normalmente no .NET Core, se estiver planejando usar contêineres) mesmo antes de habilitar o Docker no aplicativo e antes da implantação e dos testes no Docker.</span><span class="sxs-lookup"><span data-stu-id="c262a-143">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="c262a-144">No entanto, é recomendável que você comece a trabalhar no Docker assim que possível, porque que esse será o ambiente real e os problemas poderão ser descobertos o mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="c262a-144">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="c262a-145">Isso é recomendável porque o Visual Studio facilita tanto o trabalho com o Docker parecendo, até mesmo, transparente — o melhor exemplo ao depurar aplicativos de vários contêineres do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c262a-145">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c262a-146">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c262a-146">Additional resources</span></span>

- <span data-ttu-id="c262a-147">**Introdução ao Docker CE for Windows** </span><span class="sxs-lookup"><span data-stu-id="c262a-147">**Get started with Docker CE for Windows** </span></span>\
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="c262a-148">**Visual Studio 2017** </span><span class="sxs-lookup"><span data-stu-id="c262a-148">**Visual Studio 2017** </span></span>\
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)

![Imagem da etapa 2.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="c262a-150">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="c262a-150">Step 2.</span></span> <span data-ttu-id="c262a-151">Criar um Dockerfile relacionado a uma imagem base existente do .NET</span><span class="sxs-lookup"><span data-stu-id="c262a-151">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="c262a-152">Você precisa de um Dockerfile para cada imagem personalizada que você deseja criar. Você também precisará de um Dockerfile para cada contêiner a ser implantado automaticamente, por meio do Visual Studio, ou implantado manualmente, usando a CLI do Docker (comandos docker run e docker-compose).</span><span class="sxs-lookup"><span data-stu-id="c262a-152">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="c262a-153">Se seu aplicativo contém um único serviço personalizado, é necessário um único Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c262a-153">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="c262a-154">Se seu aplicativo contém vários serviços (como em uma arquitetura de microsserviços), é necessário um Dockerfile para cada serviço.</span><span class="sxs-lookup"><span data-stu-id="c262a-154">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="c262a-155">O Dockerfile é colocado na pasta raiz do seu aplicativo ou serviço.</span><span class="sxs-lookup"><span data-stu-id="c262a-155">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="c262a-156">Ele contém os comandos que indicam ao Docker como configurar e executar seu aplicativo ou serviço em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="c262a-156">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="c262a-157">Você pode criar manualmente um Dockerfile por meio de código e adicioná-lo ao seu projeto junto com as dependências do .NET.</span><span class="sxs-lookup"><span data-stu-id="c262a-157">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="c262a-158">Com o Visual Studio e suas ferramentas para Docker, esta tarefa requer apenas alguns cliques do mouse.</span><span class="sxs-lookup"><span data-stu-id="c262a-158">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="c262a-159">Quando você cria um projeto no Visual Studio 2017, há uma opção chamada **Habilitar suporte a contêiner (Docker)** , conforme mostrado na Figura 5-3.</span><span class="sxs-lookup"><span data-stu-id="c262a-159">When you create a new project in Visual Studio 2017, there's an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![Captura de tela mostrando a caixa de seleção Habilitar suporte ao Docker.](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

<span data-ttu-id="c262a-161">**Figura 5-3**.</span><span class="sxs-lookup"><span data-stu-id="c262a-161">**Figure 5-3**.</span></span> <span data-ttu-id="c262a-162">Habilitando o suporte ao Docker ao criar um projeto ASP.NET Core no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c262a-162">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2017</span></span>

<span data-ttu-id="c262a-163">Você também pode habilitar o suporte ao Docker em um projeto de aplicativo Web ASP.NET Core existente clicando com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecionando **Adicionar** > **Suporte ao Docker**, conforme mostrado na Figura 5-4.</span><span class="sxs-lookup"><span data-stu-id="c262a-163">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![Captura de tela mostrando a opção de suporte do Docker no menu Adicionar.](./media/docker-app-development-workflow/add-docker-support-option.png)

<span data-ttu-id="c262a-165">**Figura 5-4**.</span><span class="sxs-lookup"><span data-stu-id="c262a-165">**Figure 5-4**.</span></span> <span data-ttu-id="c262a-166">Habilitando o suporte do Docker em um projeto existente do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c262a-166">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="c262a-167">Essa ação adiciona um *Dockerfile* ao projeto com a configuração necessária e só está disponível em projetos ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c262a-167">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="c262a-168">De maneira semelhante, o Visual Studio também pode adicionar um arquivo docker-compose.yml a toda a solução com a opção **Adicionar > Suporte ao orquestrador de contêineres**.</span><span class="sxs-lookup"><span data-stu-id="c262a-168">In a similar fashion, Visual Studio can also add a docker-compose.yml file for the whole solution with the option **Add > Container Orchestrator Support**.</span></span> <span data-ttu-id="c262a-169">Na etapa 4, exploraremos essa opção com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="c262a-169">In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="c262a-170">Usando uma imagem do Docker do .NET oficial existente</span><span class="sxs-lookup"><span data-stu-id="c262a-170">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="c262a-171">Geralmente, você cria uma imagem personalizada para o contêiner usando uma imagem base que você pode obter de um repositório oficial, como o Registro do [Docker Hub](https://hub.docker.com/).</span><span class="sxs-lookup"><span data-stu-id="c262a-171">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="c262a-172">É exatamente isso o que acontece nos bastidores quando você habilita o suporte do Docker no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c262a-172">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="c262a-173">O Dockerfile usará uma imagem `aspnetcore` existente.</span><span class="sxs-lookup"><span data-stu-id="c262a-173">Your Dockerfile will use an existing `aspnetcore` image.</span></span>

<span data-ttu-id="c262a-174">Anteriormente, explicamos quais imagens do Docker e quais repositórios você poderia usar, dependendo da estrutura e do sistema operacional que você escolheu.</span><span class="sxs-lookup"><span data-stu-id="c262a-174">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="c262a-175">Por exemplo, se você quiser usar o ASP.NET Core (Linux ou Windows), a imagem a ser usada será `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="c262a-175">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="c262a-176">Assim, basta especificar qual imagem base do Docker será usada para o seu contêiner.</span><span class="sxs-lookup"><span data-stu-id="c262a-176">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="c262a-177">Você pode fazer isso adicionando `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` ao seu Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c262a-177">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` to your Dockerfile.</span></span> <span data-ttu-id="c262a-178">Isso será realizado automaticamente pelo Visual Studio, mas se você precisar atualizar a versão, será esse valor que você atualizará.</span><span class="sxs-lookup"><span data-stu-id="c262a-178">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="c262a-179">O uso de um repositório de imagem oficial do .NET do Hub do Docker com um número de versão garante que os mesmos recursos de linguagem estejam disponíveis em todos os computadores (incluindo desenvolvimento, teste e produção).</span><span class="sxs-lookup"><span data-stu-id="c262a-179">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="c262a-180">O exemplo a seguir mostra um Dockerfile de exemplo para um contêiner do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c262a-180">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="c262a-181">Nesse caso, a imagem é baseada na versão 2.2 da imagem oficial do Docker do ASP.NET Core (de várias arquiteturas para o Linux e o Windows).</span><span class="sxs-lookup"><span data-stu-id="c262a-181">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="c262a-182">Essa é a configuração `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="c262a-182">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="c262a-183">(Para obter mais informações sobre essa imagem base, consulte a página [imagem do Docker do .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) .) No Dockerfile, você também precisa instruir o Docker para escutar na porta TCP que será usada no tempo de execução (nesse caso, a porta 80, conforme configurado com a configuração de exposição).</span><span class="sxs-lookup"><span data-stu-id="c262a-183">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="c262a-184">Você pode especificar mais definições de configurações no Dockerfile, dependendo da linguagem e da estrutura usadas.</span><span class="sxs-lookup"><span data-stu-id="c262a-184">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="c262a-185">Por exemplo, a linha ENTRYPOINT com `["dotnet", "MySingleContainerWebApp.dll"]` diz ao Docker para executar um aplicativo do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c262a-185">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="c262a-186">Se você estiver usando o SDK e a CLI do .NET Core (CLI do dotnet) para compilar e executar o aplicativo do .NET, essa configuração será diferente.</span><span class="sxs-lookup"><span data-stu-id="c262a-186">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="c262a-187">O essencial é que a linha ENTRYPOINT e outras configurações serão diferentes dependendo da linguagem e da plataforma que você escolher para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c262a-187">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c262a-188">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c262a-188">Additional resources</span></span>

- <span data-ttu-id="c262a-189">**Criando imagens do Docker para aplicativos do .NET Core** </span><span class="sxs-lookup"><span data-stu-id="c262a-189">**Building Docker Images for .NET Core Applications** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- <span data-ttu-id="c262a-190">**Criar sua própria imagem**.</span><span class="sxs-lookup"><span data-stu-id="c262a-190">**Build your own image**.</span></span> <span data-ttu-id="c262a-191">Na documentação oficial do Docker.</span><span class="sxs-lookup"><span data-stu-id="c262a-191">In the official Docker documentation.</span></span>\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="c262a-192">**Permanecendo atualizado com as imagens de contêiner do .NET** </span><span class="sxs-lookup"><span data-stu-id="c262a-192">**Staying up-to-date with .NET Container Images** </span></span>\
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="c262a-193">**Usando o .NET e o Docker juntos – DockerCon atualização de 2018** </span><span class="sxs-lookup"><span data-stu-id="c262a-193">**Using .NET and Docker Together - DockerCon 2018 Update** </span></span>\
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="c262a-194">Usando repositórios de imagens para várias arquiteturas</span><span class="sxs-lookup"><span data-stu-id="c262a-194">Using multi-arch image repositories</span></span>

<span data-ttu-id="c262a-195">Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="c262a-195">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="c262a-196">Esse recurso permite que fornecedores, como a Microsoft (criadores de imagem base), criem um único repositório para abranger várias plataformas (ou seja, Linux e Windows).</span><span class="sxs-lookup"><span data-stu-id="c262a-196">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="c262a-197">Por exemplo, o repositório [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/), disponível no registro do Hub do Docker, é compatível com Linux e Windows Nano Server usando o mesmo nome de repositório.</span><span class="sxs-lookup"><span data-stu-id="c262a-197">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="c262a-198">Ao especificar uma marcação, você direciona a uma plataforma que é explícita, como nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="c262a-198">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  <span data-ttu-id="c262a-199">Destinos: .NET Core 2.2 somente em runtime no Linux</span><span class="sxs-lookup"><span data-stu-id="c262a-199">Targets: .NET Core 2.2 runtime-only on Linux</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  <span data-ttu-id="c262a-200">Destinos: .NET Core 2.2 somente em runtime no Windows Nano Server</span><span class="sxs-lookup"><span data-stu-id="c262a-200">Targets: .NET Core 2.2 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="c262a-201">Mas, se você especificar o mesmo nome de imagem, mesmo com a mesma marca, as imagens para várias arquiteturas (como a imagem `aspnetcore`) usarão a versão do Linux ou do Windows, dependendo do sistema operacional do host do Docker em que você esteja implantando, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c262a-201">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnetcore` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  <span data-ttu-id="c262a-202">Várias arquiteturas: .NET Core 2.2 somente em runtime no Linux ou no Windows Nano Server, dependendo do sistema operacional do host do Docker</span><span class="sxs-lookup"><span data-stu-id="c262a-202">Multi-arch: .NET Core 2.2 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="c262a-203">Dessa forma, ao efetuar pull de uma imagem de um host do Windows, será efetuado o pull da variante do Windows e, ao efetuar pull do mesmo nome de imagem de um host do Linux, será efetuado pull da variante do Linux.</span><span class="sxs-lookup"><span data-stu-id="c262a-203">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="c262a-204">Builds de vários estágios no Dockerfile</span><span class="sxs-lookup"><span data-stu-id="c262a-204">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="c262a-205">O Dockerfile é semelhante a um script em lotes.</span><span class="sxs-lookup"><span data-stu-id="c262a-205">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="c262a-206">Como o que você faria se tivesse que configurar o computador da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c262a-206">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="c262a-207">Ele começa com uma imagem base que define o contexto inicial, como o sistema de arquivos de inicialização, que se baseia no sistema operacional do host.</span><span class="sxs-lookup"><span data-stu-id="c262a-207">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="c262a-208">Não é um sistema operacional, mas você pode considerá-lo como "o sistema operacional dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="c262a-208">It's not an OS, but you can think of it like "the" OS inside the container.</span></span>

<span data-ttu-id="c262a-209">A execução de cada linha de comando cria uma camada no sistema de arquivos com as alterações em relação à anterior, para que, quando combinadas, produzam o sistema de arquivos resultante.</span><span class="sxs-lookup"><span data-stu-id="c262a-209">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="c262a-210">Como cada nova camada é baseada na anterior e o tamanho da imagem resultante aumenta com cada comando, as imagens poderão ficar muito grandes se precisarem incluir, por exemplo, o SDK necessário para criar e publicar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c262a-210">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="c262a-211">É nesse ponto que os builds de vários estágios (do Docker 17.05 e superior) entram em cena para fazer a mágica.</span><span class="sxs-lookup"><span data-stu-id="c262a-211">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="c262a-212">A ideia central é que você pode separar o processo de execução do Dockerfile em estágios, em que um estágio é uma imagem inicial seguida por um ou mais comandos, e o último estágio determina o tamanho da imagem final.</span><span class="sxs-lookup"><span data-stu-id="c262a-212">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="c262a-213">Resumindo, os builds de vários estágios permitem dividir a criação em "fases" diferentes e, em seguida, montar a imagem final usando somente os diretórios relevantes dos estágios intermediários.</span><span class="sxs-lookup"><span data-stu-id="c262a-213">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="c262a-214">A estratégia geral para usar esse recurso é:</span><span class="sxs-lookup"><span data-stu-id="c262a-214">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="c262a-215">usar uma imagem base do SDK (não importa quão grande), com todos os componentes necessários para criar e publicar o aplicativo em uma pasta e, em seguida,</span><span class="sxs-lookup"><span data-stu-id="c262a-215">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="c262a-216">usar uma imagem base pequena, somente em runtime e copiar a pasta de publicação do estágio anterior para produzir uma pequena imagem final.</span><span class="sxs-lookup"><span data-stu-id="c262a-216">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="c262a-217">Provavelmente a melhor maneira de entender os vários estágios é percorrer um Dockerfile detalhadamente, linha por linha, então, vamos começar com o Dockerfile inicial criado pelo Visual Studio ao adicionar o suporte ao Docker a um projeto e entraremos em algumas otimizações mais tarde.</span><span class="sxs-lookup"><span data-stu-id="c262a-217">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="c262a-218">O Dockerfile inicial pode ser como este:</span><span class="sxs-lookup"><span data-stu-id="c262a-218">The initial Dockerfile might look something like this:</span></span>

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

<span data-ttu-id="c262a-219">E estes são os detalhes, linha por linha:</span><span class="sxs-lookup"><span data-stu-id="c262a-219">And these are the details, line by line:</span></span>

- <span data-ttu-id="c262a-220">**#1 de linha:** Inicie um estágio com uma imagem base somente de tempo de execução "pequeno", chame-a **base** para referência.</span><span class="sxs-lookup"><span data-stu-id="c262a-220">**Line #1:** Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>

- <span data-ttu-id="c262a-221">**#2 de linha:** Crie o diretório **/app** na imagem.</span><span class="sxs-lookup"><span data-stu-id="c262a-221">**Line #2:** Create the **/app** directory in the image.</span></span>

- <span data-ttu-id="c262a-222">**#3 de linha:** Expor a porta **80**.</span><span class="sxs-lookup"><span data-stu-id="c262a-222">**Line #3:** Expose port **80**.</span></span>

- <span data-ttu-id="c262a-223">**#5 de linha:** Comece um novo estágio com a imagem "grande" para criação/publicação.</span><span class="sxs-lookup"><span data-stu-id="c262a-223">**Line #5:** Begin a new stage with the "large" image for building/publishing.</span></span> <span data-ttu-id="c262a-224">Chame-o **Build** para referência.</span><span class="sxs-lookup"><span data-stu-id="c262a-224">Call it **build** for reference.</span></span>

- <span data-ttu-id="c262a-225">**#6 de linha:** Crie o diretório **/src** na imagem.</span><span class="sxs-lookup"><span data-stu-id="c262a-225">**Line #6:** Create directory **/src** in the image.</span></span>

- <span data-ttu-id="c262a-226">**#7 de linha:** Até a linha 16, copie os arquivos de projeto **. csproj** referenciados para poder restaurar pacotes posteriormente.</span><span class="sxs-lookup"><span data-stu-id="c262a-226">**Line #7:** Up to line 16, copy referenced **.csproj** project files to be able to restore packages later.</span></span>

- <span data-ttu-id="c262a-227">**#17 de linha:** Restaure os pacotes para o projeto **Catalog. API** e os projetos referenciados.</span><span class="sxs-lookup"><span data-stu-id="c262a-227">**Line #17:** Restore packages for the **Catalog.API** project and the referenced projects.</span></span>

- <span data-ttu-id="c262a-228">**#18 de linha:** Copie **toda a árvore de diretórios da solução** (exceto os arquivos/diretórios incluídos no arquivo **. dockerignore** ) para o diretório **/src** na imagem.</span><span class="sxs-lookup"><span data-stu-id="c262a-228">**Line #18:** Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) to the **/src** directory in the image.</span></span>

- <span data-ttu-id="c262a-229">**#19 de linha:** Altere a pasta atual para o projeto **Catalog. API** .</span><span class="sxs-lookup"><span data-stu-id="c262a-229">**Line #19:** Change the current folder to the **Catalog.API** project.</span></span>

- <span data-ttu-id="c262a-230">**#20 de linha:** Compile o projeto (e outras dependências do projeto) e a saída para o diretório **/app** na imagem.</span><span class="sxs-lookup"><span data-stu-id="c262a-230">**Line #20:** Build the project (and other project dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="c262a-231">**#22 de linha:** Iniciar um novo estágio continuando a partir da compilação.</span><span class="sxs-lookup"><span data-stu-id="c262a-231">**Line #22:** Begin a new stage continuing from the build.</span></span> <span data-ttu-id="c262a-232">Chame-o de **publicar** para referência.</span><span class="sxs-lookup"><span data-stu-id="c262a-232">Call it **publish** for reference.</span></span>

- <span data-ttu-id="c262a-233">**#23 de linha:** Publique o projeto (e as dependências) e a saída para o diretório **/app** na imagem.</span><span class="sxs-lookup"><span data-stu-id="c262a-233">**Line #23:** Publish the project (and dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="c262a-234">**#25 de linha:** Inicie um novo estágio continuando da **base** e chame-o **final**.</span><span class="sxs-lookup"><span data-stu-id="c262a-234">**Line #25:** Begin a new stage continuing from **base** and call it **final**.</span></span>

- <span data-ttu-id="c262a-235">**#26 de linha:** Altere o diretório atual para **/app**.</span><span class="sxs-lookup"><span data-stu-id="c262a-235">**Line #26:** Change the current directory to **/app**.</span></span>

- <span data-ttu-id="c262a-236">**#27 de linha:** Copie o diretório **/app** do estágio **Publish** para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c262a-236">**Line #27:** Copy the **/app** directory from stage **publish** to the current directory.</span></span>

- <span data-ttu-id="c262a-237">**#28 de linha:** Defina o comando a ser executado quando o contêiner for iniciado.</span><span class="sxs-lookup"><span data-stu-id="c262a-237">**Line #28:** Define the command to run when the container is started.</span></span>

<span data-ttu-id="c262a-238">Agora vamos explorar algumas otimizações para melhorar o desempenho de todo o processo que, no caso do eShopOnContainers, significa cerca de 22 minutos ou mais para criar a solução completa em contêineres do Linux.</span><span class="sxs-lookup"><span data-stu-id="c262a-238">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="c262a-239">Você aproveitará o recurso de cache de camada do Docker, que é bastante simples: se a imagem base e os comandos forem iguais a outros já executados, ele poderá usar apenas a camada resultante sem precisar executar os comandos, economizando tempo.</span><span class="sxs-lookup"><span data-stu-id="c262a-239">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="c262a-240">Portanto, vamos nos concentrar no estágio **build**. As linhas 5 a 6 são basicamente as mesmas, mas as linhas 7 a 17 são diferentes para cada serviço do eShopOnContainers, portanto precisam ser executadas todas as vezes, no entanto, se você tiver alterado as linhas 7 a 16 para:</span><span class="sxs-lookup"><span data-stu-id="c262a-240">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```Dockerfile
COPY . .
```

<span data-ttu-id="c262a-241">Ele seria igual para cada serviço, ele poderia copiar toda a solução e criar uma camada maior, mas:</span><span class="sxs-lookup"><span data-stu-id="c262a-241">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1. <span data-ttu-id="c262a-242">o processo de cópia seria executado somente na primeira vez (e durante a recriação, se algum arquivo fosse alterado) e usaria o cache para todos os outros serviços e</span><span class="sxs-lookup"><span data-stu-id="c262a-242">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2. <span data-ttu-id="c262a-243">como a imagem maior ocorre em um estágio intermediário, ela não afeta o tamanho da imagem final.</span><span class="sxs-lookup"><span data-stu-id="c262a-243">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="c262a-244">A próxima otimização significativa envolve o comando `restore` executado na linha 17, que também é diferente para cada serviço do eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="c262a-244">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="c262a-245">Se você alterar essa linha para apenas:</span><span class="sxs-lookup"><span data-stu-id="c262a-245">If you change that line to just:</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="c262a-246">Isso restauraria os pacotes de toda a solução, mas, novamente, isso seria feito apenas uma vez, em vez de 15 vezes com a estratégia atual.</span><span class="sxs-lookup"><span data-stu-id="c262a-246">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="c262a-247">No entanto, `dotnet restore` só será executado se houver um único arquivo de projeto ou de solução na pasta, portanto, isso é um pouco mais complicado e a maneira de resolvê-lo, sem entrar em muitos detalhes, é esta:</span><span class="sxs-lookup"><span data-stu-id="c262a-247">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="c262a-248">adicione as seguintes linhas ao **.dockerignore**:</span><span class="sxs-lookup"><span data-stu-id="c262a-248">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="c262a-249">`*.sln`, para ignorar todos os arquivos de solução na árvore da pasta principal</span><span class="sxs-lookup"><span data-stu-id="c262a-249">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="c262a-250">`!eShopOnContainers-ServicesAndWebApps.sln`, para incluir apenas esse arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="c262a-250">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="c262a-251">inclua o argumento `/ignoreprojectextensions:.dcproj` em `dotnet restore`, para que ele também ignore o projeto docker-compose e só restaure os pacotes da solução eShopOnContainers-ServicesAndWebApps.</span><span class="sxs-lookup"><span data-stu-id="c262a-251">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="c262a-252">Para a otimização final, acontece que a linha 20 é redundante e a linha 23 também compila o aplicativo e vem, naturalmente, logo após a linha 20, o que gera outro comando demorado.</span><span class="sxs-lookup"><span data-stu-id="c262a-252">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="c262a-253">O arquivo resultante é:</span><span class="sxs-lookup"><span data-stu-id="c262a-253">The resulting file is then:</span></span>

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

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="c262a-254">Criação da imagem base do zero</span><span class="sxs-lookup"><span data-stu-id="c262a-254">Creating your base image from scratch</span></span>

<span data-ttu-id="c262a-255">Você pode criar sua própria imagem base do Docker do zero.</span><span class="sxs-lookup"><span data-stu-id="c262a-255">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="c262a-256">Esse cenário não é recomendável para um iniciante no Docker, mas se você desejar definir os bits específicos da sua própria imagem base, isso será possível.</span><span class="sxs-lookup"><span data-stu-id="c262a-256">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c262a-257">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c262a-257">Additional resources</span></span>

- <span data-ttu-id="c262a-258">**Imagens do .NET Core para várias arquiteturas**.</span><span class="sxs-lookup"><span data-stu-id="c262a-258">**Multi-arch .NET Core images**.</span></span>\
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="c262a-259">**Criar uma imagem base**.</span><span class="sxs-lookup"><span data-stu-id="c262a-259">**Create a base image**.</span></span> <span data-ttu-id="c262a-260">Documentação oficial do Docker.</span><span class="sxs-lookup"><span data-stu-id="c262a-260">Official Docker documentation.</span></span>\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Imagem da etapa 3.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="c262a-262">Etapa 3.</span><span class="sxs-lookup"><span data-stu-id="c262a-262">Step 3.</span></span> <span data-ttu-id="c262a-263">Criar imagens personalizadas do Docker e inserir seu aplicativo ou serviço nelas</span><span class="sxs-lookup"><span data-stu-id="c262a-263">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="c262a-264">Para cada serviço do seu aplicativo, você precisa criar uma imagem relacionada.</span><span class="sxs-lookup"><span data-stu-id="c262a-264">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="c262a-265">Se seu aplicativo é composto de um único serviço ou aplicativo Web, você precisa apenas de uma única imagem.</span><span class="sxs-lookup"><span data-stu-id="c262a-265">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="c262a-266">Observe que as imagens do Docker são criadas automaticamente para você no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c262a-266">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="c262a-267">As etapas a seguir são necessárias apenas para o fluxo de trabalho de editor/CLI e são explicadas com a finalidade de esclarecer o que acontece nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="c262a-267">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="c262a-268">Você, como desenvolvedor, precisa desenvolver e testar localmente até enviar um recurso concluído por push ou mudar para o sistema de controle do código-fonte (por exemplo, para o GitHub).</span><span class="sxs-lookup"><span data-stu-id="c262a-268">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="c262a-269">Isso significa que você precisa criar as imagens do Docker e implantar contêineres em um host do Docker local (VM do Windows ou Linux) e executar, testar e depurar nesses contêineres locais.</span><span class="sxs-lookup"><span data-stu-id="c262a-269">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="c262a-270">Para criar uma imagem personalizada no seu ambiente local, usando a CLI do Docker e o Dockerfile, você pode usar o comando docker build, como na Figura 5-5.</span><span class="sxs-lookup"><span data-stu-id="c262a-270">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Captura de tela mostrando a saída do console do comando de Build do Docker.](./media/docker-app-development-workflow/run-docker-build-command.png)

<span data-ttu-id="c262a-272">**Figura 5-5**.</span><span class="sxs-lookup"><span data-stu-id="c262a-272">**Figure 5-5**.</span></span> <span data-ttu-id="c262a-273">Criando uma imagem personalizada do Docker</span><span class="sxs-lookup"><span data-stu-id="c262a-273">Creating a custom Docker image</span></span>

<span data-ttu-id="c262a-274">Opcionalmente, em vez de executar diretamente o comando docker build na pasta do projeto, você pode, primeiro, gerar uma pasta implantável com as bibliotecas e os binários do .NET necessários, executando `dotnet publish` e, em seguida, usar o comando `docker build`.</span><span class="sxs-lookup"><span data-stu-id="c262a-274">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="c262a-275">Isso criará uma imagem do Docker com o nome `cesardl/netcore-webapi-microservice-docker:first`.</span><span class="sxs-lookup"><span data-stu-id="c262a-275">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="c262a-276">Nesse caso, :first é uma marcação que representa uma versão específica.</span><span class="sxs-lookup"><span data-stu-id="c262a-276">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="c262a-277">Você poderá repetir esta etapa para cada imagem personalizada que tiver que criar para o seu aplicativo composto do Docker.</span><span class="sxs-lookup"><span data-stu-id="c262a-277">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="c262a-278">Quando um aplicativo é composto de vários contêineres (ou seja, ele é um aplicativo multicontêineres), você também pode usar o comando `docker-compose up --build` para compilar todas as imagens relacionadas com um único comando usando os metadados expostos nos arquivos docker-compose.yml relacionados.</span><span class="sxs-lookup"><span data-stu-id="c262a-278">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="c262a-279">Você pode encontrar as imagens existentes no seu repositório local usando o comando docker images, conforme mostrado na Figura 5-6.</span><span class="sxs-lookup"><span data-stu-id="c262a-279">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Saída do console do comando docker images, mostrando as imagens existentes.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="c262a-281">**Figura 5-6.**</span><span class="sxs-lookup"><span data-stu-id="c262a-281">**Figure 5-6.**</span></span> <span data-ttu-id="c262a-282">Exibição de imagens existentes usando o comando docker images</span><span class="sxs-lookup"><span data-stu-id="c262a-282">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="c262a-283">Criação de imagens do Docker com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c262a-283">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="c262a-284">Ao usar o Visual Studio para criar um projeto com suporte ao Docker, você não cria explicitamente uma imagem.</span><span class="sxs-lookup"><span data-stu-id="c262a-284">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="c262a-285">Em vez disso, a imagem é criada quando você pressiona **F5** (ou **Ctrl+F5**) para executar o aplicativo ou o serviço convertido para Docker.</span><span class="sxs-lookup"><span data-stu-id="c262a-285">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="c262a-286">Esta etapa é automática no Visual Studio e você não verá ela ocorrer, mas é importante que você saiba o que está acontecendo nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="c262a-286">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![Imagem para a etapa 4 opcional.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="c262a-288">Etapa 4.</span><span class="sxs-lookup"><span data-stu-id="c262a-288">Step 4.</span></span> <span data-ttu-id="c262a-289">Definir os serviços no docker-compose.yml ao compilar um aplicativo de vários contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="c262a-289">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="c262a-290">O arquivo [docker-compose.yml](https://docs.docker.com/compose/compose-file/) permite que você defina um conjunto de serviços relacionados para que sejam implantados como um aplicativo composto com comandos de implantação.</span><span class="sxs-lookup"><span data-stu-id="c262a-290">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="c262a-291">Ele também configura as relações de dependência e a configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c262a-291">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="c262a-292">Para usar um arquivo docker-compose.yml, você precisa criar o arquivo na pasta principal ou raiz da sua solução, com conteúdo semelhante ao do exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c262a-292">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="c262a-293">Esse arquivo docker-compose.yml é uma versão simplificada e mesclada.</span><span class="sxs-lookup"><span data-stu-id="c262a-293">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="c262a-294">Ele contém dados de configuração estáticos para cada contêiner (como o nome da imagem personalizada), o que é sempre necessário, além das informações de configuração que poderão depender do ambiente de implantação, como a cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="c262a-294">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="c262a-295">Nas próximas seções, você aprenderá como dividir a configuração do docker-compose.yml em vários arquivos docker-compose e substituir valores dependendo do ambiente e do tipo de execução (depuração ou lançamento).</span><span class="sxs-lookup"><span data-stu-id="c262a-295">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="c262a-296">O arquivo docker-compose.yml de exemplo define quatro serviços: o serviço `webmvc` (um aplicativo Web), dois microsserviços (`ordering.api` e `basket.api`) e um contêiner de fonte de dados, `sql.data`, com base no SQL Server para Linux, em execução como um contêiner.</span><span class="sxs-lookup"><span data-stu-id="c262a-296">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering.api` and `basket.api`), and one data source container, `sql.data`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="c262a-297">Cada serviço será implantado como um contêiner, portanto, uma imagem do Docker é necessária para cada um.</span><span class="sxs-lookup"><span data-stu-id="c262a-297">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="c262a-298">O arquivo docker-compose.yml não apenas especifica quais contêineres estão sendo usados, mas também como eles são configurados individualmente.</span><span class="sxs-lookup"><span data-stu-id="c262a-298">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="c262a-299">Por exemplo, a definição de contêiner `webmvc` no arquivo .yml:</span><span class="sxs-lookup"><span data-stu-id="c262a-299">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="c262a-300">usa uma imagem `eshop/web:latest` predefinida.</span><span class="sxs-lookup"><span data-stu-id="c262a-300">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="c262a-301">Entretanto, você também poderia definir a imagem para ser compilada como parte da execução do docker-compose, com uma configuração adicional baseada em uma seção build: no arquivo docker-compose.</span><span class="sxs-lookup"><span data-stu-id="c262a-301">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="c262a-302">Inicializa duas variáveis de ambiente (CatalogUrl e OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="c262a-302">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="c262a-303">Encaminha a porta 80, exposta no contêiner, para a porta 80 externa, no computador host.</span><span class="sxs-lookup"><span data-stu-id="c262a-303">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="c262a-304">vincula o aplicativo Web ao catálogo e ao serviço de pedidos com a configuração depends_on.</span><span class="sxs-lookup"><span data-stu-id="c262a-304">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="c262a-305">Isso faz com que o serviço aguarde até que esses serviços sejam iniciados.</span><span class="sxs-lookup"><span data-stu-id="c262a-305">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="c262a-306">Vamos abordar novamente o arquivo docker-compose.yml em uma seção posterior, ao explicar como implementar microsserviços e aplicativos de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="c262a-306">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="c262a-307">Trabalhando com o docker-compose.yml no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c262a-307">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="c262a-308">Além de adicionar um Dockerfile a um projeto, como já mencionado, o Visual Studio 2017 (do 15.8 em diante) pode adicionar o suporte ao orquestrador do Docker Compose em uma solução.</span><span class="sxs-lookup"><span data-stu-id="c262a-308">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="c262a-309">Quando você adiciona o suporte ao orquestrador de contêineres, conforme mostrado na Figura 5-7, pela primeira vez, o Visual Studio cria o Dockerfile para o projeto e cria um projeto (seção de serviço) na solução com vários arquivos `docker-compose*.yml` globais e, em seguida, adiciona o projeto nesses arquivos.</span><span class="sxs-lookup"><span data-stu-id="c262a-309">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="c262a-310">Depois, você pode abrir os arquivos docker-compose.yml e atualizá-los com mais recursos.</span><span class="sxs-lookup"><span data-stu-id="c262a-310">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="c262a-311">Você precisa repetir essa forma de operação para cada projeto que deseja incluir no arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="c262a-311">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="c262a-312">No momento da redação deste artigo, o Visual Studio é compatível com os orquestradores do Docker Compose e do Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="c262a-312">At the time of this writing, Visual Studio supports Docker Compose and Service Fabric orchestrators.</span></span>

![Captura de tela mostrando a opção de suporte do orquestrador de contêiner no menu de contexto do projeto.](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

<span data-ttu-id="c262a-314">**Figura 5-7**.</span><span class="sxs-lookup"><span data-stu-id="c262a-314">**Figure 5-7**.</span></span> <span data-ttu-id="c262a-315">Adicionar suporte do Docker no Visual Studio 2017 ao clicar com o botão direito do mouse em um projeto do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c262a-315">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="c262a-316">Depois de adicionar suporte ao orquestrador à solução no Visual Studio, você também verá um novo nó (no arquivo de projeto `docker-compose.dcproj`) no Gerenciador de Soluções contendo os arquivos docker-compose.yml adicionados, conforme mostrado na Figura 5-8.</span><span class="sxs-lookup"><span data-stu-id="c262a-316">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Captura de tela do nó Docker-Compose no Gerenciador de Soluções.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

<span data-ttu-id="c262a-318">**Figura 5-8**.</span><span class="sxs-lookup"><span data-stu-id="c262a-318">**Figure 5-8**.</span></span> <span data-ttu-id="c262a-319">O nó de árvore **docker-compose** adicionado no Gerenciador de Soluções do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c262a-319">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="c262a-320">Você pode implantar um aplicativo de vários contêineres com um único arquivo docker-compose.yml usando o comando `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="c262a-320">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="c262a-321">No entanto, o Visual Studio adiciona um grupo desses arquivos, para que você possa substituir os valores de acordo com o ambiente (desenvolvimento ou produção) e o tipo de execução (lançamento ou depuração).</span><span class="sxs-lookup"><span data-stu-id="c262a-321">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="c262a-322">Essa funcionalidade será explicada nas seções posteriores.</span><span class="sxs-lookup"><span data-stu-id="c262a-322">This capability will be explained in later sections.</span></span>

![Imagem da etapa 5.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="c262a-324">Etapa 5.</span><span class="sxs-lookup"><span data-stu-id="c262a-324">Step 5.</span></span> <span data-ttu-id="c262a-325">Compilar e executar seu aplicativo do Docker</span><span class="sxs-lookup"><span data-stu-id="c262a-325">Build and run your Docker application</span></span>

<span data-ttu-id="c262a-326">Se seu aplicativo tem apenas um contêiner, você pode executá-lo implantando-o no host do Docker (VM ou servidor físico).</span><span class="sxs-lookup"><span data-stu-id="c262a-326">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="c262a-327">No entanto, se seu aplicativo contém vários serviços, você pode implantá-lo como um aplicativo composto, usando um único comando de CLI (docker-compose up), ou com o Visual Studio, que usará esse mesmo comando nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="c262a-327">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="c262a-328">Vamos examinar as diferentes opções.</span><span class="sxs-lookup"><span data-stu-id="c262a-328">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="c262a-329">Opção A: executar um aplicativo de contêiner único</span><span class="sxs-lookup"><span data-stu-id="c262a-329">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="c262a-330">Usando a CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="c262a-330">Using Docker CLI</span></span>

<span data-ttu-id="c262a-331">Você pode executar um contêiner do Docker usando o comando `docker run`, conforme mostrado na Figura 5-9:</span><span class="sxs-lookup"><span data-stu-id="c262a-331">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="c262a-332">O comando acima criará uma instância de contêiner da imagem especificada, cada vez que for executado.</span><span class="sxs-lookup"><span data-stu-id="c262a-332">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="c262a-333">Você pode usar o parâmetro `--name` para dar um nome ao contêiner e, em seguida, usar `docker start {name}` (ou usar a ID do contêiner ou o nome automático) para executar uma instância de contêiner existente.</span><span class="sxs-lookup"><span data-stu-id="c262a-333">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container id or automatic name) to run an existing container instance.</span></span>

![Captura de tela executando um contêiner do Docker usando o comando Docker Run.](./media/docker-app-development-workflow/use-docker-run-command.png)

<span data-ttu-id="c262a-335">**Figura 5-9**.</span><span class="sxs-lookup"><span data-stu-id="c262a-335">**Figure 5-9**.</span></span> <span data-ttu-id="c262a-336">Executando um contêiner do Docker usando o comando docker run</span><span class="sxs-lookup"><span data-stu-id="c262a-336">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="c262a-337">Nesse caso, o comando associa a porta interna 5000 do contêiner à porta 80 do computador host.</span><span class="sxs-lookup"><span data-stu-id="c262a-337">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="c262a-338">Isso significa que o host está escutando na porta 80 e encaminhando para a porta 5000 no contêiner.</span><span class="sxs-lookup"><span data-stu-id="c262a-338">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="c262a-339">O hash mostrado é a ID do contêiner e também recebe um nome legível aleatório quando a opção `--name` não é usada.</span><span class="sxs-lookup"><span data-stu-id="c262a-339">The hash shown is the container id and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="c262a-340">Usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c262a-340">Using Visual Studio</span></span>

<span data-ttu-id="c262a-341">Se ainda não adicionou o suporte ao orquestrador de contêineres, você também poderá executar um aplicativo de contêiner único no Visual Studio pressionando **Ctrl+F5** e usar **F5** para depurar o aplicativo dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="c262a-341">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="c262a-342">O contêiner é executado localmente usando o docker run.</span><span class="sxs-lookup"><span data-stu-id="c262a-342">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="c262a-343">Opção B: executando um aplicativo de vários contêineres</span><span class="sxs-lookup"><span data-stu-id="c262a-343">Option B: Running a multi-container application</span></span>

<span data-ttu-id="c262a-344">Na maioria dos cenários empresariais, um aplicativo do Docker será ser composto de vários serviços, o que significa que você precisará executar um aplicativo de vários contêineres, conforme mostrado na Figura 5-10.</span><span class="sxs-lookup"><span data-stu-id="c262a-344">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![VM com vários contêineres do Docker](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="c262a-346">**Figura 5-10**.</span><span class="sxs-lookup"><span data-stu-id="c262a-346">**Figure 5-10**.</span></span> <span data-ttu-id="c262a-347">VM com contêineres do Docker implantados</span><span class="sxs-lookup"><span data-stu-id="c262a-347">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="c262a-348">Usando a CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="c262a-348">Using Docker CLI</span></span>

<span data-ttu-id="c262a-349">Para executar um aplicativo de vários contêineres com a CLI do Docker, use o comando `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="c262a-349">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="c262a-350">Esse comando usa o arquivo **docker-compose.yml**, que existe no nível da solução, para implantar um aplicativo de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="c262a-350">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="c262a-351">A figura 5-11 mostra os resultados da execução do comando no diretório principal da solução, que contém o arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="c262a-351">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Exibição da tela ao executar o comando docker-compose up](./media/docker-app-development-workflow/results-docker-compose-up.png)

<span data-ttu-id="c262a-353">**Figura 5-11**.</span><span class="sxs-lookup"><span data-stu-id="c262a-353">**Figure 5-11**.</span></span> <span data-ttu-id="c262a-354">Resultados de exemplo ao executar o comando docker-compose up</span><span class="sxs-lookup"><span data-stu-id="c262a-354">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="c262a-355">Depois que o comando docker-compose up é executado, o aplicativo e os contêineres relacionados são implantados no host do Docker, como é mostrado na Figura 5-10.</span><span class="sxs-lookup"><span data-stu-id="c262a-355">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="c262a-356">Usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c262a-356">Using Visual Studio</span></span>

<span data-ttu-id="c262a-357">A execução de um aplicativo de vários contêineres com o Visual Studio 2017 é muito simples.</span><span class="sxs-lookup"><span data-stu-id="c262a-357">Running a multi-container application using Visual Studio 2017 can't get any simpler.</span></span> <span data-ttu-id="c262a-358">Basta pressionar **Ctrl+F5** para executar ou **F5** para depuração, como de costume, configurando o projeto **docker-compose** como o projeto de inicialização.</span><span class="sxs-lookup"><span data-stu-id="c262a-358">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="c262a-359">O Visual Studio trata de toda a configuração necessária, portanto, você pode criar pontos de interrupção, como de costume, e depurar os processos que acabam se tornando independentes em execução em "servidores remotos".</span><span class="sxs-lookup"><span data-stu-id="c262a-359">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", just like that.</span></span>

<span data-ttu-id="c262a-360">Conforme mencionado anteriormente, sempre que você adiciona suporte à solução do Docker a um projeto de uma solução, esse projeto é configurado no arquivo global (nível da solução) docker-compose.yml, o que permite que você execute ou depure toda a solução de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="c262a-360">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="c262a-361">O Visual Studio iniciará um contêiner para cada projeto que tenha suporte habilitado à solução do Docker e executará todas as etapas internas para você (dotnet publish, docker build, etc.).</span><span class="sxs-lookup"><span data-stu-id="c262a-361">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="c262a-362">Se você quiser dar uma olhada na parte chata do trabalho, confira o arquivo:</span><span class="sxs-lookup"><span data-stu-id="c262a-362">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="c262a-363">O ponto importante aqui é que, conforme mostrado na Figura 5-12, há um comando adicional do **Docker**, no Visual Studio 2017, para a ação da tecla F5.</span><span class="sxs-lookup"><span data-stu-id="c262a-363">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="c262a-364">Essa opção permite que você execute ou depure um aplicativo de vários contêineres executando todos os contêineres que estão definidos nos arquivos docker-compose.yml no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="c262a-364">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="c262a-365">A capacidade de depurar soluções de vários contêineres significa que você poderá definir vários pontos de interrupção, cada ponto de interrupção em um projeto (contêiner) diferente e que, durante a depuração no Visual Studio, você vai parar nos pontos de interrupção definidos em diferentes projetos e em execução em diferentes contêineres.</span><span class="sxs-lookup"><span data-stu-id="c262a-365">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Captura de tela da barra de ferramentas de depuração que executa um projeto Docker-Compose.](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

<span data-ttu-id="c262a-367">**Figura 5-12**.</span><span class="sxs-lookup"><span data-stu-id="c262a-367">**Figure 5-12**.</span></span> <span data-ttu-id="c262a-368">Executando aplicativos de vários contêineres no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c262a-368">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c262a-369">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c262a-369">Additional resources</span></span>

- <span data-ttu-id="c262a-370">**Implantar um contêiner ASP.NET em um host remoto do Docker** </span><span class="sxs-lookup"><span data-stu-id="c262a-370">**Deploy an ASP.NET container to a remote Docker host** </span></span>\
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="c262a-371">Uma observação sobre teste e implantação com orquestradores</span><span class="sxs-lookup"><span data-stu-id="c262a-371">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="c262a-372">Os comandos docker-compose up e docker run (ou executar e depurar os contêineres no Visual Studio) são adequados para contêineres de teste em seu ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="c262a-372">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="c262a-373">Mas você não deve usar essa abordagem para implantações de produção, com orquestradores de destino como [Kubernetes](https://kubernetes.io/) ou [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="c262a-373">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="c262a-374">Se você estiver usando o Kubernetes, use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) para organizar os contêineres e [serviços](https://kubernetes.io/docs/concepts/services-networking/service/) para colocá-los em rede.</span><span class="sxs-lookup"><span data-stu-id="c262a-374">If you're using Kubernetes you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="c262a-375">Você também pode usar [implantações](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) para organizar a criação e a modificação de pods.</span><span class="sxs-lookup"><span data-stu-id="c262a-375">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![Imagem da etapa 6.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="c262a-377">Etapa 6.</span><span class="sxs-lookup"><span data-stu-id="c262a-377">Step 6.</span></span> <span data-ttu-id="c262a-378">Testar seu aplicativo do Docker usando o host local do Docker</span><span class="sxs-lookup"><span data-stu-id="c262a-378">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="c262a-379">Esta etapa varia de acordo com o que seu aplicativo está fazendo.</span><span class="sxs-lookup"><span data-stu-id="c262a-379">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="c262a-380">Em um aplicativo Web .NET Core simples implantado como um único contêiner ou serviço, você pode acessar o serviço abrindo um navegador no host do Docker e navegando até o site, conforme mostrado na Figura 5-13.</span><span class="sxs-lookup"><span data-stu-id="c262a-380">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="c262a-381">(Se a configuração do Dockerfile mapear o contêiner para uma porta no host que seja diferente de 80, inclua a porta do host na URL).</span><span class="sxs-lookup"><span data-stu-id="c262a-381">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Captura de tela da resposta de localhost/API/Values.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="c262a-383">**Figura 5-13**.</span><span class="sxs-lookup"><span data-stu-id="c262a-383">**Figure 5-13**.</span></span> <span data-ttu-id="c262a-384">Exemplo de teste do seu aplicativo do Docker localmente usando localhost</span><span class="sxs-lookup"><span data-stu-id="c262a-384">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="c262a-385">Se o localhost não estiver apontando para o IP do host do Docker (por padrão, obrigatório ao usar o Docker CE), use o endereço IP da placa de rede do computador para navegar até o serviço.</span><span class="sxs-lookup"><span data-stu-id="c262a-385">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="c262a-386">Observe que a URL no navegador usa a porta 80 para o exemplo de contêiner específico que está sendo discutido.</span><span class="sxs-lookup"><span data-stu-id="c262a-386">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="c262a-387">No entanto, internamente as solicitações estão sendo redirecionadas para a porta 5000, pois é assim que ele foi implantado com o comando docker run, conforme explicado em uma etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="c262a-387">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="c262a-388">Você também pode testar o aplicativo usando o comando curl no terminal, conforme mostrado na Figura 5-14.</span><span class="sxs-lookup"><span data-stu-id="c262a-388">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="c262a-389">Em uma instalação do Docker no Windows, o IP padrão do host do Docker é sempre 10.0.75.1, além do endereço IP real do computador.</span><span class="sxs-lookup"><span data-stu-id="c262a-389">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Saída do console de obter o http://10.0.75.1/API/values com ondulação.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="c262a-391">**Figura 5-14**.</span><span class="sxs-lookup"><span data-stu-id="c262a-391">**Figure 5-14**.</span></span> <span data-ttu-id="c262a-392">Exemplo de teste do seu aplicativo do Docker localmente usando curl</span><span class="sxs-lookup"><span data-stu-id="c262a-392">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="c262a-393">Testando e depurando contêineres com o Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c262a-393">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="c262a-394">Ao executar e depurar contêineres com o Visual Studio 2017, você depura o aplicativo do .NET de maneira muito parecida como você faria ao executar sem contêineres.</span><span class="sxs-lookup"><span data-stu-id="c262a-394">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="c262a-395">Testando e depurando sem o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c262a-395">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="c262a-396">Se você estiver desenvolvendo por meio da abordagem de editor/CLI, a depuração de contêineres será mais difícil e será melhor fazer a depuração com a geração de rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="c262a-396">If you're developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c262a-397">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c262a-397">Additional resources</span></span>

- <span data-ttu-id="c262a-398">**Depurando aplicativos em um contêiner do Docker local** </span><span class="sxs-lookup"><span data-stu-id="c262a-398">**Debugging apps in a local Docker container** </span></span>\
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="c262a-399">**Steve Lasker. Crie, depure, implante aplicativos ASP.NET Core com o Docker.**</span><span class="sxs-lookup"><span data-stu-id="c262a-399">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="c262a-400">Vídeo.</span><span class="sxs-lookup"><span data-stu-id="c262a-400">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="c262a-401">Fluxo de trabalho simplificado ao desenvolver contêineres com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c262a-401">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="c262a-402">Efetivamente, o fluxo de trabalho ao usar o Visual Studio é muito mais simples do que ao usar a abordagem de editor/CLI.</span><span class="sxs-lookup"><span data-stu-id="c262a-402">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="c262a-403">A maioria das etapas necessárias pelo Docker, relacionadas ao Dockerfile e aos arquivos docker-compose.yml, são ocultas ou simplificadas pelo Visual Studio, conforme mostrado na Figura 5-15.</span><span class="sxs-lookup"><span data-stu-id="c262a-403">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

<span data-ttu-id="c262a-404">:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Diagrama mostrando as cinco etapas simplificadas necessárias para criar um aplicativo.":::</span><span class="sxs-lookup"><span data-stu-id="c262a-404">:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram showing the five simplified steps it takes to create an app.":::</span></span>
<span data-ttu-id="c262a-405">O processo de desenvolvimento para aplicativos Docker: 1-codificar seu aplicativo, 2-gravar Dockerfile/s, 3-criar imagens definidas em Dockerfile/s, 4-(opcional) compor serviços no arquivo Docker-Compose. yml, 5-executar o contêiner ou o aplicativo Docker-Compose, 6-testar seu aplicativo ou seus microserviços, 7- Envie por push para o repositório e repita.</span><span class="sxs-lookup"><span data-stu-id="c262a-405">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="c262a-406">**Figura 5-15**.</span><span class="sxs-lookup"><span data-stu-id="c262a-406">**Figure 5-15**.</span></span> <span data-ttu-id="c262a-407">Fluxo de trabalho simplificado ao desenvolver com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c262a-407">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="c262a-408">Além disso, será necessário executar a etapa 2 (adicionar suporte do Docker aos seus projetos) apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="c262a-408">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="c262a-409">Portanto, o fluxo de trabalho é semelhante às suas tarefas de desenvolvimento regulares, quando utiliza o .NET para qualquer outro desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="c262a-409">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="c262a-410">É necessário saber o que está acontecendo nos bastidores (o processo de build da imagem, quais imagens base você está usando, a implantação de contêineres, etc.) e, às vezes, você também precisará editar o Dockerfile ou o arquivo docker-compose.yml para personalizar comportamentos.</span><span class="sxs-lookup"><span data-stu-id="c262a-410">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="c262a-411">Mas a maior parte do trabalho é bastante simplificada com o uso do Visual Studio, o que o torna muito mais produtivo.</span><span class="sxs-lookup"><span data-stu-id="c262a-411">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c262a-412">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c262a-412">Additional resources</span></span>

- <span data-ttu-id="c262a-413">**Desenvolvimento do Docker no .NET com o Visual Studio 2017** </span><span class="sxs-lookup"><span data-stu-id="c262a-413">**Steve Lasker. .NET Docker Development with Visual Studio 2017** </span></span>\
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="c262a-414">Usando comandos do PowerShell em um DockerFile para configurar contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="c262a-414">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="c262a-415">Os [contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) permitem converter seus aplicativos existentes do Windows em imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker.</span><span class="sxs-lookup"><span data-stu-id="c262a-415">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="c262a-416">Para usar contêineres do Windows, você executa comandos do PowerShell no Dockerfile, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c262a-416">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="c262a-417">Nesse caso, estamos usando uma imagem base do Windows Server Core (a configuração FROM) e instalando IIS com um comando do PowerShell (a configuração RUN).</span><span class="sxs-lookup"><span data-stu-id="c262a-417">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="c262a-418">Da mesma forma, você também pode usar comandos do PowerShell para configurar outros componentes, como ASP.NET 4.x, .NET 4.6 ou qualquer outro software do Windows.</span><span class="sxs-lookup"><span data-stu-id="c262a-418">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="c262a-419">Por exemplo, o seguinte comando, em um Dockerfile, configura o ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="c262a-419">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="c262a-420">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c262a-420">Additional resources</span></span>

- <span data-ttu-id="c262a-421">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="c262a-421">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="c262a-422">Comandos do PowerShell de exemplo a serem executados em Dockerfiles para incluir recursos do Windows.</span><span class="sxs-lookup"><span data-stu-id="c262a-422">Example PowerShell commands to run from dockerfiles to include Windows features.</span></span>\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="c262a-423">[Anterior](index.md)
>[Próximo](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="c262a-423">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
