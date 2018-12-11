---
title: Fluxo de trabalho de desenvolvimento de loop interno para aplicativos do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: f7acb60e6136c0250d18bdce23ac21fb6aa80b34
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148846"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="cbe3e-103">Fluxo de trabalho de desenvolvimento de loop interno para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="cbe3e-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="cbe3e-104">Antes de disparar o fluxo de trabalho de loop externo que abrangem o DevOps todo ciclo, tudo começa em cada computador de desenvolvedor, codificando o aplicativo em si, usando seus idiomas preferenciais ou plataformas e testá-lo localmente (Figura 4 a 14).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-14).</span></span> <span data-ttu-id="cbe3e-105">Mas, em todos os casos, você terá um ponto muito importante em comum, não importa qual linguagem, estrutura ou plataformas você escolher.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-105">But in every case, you will have a very important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="cbe3e-106">Nesse fluxo de trabalho específico, você sempre estiver desenvolvendo e testando contêineres do Docker, mas localmente.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-106">In this specific workflow, you are always developing and testing Docker containers, but locally.</span></span>

![](./media/image18.png)

<span data-ttu-id="cbe3e-107">Figura 4 a 14: Contexto de desenvolvimento de loop interno</span><span class="sxs-lookup"><span data-stu-id="cbe3e-107">Figure 4-14: Inner-loop development context</span></span>

<span data-ttu-id="cbe3e-108">O contêiner ou uma instância de uma imagem de Docker conterá esses componentes:</span><span class="sxs-lookup"><span data-stu-id="cbe3e-108">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="cbe3e-109">Uma seleção do sistema operacional (por exemplo, uma distribuição Linux ou Windows)</span><span class="sxs-lookup"><span data-stu-id="cbe3e-109">An operating system selection (for example, a Linux distribution or Windows)</span></span>

-   <span data-ttu-id="cbe3e-110">Arquivos adicionados pelo desenvolvedor (por exemplo, binários de aplicativo)</span><span class="sxs-lookup"><span data-stu-id="cbe3e-110">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="cbe3e-111">Configuração (por exemplo, as configurações de ambiente e dependências)</span><span class="sxs-lookup"><span data-stu-id="cbe3e-111">Configuration (for example, environment settings and dependencies)</span></span>

-   <span data-ttu-id="cbe3e-112">Instruções para quais processos para ser executado pelo Docker</span><span class="sxs-lookup"><span data-stu-id="cbe3e-112">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="cbe3e-113">Você pode configurar o fluxo de trabalho de desenvolvimento do loop interno que utiliza o Docker como o processo (descrito na próxima seção).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-113">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="cbe3e-114">Leve em consideração que as etapas iniciais para configurar o ambiente não está incluída, pois você precisa fazer isso apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-114">Take into account that the initial steps to set up the environment is not included, because you need to do that just once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="cbe3e-115">Criação de um único aplicativo dentro de um contêiner do Docker usando o Visual Studio Code e CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="cbe3e-115">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="cbe3e-116">Aplicativos são compostos de seus próprios serviços e bibliotecas adicionais (dependências).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-116">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="cbe3e-117">Figura 4-15 mostra as etapas básicas que você normalmente precisará realizar ao compilar um aplicativo do Docker, seguido por descrições detalhadas de cada etapa.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-117">Figure 4-15 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![](./media/image19.png)

<span data-ttu-id="cbe3e-118">Figura 4-15: Fluxo de trabalho de alto nível para o ciclo de vida de aplicativos do Docker em contêineres usando a CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="cbe3e-118">Figure 4-15: High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="cbe3e-119">Etapa 1: Iniciar a codificação no Visual Studio Code e crie sua linha de base inicial/serviço de aplicativo</span><span class="sxs-lookup"><span data-stu-id="cbe3e-119">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="cbe3e-120">A maneira que você desenvolve seu aplicativo é muito semelhante à forma como você pode fazê-lo sem o Docker.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-120">The way you develop your application is pretty similar to the way you do it without Docker.</span></span> <span data-ttu-id="cbe3e-121">A diferença é que, durante o desenvolvimento, você está implantando e testando o aplicativo ou serviços em execução em contêineres do Docker colocados no seu ambiente local (como uma VM do Linux ou Windows).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-121">The difference is that while developing, you are deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="cbe3e-122">**Como configurar seu ambiente local**</span><span class="sxs-lookup"><span data-stu-id="cbe3e-122">**Setting up your local environment**</span></span>

