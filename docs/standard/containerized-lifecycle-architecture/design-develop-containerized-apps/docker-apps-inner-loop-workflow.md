---
title: Fluxo de trabalho de desenvolvimento do loop interno para aplicativos do Docker
description: Aprenda o fluxo de trabalho de "loop interno" para o desenvolvimento de aplicativos do Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 36fcf5769376375854c2a2631e26e8b136df0de6
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920903"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="e0bdf-103">Fluxo de trabalho de desenvolvimento do loop interno para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="e0bdf-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="e0bdf-104">Antes de disparar o fluxo de trabalho de loop externo que abrangem o DevOps todo ciclo, tudo começa em cada computador de desenvolvedor, codificando o aplicativo em si, usando seus idiomas preferenciais ou plataformas e testá-lo localmente (Figura 4-21).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="e0bdf-105">Mas, em todos os casos, você terá um ponto importante em comum, não importa qual linguagem, estrutura ou plataformas você escolher.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="e0bdf-106">Nesse fluxo de trabalho específico, você sempre está desenvolvendo e testando contêineres do Docker, mas localmente.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![Etapa 1 - código/execução/depuração](./media/image18.png)

<span data-ttu-id="e0bdf-108">**Figura 4-21**.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-108">**Figure 4-21**.</span></span> <span data-ttu-id="e0bdf-109">Contexto de desenvolvimento de loop interno</span><span class="sxs-lookup"><span data-stu-id="e0bdf-109">Inner-loop development context</span></span>

<span data-ttu-id="e0bdf-110">O contêiner ou uma instância de uma imagem de Docker conterá esses componentes:</span><span class="sxs-lookup"><span data-stu-id="e0bdf-110">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="e0bdf-111">Uma seleção do sistema operacional (por exemplo, uma distribuição Linux ou Windows)</span><span class="sxs-lookup"><span data-stu-id="e0bdf-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="e0bdf-112">Arquivos adicionados pelo desenvolvedor (por exemplo, binários de aplicativo)</span><span class="sxs-lookup"><span data-stu-id="e0bdf-112">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="e0bdf-113">Configuração (por exemplo, as configurações de ambiente e dependências)</span><span class="sxs-lookup"><span data-stu-id="e0bdf-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="e0bdf-114">Instruções para quais processos para ser executado pelo Docker</span><span class="sxs-lookup"><span data-stu-id="e0bdf-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="e0bdf-115">Você pode configurar o fluxo de trabalho de desenvolvimento do loop interno que utiliza o Docker como o processo (descrito na próxima seção).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="e0bdf-116">Considere as etapas iniciais para configurar o ambiente não são incluídas, porque você só precisa fazê-lo uma vez.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="e0bdf-117">Criação de um único aplicativo dentro de um contêiner do Docker usando o Visual Studio Code e CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="e0bdf-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="e0bdf-118">Aplicativos são compostos de seus próprios serviços e bibliotecas adicionais (dependências).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="e0bdf-119">Figura 4-22 mostra as etapas básicas que você normalmente precisará realizar ao compilar um aplicativo do Docker, seguido por descrições detalhadas de cada etapa.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Visão geral do fluxo de trabalho: Etapa 1: código, etapa 2 - escrever Dockerfiles, etapa 3 - criar imagens definidas com Dockerfiles, etapa 4 – definir serviços com o arquivo docker-Compose, etapa 5: executar contêineres ou aplicativos compostos, etapa 6 - teste de aplicativos, etapa 7 – enviar por Push para iniciar o loop externo (pipelines de CI/CD) ou continuar de veloping.](./media/image19.png)

<span data-ttu-id="e0bdf-121">**Figura 4-22**.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-121">**Figure 4-22**.</span></span> <span data-ttu-id="e0bdf-122">Fluxo de trabalho de alto nível para o ciclo de vida de aplicativos do Docker em contêineres usando a CLI do Docker</span><span class="sxs-lookup"><span data-stu-id="e0bdf-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="e0bdf-123">Etapa 1: Iniciar a codificação no Visual Studio Code e crie sua linha de base inicial/serviço de aplicativo</span><span class="sxs-lookup"><span data-stu-id="e0bdf-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="e0bdf-124">A maneira de desenvolver seu aplicativo é semelhante à forma como você pode fazê-lo sem o Docker.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="e0bdf-125">A diferença é que, durante o desenvolvimento, você está implantando e testando seu aplicativo ou serviços em execução em contêineres do Docker colocados no seu ambiente local (como uma VM do Linux ou Windows).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

