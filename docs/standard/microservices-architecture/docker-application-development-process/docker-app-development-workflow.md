---
title: Fluxo de trabalho de desenvolvimento para aplicativos de Docker
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Fluxo de trabalho de desenvolvimento para aplicativos de Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5a53aee4261a5a0bfc25b3520c50cf505b84f287
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="1377d-104">Fluxo de trabalho de desenvolvimento para aplicativos de Docker</span><span class="sxs-lookup"><span data-stu-id="1377d-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="1377d-105">O ciclo de vida de desenvolvimento de aplicativo é iniciado no computador de cada desenvolvedor, onde o desenvolvedor códigos de aplicativo usando o seu idioma preferencial e testa-o localmente.</span><span class="sxs-lookup"><span data-stu-id="1377d-105">The application development lifecycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="1377d-106">Não importa qual idioma, framework e plataforma escolhe o desenvolvedor, com esse fluxo de trabalho, o desenvolvedor é sempre desenvolver e testar contêineres do Docker, mas fazê-lo localmente.</span><span class="sxs-lookup"><span data-stu-id="1377d-106">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="1377d-107">Cada contêiner (uma instância de uma imagem do Docker) inclui os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="1377d-107">Each container (an instance of a Docker image) includes the following components:</span></span>

-   <span data-ttu-id="1377d-108">Uma seleção de sistema operacional (por exemplo, uma distribuição de Linux, Windows Nano Server ou Windows Server Core).</span><span class="sxs-lookup"><span data-stu-id="1377d-108">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

-   <span data-ttu-id="1377d-109">Arquivos adicionados pelo desenvolvedor do (binários do aplicativo, etc.).</span><span class="sxs-lookup"><span data-stu-id="1377d-109">Files added by the developer (application binaries, etc.).</span></span>

-   <span data-ttu-id="1377d-110">Informações de configuração (configurações de ambiente e dependências).</span><span class="sxs-lookup"><span data-stu-id="1377d-110">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="1377d-111">Fluxo de trabalho para o desenvolvimento de aplicativos baseados no contêiner do Docker</span><span class="sxs-lookup"><span data-stu-id="1377d-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="1377d-112">Esta seção descreve o *loop interno* fluxo de trabalho de desenvolvimento para aplicativos baseados no contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="1377d-113">O fluxo de trabalho do loop interno significa que ele é não levando em conta o fluxo de trabalho DevOps mais amplo e apenas se concentra em suas tarefas de desenvolvimento no computador do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="1377d-113">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="1377d-114">As etapas iniciais para configurar o ambiente não são incluídas, como aquelas terminar apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="1377d-114">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="1377d-115">Um aplicativo é composto de seus próprios serviços mais bibliotecas adicionais (dependências).</span><span class="sxs-lookup"><span data-stu-id="1377d-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="1377d-116">A seguir estão as etapas básicas normalmente ao criar um aplicativo do Docker, conforme ilustrado na Figura 5-1.</span><span class="sxs-lookup"><span data-stu-id="1377d-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="1377d-117">**Figura 5-1.**</span><span class="sxs-lookup"><span data-stu-id="1377d-117">**Figure 5-1.**</span></span> <span data-ttu-id="1377d-118">Fluxo de trabalho passo a passo para desenvolvimento de aplicativos em contêineres de Docker</span><span class="sxs-lookup"><span data-stu-id="1377d-118">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="1377d-119">Neste guia, esse processo todo é detalhado e cada etapa principal é explicada concentrando-se em um ambiente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1377d-119">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="1377d-120">Quando você estiver usando uma abordagem de desenvolvimento do editor/CLI (por exemplo, código do Visual Studio mais CLI do Docker em macOS ou Windows), você precisa saber a cada etapa, geralmente em mais detalhes do que se você estiver usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1377d-120">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="1377d-121">Para obter mais detalhes sobre como trabalhar em um ambiente de CLI, consulte o livro eletrônico [ciclo de vida do aplicativo de Docker em contêineres com ferramentas e Microsoft Platforms](http://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="1377d-121">For more details about working in a CLI environment, refer to the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="1377d-122">Quando você estiver usando o Visual Studio 2015 ou Visual Studio de 2017, muitas dessas etapas serão manipuladas para você, o que melhora significativamente a produtividade.</span><span class="sxs-lookup"><span data-stu-id="1377d-122">When you are using Visual Studio 2015 or Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="1377d-123">Isso é especialmente verdadeiro quando você estiver usando o Visual Studio de 2017 e contêiner vários aplicativos de destino.</span><span class="sxs-lookup"><span data-stu-id="1377d-123">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="1377d-124">Por exemplo, com apenas um clique do mouse, o Visual Studio adiciona o arquivo Dockerfile e docker compose.yml seus projetos com a configuração do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1377d-124">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="1377d-125">Quando você executa o aplicativo no Visual Studio, ele cria a imagem do Docker e executa o aplicativo de multi-container diretamente no Docker; até mesmo permite depurar vários contêineres de uma vez.</span><span class="sxs-lookup"><span data-stu-id="1377d-125">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="1377d-126">Esses recursos melhora a velocidade de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1377d-126">These features will boost your development speed.</span></span>