<span data-ttu-id="cbe3e-123">Com as versões mais recentes do Docker para Mac e Windows, é mais fácil do que nunca para desenvolver aplicativos do Docker e a instalação é simples.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-123">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

<span data-ttu-id="cbe3e-124">**Obter mais informações** para obter instruções sobre como configurar o Docker para Windows, acesse [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-124">**More info** For instructions on setting up Docker for Windows, go to [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span></span>

<span data-ttu-id="cbe3e-125">Para obter instruções sobre como configurar o Docker para Mac, acesse <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-125">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="cbe3e-126">Além disso, será necessário um editor de código, de modo que, na verdade, você pode desenvolver seu aplicativo enquanto estiver usando a CLI do Docker.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-126">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="cbe3e-127">A Microsoft fornece o Visual Studio Code, que é um editor de código leve que tem suporte no Mac, Windows e Linux e fornece o IntelliSense com [suporte para várias linguagens](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python e mais linguagens modernas), [depurando](https://code.visualstudio.com/Docs/editor/debugging), [integração com o Git](https://code.visualstudio.com/Docs/editor/versioncontrol) e [suporte a extensões](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-127">Microsoft provides Visual Studio Code, which is a lightweight code editor that is supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="cbe3e-128">Esse editor é uma excelente opção para os desenvolvedores do Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-128">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="cbe3e-129">No Windows, você também pode usar o aplicativo completo do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-129">In Windows, you also can use the full Visual Studio application.</span></span>

<span data-ttu-id="cbe3e-130">**Obter mais informações** para obter instruções sobre como instalar o Visual Studio para Windows, Mac ou Linux, vá para <https://code.visualstudio.com/docs/setup/setup-overview/>.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-130">**More info** For instructions on installing Visual Studio for Windows, Mac, or Linux, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>

<span data-ttu-id="cbe3e-131">Você pode trabalhar com a CLI do Docker e escrever seu código usando qualquer editor de código, mas se você usar o Visual Studio Code, faz a autor Dockerfile e docker-Compose. yml arquivos em seu espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-131">You can work with Docker CLI and write your code using any code editor, but if you use Visual Studio Code, it makes it easy to author Dockerfile and docker-compose.yml files in your workspace.</span></span> <span data-ttu-id="cbe3e-132">Além disso, você pode executar tarefas do Visual Studio Code do IDE que solicitará que os scripts que podem executar operações elaboradas usando a CLI do Docker abaixo.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-132">Plus, you can run Visual Studio Code tasks from the IDE that will prompt scripts that can be running elaborated operations using Docker CLI underneath.</span></span>

<span data-ttu-id="cbe3e-133">Visual Studio Code é fornecido por uma extensão, que você precisará instalar.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-133">Visual Studio Code is provided by an extension, which you'll need to install.</span></span> <span data-ttu-id="cbe3e-134">Para fazer isso, pressione Ctrl + Shift + P, digite **ext instalar**, e, em seguida, executar as extensões: Instale o comando de extensão para abrir a lista de extensões do Marketplace.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-134">To do so, Press Ctrl+Shift+P, type **ext install**, and then run the Extensions: Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="cbe3e-135">Em seguida, digite **docker** para filtrar os resultados e, em seguida, selecione o Dockerfile e Docker Compose arquivo (yml) a extensão de suporte, conforme ilustrado na Figura 4 a 16.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-135">Next, type **docker** to filter the results, and then select the Dockerfile And Docker Compose File (yml) Support extension, as depicted in Figure 4-16.</span></span>

![](./media/image20.png)

<span data-ttu-id="cbe3e-136">Figura 4 a 16: Instalando a extensão do Docker no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cbe3e-136">Figure 4-16: Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="cbe3e-137">Etapa 2: Criar um DockerFile relacionado a uma imagem existente (sem formatação do sistema operacional ou ambientes de desenvolvimento, como Ruby, Node. js e .NET Core)</span><span class="sxs-lookup"><span data-stu-id="cbe3e-137">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="cbe3e-138">Você precisará de um DockerFile por uma imagem personalizada a ser criado e por contêiner a serem implantados, portanto, se seu aplicativo é composto por um único serviço personalizado, será necessário um único DockerFile.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-138">You will need a DockerFile per custom image to be built and per container to be deployed, therefore, if your app is made up of a single custom service, you will need a single DockerFile.</span></span> <span data-ttu-id="cbe3e-139">Mas, se seu aplicativo é composto de vários serviços (como em uma arquitetura de microsserviços), será necessário um Dockerfile por serviço.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-139">But, if your app is composed of multiple services (as in a microservices architecture), you'll need one Dockerfile per service.</span></span>

<span data-ttu-id="cbe3e-140">O DockerFile normalmente é colocado dentro da pasta raiz do seu aplicativo ou serviço e contém os comandos necessários para que o Docker Saiba como configurar e executar esse aplicativo ou serviço.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-140">The DockerFile is usually placed within the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="cbe3e-141">Você pode criar seu DockerFile e adicioná-lo ao seu projeto, juntamente com seu código (Node. js, .NET Core, etc.), ou, se você for novo no ambiente, examine a seguinte dica.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-141">You can create your DockerFile and add it to your project along with your code (node.js, .NET Core, etc.), or, if you are new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="cbe3e-142">Você pode usar uma ferramenta de linha de comando chamada [yo docker](https://github.com/Microsoft/generator-docker), que usa o Scaffold de arquivos do seu projeto no idioma que você escolha e adiciona os arquivos de configuração necessários do Docker.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-142">You can use a command-line tool called [yo docker](https://github.com/Microsoft/generator-docker), which scaffolds files from your project in the language you choose and adds the required Docker configuration files.</span></span> <span data-ttu-id="cbe3e-143">Basicamente, para ajudar os desenvolvedores de Introdução, ele cria o DockerFile apropriado, docker-Compose. yml e outros scripts associados para compilar e executar seus contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-143">Basically, to assist developers getting started, it creates the appropriate DockerFile, docker-compose.yml, and other associated scripts to build and run your Docker containers.</span></span> <span data-ttu-id="cbe3e-144">Esse gerador yeoman solicitará que você com algumas perguntas, solicitando que o host do contêiner selecionado desenvolvimento idioma e de destino.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-144">This yeoman generator will prompt you with a few questions, asking your selected development language and destination container host.</span></span>

![yo docker](./media/image21.png)

<span data-ttu-id="cbe3e-146">Por exemplo, a Figura 4-17 mostra duas capturas de tela dos terminais de, no Windows e no Mac, em ambos os casos, executando yo docker, que irá gerar os código projetos de exemplo (atualmente, o .NET Core, Golang e Node. js como idiomas com suporte) já está configurados para funcionar em parte superior do Docker.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-146">For instance, Figure 4-17 shows two screenshots from the terminals in Windows and on a Mac, in both cases, running yo docker, which will generate the sample code projects (currently .NET Core, Golang, and Node.js as supported languages) already configured to work on top of Docker.</span></span>

![](./media/image22.PNG)  ![](./media/image23.png)

<span data-ttu-id="cbe3e-147">Figura 4-17: yo docker ferramenta de comando no Windows (esquerda) e em um Mac</span><span class="sxs-lookup"><span data-stu-id="cbe3e-147">Figure 4-17: yo docker command tool in Windows (left) and on a Mac</span></span>

<span data-ttu-id="cbe3e-148">Figura 4-18 apresenta um exemplo usando yo docker depois que você tiver um projeto existente do .NET Core em vigor para ser gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-148">Figure 4-18 presents an example using yo docker after you have an existing .NET Core project in place to be scaffolded.</span></span>

![](./media/image24.PNG)

<span data-ttu-id="cbe3e-149">Figura 4-18: yo docker com um existentes do .NET Core de projeto em vigor</span><span class="sxs-lookup"><span data-stu-id="cbe3e-149">Figure 4-18: yo docker with an existing .NET Core project in place</span></span>

<span data-ttu-id="cbe3e-150">O DockerFile, você especifica qual imagem base do Docker, você vai usar (como usando "de microsoft/dotnet:1.0.0-core").</span><span class="sxs-lookup"><span data-stu-id="cbe3e-150">From the DockerFile, you specify what base Docker image you'll be using (like using "FROM microsoft/dotnet:1.0.0-core").</span></span> <span data-ttu-id="cbe3e-151">Normalmente, você irá criar sua imagem personalizada na parte superior de uma imagem de base que pode ser de qualquer repositório oficial na [registro de Hub do Docker](https://hub.docker.com/) (como um [imagem para o .NET Core](https://hub.docker.com/r/microsoft/dotnet/) ou um [para Node. js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-151">You usually will build your custom image on top of a base image that you can get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="cbe3e-152">***Opção a: Usar uma imagem de Docker oficial existente***</span><span class="sxs-lookup"><span data-stu-id="cbe3e-152">***Option A: Use an existing official Docker image***</span></span>

<span data-ttu-id="cbe3e-153">Usando um repositório oficial de uma pilha de idiomas com um número de versão garante que os mesmos recursos de idioma estão disponíveis em todos os computadores (incluindo desenvolvimento, teste e produção).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-153">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="cbe3e-154">A seguir está um exemplo de DockerFile para um contêiner do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="cbe3e-154">Following is a sample DockerFile for a .NET Core container:</span></span>

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="cbe3e-155">Nesse caso, ele está usando a versão 1.0.1 da imagem oficial do docker do ASP.NET Core para Linux denominado microsoft/aspnetcore:1.0.1.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-155">In this case, it is using the version 1.0.1 of the official ASP.NET Core Docker image for Linux named microsoft/aspnetcore:1.0.1.</span></span> <span data-ttu-id="cbe3e-156">Para obter mais detalhes, consulte o [página de imagem do Docker do ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) e o [página de imagem do Docker do .NET Core](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-156">For further details, consult the [ASP.NET Core Docker Image page](https://hub.docker.com/r/microsoft/aspnetcore/) and the [.NET Core Docker Image page](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="cbe3e-157">Você também pode usar outra imagem comparável, como o nó: 4-onbuild para Node. js ou muitas outras imagens pré-configuradas para linguagens de desenvolvimento, estão disponíveis em [Hub do Docker](https://hub.docker.com/explore/).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-157">You also could be using another comparable image like node:4-onbuild for Node.js, or many other preconfigured images for development languages, which are available at [Docker Hub](https://hub.docker.com/explore/).</span></span>

<span data-ttu-id="cbe3e-158">No DockerFile, você também precisará instruir o Docker a escutar na porta TCP que você usará em tempo de execução (como a porta 80).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-158">In the DockerFile, you also need to instruct Docker to listen to the TCP port that you will use at runtime (such as port 80).</span></span>

<span data-ttu-id="cbe3e-159">Há outras linhas de configuração que podem ser adicionados no DockerFile, dependendo da linguagem/estrutura que você está usando, para que o Docker Saiba como executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-159">There are other lines of configuration that you can add in the DockerFile depending on the language/framework you are using, so Docker knows how to run the app.</span></span> <span data-ttu-id="cbe3e-160">Por exemplo, você precisa que a linha ENTRYPOINT, com \["dotnet", "MyCustomMicroservice.dll"\] para executar um aplicativo .NET Core, embora você possa ter várias variantes dependendo da abordagem para compilar e executar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-160">For instance, you need the ENTRYPOINT line with \["dotnet", "MyCustomMicroservice.dll"\] to run a .NET Core app, although you can have multiple variants depending on the approach to build and run your service.</span></span> <span data-ttu-id="cbe3e-161">Se você estiver usando o SDK e a CLI do dotnet para compilar e executar o aplicativo .NET, ele seria um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-161">If you're using the SDK and dotnet CLI to build and run the .NET app, it would be slightly different.</span></span> <span data-ttu-id="cbe3e-162">O resultado final é que a linha ENTRYPOINT mais linhas adicionais serão diferentes dependendo da linguagem/plataforma escolhidas para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-162">The bottom line is that the ENTRYPOINT line plus additional lines will be different depending on the language/platform you choose for your application.</span></span>

<span data-ttu-id="cbe3e-163">**Obter mais informações** para obter informações sobre a criação de imagens do Docker para aplicativos .NET Core, acesse <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-163">**More info** For information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>

<span data-ttu-id="cbe3e-164">Para saber mais sobre como criar suas próprias imagens, acesse [ https://docs.docker.com/engine/\ tutoriais/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-164">To learn more about building your own images, go to [https://docs.docker.com/engine/\ tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span></span>

<span data-ttu-id="cbe3e-165">**Repositórios de imagens de várias plataformas**</span><span class="sxs-lookup"><span data-stu-id="cbe3e-165">**Multiplatform image repositories**</span></span>

<span data-ttu-id="cbe3e-166">Como contêineres do Windows mais usado ultimamente, um único repositório pode conter variantes de plataforma, como uma imagem do Linux e Windows.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-166">As Windows containers become more prevalent, a single repository can contain platform variants, such as a Linux and Windows image.</span></span> <span data-ttu-id="cbe3e-167">Isso é um novo recurso do Docker que torna possível usar um único repositório para abranger várias plataformas, como os fornecedores [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repositório, que está disponível no registro do DockerHub.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-167">This is a new feature coming in Docker that makes it possible for vendors to use a single repository to cover multiple platforms, such as [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository, which is available at DockerHub registry.</span></span> <span data-ttu-id="cbe3e-168">Como o recurso se torna ativo, extraindo essa imagem de um host Windows efetuará pull a variante do Windows, enquanto recebendo o mesmo nome de imagem de um host Linux efetuará o pull da variante do Linux.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-168">As the feature comes alive, pulling this image from a Windows host will pull the Windows variant, whereas pulling the same image name from a Linux host will pull the Linux variant.</span></span>

<span data-ttu-id="cbe3e-169">***Opção b: Criar sua imagem de base a partir do zero***</span><span class="sxs-lookup"><span data-stu-id="cbe3e-169">***Option B: Create your base image from scratch***</span></span>

<span data-ttu-id="cbe3e-170">Você pode criar sua própria imagem base do Docker do zero, conforme explicado neste [artigo](https://docs.docker.com/engine/userguide/eng-image/baseimages/) do Docker.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-170">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="cbe3e-171">Esse é um cenário que provavelmente não é melhor para você se você estiver apenas começando com o Docker, mas se você quiser definir as partes específicas de sua própria imagem base, você pode fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-171">This is a scenario that is probably not best for you if you are just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="cbe3e-172">Etapa 3: Criar imagens personalizadas do Docker inserindo seu serviço nele</span><span class="sxs-lookup"><span data-stu-id="cbe3e-172">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="cbe3e-173">Para cada serviço personalizado que consiste em seu aplicativo, você precisará criar uma imagem relacionada.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-173">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="cbe3e-174">Se seu aplicativo é composto por um único serviço ou aplicativo web, você precisará apenas uma única imagem.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-174">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="cbe3e-175">Ao levar em consideração o "loop externo DevOps fluxo de trabalho", as imagens serão criadas por um processo automatizado de compilação sempre que você enviar por push seu código-fonte para um repositório Git (integração contínua) para que as imagens serão criadas no ambiente global do seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-175">When taking into account the "outer-loop DevOps workflow," the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration) so the images will be created in that global environment from your source code.</span></span>

<span data-ttu-id="cbe3e-176">Mas, antes de considerarmos indo para aquela rota de loop externo, precisamos garantir que o aplicativo do Docker está funcionando corretamente, de modo que eles não envie por push o código que pode não funcionar corretamente para o sistema de controle do código-fonte (Git, etc.).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-176">But, before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>

<span data-ttu-id="cbe3e-177">Portanto, cada desenvolvedor precisa primeiro fazer todo o processo de loop interno para testar localmente e continuar a desenvolver até que eles querem enviar por push a um recurso completo ou altere para o sistema de controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-177">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="cbe3e-178">Para criar uma imagem no seu ambiente local e usando o DockerFile, você pode usar o comando docker build, conforme demonstrado na Figura 4-19 (você também pode executar docker-compose up-- compilar para aplicativos compostos por vários contêineres/serviços).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-178">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-19 (you also can run docker-compose up --build for applications composed by several containers/services).</span></span>

![](./media/image25.png)

<span data-ttu-id="cbe3e-179">Figura 4-19: Compilação do docker em execução</span><span class="sxs-lookup"><span data-stu-id="cbe3e-179">Figure 4-19: Running docker build</span></span>

<span data-ttu-id="cbe3e-180">Opcionalmente, em vez de executar diretamente o docker build na pasta do projeto, você primeiro pode gerar uma pasta implantável com as bibliotecas .NET necessárias usando a execução do dotnet publicar comando e, em seguida, executar build do docker.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-180">Optionally, instead of directly running docker build from the project's folder, you first can generate a deployable folder with the .NET libraries needed by using the run dotnet publish command, and then run docker build.</span></span>

<span data-ttu-id="cbe3e-181">Neste exemplo, isso cria uma imagem do Docker com o nome cesardl/netcore-webapi-microsserviço-docker: first (: first é uma marcação, como uma versão específica).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-181">In this example, this creates a Docker image with the name cesardl/netcore-webapi-microservice-docker:first (:first is a tag, like a specific version).</span></span> <span data-ttu-id="cbe3e-182">Você pode executar esta etapa para cada imagem personalizada, que você precisará criar seu aplicativo composto do Docker com vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-182">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="cbe3e-183">Você pode encontrar imagens existentes no seu repositório local (computador de desenvolvimento) usando o docker imagens comando, conforme ilustrado na Figura 4 a 20.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-183">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-20.</span></span>

![](./media/image26.png)

<span data-ttu-id="cbe3e-184">Figura 4 a 20: Visualização das imagens existentes usando imagens do docker</span><span class="sxs-lookup"><span data-stu-id="cbe3e-184">Figure 4-20: Viewing existing images using docker images</span></span>

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="cbe3e-185">Etapa 4: (Opcional) Definir os serviços no docker-Compose. yml ao compilar um aplicativo composto do Docker com vários serviços</span><span class="sxs-lookup"><span data-stu-id="cbe3e-185">Step 4: (Optional) Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="cbe3e-186">Com o arquivo docker-Compose. yml, você pode definir um conjunto de serviços relacionados para ser implantado como um aplicativo composto com os comandos de implantação, explicados na seção próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-186">With the docker-compose.yml file you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="cbe3e-187">Você precisa criar esse arquivo em seu principal ou a pasta raiz da solução; ele deve ter um conteúdo semelhante ao seguinte arquivo docker-Compose. yml:</span><span class="sxs-lookup"><span data-stu-id="cbe3e-187">You need to create that file in your main or root solution folder; it should have a similar content to the following docker-compose.yml file:</span></span>

```yml
version: '2'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

<span data-ttu-id="cbe3e-188">Nesse caso específico, esse arquivo define dois serviços: o serviço web (seu serviço personalizado) e o serviço de redis (um serviço de cache populares).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-188">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="cbe3e-189">Cada serviço será implantado como um contêiner, portanto, precisamos usar uma imagem do Docker concreta para cada um.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-189">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="cbe3e-190">Para este serviço da web específica, a imagem será necessário fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cbe3e-190">For this particular web service, the image will need to do the following:</span></span>

-   <span data-ttu-id="cbe3e-191">Build do DockerFile no diretório atual</span><span class="sxs-lookup"><span data-stu-id="cbe3e-191">Build from the DockerFile in the current directory</span></span>

-   <span data-ttu-id="cbe3e-192">Encaminhar a porta 80 no contêiner para a porta 81 no computador host, exposta</span><span class="sxs-lookup"><span data-stu-id="cbe3e-192">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

-   <span data-ttu-id="cbe3e-193">Montar o diretório do projeto no host para /code dentro do contêiner, possibilitando que você pode modificar o código sem ter que recompilar a imagem</span><span class="sxs-lookup"><span data-stu-id="cbe3e-193">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

-   <span data-ttu-id="cbe3e-194">Vincular o serviço web para o serviço de redis</span><span class="sxs-lookup"><span data-stu-id="cbe3e-194">Link the web service to the redis service</span></span>

<span data-ttu-id="cbe3e-195">O serviço do redis usa o [imagem mais recente do redis público](https://hub.docker.com/_/redis/) extraído do registro de Hub do Docker.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-195">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="cbe3e-196">[redis](https://redis.io/) é um sistema de cache muito popular para aplicativos do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-196">[redis](https://redis.io/) is a very popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="cbe3e-197">Etapa 5: Compilar e executar seu aplicativo do Docker</span><span class="sxs-lookup"><span data-stu-id="cbe3e-197">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="cbe3e-198">Se seu aplicativo tem apenas um único contêiner, basta executá-lo Implantando-o em seu Host do Docker (VM ou servidor físico).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-198">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="cbe3e-199">No entanto, se seu aplicativo é composto por vários serviços, você precisará *compô-la*também.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-199">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="cbe3e-200">Vamos ver as diferentes opções.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-200">Let's see the different options.</span></span>

<span data-ttu-id="cbe3e-201">***Opção a: Executar um único contêiner ou serviço***</span><span class="sxs-lookup"><span data-stu-id="cbe3e-201">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="cbe3e-202">Você pode executar a imagem do Docker usando o comando docker run, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="cbe3e-202">You can run the Docker image by using the docker run command, as shown here:</span></span>

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="cbe3e-203">Observe que, para essa implantação específica, podemos vai ser redirecionar as solicitações enviadas para a porta 80 para a porta interna 5000.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-203">Note that for this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="cbe3e-204">Agora, o aplicativo está escutando na porta 80 no nível do host externa.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-204">Now, the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="cbe3e-205">***Opção b: Compor e executar um aplicativo de vários contêineres***</span><span class="sxs-lookup"><span data-stu-id="cbe3e-205">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="cbe3e-206">Na maioria dos cenários empresariais, um aplicativo do Docker será ser composto de vários serviços.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-206">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="cbe3e-207">Nesses casos, você pode executar o comando docker-compose para cima (Figura 4-21), que usará o arquivo docker-Compose. yml que talvez você tenha criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-207">For these cases, you can run the command docker-compose up (Figure 4-21), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="cbe3e-208">Executar esse comando implanta um aplicativo composto com todos os seus contêineres relacionados.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-208">Running this command deploys a composed application with all of its related containers.</span></span>

![](./media/image27.png)

<span data-ttu-id="cbe3e-209">Figura 4-21: Resultados da execução do comando "docker-compose up"</span><span class="sxs-lookup"><span data-stu-id="cbe3e-209">Figure 4-21: Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="cbe3e-210">Depois de executar docker-compose, você implantar seu aplicativo e seus contêineres relacionados no Host do Docker, conforme ilustrado na Figura 4-22, na representação de VM.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-210">After you run docker-compose up, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-22, in the VM representation.</span></span>

![](./media/image28.png)

<span data-ttu-id="cbe3e-211">Figura 4-22: VM com contêineres do Docker implantados</span><span class="sxs-lookup"><span data-stu-id="cbe3e-211">Figure 4-22: VM with Docker containers deployed</span></span>

<span data-ttu-id="cbe3e-212">Observação docker-compose e execução do docker pode ser suficiente para testar seus contêineres em seu ambiente de desenvolvimento, mas você talvez não usá-los em todos os se você está esperando trabalhar com clusters do Docker e orquestradores como Kubernetes, Mesosphere DC/SO ou Docker Swarm para poder escalar verticalmente.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-212">Note docker-compose up and docker run might be enough for testing your containers in your development environment, but you might not use them at all if you are expecting to work with Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes in order to be able to scale up.</span></span> <span data-ttu-id="cbe3e-213">Se você estiver usando um cluster, como [modo Docker Swarm](https://docs.docker.com/engine/swarm/) (disponível no Docker para Windows e Mac desde a versão 1.12), você precisa implantar e testar com comandos adicionais, como o serviço docker criar para serviços únicos ou quando você estiver implantar um aplicativo composto de vários contêineres, usando o docker compose bundle e implantar o docker myBundleFile, implantando o aplicativo composto como uma pilha, conforme explicado no artigo [pacotes de aplicativos distribuídos](https://blog.docker.com/2016/06/docker-app-bundle/) do Docker.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-213">If you're using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker for Windows and Mac since version 1.12), you need to deploy and test with additional commands such as docker service create for single services, or when you're deploying an app composed of several containers, using docker compose bundle and docker deploy myBundleFile, by deploying the composed app as a stack, as explained in the article [Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) from Docker.</span></span>

<span data-ttu-id="cbe3e-214">Para [DC/SO](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) e [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) você usaria também scripts e comandos de implantação diferentes.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-214">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) you would use different deployment commands and scripts, as well.</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="cbe3e-215">Etapa 6: Testar seu aplicativo do Docker (localmente, em sua VM local do CD)</span><span class="sxs-lookup"><span data-stu-id="cbe3e-215">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="cbe3e-216">Esta etapa irá variar dependendo de seu aplicativo está funcionando.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-216">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="cbe3e-217">Uma .NET Core da Web muito simples "Hello World" implantado como um único contêiner ou serviço de API, você apenas precisará acessar o serviço, fornecendo a porta TCP especificada no DockerFile.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-217">In a very simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="cbe3e-218">Se o host local não está ativado, para navegar até seu serviço, localize o endereço IP para a máquina usando este comando:</span><span class="sxs-lookup"><span data-stu-id="cbe3e-218">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

<span data-ttu-id="cbe3e-219">ip do computador docker *seu nome de contêiner*</span><span class="sxs-lookup"><span data-stu-id="cbe3e-219">docker-machine ip *your-container-name*</span></span>

<span data-ttu-id="cbe3e-220">No host do Docker, abra um navegador e navegue até o site; Você deve ver seu aplicativo ou serviço em execução, conforme demonstrado na Figura 4 a 23.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-220">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-23.</span></span>

![](./media/image29.png)

<span data-ttu-id="cbe3e-221">Figura 4 a 23: Teste seu aplicativo do Docker localmente usando localhost</span><span class="sxs-lookup"><span data-stu-id="cbe3e-221">Figure 4-23: Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="cbe3e-222">Observe que ele está usando a porta 80, mas internamente estava sendo redirecionado para a porta 5000, pois é como ele foi implantado com docker run, conforme explicado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-222">Note that it is using port 80, but internally it was being redirected to port 5000, because that's how it was deployed with docker run, as explained earlier.</span></span>

<span data-ttu-id="cbe3e-223">Você pode testar isso usando o CURL no terminal.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-223">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="cbe3e-224">Em uma instalação do Docker no Windows, o IP padrão é 10.0.75.1, conforme ilustrado na Figura 4-24.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-224">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-24.</span></span>

![](./media/image30.png)

<span data-ttu-id="cbe3e-225">Figura 4-24: Testando um aplicativo do Docker localmente usando CURL</span><span class="sxs-lookup"><span data-stu-id="cbe3e-225">Figure 4-24: Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="cbe3e-226">**Depuração de um contêiner em execução no Docker**</span><span class="sxs-lookup"><span data-stu-id="cbe3e-226">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="cbe3e-227">Visual Studio Code dá suporte à depuração Docker se você estiver usando o Node. js e outras plataformas como contêineres do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-227">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="cbe3e-228">Você também pode depurar contêineres do .NET Core no Docker ao usar o Visual Studio, conforme descrito na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="cbe3e-228">You also can debug .NET Core containers in Docker when using Visual Studio, as described in the next section.</span></span>

<span data-ttu-id="cbe3e-229">**Obter mais informações:** para saber mais sobre a depuração de contêineres do Docker do Node. js, acesse <https://blog.docker.com/2016/07/live-debugging-docker/> e [ https://blogs.msdn.microsoft.com/\ usuário\_ed/2016/02/27 / Visual-Studio-Code-New-Features-13-big-Debugging-Updates-Rich-Object-hover-Conditional-Breakpoints-Node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span><span class="sxs-lookup"><span data-stu-id="cbe3e-229">**More info:** To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and [https://blogs.msdn.microsoft.com/\ user\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cbe3e-230">[Anterior](docker-apps-development-environment.md)
>[Próximo](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="cbe3e-230">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>