**<span data-ttu-id="e0bdf-126">Como configurar seu ambiente local</span><span class="sxs-lookup"><span data-stu-id="e0bdf-126">Setting up your local environment</span></span>**

<span data-ttu-id="e0bdf-127">Com as versões mais recentes do Docker para Mac e Windows, é mais fácil do que nunca para desenvolver aplicativos do Docker e a instalação é simples.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [! INFORMAÇÕES]
>
> <span data-ttu-id="e0bdf-129">Para obter instruções sobre como configurar o Docker para Windows, acesse <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-129">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="e0bdf-130">Para obter instruções sobre como configurar o Docker para Mac, acesse <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-130">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="e0bdf-131">Além disso, será necessário um editor de código, de modo que, na verdade, você pode desenvolver seu aplicativo enquanto estiver usando a CLI do Docker.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-131">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="e0bdf-132">A Microsoft fornece o Visual Studio Code, que é um editor de código leve que tem suporte no Mac, Windows e Linux e fornece o IntelliSense com [suporte para várias linguagens](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python e mais linguagens modernas), [depurando](https://code.visualstudio.com/Docs/editor/debugging), [integração com o Git](https://code.visualstudio.com/Docs/editor/versioncontrol) e [suporte a extensões](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-132">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="e0bdf-133">Esse editor é uma excelente opção para os desenvolvedores do Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-133">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="e0bdf-134">No Windows, você também pode usar o aplicativo completo do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-134">In Windows, you also can use the full Visual Studio application.</span></span>

> [! INFORMAÇÕES]
>
> <span data-ttu-id="e0bdf-136">Para obter instruções sobre como instalar o Visual Studio código para Windows, Mac ou Linux, vá para <https://code.visualstudio.com/docs/setup/setup-overview/>.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-136">For instructions on installing Visual Studio Code for Windows, Mac, or Linux, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="e0bdf-137">Para obter instruções sobre como configurar o Docker para Mac, acesse <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-137">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="e0bdf-138">Você pode trabalhar com a CLI do Docker e escrever seu código usando qualquer editor de código, mas usando o Visual Studio Code com a extensão Docker torna mais fácil para o autor `Dockerfile` e `docker-compose.yml` arquivos em seu espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-138">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="e0bdf-139">Você também pode executar tarefas e scripts do IDE do Visual Studio código para executar comandos do Docker usando a CLI do Docker abaixo.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-139">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="e0bdf-140">A extensão do Docker para VS Code fornece os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="e0bdf-140">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="e0bdf-141">Automática `Dockerfile` e `docker-compose.yml` geração de arquivo</span><span class="sxs-lookup"><span data-stu-id="e0bdf-141">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="e0bdf-142">Dicas de sintaxe realce e passe o mouse para `docker-compose.yml` e `Dockerfile` arquivos</span><span class="sxs-lookup"><span data-stu-id="e0bdf-142">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="e0bdf-143">IntelliSense (preenchimentos) para `Dockerfile` e `docker-compose.yml` arquivos</span><span class="sxs-lookup"><span data-stu-id="e0bdf-143">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="e0bdf-144">Linting (erros e avisos) para `Dockerfile` arquivos</span><span class="sxs-lookup"><span data-stu-id="e0bdf-144">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="e0bdf-145">Integração de paleta (F1) para os comandos mais comuns do Docker de comando</span><span class="sxs-lookup"><span data-stu-id="e0bdf-145">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="e0bdf-146">Integração com o Gerenciador para gerenciar imagens e contêineres</span><span class="sxs-lookup"><span data-stu-id="e0bdf-146">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="e0bdf-147">Implantar imagens do DockerHub e registros de contêiner do Azure para o serviço de aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="e0bdf-147">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="e0bdf-148">Para instalar a extensão do Docker, pressione Ctrl + Shift + P, digite `ext install`, e, em seguida, execute o comando de extensão de instalação para abrir a lista de extensões do Marketplace.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-148">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="e0bdf-149">Em seguida, digite **docker** para filtrar os resultados e, em seguida, selecione a extensão de suporte do Docker, conforme ilustrado na Figura 4 a 23.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-149">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Modo de exibição da extensão do Docker para VS Code.](./media/image20.png)

