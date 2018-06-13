---
title: Fluxo de trabalho de desenvolvimento do loop interno para aplicativos de Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: cda9aa77ca033dced8b6b30538f19f28a5fa63a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579204"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="f9e14-103">Fluxo de trabalho de desenvolvimento do loop interno para aplicativos de Docker</span><span class="sxs-lookup"><span data-stu-id="f9e14-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="f9e14-104">Antes de disparar o fluxo de trabalho do loop externo abrangendo o DevOps todo o ciclo, tudo começa em cada computador de um desenvolvedor, codificar o aplicativo em si, usando seu idioma de preferência ou plataformas e testá-lo localmente (Figura 4-14).</span><span class="sxs-lookup"><span data-stu-id="f9e14-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-14).</span></span> <span data-ttu-id="f9e14-105">Mas em todos os casos, você terá um ponto muito importante em comum, não importa quais plataformas, idioma ou estrutura que você escolher.</span><span class="sxs-lookup"><span data-stu-id="f9e14-105">But in every case, you will have a very important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="f9e14-106">Nesse fluxo de trabalho específico, você sempre estiver desenvolvendo e testando contêineres do Docker, mas localmente.</span><span class="sxs-lookup"><span data-stu-id="f9e14-106">In this specific workflow, you are always developing and testing Docker containers, but locally.</span></span>

![](./media/image18.png)

<span data-ttu-id="f9e14-107">Figura 4-14: contexto de desenvolvimento de loop interno</span><span class="sxs-lookup"><span data-stu-id="f9e14-107">Figure 4-14: Inner-loop development context</span></span>

<span data-ttu-id="f9e14-108">O contêiner ou uma instância de uma imagem do Docker conterá esses componentes:</span><span class="sxs-lookup"><span data-stu-id="f9e14-108">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="f9e14-109">Uma seleção de sistema operacional (por exemplo, uma distribuição de Linux ou Windows)</span><span class="sxs-lookup"><span data-stu-id="f9e14-109">An operating system selection (for example, a Linux distribution or Windows)</span></span>

-   <span data-ttu-id="f9e14-110">Arquivos adicionados pelo desenvolvedor (por exemplo, binários de aplicativo)</span><span class="sxs-lookup"><span data-stu-id="f9e14-110">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="f9e14-111">Configuração (por exemplo, configurações de ambiente e dependências)</span><span class="sxs-lookup"><span data-stu-id="f9e14-111">Configuration (for example, environment settings and dependencies)</span></span>

-   <span data-ttu-id="f9e14-112">Instruções para o que processa a execução do Docker</span><span class="sxs-lookup"><span data-stu-id="f9e14-112">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="f9e14-113">Você pode configurar o fluxo de trabalho de desenvolvimento do loop interno que utiliza o Docker como o processo (descrito na próxima seção).</span><span class="sxs-lookup"><span data-stu-id="f9e14-113">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="f9e14-114">Leve em consideração as etapas iniciais para configurar o ambiente não é incluído, porque você precisa fazer isso apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="f9e14-114">Take into account that the initial steps to set up the environment is not included, because you need to do that just once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="f9e14-115">Criação de um único aplicativo em um contêiner do Docker usando o código do Visual Studio e a CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="f9e14-115">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="f9e14-116">Aplicativos são compostos de seus próprios serviços mais bibliotecas adicionais (dependências).</span><span class="sxs-lookup"><span data-stu-id="f9e14-116">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="f9e14-117">Figura 4-15 mostra as etapas básicas que você geralmente precisa realizar ao compilar um aplicativo do Docker, seguido por descrições detalhadas de cada etapa.</span><span class="sxs-lookup"><span data-stu-id="f9e14-117">Figure 4-15 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![](./media/image19.png)

<span data-ttu-id="f9e14-118">Figura 4-15: aplicativos usando a CLI do Docker em contêineres de fluxo de trabalho de alto nível para o ciclo de vida para Docker</span><span class="sxs-lookup"><span data-stu-id="f9e14-118">Figure 4-15: High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="f9e14-119">Etapa 1: Iniciar a codificação no código do Visual Studio e crie a linha de base do aplicativo/serviço inicial</span><span class="sxs-lookup"><span data-stu-id="f9e14-119">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="f9e14-120">A maneira que você desenvolve seu aplicativo é muito semelhante à forma como você pode fazê-lo sem Docker.</span><span class="sxs-lookup"><span data-stu-id="f9e14-120">The way you develop your application is pretty similar to the way you do it without Docker.</span></span> <span data-ttu-id="f9e14-121">A diferença é que, durante o desenvolvimento, você está implantando e testando seu aplicativo ou serviços em execução dentro de contêineres do Docker colocados em seu ambiente local (como uma VM do Linux ou Windows).</span><span class="sxs-lookup"><span data-stu-id="f9e14-121">The difference is that while developing, you are deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="f9e14-122">**Configurando o ambiente local**</span><span class="sxs-lookup"><span data-stu-id="f9e14-122">**Setting up your local environment**</span></span>