<span data-ttu-id="1377d-127">No entanto, apenas porque o Visual Studio torna essas etapas automática não significa que você não precisa saber o que está acontecendo em sob com o Docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-127">However, just because Visual Studio makes those steps automatic does not mean that you do not need to know what is going on underneath with Docker.</span></span> <span data-ttu-id="1377d-128">Portanto, na orientação a seguir, estamos detalhes de cada etapa.</span><span class="sxs-lookup"><span data-stu-id="1377d-128">Therefore, in the guidance that follows, we detail every step.</span></span>

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="1377d-129">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="1377d-129">Step 1.</span></span> <span data-ttu-id="1377d-130">Iniciar a codificação e criar o aplicativo inicial ou a linha de base de serviço</span><span class="sxs-lookup"><span data-stu-id="1377d-130">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="1377d-131">Desenvolvendo um aplicativo de Docker é semelhante à forma como desenvolver um aplicativo sem Docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-131">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="1377d-132">A diferença é que durante o desenvolvimento de Docker, você implantar e testar o aplicativo ou os serviços em execução dentro de contêineres do Docker em seu ambiente local.</span><span class="sxs-lookup"><span data-stu-id="1377d-132">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="1377d-133">O contêiner pode ser um contêiner do Linux ou um contêiner do Windows.</span><span class="sxs-lookup"><span data-stu-id="1377d-133">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="1377d-134">Configurar seu ambiente local com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1377d-134">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="1377d-135">Para começar, verifique se você tem [Docker Community Edition (CE)](https://www.docker.com/community-edition) para o Windows instalado, conforme explicado nas instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="1377d-135">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="1377d-136">Introdução ao Docker CE para Windows</span><span class="sxs-lookup"><span data-stu-id="1377d-136">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="1377d-137">Além disso, você precisará Visual Studio de 2017 instalado.</span><span class="sxs-lookup"><span data-stu-id="1377d-137">In addition, you will need Visual Studio 2017 installed.</span></span> <span data-ttu-id="1377d-138">Isso é preferível Visual Studio 2015 com o Visual Studio Tools para Docker suplemento, porque o Visual Studio de 2017 tem mais suporte avançado para Docker, como suporte para depuração de contêineres.</span><span class="sxs-lookup"><span data-stu-id="1377d-138">This is preferred over Visual Studio 2015 with the Visual Studio Tools for Docker add-in, because Visual Studio 2017 has more advanced support for Docker, like support for debugging containers.</span></span> <span data-ttu-id="1377d-139">2017 do Visual Studio inclui as ferramentas do Docker, se você tiver selecionado o **.NET Core e o Docker** cargas de trabalho durante a instalação, conforme mostrado na Figura 5-2.</span><span class="sxs-lookup"><span data-stu-id="1377d-139">Visual Studio 2017 includes the tooling for Docker if you selected the **.NET Core and Docker** workload during installation, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="1377d-140">**Figura 5-2**.</span><span class="sxs-lookup"><span data-stu-id="1377d-140">**Figure 5-2**.</span></span> <span data-ttu-id="1377d-141">Selecionando o **.NET Core e o Docker** cargas de trabalho durante a instalação do Visual Studio de 2017</span><span class="sxs-lookup"><span data-stu-id="1377d-141">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="1377d-142">Você pode iniciar a codificação do seu aplicativo no .NET simples (normalmente no núcleo do .NET se você estiver planejando usar contêineres) mesmo antes de habilitar Docker em seu aplicativo e implantação e teste no Docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-142">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="1377d-143">No entanto, é recomendável que você começa a trabalhar no Docker assim que possível, porque que será o ambiente real e os problemas podem ser descobertos assim que possível.</span><span class="sxs-lookup"><span data-stu-id="1377d-143">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="1377d-144">Isso é recomendável porque o Visual Studio facilita a trabalhar com o Docker que quase parece transparente — o melhor exemplo durante a depuração de contêiner de vários aplicativos do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1377d-144">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1377d-145">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1377d-145">Additional resources</span></span>

-   <span data-ttu-id="1377d-146">**Introdução ao Docker CE para Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span><span class="sxs-lookup"><span data-stu-id="1377d-146">**Get started with Docker CE for Windows**
[*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span></span>

-   <span data-ttu-id="1377d-147">**Visual Studio de 2017**
    [*https://www.visualstudio.com/vs/visual-studio-2017/*](https://www.visualstudio.com/vs/visual-studio-2017/)</span><span class="sxs-lookup"><span data-stu-id="1377d-147">**Visual Studio 2017**
[*https://www.visualstudio.com/vs/visual-studio-2017/*](https://www.visualstudio.com/vs/visual-studio-2017/)</span></span>

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="1377d-148">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="1377d-148">Step 2.</span></span> <span data-ttu-id="1377d-149">Crie um Dockerfile relacionado a uma imagem de base existente do .NET</span><span class="sxs-lookup"><span data-stu-id="1377d-149">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="1377d-150">Você precisa de um Dockerfile para cada imagem personalizada que você deseja criar; Você também precisa de um Dockerfile para cada contêiner a ser implantado, se você implantar automaticamente do Visual Studio ou manualmente usando a CLI do Docker (execução de docker e o docker-compor comandos).</span><span class="sxs-lookup"><span data-stu-id="1377d-150">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="1377d-151">Se seu aplicativo contém um único serviço personalizado, é necessário um Dockerfile único.</span><span class="sxs-lookup"><span data-stu-id="1377d-151">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="1377d-152">Se seu aplicativo contém vários serviços (como em uma arquitetura microservices), será necessário um Dockerfile para cada serviço.</span><span class="sxs-lookup"><span data-stu-id="1377d-152">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="1377d-153">O Dockerfile é colocado na pasta raiz do seu aplicativo ou serviço.</span><span class="sxs-lookup"><span data-stu-id="1377d-153">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="1377d-154">Ele contém os comandos que indicam como configurar e executar seu aplicativo ou serviço em um contêiner de Docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-154">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="1377d-155">Manualmente, você pode criar um Dockerfile no código e adicioná-lo ao seu projeto junto com suas dependências do .NET.</span><span class="sxs-lookup"><span data-stu-id="1377d-155">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="1377d-156">Com o Visual Studio e suas ferramentas para Docker, esta tarefa requer apenas alguns cliques do mouse.</span><span class="sxs-lookup"><span data-stu-id="1377d-156">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="1377d-157">Quando você cria um novo projeto no Visual Studio de 2017, há uma opção chamada **suporte habilitar contêiner (Docker)**, conforme mostrado na Figura 5-3.</span><span class="sxs-lookup"><span data-stu-id="1377d-157">When you create a new project in Visual Studio 2017, there is an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![](./media/image5.png)

<span data-ttu-id="1377d-158">**Figura 5-3**.</span><span class="sxs-lookup"><span data-stu-id="1377d-158">**Figure 5-3**.</span></span> <span data-ttu-id="1377d-159">Habilitar o suporte do Docker ao criar um novo projeto no Visual Studio de 2017</span><span class="sxs-lookup"><span data-stu-id="1377d-159">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="1377d-160">Você também pode habilitar o suporte de Docker em um projeto novo ou existente clicando duas vezes o arquivo de projeto no Visual Studio e selecionando a opção **Docker Adicionar projeto suporte**, conforme mostrado na Figura 5-4.</span><span class="sxs-lookup"><span data-stu-id="1377d-160">You can also enable Docker support on a new or existing project by right-clicking your project file in Visual Studio and selecting the option **Add-Docker Project Support**, as shown in Figure 5-4.</span></span>

![](./media/image6.png)

<span data-ttu-id="1377d-161">**Figura 5-4**.</span><span class="sxs-lookup"><span data-stu-id="1377d-161">**Figure 5-4**.</span></span> <span data-ttu-id="1377d-162">Habilitar o suporte de Docker em um projeto existente do Visual Studio de 2017</span><span class="sxs-lookup"><span data-stu-id="1377d-162">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="1377d-163">Essa ação em um projeto (como um aplicativo Web ASP.NET ou um serviço de API da Web) adiciona um Dockerfile para o projeto com a configuração necessária.</span><span class="sxs-lookup"><span data-stu-id="1377d-163">This action on a project (like an ASP.NET Web application or Web API service) adds a Dockerfile to the project with the required configuration.</span></span> <span data-ttu-id="1377d-164">Ele também adiciona um arquivo de docker compose.yml de toda a solução.</span><span class="sxs-lookup"><span data-stu-id="1377d-164">It also adds a docker-compose.yml file for the whole solution.</span></span> <span data-ttu-id="1377d-165">As seções a seguir, descrevemos as informações que vão para cada um desses arquivos.</span><span class="sxs-lookup"><span data-stu-id="1377d-165">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="1377d-166">O Visual Studio pode executar esse trabalho para você, mas é útil entender o que acontece em um Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="1377d-166">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="1377d-167">Opção a: Criando um projeto usando uma imagem do Docker .NET oficial existente</span><span class="sxs-lookup"><span data-stu-id="1377d-167">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="1377d-168">Você normalmente cria uma imagem personalizada para seu contêiner na parte superior de uma imagem de base que você pode obter de um repositório oficial no [Hub do Docker](https://hub.docker.com/) registro.</span><span class="sxs-lookup"><span data-stu-id="1377d-168">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="1377d-169">É exatamente o que acontece nos bastidores, quando você habilitar o suporte de Docker no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1377d-169">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="1377d-170">O Dockerfile usará uma imagem aspnetcore existente.</span><span class="sxs-lookup"><span data-stu-id="1377d-170">Your Dockerfile will use an existing aspnetcore image.</span></span>

<span data-ttu-id="1377d-171">Anteriormente, explicamos quais imagens do Docker e repositórios, você pode usar, dependendo da estrutura e o sistema operacional que você escolheu.</span><span class="sxs-lookup"><span data-stu-id="1377d-171">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="1377d-172">Por exemplo, se você quiser usar o ASP.NET Core (Linux ou Windows), a imagem a ser usada é microsoft / aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="1377d-172">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="1377d-173">Por isso, basta especificar qual imagem base do Docker será usado para o contêiner.</span><span class="sxs-lookup"><span data-stu-id="1377d-173">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="1377d-174">Você pode fazer isso com a adição da microsoft / aspnetcore:2.0 para o Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="1377d-174">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="1377d-175">Isso será executado automaticamente pelo Visual Studio, mas se você atualizar a versão, atualize esse valor.</span><span class="sxs-lookup"><span data-stu-id="1377d-175">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="1377d-176">Usar um repositório de imagem de .NET oficial do Hub do Docker com um número de versão garante que os mesmos recursos de idioma estão disponíveis em todos os computadores (incluindo o desenvolvimento, teste e produção).</span><span class="sxs-lookup"><span data-stu-id="1377d-176">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="1377d-177">O exemplo a seguir mostra um exemplo de Dockerfile para um contêiner do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1377d-177">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="1377d-178">Nesse caso, o contêiner se baseia na versão 2.0 da imagem do ASP.NET Core Docker oficial (Multi-arch para Linux e Windows).</span><span class="sxs-lookup"><span data-stu-id="1377d-178">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="1377d-179">Essa é a configuração `FROM microsoft/aspnetcore:2.0`.</span><span class="sxs-lookup"><span data-stu-id="1377d-179">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="1377d-180">(Para obter mais detalhes sobre essa imagem base, consulte o [imagem do ASP.NET Core Docker](https://hub.docker.com/r/microsoft/aspnetcore/) página e o [.NET Core Docker imagem](https://hub.docker.com/r/microsoft/dotnet/) página.) No Dockerfile, você também precisa instruem o Docker para escutar na porta TCP que você usará em tempo de execução (nesse caso, a porta 80, conforme configurado com a configuração de EXPOR).</span><span class="sxs-lookup"><span data-stu-id="1377d-180">(For further details about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="1377d-181">Você pode especificar configurações adicionais no Dockerfile, dependendo do idioma e do framework que você está usando.</span><span class="sxs-lookup"><span data-stu-id="1377d-181">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="1377d-182">Por exemplo, a linha do ponto de entrada com \["dotnet", "MySingleContainerWebApp.dll"\] informa Docker para executar um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1377d-182">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="1377d-183">Se você estiver usando o SDK e .NET Core CLI (dotnet CLI) para compilar e executar o aplicativo do .NET, essa configuração deve ser diferente.</span><span class="sxs-lookup"><span data-stu-id="1377d-183">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="1377d-184">O resultado final é que a linha do ponto de entrada e outras configurações serão diferentes dependendo do idioma e plataforma que você escolhe para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1377d-184">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1377d-185">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1377d-185">Additional resources</span></span>

-   <span data-ttu-id="1377d-186">**Criação de imagens do Docker para aplicativos do .NET Core**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images)</span><span class="sxs-lookup"><span data-stu-id="1377d-186">**Building Docker Images for .NET Core Applications**
[*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images)</span></span>

-   <span data-ttu-id="1377d-187">**Criar sua própria imagem**.</span><span class="sxs-lookup"><span data-stu-id="1377d-187">**Build your own image**.</span></span> <span data-ttu-id="1377d-188">Na documentação oficial do Docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-188">In the official Docker documentation.</span></span>
    [<span data-ttu-id="1377d-189">*https://docs.docker.com/Engine/Tutorials/dockerimages/*</span><span class="sxs-lookup"><span data-stu-id="1377d-189">*https://docs.docker.com/engine/tutorials/dockerimages/*</span></span>](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="1377d-190">Usando repositórios de arch várias imagens</span><span class="sxs-lookup"><span data-stu-id="1377d-190">Using multi-arch image repositories</span></span>

<span data-ttu-id="1377d-191">Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="1377d-191">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="1377d-192">Esse recurso permite que fornecedores como a Microsoft (criadores de imagem de base) criar um único repositório para abranger várias plataformas (ou seja, Linux e Windows).</span><span class="sxs-lookup"><span data-stu-id="1377d-192">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="1377d-193">Por exemplo, o [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repositório disponível no registro do Hub do Docker fornece suporte para Linux e Windows Nano Server usando o mesmo nome de repositório.</span><span class="sxs-lookup"><span data-stu-id="1377d-193">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="1377d-194">Se você especificar uma marca, direcionar uma plataforma que é explícita como nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="1377d-194">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

-   <span data-ttu-id="1377d-195">**Microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="1377d-195">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux 

-   <span data-ttu-id="1377d-196">**Microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="1377d-196">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="1377d-197">Mas e isso é novo desde meados de 2017, se você especificar o mesmo nome de imagem, mesmo com a mesma marca, as novas imagens de várias arch (como a imagem de aspnetcore que dá suporte a vários arch) usará a versão do Windows ou do Linux dependendo do host do Docker sistema operacional você está implantando , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1377d-197">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

-   <span data-ttu-id="1377d-198">**Microsoft / aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="1377d-198">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="1377d-199">Dessa forma, quando você efetuar o pull de uma imagem de um host do Windows, ele obterá a variante do Windows e extrair o mesmo nome da imagem de um host Linux obterá a variante de Linux.</span><span class="sxs-lookup"><span data-stu-id="1377d-199">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="1377d-200">Opção b: Criando a imagem base do zero</span><span class="sxs-lookup"><span data-stu-id="1377d-200">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="1377d-201">Você pode criar sua própria imagem base do Docker do zero.</span><span class="sxs-lookup"><span data-stu-id="1377d-201">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="1377d-202">Esse cenário não é recomendado para alguém que está iniciando com o Docker, mas se você deseja definir os bits específicos de sua própria imagem base, você pode fazer isso.</span><span class="sxs-lookup"><span data-stu-id="1377d-202">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1377d-203">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1377d-203">Additional resources</span></span>

-   <span data-ttu-id="1377d-204">**Arch várias imagens de .NET Core**.</span><span class="sxs-lookup"><span data-stu-id="1377d-204">**Multi-arch .NET Core images**.</span></span>
<span data-ttu-id="1377d-205">https://GitHub.com/dotnet/Announcements/issues/14</span><span class="sxs-lookup"><span data-stu-id="1377d-205">https://github.com/dotnet/announcements/issues/14</span></span> 
-   <span data-ttu-id="1377d-206">**Criar uma imagem de base**.</span><span class="sxs-lookup"><span data-stu-id="1377d-206">**Create a base image**.</span></span> <span data-ttu-id="1377d-207">Documentação oficial do Docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-207">Official Docker documentation.</span></span>
    [<span data-ttu-id="1377d-208">*https://docs.docker.com/Engine/UserGuide/eng-Image/BaseImages/*</span><span class="sxs-lookup"><span data-stu-id="1377d-208">*https://docs.docker.com/engine/userguide/eng-image/baseimages/*</span></span>](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="1377d-209">Etapa 3.</span><span class="sxs-lookup"><span data-stu-id="1377d-209">Step 3.</span></span> <span data-ttu-id="1377d-210">Criar imagens personalizadas do Docker e inserir seu aplicativo ou serviço neles</span><span class="sxs-lookup"><span data-stu-id="1377d-210">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="1377d-211">Para cada serviço em seu aplicativo, você precisa criar uma imagem de relacionados.</span><span class="sxs-lookup"><span data-stu-id="1377d-211">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="1377d-212">Se seu aplicativo é composto de um único serviço ou aplicativo web, você precisa apenas uma única imagem.</span><span class="sxs-lookup"><span data-stu-id="1377d-212">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="1377d-213">Observe que as imagens do Docker são criadas automaticamente para você no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1377d-213">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="1377d-214">As etapas a seguir apenas são necessários para o fluxo de trabalho do editor/CLI e explicadas para fins de esclarecimento sobre o que acontece abaixo.</span><span class="sxs-lookup"><span data-stu-id="1377d-214">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="1377d-215">Você, como desenvolvedor, precisa para desenvolver e testar localmente até que você enviar por push uma concluído recurso ou altere para o sistema de controle de origem (por exemplo, para GitHub).</span><span class="sxs-lookup"><span data-stu-id="1377d-215">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="1377d-216">Isso significa que você precisa criar as imagens do Docker e implantar contêineres em um host Docker local (Windows ou Linux VM) e executar, testar e depurar em relação a esses contêineres locais.</span><span class="sxs-lookup"><span data-stu-id="1377d-216">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="1377d-217">Para criar uma imagem personalizada no seu ambiente local usando a CLI do Docker e o Dockerfile, você pode usar o comando de build do docker, como na Figura 5-5.</span><span class="sxs-lookup"><span data-stu-id="1377d-217">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![](./media/image8.png)

<span data-ttu-id="1377d-218">**Figura 5-5**.</span><span class="sxs-lookup"><span data-stu-id="1377d-218">**Figure 5-5**.</span></span> <span data-ttu-id="1377d-219">Criar uma imagem personalizada do Docker</span><span class="sxs-lookup"><span data-stu-id="1377d-219">Creating a custom Docker image</span></span>

<span data-ttu-id="1377d-220">Opcionalmente, em vez de executar diretamente o build do docker da pasta do projeto, primeiro você pode gerar uma pasta de implantação com as bibliotecas necessárias do .NET e binários executando dotnet publicarem e, em seguida, usam o comando de build do docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-220">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="1377d-221">Isso criará uma imagem do Docker com o nome cesardl/netcore-webapi-microsserviço-docker: primeiro.</span><span class="sxs-lookup"><span data-stu-id="1377d-221">This will create a Docker image with the name cesardl/netcore-webapi-microservice-docker:first.</span></span> <span data-ttu-id="1377d-222">Nesse caso,: primeiro é uma marca que representa uma versão específica.</span><span class="sxs-lookup"><span data-stu-id="1377d-222">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="1377d-223">Você pode repetir esta etapa para cada imagem personalizada, que você precisa criar seu aplicativo composto do Docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-223">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="1377d-224">Quando um aplicativo é feito de vários contêineres (isto é, é um aplicativo de contêiner vários), você também pode usar a compor docker backup – de comando de compilação para compilar todas as imagens relacionadas com um único comando usando os metadados expostos no relacionado arquivos de docker compose.yml.</span><span class="sxs-lookup"><span data-stu-id="1377d-224">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="1377d-225">Você pode encontrar as imagens existentes no seu repositório local usando o docker imagens comando, conforme mostrado na Figura 5-6.</span><span class="sxs-lookup"><span data-stu-id="1377d-225">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![](./media/image9.png)

<span data-ttu-id="1377d-226">**Figura 5-6.**</span><span class="sxs-lookup"><span data-stu-id="1377d-226">**Figure 5-6.**</span></span> <span data-ttu-id="1377d-227">Exibindo imagens existentes usando o comando de imagens do docker</span><span class="sxs-lookup"><span data-stu-id="1377d-227">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="1377d-228">Criação de imagens do Docker com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1377d-228">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="1377d-229">Quando você estiver usando o Visual Studio para criar um projeto com suporte do Docker, você não criar explicitamente uma imagem.</span><span class="sxs-lookup"><span data-stu-id="1377d-229">When you are using Visual Studio to create a project with Docker support, you do not explicitly create an image.</span></span> <span data-ttu-id="1377d-230">Em vez disso, a imagem é criada para você quando você pressiona F5 e executar o aplicativo dockerized ou serviço.</span><span class="sxs-lookup"><span data-stu-id="1377d-230">Instead, the image is created for you when you press F5 and run the dockerized application or service.</span></span> <span data-ttu-id="1377d-231">Esta etapa é automática no Visual Studio e você não verá ele ocorrer, mas é importante que você sabe o que está acontecendo em sob.</span><span class="sxs-lookup"><span data-stu-id="1377d-231">This step is automatic in Visual Studio, and you will not see it happen, but it is important that you know what is going on underneath.</span></span>

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="1377d-232">Etapa 4.</span><span class="sxs-lookup"><span data-stu-id="1377d-232">Step 4.</span></span> <span data-ttu-id="1377d-233">Definir os serviços no docker compose.yml ao compilar um aplicativo de multi-contêiner de Docker</span><span class="sxs-lookup"><span data-stu-id="1377d-233">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="1377d-234">O [docker compose.yml](https://docs.docker.com/compose/compose-file/) arquivo permite que você defina um conjunto de serviços relacionados a ser implantado como um aplicativo composto com comandos de implantação.</span><span class="sxs-lookup"><span data-stu-id="1377d-234">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="1377d-235">Para usar um arquivo de docker compose.yml, você precisa criar o arquivo em seu principal ou a pasta de solução raiz, com conteúdo semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1377d-235">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="1377d-236">Observe que esse arquivo compose.yml docker é uma versão simplificada e mesclada.</span><span class="sxs-lookup"><span data-stu-id="1377d-236">Note that this docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="1377d-237">Ele contém dados de configuração estática para cada contêiner (como o nome da imagem personalizada), que se aplica sempre, além de informações de configuração que podem depender do ambiente de implantação, como a cadeia de caracteres de conexão.</span><span class="sxs-lookup"><span data-stu-id="1377d-237">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="1377d-238">Nas próximas seções, você aprenderá como você pode dividir a configuração do docker compose.yml em vários compor docker arquivos e valores de substituição, dependendo do tipo de ambiente e a execução (debug ou release).</span><span class="sxs-lookup"><span data-stu-id="1377d-238">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="1377d-239">O exemplo de arquivo de docker compose.yml define cinco serviços: o serviço de webmvc (um aplicativo web), dois microservices (catalog.api e ordering.api) e contêiner de fonte dados, sql.data, com base no SQL Server para Linux em execução como um contêiner.</span><span class="sxs-lookup"><span data-stu-id="1377d-239">The docker-compose.yml file example defines five services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="1377d-240">Cada serviço é implantado como um contêiner para que uma imagem do Docker é necessária para cada um.</span><span class="sxs-lookup"><span data-stu-id="1377d-240">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="1377d-241">O arquivo de docker compose.yml especifica não apenas quais contêineres estão sendo usados, mas como eles são configurados individualmente.</span><span class="sxs-lookup"><span data-stu-id="1377d-241">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="1377d-242">Por exemplo, webmvc contêiner definição no arquivo .yml:</span><span class="sxs-lookup"><span data-stu-id="1377d-242">For instance, the webmvc container definition in the .yml file:</span></span>

-   <span data-ttu-id="1377d-243">Usa um eshop pré-criado / imagem da web: mais recente.</span><span class="sxs-lookup"><span data-stu-id="1377d-243">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="1377d-244">No entanto, você também pode definir a imagem a ser criado como parte da compor docker execução com uma configuração adicional com base em uma compilação: seção no arquivo docker-compose.</span><span class="sxs-lookup"><span data-stu-id="1377d-244">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

-   <span data-ttu-id="1377d-245">Inicializa as duas variáveis de ambiente (URL do catálogo e OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="1377d-245">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

-   <span data-ttu-id="1377d-246">Encaminha a exposto a porta 80 no contêiner para a porta 80 externa no computador host.</span><span class="sxs-lookup"><span data-stu-id="1377d-246">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

-   <span data-ttu-id="1377d-247">Vincula o aplicativo web para o catálogo e a ordenação de serviço com o depende\_na configuração.</span><span class="sxs-lookup"><span data-stu-id="1377d-247">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="1377d-248">Isso faz com que o serviço aguardar até que esses serviços são iniciados.</span><span class="sxs-lookup"><span data-stu-id="1377d-248">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="1377d-249">Vamos revisitar o arquivo de docker compose.yml em uma seção posterior quando abordaremos como implementar microservices e contêiner vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1377d-249">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="1377d-250">Trabalhando com o docker-compose.yml no Visual Studio de 2017</span><span class="sxs-lookup"><span data-stu-id="1377d-250">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="1377d-251">Quando você adiciona suporte de solução de Docker para um projeto de serviço em uma solução do Visual Studio, conforme mostrado na Figura 5-7, o Visual Studio adiciona um Dockerfile ao seu projeto, e ele adiciona uma seção de serviço (projeto) em sua solução com os arquivos de docker compose.yml.</span><span class="sxs-lookup"><span data-stu-id="1377d-251">When you add Docker solution support to a service project in a Visual Studio solution, as shown in Figure 5-7, Visual Studio adds a Dockerfile to your project, and it adds a service section (project) in your solution with the docker-compose.yml files.</span></span> <span data-ttu-id="1377d-252">É uma maneira fácil de iniciar a composição de sua solução de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="1377d-252">It is an easy way to start composing your multiple-container solution.</span></span> <span data-ttu-id="1377d-253">Em seguida, você pode abrir os arquivos de docker compose.yml e atualizá-los com recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="1377d-253">You can then open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image6.png)

<span data-ttu-id="1377d-254">**Figura 5-7**.</span><span class="sxs-lookup"><span data-stu-id="1377d-254">**Figure 5-7**.</span></span> <span data-ttu-id="1377d-255">Adicionando suporte de Docker no Visual Studio de 2017 clicando em um projeto do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1377d-255">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="1377d-256">Adicionando suporte de Docker no Visual Studio não apenas adiciona o Dockerfile ao seu projeto, mas adiciona as informações de configuração em vários arquivos de docker-compose.yml globais que são definidos no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="1377d-256">Adding Docker support in Visual Studio not only adds the Dockerfile to your project, but adds the configuration information to several global docker-compose.yml files that are set at the solution level.</span></span>

<span data-ttu-id="1377d-257">Depois de adicionar suporte de Docker para sua solução no Visual Studio, você também verá um novo nó (no arquivo de projeto docker compose.dcproj) no Gerenciador de soluções que contém os arquivos de inclusão docker-compose.yml, conforme mostrado na Figura 5-8.</span><span class="sxs-lookup"><span data-stu-id="1377d-257">After you add Docker support to your solution in Visual Studio, you will also see a new node (in the docker-compose.dcproj project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![](./media/image11.PNG)

<span data-ttu-id="1377d-258">**Figura 5-8**.</span><span class="sxs-lookup"><span data-stu-id="1377d-258">**Figure 5-8**.</span></span> <span data-ttu-id="1377d-259">O **compor docker** adicionado no Gerenciador de soluções do Visual Studio 2017 do nó de árvore</span><span class="sxs-lookup"><span data-stu-id="1377d-259">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="1377d-260">Você pode implantar um aplicativo de contêiner vários com um arquivo único docker-compose.yml usando o docker-compor o comando.</span><span class="sxs-lookup"><span data-stu-id="1377d-260">You could deploy a multi-container application with a single docker-compose.yml file by using the docker-compose up command.</span></span> <span data-ttu-id="1377d-261">No entanto, o Visual Studio adiciona um grupo de-los para que você pode substituir valores dependendo do ambiente (desenvolvimento e produção) e a execução de tipo (versão versus depuração).</span><span class="sxs-lookup"><span data-stu-id="1377d-261">However, Visual Studio adds a group of them so you can override values depending on the environment (development versus production) and execution type (release versus debug).</span></span> <span data-ttu-id="1377d-262">Esse recurso será explicado nas seções posteriores.</span><span class="sxs-lookup"><span data-stu-id="1377d-262">This capability will be explained in later sections.</span></span>

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="1377d-263">Etapa 5.</span><span class="sxs-lookup"><span data-stu-id="1377d-263">Step 5.</span></span> <span data-ttu-id="1377d-264">Compilar e executar seu aplicativo de Docker</span><span class="sxs-lookup"><span data-stu-id="1377d-264">Build and run your Docker application</span></span>

<span data-ttu-id="1377d-265">Se seu aplicativo tiver apenas um único contêiner, você pode executá-lo, implantando-a para o host do Docker (VM ou servidor físico).</span><span class="sxs-lookup"><span data-stu-id="1377d-265">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="1377d-266">No entanto, se seu aplicativo contém vários serviços, você pode implantá-lo como um aplicativo composto, usando um único comando CLI (docker-compor backup), ou com o Visual Studio, que usará esse comando nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="1377d-266">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="1377d-267">Vamos examinar as diferentes opções.</span><span class="sxs-lookup"><span data-stu-id="1377d-267">Let’s look at the different options.</span></span>

### <a name="option-a-running-a-single-container-with-docker-cli"></a><span data-ttu-id="1377d-268">Opção a: executando um único contêiner com Docker CLI</span><span class="sxs-lookup"><span data-stu-id="1377d-268">Option A: Running a single-container with Docker CLI</span></span>

<span data-ttu-id="1377d-269">Você pode executar um contêiner do Docker usando o comando docker run, como na Figura 5-9:</span><span class="sxs-lookup"><span data-stu-id="1377d-269">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

<span data-ttu-id="1377d-270">**Figura 5-9**.</span><span class="sxs-lookup"><span data-stu-id="1377d-270">**Figure 5-9**.</span></span> <span data-ttu-id="1377d-271">Executando um contêiner do Docker usando o comando docker run</span><span class="sxs-lookup"><span data-stu-id="1377d-271">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="1377d-272">Nesse caso, o comando associa a porta interna 5000 do contêiner para a porta 80 da máquina de host.</span><span class="sxs-lookup"><span data-stu-id="1377d-272">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="1377d-273">Isso significa que o host está escutando na porta 80 e encaminhamento de porta 5000 no contêiner.</span><span class="sxs-lookup"><span data-stu-id="1377d-273">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="1377d-274">Opção b: executando um aplicativo de contêiner de vários</span><span class="sxs-lookup"><span data-stu-id="1377d-274">Option B: Running a multi-container application</span></span>

<span data-ttu-id="1377d-275">Na maioria dos cenários de empresa, um aplicativo de Docker será ser composto de vários serviços, que significa que você precisa executar um aplicativo de multi-container, conforme mostrado na Figura 5-10.</span><span class="sxs-lookup"><span data-stu-id="1377d-275">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![](./media/image14.png)

<span data-ttu-id="1377d-276">**Figura 5-10**.</span><span class="sxs-lookup"><span data-stu-id="1377d-276">**Figure 5-10**.</span></span> <span data-ttu-id="1377d-277">VM com contêineres do Docker implantado</span><span class="sxs-lookup"><span data-stu-id="1377d-277">VM with Docker containers deployed</span></span>

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a><span data-ttu-id="1377d-278">Executando um aplicativo de contêiner vários da CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="1377d-278">Running a multi-container application with the Docker CLI</span></span>

<span data-ttu-id="1377d-279">Para executar um aplicativo de contêiner vários da CLI do Docker, você pode executar o docker-compor o comando.</span><span class="sxs-lookup"><span data-stu-id="1377d-279">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="1377d-280">Este arquivo de usa docker-compose.yml de comando que você tem no nível da solução para implantar um aplicativo de contêiner de vários.</span><span class="sxs-lookup"><span data-stu-id="1377d-280">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="1377d-281">Figura 5-11 mostra os resultados ao executar o comando do diretório de projeto principal, que contém o arquivo compose.yml docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-281">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![](./media/image15.png)

<span data-ttu-id="1377d-282">**Figura 5-11**.</span><span class="sxs-lookup"><span data-stu-id="1377d-282">**Figure 5-11**.</span></span> <span data-ttu-id="1377d-283">Exemplo de resultados ao executar o docker-compor o comando</span><span class="sxs-lookup"><span data-stu-id="1377d-283">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="1377d-284">Após o docker-compor é executado, o comando, o aplicativo e seus contêineres relacionados são implantados em seu host do Docker, conforme ilustrado na Figura 5-10 de representação de VM.</span><span class="sxs-lookup"><span data-stu-id="1377d-284">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as illustrated in the VM representation in Figure 5-10.</span></span>

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a><span data-ttu-id="1377d-285">Executando e depurando um aplicativo de multi-contêiner com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1377d-285">Running and debugging a multi-container application with Visual Studio</span></span> 

<span data-ttu-id="1377d-286">Executando um aplicativo de multi-contêiner usando o Visual Studio de 2017 não é possível obter mais simples.</span><span class="sxs-lookup"><span data-stu-id="1377d-286">Running a multi-container application using Visual Studio 2017 cannot get simpler.</span></span> <span data-ttu-id="1377d-287">Você não pode executar o aplicativo de multi-contêiner só, mas é possível depurar todos os seus contêineres diretamente do Visual Studio, definindo pontos de interrupção regulares.</span><span class="sxs-lookup"><span data-stu-id="1377d-287">You can not only run the multi-container application, but you are able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="1377d-288">Conforme mencionado anteriormente, cada vez que você adicionar suporte de solução de Docker para um projeto em uma solução, projeto está configurado no arquivo global (nível de solução) docker-compose.yml, que permite que você executar ou depurar a solução completa de uma vez.</span><span class="sxs-lookup"><span data-stu-id="1377d-288">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="1377d-289">Visual Studio iniciar um contêiner para cada projeto que tem suporte a soluções Docker habilitado e executar todas as etapas internas para você (dotnet publicar, build do docker, etc.).</span><span class="sxs-lookup"><span data-stu-id="1377d-289">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="1377d-290">O ponto importante aqui é que, conforme mostrado na Figura 5-12, no Visual Studio de 2017 há adicional **Docker** comando para a ação de chave F5.</span><span class="sxs-lookup"><span data-stu-id="1377d-290">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="1377d-291">Essa opção permite a você executar ou depurar um aplicativo de contêiner vários executando todos os contêineres que são definidos nos arquivos de docker compose.yml no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="1377d-291">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="1377d-292">A capacidade de depurar o contêiner de várias soluções significa que você pode definir vários pontos de interrupção, cada ponto de interrupção em um projeto diferente (contêiner) e durante a depuração do Visual Studio, você irá parar em pontos de interrupção definidos em diferentes projetos e em execução em contêineres diferentes.</span><span class="sxs-lookup"><span data-stu-id="1377d-292">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![](./media/image16.png)

<span data-ttu-id="1377d-293">**Figura 5-12**.</span><span class="sxs-lookup"><span data-stu-id="1377d-293">**Figure 5-12**.</span></span> <span data-ttu-id="1377d-294">Executando aplicativos de multi-contêiner no Visual Studio de 2017</span><span class="sxs-lookup"><span data-stu-id="1377d-294">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1377d-295">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1377d-295">Additional resources</span></span>

-   <span data-ttu-id="1377d-296">**Implantar um contêiner do ASP.NET em um host remoto do Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="1377d-296">**Deploy an ASP.NET container to a remote Docker host**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="1377d-297">Uma observação sobre como testar e implantar com orchestrators</span><span class="sxs-lookup"><span data-stu-id="1377d-297">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="1377d-298">O docker-compor o e execute os comandos (ou executando e depurando os contêineres no Visual Studio) são adequadas para contêineres de teste em seu ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1377d-298">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="1377d-299">Mas você não deve usar essa abordagem se tiver como alvo clusters do Docker e orchestrators como Docker Swarm, Mesosphere DC/sistema operacional ou Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="1377d-299">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="1377d-300">Se você estiver usando um cluster como [Docker Swarm modo](https://docs.docker.com/engine/swarm/) (disponível no Docker CE para Windows e Mac desde a versão 1.12), você precisa implantar e testar com comandos adicionais como [criar serviço do docker](https://docs.docker.com/engine/reference/commandline/service_create/) para Serviços de único.</span><span class="sxs-lookup"><span data-stu-id="1377d-300">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="1377d-301">Se você estiver implantando um aplicativo composto por vários contêineres, você usa [docker compor pacote](https://docs.docker.com/compose/reference/bundle/) e [docker implantar myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) para implantar o aplicativo composto como um *pilha*.</span><span class="sxs-lookup"><span data-stu-id="1377d-301">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="1377d-302">Para obter mais informações, consulte o postagem de blog [apresentando Experimental distribuídas pacotes de aplicativos](https://blog.docker.com/2016/06/docker-app-bundle/) na documentação do Docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-302">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="1377d-303">no site do Docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-303">on the Docker site.</span></span>

<span data-ttu-id="1377d-304">Para [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) e [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) você usaria também scripts e comandos de implantação diferentes.</span><span class="sxs-lookup"><span data-stu-id="1377d-304">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="1377d-305">Etapa 6.</span><span class="sxs-lookup"><span data-stu-id="1377d-305">Step 6.</span></span> <span data-ttu-id="1377d-306">Testar seu aplicativo de Docker usando o host local do Docker</span><span class="sxs-lookup"><span data-stu-id="1377d-306">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="1377d-307">Esta etapa irá variar dependendo de seu aplicativo está fazendo.</span><span class="sxs-lookup"><span data-stu-id="1377d-307">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="1377d-308">Em um aplicativo .NET Core Web simple que é implantado como um único contêiner ou um serviço, você pode acessar o serviço abrindo um navegador no host do Docker e navegar para o site, conforme mostrado na Figura 5-13.</span><span class="sxs-lookup"><span data-stu-id="1377d-308">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site as shown in Figure 5-13.</span></span> <span data-ttu-id="1377d-309">(Se a configuração no Dockerfile mapeia o contêiner para uma porta no host que é diferente de 80, incluir a postagem de host na URL).</span><span class="sxs-lookup"><span data-stu-id="1377d-309">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host post in the URL.)</span></span>

![](./media/image18.png)

<span data-ttu-id="1377d-310">**Figura 5-13**.</span><span class="sxs-lookup"><span data-stu-id="1377d-310">**Figure 5-13**.</span></span> <span data-ttu-id="1377d-311">Exemplo de testar seu aplicativo de Docker localmente usando localhost</span><span class="sxs-lookup"><span data-stu-id="1377d-311">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="1377d-312">Se o host local não está apontando para o Docker IP de host (por padrão, ao usar o CE Docker, deveria), para navegar para o serviço, use o endereço IP da placa de rede do seu computador.</span><span class="sxs-lookup"><span data-stu-id="1377d-312">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="1377d-313">Observe que essa URL no navegador usa a porta 80 para o exemplo de contêiner específico que está sendo discutido.</span><span class="sxs-lookup"><span data-stu-id="1377d-313">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="1377d-314">No entanto, internamente as solicitações estão sendo redirecionadas para a porta 5000, pois esse era como ele foi implantado com o comando docker run, conforme explicado em uma etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="1377d-314">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="1377d-315">Você também pode testar o aplicativo usando a rotação de terminal, conforme mostrado na Figura 5-14.</span><span class="sxs-lookup"><span data-stu-id="1377d-315">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="1377d-316">Em uma instalação de Docker no Windows, o padrão de IP do Host do Docker é sempre 10.0.75.1 conjunto de endereço IP real do seu computador.</span><span class="sxs-lookup"><span data-stu-id="1377d-316">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![](./media/image19.png)

<span data-ttu-id="1377d-317">**Figura 5-14**.</span><span class="sxs-lookup"><span data-stu-id="1377d-317">**Figure 5-14**.</span></span> <span data-ttu-id="1377d-318">Exemplo de testar seu aplicativo de Docker localmente usando ondulação</span><span class="sxs-lookup"><span data-stu-id="1377d-318">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="1377d-319">Testando e depurando contêineres com o Visual Studio de 2017</span><span class="sxs-lookup"><span data-stu-id="1377d-319">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="1377d-320">Quando executando e depurando contêineres com 2017 do Visual Studio, você pode depurar o aplicativo do .NET em quase da mesma forma como você faria durante a execução sem contêineres.</span><span class="sxs-lookup"><span data-stu-id="1377d-320">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="1377d-321">Testar e depurar sem o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1377d-321">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="1377d-322">Se você estiver desenvolvendo usando a abordagem de editor/CLI, contêineres de depuração é mais difícil e você deve gerar rastreamentos de depuração.</span><span class="sxs-lookup"><span data-stu-id="1377d-322">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1377d-323">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1377d-323">Additional resources</span></span>

-   <span data-ttu-id="1377d-324">**Depuração de aplicativos em um contêiner de Docker local**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="1377d-324">**Debugging apps in a local Docker container**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

-   <span data-ttu-id="1377d-325">**Steve Lasker. Compilar, depurar, implantar aplicativos do ASP.NET Core com o Docker.**</span><span class="sxs-lookup"><span data-stu-id="1377d-325">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="1377d-326">Vídeo.</span><span class="sxs-lookup"><span data-stu-id="1377d-326">Video.</span></span>
    [<span data-ttu-id="1377d-327">*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*</span><span class="sxs-lookup"><span data-stu-id="1377d-327">*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*</span></span>](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="1377d-328">Fluxo de trabalho simplificado ao desenvolver contêineres com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1377d-328">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="1377d-329">Efetivamente, o fluxo de trabalho ao usar o Visual Studio é muito mais simples do que se você usar a abordagem de editor/CLI.</span><span class="sxs-lookup"><span data-stu-id="1377d-329">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="1377d-330">A maioria das etapas necessárias pelo Docker relacionada ao Dockerfile e arquivos de docker compose.yml ocultos ou simplificados pelo Visual Studio, conforme mostrado na Figura 5-15.</span><span class="sxs-lookup"><span data-stu-id="1377d-330">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![](./media/image20.png)

<span data-ttu-id="1377d-331">**Figura 5-15**.</span><span class="sxs-lookup"><span data-stu-id="1377d-331">**Figure 5-15**.</span></span> <span data-ttu-id="1377d-332">Fluxo de trabalho simplificado ao desenvolver com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1377d-332">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="1377d-333">Além disso, você precisa executar a etapa 2 (Adicionar suporte de Docker para seus projetos) apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="1377d-333">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="1377d-334">Portanto, o fluxo de trabalho é semelhante a suas tarefas de desenvolvimento comuns ao usar o .NET para qualquer outro desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1377d-334">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="1377d-335">Você precisa saber o que está acontecendo nos bastidores (o processo de criação de imagem, quais imagens de base que você está usando, implantação de contêineres, etc.) e, às vezes, que você também precisará editar o arquivo Dockerfile ou compose.yml docker para personalizar os comportamentos.</span><span class="sxs-lookup"><span data-stu-id="1377d-335">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="1377d-336">Mas a maioria do trabalho seja bastante simplificado usando o Visual Studio, o que o torna muito mais produtivo.</span><span class="sxs-lookup"><span data-stu-id="1377d-336">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1377d-337">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1377d-337">Additional resources</span></span>

-   <span data-ttu-id="1377d-338">**Steve Lasker. Desenvolvimento de docker .NET com o Visual Studio de 2017**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span><span class="sxs-lookup"><span data-stu-id="1377d-338">**Steve Lasker. .NET Docker Development with Visual Studio 2017**
[*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span></span>

-   <span data-ttu-id="1377d-339">**Jeffrey T. Fritz. Coloque um aplicativo de núcleo do .NET em um contêiner com as novas ferramentas do Docker para Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span><span class="sxs-lookup"><span data-stu-id="1377d-339">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**
[*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span></span>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="1377d-340">Usando comandos do PowerShell em um Dockerfile para configurar a contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="1377d-340">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="1377d-341">[Contêineres do Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) permitem converter seus aplicativos existentes do Windows em imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker.</span><span class="sxs-lookup"><span data-stu-id="1377d-341">[Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="1377d-342">Para usar contêineres do Windows, execute comandos do PowerShell no Dockerfile, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1377d-342">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="1377d-343">Nesse caso, estamos usando uma imagem base do Windows Server Core (a configuração de) e instalar o IIS com um comando do PowerShell (a configuração de execução).</span><span class="sxs-lookup"><span data-stu-id="1377d-343">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="1377d-344">De maneira semelhante, você também pode usar comandos do PowerShell para configurar componentes adicionais como o ASP.NET 4. x, .NET 4.6 ou qualquer outro software do Windows.</span><span class="sxs-lookup"><span data-stu-id="1377d-344">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="1377d-345">Por exemplo, o seguinte comando em um Dockerfile configura o ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="1377d-345">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="1377d-346">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1377d-346">Additional resources</span></span>

-   <span data-ttu-id="1377d-347">**docker-ASPNET/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="1377d-347">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="1377d-348">Comandos do Powershell de exemplo para executar a partir de dockerfiles para incluir recursos do Windows.</span><span class="sxs-lookup"><span data-stu-id="1377d-348">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>
    [<span data-ttu-id="1377d-349">*https://GitHub.com/Microsoft/ASPNET-docker/blob/Master/4.6.2/Dockerfile*</span><span class="sxs-lookup"><span data-stu-id="1377d-349">*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*</span></span>](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="1377d-350">[Anterior] (index.md) [Avançar] (... / net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="1377d-350">[Previous] (index.md) [Next] (../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>