<span data-ttu-id="e0bdf-151">**Figura 4-23**.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-151">**Figure 4-23**.</span></span> <span data-ttu-id="e0bdf-152">Instalando a extensão do Docker no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e0bdf-152">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="e0bdf-153">Etapa 2: Criar um DockerFile relacionado a uma imagem existente (sem formatação do sistema operacional ou ambientes de desenvolvimento, como Ruby, Node. js e .NET Core)</span><span class="sxs-lookup"><span data-stu-id="e0bdf-153">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="e0bdf-154">Você precisará de um `DockerFile` por uma imagem personalizada a ser criado e por contêiner a ser implantado.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-154">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="e0bdf-155">Se seu aplicativo é composto por um único serviço personalizado, você precisará de um único `DockerFile`.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-155">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="e0bdf-156">Mas se seu aplicativo é composto de vários serviços (como em uma arquitetura de microsserviços), você precisará de uma `Dockerfile` por serviço.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-156">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="e0bdf-157">O `DockerFile` normalmente é colocado na pasta raiz do seu aplicativo ou serviço e contém os comandos necessários para que o Docker Saiba como configurar e executar esse aplicativo ou serviço.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-157">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="e0bdf-158">Você pode criar seu `DockerFile` e adicioná-lo ao seu projeto, juntamente com seu código (Node. js, .NET Core, etc.), ou, se você for novo no ambiente, examine a seguinte dica.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-158">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
>
> <span data-ttu-id="e0bdf-159">Você pode usar a extensão do Docker para orientá-lo ao usar o `Dockerfile` e `docker-compose.yml` arquivos relacionados ao seus contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-159">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="e0bdf-160">Por fim, você provavelmente vai gravar esses tipos de arquivos sem essa ferramenta, mas usando a extensão do Docker é um bom ponto de partida que acelerará sua curva de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-160">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="e0bdf-161">Na Figura 4-24, você pode ver como o docker-compose arquivo for adicionado usando a extensão do Docker para VS Code.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-161">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![Exibição do console da extensão do Docker para VS Code.](./media/image24.png)