<span data-ttu-id="f9e14-123">Com as versões mais recentes do Docker para Mac e Windows, é mais fácil do que nunca para desenvolver aplicativos do Docker e a instalação é simples.</span><span class="sxs-lookup"><span data-stu-id="f9e14-123">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

<span data-ttu-id="f9e14-124">**Obter mais informações** para obter instruções sobre como configurar o Docker para Windows, acesse [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="f9e14-124">**More info** For instructions on setting up Docker for Windows, go to [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span></span>

<span data-ttu-id="f9e14-125">Para obter instruções sobre como configurar o Docker para Mac, vá para <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="f9e14-125">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="f9e14-126">Além disso, você precisará de um editor de código para que, na verdade, você pode desenvolver seu aplicativo enquanto estiver usando a CLI do Docker.</span><span class="sxs-lookup"><span data-stu-id="f9e14-126">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="f9e14-127">A Microsoft fornece o código do Visual Studio, que é um editor de código leve que é suportado no Linux, Mac e Windows e fornece o IntelliSense com [suporte para vários idiomas](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python e mais linguagens modernas), [depuração](https://code.visualstudio.com/Docs/editor/debugging), [integração com o Git](https://code.visualstudio.com/Docs/editor/versioncontrol) e [suporte a extensões](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="f9e14-127">Microsoft provides Visual Studio Code, which is a lightweight code editor that is supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="f9e14-128">Este editor é ideal para desenvolvedores de Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="f9e14-128">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="f9e14-129">No Windows, você também pode usar o aplicativo do Visual Studio completo.</span><span class="sxs-lookup"><span data-stu-id="f9e14-129">In Windows, you also can use the full Visual Studio application.</span></span>

<span data-ttu-id="f9e14-130">**Obter mais informações** para obter instruções sobre como instalar o Visual Studio para Windows, Mac ou Linux, acesse [ http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/ ](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).</span><span class="sxs-lookup"><span data-stu-id="f9e14-130">**More info** For instructions on installing Visual Studio for Windows, Mac, or Linux, go to [http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).</span></span>

<span data-ttu-id="f9e14-131">Você pode trabalhar com a CLI do Docker e escrever seu código usando qualquer editor de códigos, mas se você usar o código do Visual Studio, faz a autor Dockerfile e arquivos de docker compose.yml no espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f9e14-131">You can work with Docker CLI and write your code using any code editor, but if you use Visual Studio Code, it makes it easy to author Dockerfile and docker-compose.yml files in your workspace.</span></span> <span data-ttu-id="f9e14-132">Além disso, você pode executar tarefas de código do Visual Studio do IDE que solicitará scripts que podem executar operações elaboradas usando a CLI do Docker abaixo.</span><span class="sxs-lookup"><span data-stu-id="f9e14-132">Plus, you can run Visual Studio Code tasks from the IDE that will prompt scripts that can be running elaborated operations using Docker CLI underneath.</span></span>

<span data-ttu-id="f9e14-133">Código do Visual Studio é fornecido por uma extensão, o que você precisará instalar.</span><span class="sxs-lookup"><span data-stu-id="f9e14-133">Visual Studio Code is provided by an extension, which you'll need to install.</span></span> <span data-ttu-id="f9e14-134">Para fazer isso, pressione Ctrl + Shift + P, digite **ext instalar**, e, em seguida, executar as extensões: comando de extensão de instalação para exibir a lista de extensão do Marketplace.</span><span class="sxs-lookup"><span data-stu-id="f9e14-134">To do so, Press Ctrl+Shift+P, type **ext install**, and then run the Extensions: Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="f9e14-135">Em seguida, digite **docker** para filtrar os resultados e, em seguida, selecione o Dockerfile e compor Dockerfile (yml) extensão de suporte, conforme ilustrado na Figura 4-16.</span><span class="sxs-lookup"><span data-stu-id="f9e14-135">Next, type **docker** to filter the results, and then select the Dockerfile And Docker Compose File (yml) Support extension, as depicted in Figure 4-16.</span></span>

![](./media/image20.png)

<span data-ttu-id="f9e14-136">Figura 4-16: instalar a extensão de Docker no código do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f9e14-136">Figure 4-16: Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="f9e14-137">Etapa 2: Criar um DockerFile relacionado a uma imagem existente (SO simples ou ambientes de desenvolvimento como o núcleo do .NET, Node.js e Ruby)</span><span class="sxs-lookup"><span data-stu-id="f9e14-137">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="f9e14-138">Você precisará de um DockerFile por uma imagem personalizada a ser criado e por contêiner a ser implantado, portanto, se seu aplicativo é composto de um único serviço personalizado, será necessário um DockerFile único.</span><span class="sxs-lookup"><span data-stu-id="f9e14-138">You will need a DockerFile per custom image to be built and per container to be deployed, therefore, if your app is made up of a single custom service, you will need a single DockerFile.</span></span> <span data-ttu-id="f9e14-139">Mas, se seu aplicativo é composto de vários serviços (como em uma arquitetura microservices), você precisará de um Dockerfile por serviço.</span><span class="sxs-lookup"><span data-stu-id="f9e14-139">But, if your app is composed of multiple services (as in a microservices architecture), you'll need one Dockerfile per service.</span></span>

<span data-ttu-id="f9e14-140">O DockerFile é posicionado dentro da pasta raiz do seu aplicativo ou serviço e contém os comandos necessários para que Docker Saiba como configurar e executar esse aplicativo ou serviço.</span><span class="sxs-lookup"><span data-stu-id="f9e14-140">The DockerFile is usually placed within the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="f9e14-141">Você pode criar o DockerFile e adicioná-lo ao seu projeto junto com seu código (Node. js, .NET Core, etc.), ou, se você estiver familiarizado com o ambiente, examine a seguinte dica.</span><span class="sxs-lookup"><span data-stu-id="f9e14-141">You can create your DockerFile and add it to your project along with your code (node.js, .NET Core, etc.), or, if you are new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="f9e14-142">Você pode usar uma ferramenta de linha de comando chamada [de docker](https://github.com/Microsoft/generator-docker), qual scaffolds arquivos do seu projeto no idioma que você escolhe e adiciona os arquivos de configuração necessários do Docker.</span><span class="sxs-lookup"><span data-stu-id="f9e14-142">You can use a command-line tool called [yo docker](https://github.com/Microsoft/generator-docker), which scaffolds files from your project in the language you choose and adds the required Docker configuration files.</span></span> <span data-ttu-id="f9e14-143">Basicamente, para ajudar os desenvolvedores de Introdução, ele cria o DockerFile apropriado, docker compose.yml e outros scripts associados para compilar e executar seus contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="f9e14-143">Basically, to assist developers getting started, it creates the appropriate DockerFile, docker-compose.yml, and other associated scripts to build and run your Docker containers.</span></span> <span data-ttu-id="f9e14-144">Esse gerador yeoman solicitará a algumas perguntas, solicitando que o host do contêiner selecionado desenvolvimento idioma e de destino.</span><span class="sxs-lookup"><span data-stu-id="f9e14-144">This yeoman generator will prompt you with a few questions, asking your selected development language and destination container host.</span></span>

![de docker](./media/image21.png)

<span data-ttu-id="f9e14-146">Por exemplo, a Figura 4-17 mostra duas capturas de tela dos terminais no Windows e em um Mac, ambos os casos, execução de docker, o que irá gerar os código projetos de exemplo (atualmente .NET Core, Golang e Node. js como idiomas com suporte) já está configurados para funcionar em parte superior do Docker.</span><span class="sxs-lookup"><span data-stu-id="f9e14-146">For instance, Figure 4-17 shows two screenshots from the terminals in Windows and on a Mac, in both cases, running yo docker, which will generate the sample code projects (currently .NET Core, Golang, and Node.js as supported languages) already configured to work on top of Docker.</span></span>

![](./media/image22.PNG)  ![](./media/image23.png)

<span data-ttu-id="f9e14-147">Figura 4-17: de docker ferramenta de comando no Windows (esquerdo) e em um Mac</span><span class="sxs-lookup"><span data-stu-id="f9e14-147">Figure 4-17: yo docker command tool in Windows (left) and on a Mac</span></span>

<span data-ttu-id="f9e14-148">Figura 4-18 apresenta um exemplo de uso de docker depois de ter um projeto existente do .NET Core em vigor para ser Scaffold.</span><span class="sxs-lookup"><span data-stu-id="f9e14-148">Figure 4-18 presents an example using yo docker after you have an existing .NET Core project in place to be scaffolded.</span></span>

![](./media/image24.PNG)

<span data-ttu-id="f9e14-149">Figura 4-18: de docker com um .NET Core existente do projeto no local</span><span class="sxs-lookup"><span data-stu-id="f9e14-149">Figure 4-18: yo docker with an existing .NET Core project in place</span></span>

<span data-ttu-id="f9e14-150">Do DockerFile, você deve especificar quais imagem base do Docker, você vai usar (como usando "de microsoft/dotnet:1.0.0-core").</span><span class="sxs-lookup"><span data-stu-id="f9e14-150">From the DockerFile, you specify what base Docker image you'll be using (like using "FROM microsoft/dotnet:1.0.0-core").</span></span> <span data-ttu-id="f9e14-151">Você geralmente criará sua imagem personalizada na parte superior de uma imagem de base que pode ser de qualquer repositório oficial no [registro do Hub do Docker](https://hub.docker.com/) (como um [imagem para .NET Core](https://hub.docker.com/r/microsoft/dotnet/) ou um [para Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="f9e14-151">You usually will build your custom image on top of a base image that you can get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="f9e14-152">***R: a opção Usar uma imagem de Docker oficial existente***</span><span class="sxs-lookup"><span data-stu-id="f9e14-152">***Option A: Use an existing official Docker image***</span></span>

<span data-ttu-id="f9e14-153">Usar um repositório oficial de uma pilha de idioma com um número de versão garante que os mesmos recursos de idioma estão disponíveis em todos os computadores (incluindo o desenvolvimento, teste e produção).</span><span class="sxs-lookup"><span data-stu-id="f9e14-153">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="f9e14-154">A seguir está um exemplo DockerFile para um contêiner de núcleo do .NET:</span><span class="sxs-lookup"><span data-stu-id="f9e14-154">Following is a sample DockerFile for a .NET Core container:</span></span>

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

<span data-ttu-id="f9e14-155">Nesse caso, ele está usando a versão 1.0.1 da imagem do ASP.NET Core Docker oficial para Linux denominada microsoft/aspnetcore:1.0.1.</span><span class="sxs-lookup"><span data-stu-id="f9e14-155">In this case, it is using the version 1.0.1 of the official ASP.NET Core Docker image for Linux named microsoft/aspnetcore:1.0.1.</span></span> <span data-ttu-id="f9e14-156">Para obter detalhes, consulte o [página de imagem do ASP.NET Core Docker](https://hub.docker.com/r/microsoft/aspnetcore/) e [página de imagem do Docker .NET Core](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="f9e14-156">For further details, consult the [ASP.NET Core Docker Image page](https://hub.docker.com/r/microsoft/aspnetcore/) and the [.NET Core Docker Image page](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="f9e14-157">Você também pode usar outra imagem comparável como nó: 4-onbuild para Node.js ou muitas outras imagens pré-configuradas para linguagens de desenvolvimento que estão disponíveis em [Hub do Docker](https://hub.docker.com/explore/).</span><span class="sxs-lookup"><span data-stu-id="f9e14-157">You also could be using another comparable image like node:4-onbuild for Node.js, or many other preconfigured images for development languages, which are available at [Docker Hub](https://hub.docker.com/explore/).</span></span>

<span data-ttu-id="f9e14-158">No DockerFile, você também precisa instruem o Docker para escutar na porta TCP que você usará em tempo de execução (como a porta 80).</span><span class="sxs-lookup"><span data-stu-id="f9e14-158">In the DockerFile, you also need to instruct Docker to listen to the TCP port that you will use at runtime (such as port 80).</span></span>

<span data-ttu-id="f9e14-159">Há outras linhas de configuração que você pode adicionar o DockerFile dependendo da linguagem/estrutura que você está usando, para que Docker Saiba como executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f9e14-159">There are other lines of configuration that you can add in the DockerFile depending on the language/framework you are using, so Docker knows how to run the app.</span></span> <span data-ttu-id="f9e14-160">Por exemplo, é necessário que a linha do ponto de entrada com \["dotnet", "MyCustomMicroservice.dll"\] para executar um aplicativo .NET Core, embora você possa ter várias variantes dependendo da abordagem para compilar e executar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="f9e14-160">For instance, you need the ENTRYPOINT line with \["dotnet", "MyCustomMicroservice.dll"\] to run a .NET Core app, although you can have multiple variants depending on the approach to build and run your service.</span></span> <span data-ttu-id="f9e14-161">Se você estiver usando o SDK e dotnet CLI para compilar e executar o aplicativo .NET, poderá ser ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="f9e14-161">If you're using the SDK and dotnet CLI to build and run the .NET app, it would be slightly different.</span></span> <span data-ttu-id="f9e14-162">O resultado final é que a linha do ponto de entrada mais linhas adicionais serão diferentes dependendo da linguagem/plataforma que você escolhe para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f9e14-162">The bottom line is that the ENTRYPOINT line plus additional lines will be different depending on the language/platform you choose for your application.</span></span>

<span data-ttu-id="f9e14-163">**Obter mais informações** para obter informações sobre como criar imagens do Docker para aplicativos .NET Core, vá para <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="f9e14-163">**More info** For information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>

<span data-ttu-id="f9e14-164">Para saber mais sobre como criar suas próprias imagens, vá para [ https://docs.docker.com/engine/\tutoriais/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span><span class="sxs-lookup"><span data-stu-id="f9e14-164">To learn more about building your own images, go to [https://docs.docker.com/engine/\ tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span></span>

<span data-ttu-id="f9e14-165">**Repositórios de imagens em várias plataformas**</span><span class="sxs-lookup"><span data-stu-id="f9e14-165">**Multiplatform image repositories**</span></span>

<span data-ttu-id="f9e14-166">Conforme os contêineres do Windows se tornam mais frequente, um único repositório pode conter variantes de plataforma, como uma imagem do Linux e Windows.</span><span class="sxs-lookup"><span data-stu-id="f9e14-166">As Windows containers become more prevalent, a single repository can contain platform variants, such as a Linux and Windows image.</span></span> <span data-ttu-id="f9e14-167">Este é um novo recurso disponível no Docker que torna possível usar um único repositório para abranger várias plataformas, como fornecedores de [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repositório, que está disponível no registro de DockerHub.</span><span class="sxs-lookup"><span data-stu-id="f9e14-167">This is a new feature coming in Docker that makes it possible for vendors to use a single repository to cover multiple platforms, such as [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository, which is available at DockerHub registry.</span></span> <span data-ttu-id="f9e14-168">Como o recurso é ativado, recebendo essa imagem de um host Windows efetuará o pull a variante do Windows, enquanto recebendo o mesmo nome da imagem de um host Linux obterá a variante de Linux.</span><span class="sxs-lookup"><span data-stu-id="f9e14-168">As the feature comes alive, pulling this image from a Windows host will pull the Windows variant, whereas pulling the same image name from a Linux host will pull the Linux variant.</span></span>

<span data-ttu-id="f9e14-169">***Opção b: criar a imagem base do zero***</span><span class="sxs-lookup"><span data-stu-id="f9e14-169">***Option B: Create your base image from scratch***</span></span>

<span data-ttu-id="f9e14-170">Você pode criar sua própria imagem base do Docker do zero, conforme explicado neste [artigo](https://docs.docker.com/engine/userguide/eng-image/baseimages/) do Docker.</span><span class="sxs-lookup"><span data-stu-id="f9e14-170">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="f9e14-171">Este é um cenário que provavelmente não é melhor para você se você estiver apenas começando com o Docker, mas se você deseja definir os bits específicos de sua própria imagem base, você pode fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="f9e14-171">This is a scenario that is probably not best for you if you are just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="f9e14-172">Etapa 3: Criar as imagens do Docker personalizadas inserindo seu serviço nele</span><span class="sxs-lookup"><span data-stu-id="f9e14-172">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="f9e14-173">Para cada serviço personalizado que consiste em seu aplicativo, você precisará criar uma imagem de relacionados.</span><span class="sxs-lookup"><span data-stu-id="f9e14-173">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="f9e14-174">Se seu aplicativo é composto de um único serviço ou aplicativo web, você precisará apenas uma única imagem.</span><span class="sxs-lookup"><span data-stu-id="f9e14-174">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="f9e14-175">Ao levar em consideração o "loop externo DevOps fluxo de trabalho", as imagens serão criadas por um processo de compilação automatizado sempre que você enviar seu código-fonte para um repositório Git (integração contínua) para que as imagens serão criadas no ambiente global do seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="f9e14-175">When taking into account the "outer-loop DevOps workflow," the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration) so the images will be created in that global environment from your source code.</span></span>

<span data-ttu-id="f9e14-176">Mas, antes de considerarmos indo para essa rota de loop externo, precisamos garantir que o aplicativo do Docker está funcionando corretamente para que eles não enviar por push o código que pode não funcionar corretamente para o sistema de controle do código-fonte (Git, etc.).</span><span class="sxs-lookup"><span data-stu-id="f9e14-176">But, before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>

<span data-ttu-id="f9e14-177">Portanto, cada desenvolvedor deve primeiro fazer todo o processo de loop interno para testar localmente e continuar a desenvolver até que deseja enviar por push a um recurso completo ou altere para o sistema de controle de origem.</span><span class="sxs-lookup"><span data-stu-id="f9e14-177">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="f9e14-178">Para criar uma imagem em seu ambiente local e usando o DockerFile, você pode usar o comando de build do docker, conforme mostrado na Figura 4-19 (você também pode executar compor docker backup – criar aplicativos compostos por vários contêineres/serviços).</span><span class="sxs-lookup"><span data-stu-id="f9e14-178">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-19 (you also can run docker-compose up --build for applications composed by several containers/services).</span></span>

![](./media/image25.png)

<span data-ttu-id="f9e14-179">Figura 4-19: executando o build do docker</span><span class="sxs-lookup"><span data-stu-id="f9e14-179">Figure 4-19: Running docker build</span></span>

<span data-ttu-id="f9e14-180">Opcionalmente, em vez de executar o docker build da pasta do projeto, você primeiro pode gerar uma pasta de implantação com as bibliotecas .NET necessárias usando a execução dotnet publicar o comando e, em seguida, execute o build do docker.</span><span class="sxs-lookup"><span data-stu-id="f9e14-180">Optionally, instead of directly running docker build from the project's folder, you first can generate a deployable folder with the .NET libraries needed by using the run dotnet publish command, and then run docker build.</span></span>

<span data-ttu-id="f9e14-181">Neste exemplo, isso cria uma imagem do Docker com o nome cesardl/netcore-webapi-microsserviço-docker: primeiro (: primeiro, é uma marca, como uma versão específica).</span><span class="sxs-lookup"><span data-stu-id="f9e14-181">In this example, this creates a Docker image with the name cesardl/netcore-webapi-microservice-docker:first (:first is a tag, like a specific version).</span></span> <span data-ttu-id="f9e14-182">Você pode adotar essa etapa para cada imagem personalizada, que você precisa criar seu aplicativo Docker composto com vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="f9e14-182">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="f9e14-183">Você pode encontrar as imagens existentes no seu repositório local (computador de desenvolvimento) usando o docker imagens comando, conforme ilustrado na Figura 4-20.</span><span class="sxs-lookup"><span data-stu-id="f9e14-183">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-20.</span></span>

![](./media/image26.png)

<span data-ttu-id="f9e14-184">Figura 4-20: exibindo imagens existentes usando imagens do docker</span><span class="sxs-lookup"><span data-stu-id="f9e14-184">Figure 4-20: Viewing existing images using docker images</span></span>

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="f9e14-185">Etapa 4: (Opcional) definir seus serviços no docker-compose.yml ao compilar um aplicativo de Docker composto com vários serviços</span><span class="sxs-lookup"><span data-stu-id="f9e14-185">Step 4: (Optional) Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="f9e14-186">Com o arquivo de docker compose.yml, você pode definir um conjunto de serviços relacionados a ser implantado como um aplicativo composto com os comandos de implantação explicados na seção próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="f9e14-186">With the docker-compose.yml file you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="f9e14-187">Você precisa criar esse arquivo em seu principal ou a pasta de solução raiz; ele deve ter um conteúdo semelhante ao arquivo de docker compose.yml a seguir:</span><span class="sxs-lookup"><span data-stu-id="f9e14-187">You need to create that file in your main or root solution folder; it should have a similar content to the following docker-compose.yml file:</span></span>

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

<span data-ttu-id="f9e14-188">Nesse caso específico, esse arquivo define dois serviços: o serviço da web (o personalizado) e o serviço de redis (um serviço de cache populares).</span><span class="sxs-lookup"><span data-stu-id="f9e14-188">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="f9e14-189">Cada serviço será implantado como um contêiner, portanto, precisamos usar uma imagem de Docker concreta para cada.</span><span class="sxs-lookup"><span data-stu-id="f9e14-189">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="f9e14-190">Para este serviço web específico, a imagem será necessário fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f9e14-190">For this particular web service, the image will need to do the following:</span></span>

-   <span data-ttu-id="f9e14-191">Compilação do DockerFile no diretório atual</span><span class="sxs-lookup"><span data-stu-id="f9e14-191">Build from the DockerFile in the current directory</span></span>

-   <span data-ttu-id="f9e14-192">Encaminhar a exposto a porta 80 no contêiner para a porta 81 no computador host</span><span class="sxs-lookup"><span data-stu-id="f9e14-192">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

-   <span data-ttu-id="f9e14-193">Montar o diretório do projeto no host para /code dentro do contêiner, tornando possível para modificar o código sem precisar recriar a imagem</span><span class="sxs-lookup"><span data-stu-id="f9e14-193">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

-   <span data-ttu-id="f9e14-194">Vincular o serviço web para o serviço de redis</span><span class="sxs-lookup"><span data-stu-id="f9e14-194">Link the web service to the redis service</span></span>

<span data-ttu-id="f9e14-195">O serviço de redis usa o [imagem pública redis mais recente](https://hub.docker.com/_/redis/) extraída do registro do Hub do Docker.</span><span class="sxs-lookup"><span data-stu-id="f9e14-195">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="f9e14-196">[redis](https://redis.io/) é um sistema de cache muito popular para aplicativos do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="f9e14-196">[redis](https://redis.io/) is a very popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="f9e14-197">Etapa 5: Criar e executar seu aplicativo de Docker</span><span class="sxs-lookup"><span data-stu-id="f9e14-197">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="f9e14-198">Se seu aplicativo tiver apenas um único contêiner, basta executá-lo, implantando-a para o Host do Docker (VM ou servidor físico).</span><span class="sxs-lookup"><span data-stu-id="f9e14-198">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="f9e14-199">No entanto, se seu aplicativo é composto de vários serviços, você precisa *compô-la*também.</span><span class="sxs-lookup"><span data-stu-id="f9e14-199">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="f9e14-200">Vamos ver as diferentes opções.</span><span class="sxs-lookup"><span data-stu-id="f9e14-200">Let's see the different options.</span></span>

<span data-ttu-id="f9e14-201">***Opção de execução de r: um único contêiner ou serviço***</span><span class="sxs-lookup"><span data-stu-id="f9e14-201">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="f9e14-202">Você pode executar a imagem do Docker usando o comando docker run, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="f9e14-202">You can run the Docker image by using the docker run command, as shown here:</span></span>

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="f9e14-203">Observe que para essa implantação específica, vai redirecionar as solicitações enviadas para a porta 80 para a porta interna 5000.</span><span class="sxs-lookup"><span data-stu-id="f9e14-203">Note that for this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="f9e14-204">Agora, o aplicativo está escutando na porta 80 no nível do host externa.</span><span class="sxs-lookup"><span data-stu-id="f9e14-204">Now, the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="f9e14-205">***Opção b: compor e executar um aplicativo de contêiner de vários***</span><span class="sxs-lookup"><span data-stu-id="f9e14-205">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="f9e14-206">Na maioria dos cenários de empresa, um aplicativo de Docker será ser composto de vários serviços.</span><span class="sxs-lookup"><span data-stu-id="f9e14-206">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="f9e14-207">Nesses casos, você pode executar o comando docker-compor para cima (Figura 4-21), que usará o arquivo de docker compose.yml que talvez você tenha criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f9e14-207">For these cases, you can run the command docker-compose up (Figure 4-21), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="f9e14-208">A execução desse comando implanta um aplicativo composto com todos os seus contêineres relacionados.</span><span class="sxs-lookup"><span data-stu-id="f9e14-208">Running this command deploys a composed application with all of its related containers.</span></span>

![](./media/image27.png)

<span data-ttu-id="f9e14-209">Figura 4-21: resultados da execução do comando "docker-compor a"</span><span class="sxs-lookup"><span data-stu-id="f9e14-209">Figure 4-21: Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="f9e14-210">Após a execução do docker-compor backup, você implantar seu aplicativo e seus contêineres relacionados em seu Host do Docker, conforme ilustrado na Figura 4-22, a representação de VM.</span><span class="sxs-lookup"><span data-stu-id="f9e14-210">After you run docker-compose up, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-22, in the VM representation.</span></span>

![](./media/image28.png)

<span data-ttu-id="f9e14-211">Figura 4-22: VM com contêineres do Docker implantado</span><span class="sxs-lookup"><span data-stu-id="f9e14-211">Figure 4-22: VM with Docker containers deployed</span></span>

<span data-ttu-id="f9e14-212">Observação compor docker backup e docker executar pode ser suficiente para os contêineres de teste em seu ambiente de desenvolvimento, mas você talvez não usá-los em todos os se você está esperando trabalhar com clusters de Docker e orchestrators como Docker Swarm, Mesosphere DC/sistema operacional ou Kubernetes para poder dimensionar.</span><span class="sxs-lookup"><span data-stu-id="f9e14-212">Note docker-compose up and docker run might be enough for testing your containers in your development environment, but you might not use them at all if you are expecting to work with Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes in order to be able to scale up.</span></span> <span data-ttu-id="f9e14-213">Se você estiver usando um cluster como [Docker Swarm modo](https://docs.docker.com/engine/swarm/) (disponível no Docker para Windows e Mac desde a versão 1.12), você precisa implantar e testar com comandos adicionais, como criar serviço do docker para serviços únicos ou quando estiver Implantando um aplicativo composto por vários contêineres, usando o docker compõem o pacote e implantar o docker myBundleFile, ao implantar o aplicativo composto como uma pilha, conforme explicado no artigo [pacotes de aplicativos distribuídos](https://blog.docker.com/2016/06/docker-app-bundle/) do Docker.</span><span class="sxs-lookup"><span data-stu-id="f9e14-213">If you're using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker for Windows and Mac since version 1.12), you need to deploy and test with additional commands such as docker service create for single services, or when you're deploying an app composed of several containers, using docker compose bundle and docker deploy myBundleFile, by deploying the composed app as a stack, as explained in the article [Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) from Docker.</span></span>

<span data-ttu-id="f9e14-214">Para [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) e [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) você usaria comandos de implantação diferentes e scripts, também.</span><span class="sxs-lookup"><span data-stu-id="f9e14-214">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) you would use different deployment commands and scripts, as well.</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="f9e14-215">Etapa 6: Testar seu aplicativo de Docker (localmente, em sua VM local do CD)</span><span class="sxs-lookup"><span data-stu-id="f9e14-215">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="f9e14-216">Esta etapa irá variar dependendo de seu aplicativo está funcionando.</span><span class="sxs-lookup"><span data-stu-id="f9e14-216">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="f9e14-217">Uma muito simple .NET Core API da Web "Olá, mundo" implantado como um único contêiner ou um serviço, você apenas precisa acessar o serviço, fornecendo a porta TCP especificada no DockerFile.</span><span class="sxs-lookup"><span data-stu-id="f9e14-217">In a very simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="f9e14-218">Se o host local não está ativado, para navegar até o seu serviço, localize o endereço IP para a máquina usando este comando:</span><span class="sxs-lookup"><span data-stu-id="f9e14-218">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

<span data-ttu-id="f9e14-219">ip de máquinas de docker *seu nome de contêiner*</span><span class="sxs-lookup"><span data-stu-id="f9e14-219">docker-machine ip *your-container-name*</span></span>

<span data-ttu-id="f9e14-220">No host do Docker, abra um navegador e navegue para o site; Você deve ver o aplicativo/serviço em execução, conforme mostrado na Figura 4-23.</span><span class="sxs-lookup"><span data-stu-id="f9e14-220">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-23.</span></span>

![](./media/image29.png)

<span data-ttu-id="f9e14-221">Figura 4-23: testar seu aplicativo de Docker localmente usando localhost</span><span class="sxs-lookup"><span data-stu-id="f9e14-221">Figure 4-23: Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="f9e14-222">Observe que ele está usando a porta 80, mas internamente ele estava sendo redirecionado para porta 5000, pois é como ele foi implantado com docker run, conforme explicado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f9e14-222">Note that it is using port 80, but internally it was being redirected to port 5000, because that's how it was deployed with docker run, as explained earlier.</span></span>

<span data-ttu-id="f9e14-223">Você pode testar isso, usando a ROTAÇÃO de terminal.</span><span class="sxs-lookup"><span data-stu-id="f9e14-223">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="f9e14-224">Em uma instalação de Docker no Windows, o IP padrão é 10.0.75.1, conforme ilustrado na Figura 4-24.</span><span class="sxs-lookup"><span data-stu-id="f9e14-224">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-24.</span></span>

![](./media/image30.png)

<span data-ttu-id="f9e14-225">Figura 4-24: Testando um aplicativo de Docker localmente usando ONDULAÇÃO</span><span class="sxs-lookup"><span data-stu-id="f9e14-225">Figure 4-24: Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="f9e14-226">**Depuração de um contêiner em execução no Docker**</span><span class="sxs-lookup"><span data-stu-id="f9e14-226">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="f9e14-227">Código do Visual Studio oferece suporte à depuração Docker se você estiver usando o Node. js e outras plataformas como contêineres de núcleo do .NET.</span><span class="sxs-lookup"><span data-stu-id="f9e14-227">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="f9e14-228">Você também pode depurar recipientes de núcleo do .NET do Docker ao usar o Visual Studio, conforme descrito na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="f9e14-228">You also can debug .NET Core containers in Docker when using Visual Studio, as described in the next section.</span></span>

<span data-ttu-id="f9e14-229">**Obter mais informações:** para saber mais sobre a depuração de contêineres do Docker Node. js, vá para <https://blog.docker.com/2016/07/live-debugging-docker/> e [ https://blogs.msdn.microsoft.com/\ usuário\_ed/2016/02/27 / Visual-Studio-Code-New-Features-13-big-Debugging-Updates-Rich-Object-hover-Conditional-Breakpoints-Node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span><span class="sxs-lookup"><span data-stu-id="f9e14-229">**More info:** To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and [https://blogs.msdn.microsoft.com/\ user\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f9e14-230">[Anterior] (docker-aplicativos-desenvolvimento-environment.md) [Avançar] (visual-studio-ferramentas-para-docker.md)</span><span class="sxs-lookup"><span data-stu-id="f9e14-230">[Previous] (docker-apps-development-environment.md) [Next] (visual-studio-tools-for-docker.md)</span></span>