<span data-ttu-id="e0bdf-163">**Figura 4-24**.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-163">**Figure 4-24**.</span></span> <span data-ttu-id="e0bdf-164">Arquivos do docker adicionados usando o **arquivos Docker adicionar ao comando de espaço de trabalho**</span><span class="sxs-lookup"><span data-stu-id="e0bdf-164">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="e0bdf-165">Quando você adiciona um DockerFile, você especificar qual imagem base do Docker, você vai usar (como o uso de `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-165">When you add a DockerFile, you specify what base Docker image you’ll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="e0bdf-166">Normalmente, você criará sua imagem personalizada na parte superior de uma imagem de base que você obteve de qualquer repositório oficial, nos [registro de Hub do Docker](https://hub.docker.com/) (como um [imagem para o .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) o um ou mais [para Node. js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-166">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

***<span data-ttu-id="e0bdf-167">Usar uma imagem de Docker oficial existente</span><span class="sxs-lookup"><span data-stu-id="e0bdf-167">Use an existing official Docker image</span></span>***

<span data-ttu-id="e0bdf-168">Usando um repositório oficial de uma pilha de idiomas com um número de versão garante que os mesmos recursos de idioma estão disponíveis em todos os computadores (incluindo desenvolvimento, teste e produção).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-168">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="e0bdf-169">Este é um DockerFile de exemplo para um contêiner do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="e0bdf-169">The following is a sample DockerFile for a .NET Core container:</span></span>

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.1
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="e0bdf-170">Nesse caso, a imagem se baseia na versão 2.1 da imagem de docker do ASP.NET Core oficial (de várias arquiteturas para Linux e Windows), de acordo com a linha `FROM mcr.microsoft.com/dotnet/core/aspnet:2.1`.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-170">In this case, the image is based on version 2.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.1`.</span></span> <span data-ttu-id="e0bdf-171">(Para obter mais informações sobre esse tópico, consulte o [imagem do Docker do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) página e o [imagem do Docker do .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) página).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-171">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="e0bdf-172">No DockerFile, você também pode instruir o Docker a escutar na porta TCP que você usará em tempo de execução (como a porta 80).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-172">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="e0bdf-173">Você pode especificar mais definições de configurações no Dockerfile, dependendo da linguagem e da estrutura usadas.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-173">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="e0bdf-174">Por exemplo, o `ENTRYPOINT` de linha com `["dotnet", "MySingleContainerWebApp.dll"]` diz ao Docker para executar um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-174">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="e0bdf-175">Se você estiver usando o SDK e a CLI do .NET Core (`dotnet CLI`) para compilar e executar o aplicativo .NET, essa configuração será diferente.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-175">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="e0bdf-176">O ponto principal aqui é que a linha ENTRYPOINT e outras configurações dependem do idioma e plataforma que escolher para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-176">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [! INFORMAÇÕES]
>
> <span data-ttu-id="e0bdf-178">Para obter mais informações sobre a criação de imagens do Docker para aplicativos .NET Core, acesse <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-178">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="e0bdf-179">Para saber mais sobre como criar suas próprias imagens, acesse <https://docs.docker.com/engine/tutorials/dockerimages/>.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-179">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

**<span data-ttu-id="e0bdf-180">Usar repositórios de imagem para várias arquiteturas</span><span class="sxs-lookup"><span data-stu-id="e0bdf-180">Use multi-arch image repositories</span></span>**

<span data-ttu-id="e0bdf-181">Um nome de imagem única em um repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-181">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="e0bdf-182">Esse recurso permite que os fornecedores, como a Microsoft (criadores de imagem base) criar um único repositório para abranger várias plataformas (ou seja, Linux e Windows).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-182">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="e0bdf-183">Por exemplo, o [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repositório disponível no registro do Hub do Docker fornece suporte para Linux e Windows Nano Server usando o mesmo nome de imagem.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-183">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="e0bdf-184">Extraindo o [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) pulls de imagem de um host do Windows a variante do Windows, ao passo que recebendo o mesmo nome de imagem de um host Linux efetua pull da variante do Linux.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-184">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

***<span data-ttu-id="e0bdf-185">Criar sua imagem de base a partir do zero</span><span class="sxs-lookup"><span data-stu-id="e0bdf-185">Create your base image from scratch</span></span>***

<span data-ttu-id="e0bdf-186">Você pode criar sua própria imagem base do Docker do zero, conforme explicado neste [artigo](https://docs.docker.com/engine/userguide/eng-image/baseimages/) do Docker.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-186">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="e0bdf-187">Esse cenário provavelmente não é o melhor para você, se você estiver começando com o Docker, mas se você quiser definir as partes específicas de sua própria imagem base, você pode fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-187">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="e0bdf-188">Etapa 3: Criar imagens personalizadas do Docker inserindo seu serviço nele</span><span class="sxs-lookup"><span data-stu-id="e0bdf-188">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="e0bdf-189">Para cada serviço personalizado que consiste em seu aplicativo, você precisará criar uma imagem relacionada.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-189">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="e0bdf-190">Se seu aplicativo é composto por um único serviço ou aplicativo web, você precisará apenas uma única imagem.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-190">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
>
> <span data-ttu-id="e0bdf-191">Ao levar em consideração o "loop externo DevOps fluxo de trabalho", as imagens serão criadas por um processo de build automatizado sempre que você enviar por push seu código-fonte para um repositório Git (integração contínua), portanto, as imagens serão criadas no ambiente global do seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-191">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="e0bdf-192">Mas antes de considerarmos indo para aquela rota de loop externo, é necessário garantir que o aplicativo do Docker está funcionando corretamente, de modo que eles não envie por push o código que pode não funcionar corretamente para o sistema de controle do código-fonte (Git, etc.).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-192">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="e0bdf-193">Portanto, cada desenvolvedor precisa primeiro fazer todo o processo de loop interno para testar localmente e continuar a desenvolver até que eles querem enviar por push a um recurso completo ou altere para o sistema de controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-193">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="e0bdf-194">Para criar uma imagem no seu ambiente local e usando o DockerFile, você pode usar o comando docker build, conforme demonstrado na Figura 4-25 (você também pode executar `docker-compose up --build` para aplicativos compostos por vários contêineres/serviços).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-194">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you also can run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![Saída do console de build do docker-Compose, que mostra as imagens de progresso de download.](./media/image25.png)

<span data-ttu-id="e0bdf-196">**Figura 4-25**.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-196">**Figure 4-25**.</span></span> <span data-ttu-id="e0bdf-197">Compilação do docker em execução</span><span class="sxs-lookup"><span data-stu-id="e0bdf-197">Running docker build</span></span>

<span data-ttu-id="e0bdf-198">Opcionalmente, em vez de diretamente em execução `docker build` da pasta do projeto, você pode gerar primeiro uma pasta implantável com as bibliotecas .NET necessárias por meio da execução `dotnet publish` de comando e, em seguida, executar `docker build`.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-198">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="e0bdf-199">Este exemplo cria uma imagem do Docker com o nome `cesardl/netcore-webapi-microservice-docker:first` (`:first` é uma marca, como uma versão específica).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-199">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="e0bdf-200">Você pode executar esta etapa para cada imagem personalizada, que você precisará criar seu aplicativo composto do Docker com vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-200">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="e0bdf-201">Você pode encontrar imagens existentes no seu repositório local (computador de desenvolvimento) usando o docker imagens comando, conforme ilustrado na Figura 4-26.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-201">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![Console de saída do comando docker images, que mostra imagens existentes.](./media/image26.png)

<span data-ttu-id="e0bdf-203">**Figura 4-26**.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-203">**Figure 4-26**.</span></span> <span data-ttu-id="e0bdf-204">Visualização das imagens existentes usando imagens do docker</span><span class="sxs-lookup"><span data-stu-id="e0bdf-204">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="e0bdf-205">Etapa 4: Definir os serviços no docker-Compose. yml ao compilar um aplicativo composto do Docker com vários serviços</span><span class="sxs-lookup"><span data-stu-id="e0bdf-205">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="e0bdf-206">Com o `docker-compose.yml` arquivo, você pode definir um conjunto de serviços relacionados para ser implantado como um aplicativo composto com os comandos de implantação, explicados na seção próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-206">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="e0bdf-207">Crie esse arquivo em seu principal ou a pasta raiz da solução; ele deve ter conteúdo semelhante ao mostrado neste `docker-compose.yml` arquivo:</span><span class="sxs-lookup"><span data-stu-id="e0bdf-207">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: '3.4'
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

<span data-ttu-id="e0bdf-208">Nesse caso específico, esse arquivo define dois serviços: o serviço web (seu serviço personalizado) e o serviço de redis (um serviço de cache populares).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-208">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="e0bdf-209">Cada serviço será implantado como um contêiner, portanto, precisamos usar uma imagem do Docker concreta para cada um.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-209">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="e0bdf-210">Para este serviço da web específica, a imagem será necessário fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e0bdf-210">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="e0bdf-211">Build do DockerFile no diretório atual</span><span class="sxs-lookup"><span data-stu-id="e0bdf-211">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="e0bdf-212">Encaminhar a porta 80 no contêiner para a porta 81 no computador host, exposta</span><span class="sxs-lookup"><span data-stu-id="e0bdf-212">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="e0bdf-213">Montar o diretório do projeto no host para /code dentro do contêiner, possibilitando que você pode modificar o código sem ter que recompilar a imagem</span><span class="sxs-lookup"><span data-stu-id="e0bdf-213">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="e0bdf-214">Vincular o serviço web para o serviço de redis</span><span class="sxs-lookup"><span data-stu-id="e0bdf-214">Link the web service to the redis service</span></span>

<span data-ttu-id="e0bdf-215">O serviço do redis usa o [imagem mais recente do redis público](https://hub.docker.com/_/redis/) extraído do registro de Hub do Docker.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-215">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="e0bdf-216">[redis](https://redis.io/) é um sistema de cache populares para aplicativos do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-216">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="e0bdf-217">Etapa 5: Compilar e executar seu aplicativo do Docker</span><span class="sxs-lookup"><span data-stu-id="e0bdf-217">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="e0bdf-218">Se seu aplicativo tem apenas um único contêiner, basta executá-lo Implantando-o em seu Host do Docker (VM ou servidor físico).</span><span class="sxs-lookup"><span data-stu-id="e0bdf-218">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="e0bdf-219">No entanto, se seu aplicativo é composto por vários serviços, você precisará *compô-la*também.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-219">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="e0bdf-220">Vamos ver as diferentes opções.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-220">Let's see the different options.</span></span>

***<span data-ttu-id="e0bdf-221">Opção A: Executar um único contêiner ou serviço</span><span class="sxs-lookup"><span data-stu-id="e0bdf-221">Option A: Run a single container or service</span></span>***

<span data-ttu-id="e0bdf-222">Você pode executar a imagem do Docker usando o comando docker run, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="e0bdf-222">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="e0bdf-223">Para essa implantação específica, podemos irá redirecionar as solicitações enviadas para a porta 80 para a porta interna 5000.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-223">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="e0bdf-224">Agora o aplicativo está escutando na porta 80 no nível do host externa.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-224">Now the application is listening on the external port 80 at the host level.</span></span>

***<span data-ttu-id="e0bdf-225">Opção B: Compor e executar um aplicativo de vários contêineres</span><span class="sxs-lookup"><span data-stu-id="e0bdf-225">Option B: Compose and run a multiple-container application</span></span>***

<span data-ttu-id="e0bdf-226">Na maioria dos cenários empresariais, um aplicativo do Docker será ser composto de vários serviços.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-226">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="e0bdf-227">Nesses casos, você pode executar o `docker-compose up` comando (Figura 4-27), que usará o arquivo docker-Compose. yml que talvez você tenha criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-227">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="e0bdf-228">Executar esse comando implanta um aplicativo composto com todos os seus contêineres relacionados.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-228">Running this command deploys a composed application with all of its related containers.</span></span>

![Saída a partir do console de-comando docker compose up.](./media/image27.png)

<span data-ttu-id="e0bdf-230">**Figura 4-27**.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-230">**Figure 4-27**.</span></span> <span data-ttu-id="e0bdf-231">Resultados da execução do comando "docker-compose up"</span><span class="sxs-lookup"><span data-stu-id="e0bdf-231">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="e0bdf-232">Depois de executar `docker-compose up`, implantar seu aplicativo e seus contêineres relacionados no Host do Docker, conforme ilustrado na Figura 4-28, na representação de VM.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-232">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![VM executando aplicativos de vários contêineres.](./media/image28.png)

<span data-ttu-id="e0bdf-234">**Figura 4-28**.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-234">**Figure 4-28**.</span></span> <span data-ttu-id="e0bdf-235">VM com contêineres do Docker implantados</span><span class="sxs-lookup"><span data-stu-id="e0bdf-235">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="e0bdf-236">Etapa 6: Testar seu aplicativo do Docker (localmente, em sua VM local do CD)</span><span class="sxs-lookup"><span data-stu-id="e0bdf-236">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="e0bdf-237">Esta etapa irá variar dependendo de seu aplicativo está funcionando.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-237">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="e0bdf-238">Uma simple API do .NET Core Web "Hello World" implantado como um único contêiner ou serviço, você apenas precisará acessar o serviço, fornecendo a porta TCP especificada no DockerFile.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-238">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="e0bdf-239">Se o host local não está ativado, para navegar até seu serviço, localize o endereço IP para a máquina usando este comando:</span><span class="sxs-lookup"><span data-stu-id="e0bdf-239">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="e0bdf-240">No host do Docker, abra um navegador e navegue até o site; Você deve ver seu aplicativo ou serviço em execução, conforme demonstrado na Figura 4-29.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-240">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Modo de exibição de navegador da resposta do localhost/API/values.](./media/image29.png)

<span data-ttu-id="e0bdf-242">**Figura 4-29**.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-242">**Figure 4-29**.</span></span> <span data-ttu-id="e0bdf-243">Teste seu aplicativo do Docker localmente usando localhost</span><span class="sxs-lookup"><span data-stu-id="e0bdf-243">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="e0bdf-244">Observe que ele está usando a porta 80, mas internamente está sendo redirecionado para a porta 5000, pois é como ele foi implantado com `docker run`, conforme explicado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-244">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="e0bdf-245">Você pode testar isso usando o CURL no terminal.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-245">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="e0bdf-246">Em uma instalação do Docker no Windows, o IP padrão é 10.0.75.1, conforme ilustrado na Figura 4-30.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-246">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![Saída de Introdução do console a http://10.0.75.1/API/values com curl](./media/image30.png)

<span data-ttu-id="e0bdf-248">**Figura 4-30**.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-248">**Figure 4-30**.</span></span> <span data-ttu-id="e0bdf-249">Testando um aplicativo do Docker localmente usando CURL</span><span class="sxs-lookup"><span data-stu-id="e0bdf-249">Testing a Docker application locally by using CURL</span></span>

**<span data-ttu-id="e0bdf-250">Depuração de um contêiner em execução no Docker</span><span class="sxs-lookup"><span data-stu-id="e0bdf-250">Debugging a container running on Docker</span></span>**

<span data-ttu-id="e0bdf-251">Visual Studio Code dá suporte à depuração Docker se você estiver usando o Node. js e outras plataformas como contêineres do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-251">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="e0bdf-252">Você também pode depurar contêineres do .NET Core ou .NET Framework no Docker ao usar o Visual Studio para Windows ou Mac, conforme descrito na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-252">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [! INFORMAÇÕES]
>
> <span data-ttu-id="e0bdf-254">Para saber mais sobre a depuração de contêineres do Docker do Node. js, acesse <https://blog.docker.com/2016/07/live-debugging-docker/> e <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span><span class="sxs-lookup"><span data-stu-id="e0bdf-254">To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e0bdf-255">[Anterior](docker-apps-development-environment.md)
>[Próximo](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="e0bdf-255">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
