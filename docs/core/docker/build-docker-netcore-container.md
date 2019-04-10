---
title: 'Tutorial: Colocar em contêiner um aplicativo com o Docker'
description: Neste tutorial, você aprenderá a colocar um aplicativo .NET Core em contêiner com o Docker.
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 8255a901c706e55e143cdf23dda0eb9bc79d245d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58844956"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="d9e8c-103">Tutorial: Colocar em contêiner um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="d9e8c-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="d9e8c-104">Este tutorial ensina como criar uma imagem do Docker que contenha seu aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="d9e8c-105">A imagem pode ser usada para criar contêineres para seu ambiente de desenvolvimento local, nuvem privada ou nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="d9e8c-106">Neste tutorial, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-106">In this tutorial you will learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="d9e8c-107">Criar um Dockerfile</span><span class="sxs-lookup"><span data-stu-id="d9e8c-107">Create a Dockerfile</span></span>
> * <span data-ttu-id="d9e8c-108">Efetuar pull de uma imagem base do Docker no Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="d9e8c-108">Pull a Microsoft .NET Core Docker base image</span></span>
> * <span data-ttu-id="d9e8c-109">Personalizar e implantar seu aplicativo para a imagem</span><span class="sxs-lookup"><span data-stu-id="d9e8c-109">Customize and deploy your app to the image</span></span>
> * <span data-ttu-id="d9e8c-110">Criar e executar um contêiner</span><span class="sxs-lookup"><span data-stu-id="d9e8c-110">Create and run a container</span></span>
> * <span data-ttu-id="d9e8c-111">Implantar no Azure</span><span class="sxs-lookup"><span data-stu-id="d9e8c-111">Deploy to Azure</span></span>

<span data-ttu-id="d9e8c-112">Este tutorial ensina as tarefas de build e implantação de contêiner do Docker para um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-112">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="d9e8c-113">A [plataforma Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) usa o [Mecanismo do Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) para criar e empacotar aplicativos com agilidade [imagens do Docker](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="d9e8c-113">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="d9e8c-114">Essas imagens são gravadas no formato [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) para serem implantadas e executadas em um [contêiner em camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="d9e8c-114">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>



## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="d9e8c-115">.NET Core: A maneira mais fácil para começar</span><span class="sxs-lookup"><span data-stu-id="d9e8c-115">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="d9e8c-116">Antes de criar a imagem do Docker, é necessário ter um aplicativo para colocá-lo em contêiner.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-116">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="d9e8c-117">Crie-o no Linux, MacOS ou Windows.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-117">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="d9e8c-118">A maneira mais rápida e fácil de fazer isso é usando o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-118">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="d9e8c-119">Se não estiver familiarizado com o conjunto de ferramentas da CLI do .NET Core, leia a [Visão geral do SDK do .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9e8c-119">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="d9e8c-120">Criar contêineres do Windows e Linux com [marcas baseadas em vários arcos](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="d9e8c-120">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="d9e8c-121">Seu primeiro aplicativo .NET Core do Docker</span><span class="sxs-lookup"><span data-stu-id="d9e8c-121">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d9e8c-122">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d9e8c-122">Prerequisites</span></span>

<span data-ttu-id="d9e8c-123">Para concluir este tutorial:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-123">To complete this tutorial:</span></span>

#### <a name="net-core-sdk"></a><span data-ttu-id="d9e8c-124">SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d9e8c-124">.NET Core SDK</span></span>

* <span data-ttu-id="d9e8c-125">Instale o [SDK do .NET Core 2.1](https://www.microsoft.com/net/download) ou posterior.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-125">Install [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later.</span></span>

<span data-ttu-id="d9e8c-126">Consulte [Versões de sistema operacional compatíveis com .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) para obter a lista completa de sistemas operacionais compatíveis com .NET Core 2.1, versões de sistema operacional não compatíveis e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-126">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="d9e8c-127">Instale seu editor de código favorito, caso ainda não tenha um.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-127">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="d9e8c-128">Precisa instalar um editor de código?</span><span class="sxs-lookup"><span data-stu-id="d9e8c-128">Need to install a code editor?</span></span> <span data-ttu-id="d9e8c-129">Experimente o [Visual Studio Code](https://code.visualstudio.com/download)!</span><span class="sxs-lookup"><span data-stu-id="d9e8c-129">Try [Visual Studio Code](https://code.visualstudio.com/download)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="d9e8c-130">Instalando o Cliente do Docker</span><span class="sxs-lookup"><span data-stu-id="d9e8c-130">Installing Docker Client</span></span>

<span data-ttu-id="d9e8c-131">Instale o [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) ou cliente do Docker posterior.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-131">Install [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="d9e8c-132">O cliente do Docker pode ser instalado em:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-132">The Docker client can be installed in:</span></span>

* <span data-ttu-id="d9e8c-133">Distribuições Linux</span><span class="sxs-lookup"><span data-stu-id="d9e8c-133">Linux distributions</span></span>

   * [<span data-ttu-id="d9e8c-134">CentOS</span><span class="sxs-lookup"><span data-stu-id="d9e8c-134">CentOS</span></span>](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [<span data-ttu-id="d9e8c-135">Debian</span><span class="sxs-lookup"><span data-stu-id="d9e8c-135">Debian</span></span>](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [<span data-ttu-id="d9e8c-136">Fedora</span><span class="sxs-lookup"><span data-stu-id="d9e8c-136">Fedora</span></span>](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [<span data-ttu-id="d9e8c-137">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d9e8c-137">Ubuntu</span></span>](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [<span data-ttu-id="d9e8c-138">macOS</span><span class="sxs-lookup"><span data-stu-id="d9e8c-138">macOS</span></span>](https://docs.docker.com/docker-for-mac/install/)

* <span data-ttu-id="d9e8c-139">[Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="d9e8c-139">[Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

### <a name="create-a-net-core-21-console-app-for-dockerization"></a><span data-ttu-id="d9e8c-140">Criar um aplicativo de console .NET Core 2.1 para colocá-lo no Docker</span><span class="sxs-lookup"><span data-stu-id="d9e8c-140">Create a .NET Core 2.1 console app for Dockerization</span></span>

<span data-ttu-id="d9e8c-141">Abra um prompt de comando e crie uma pasta chamada *Hello*.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-141">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="d9e8c-142">Navegue para a pasta criada e digite os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-142">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="d9e8c-143">Vejamos um breve passo a passo:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-143">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="d9e8c-144">[`dotnet new`](../tools/dotnet-new.md) cria um arquivo de projeto `Hello.csproj` atualizado com as dependências necessárias para criar um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-144">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="d9e8c-145">Ele também cria um `Program.cs`, um arquivo básico que contém o ponto de entrada para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-145">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="d9e8c-146">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-146">`Hello.csproj`:</span></span>

   <span data-ttu-id="d9e8c-147">O arquivo de projeto especifica tudo o que é necessário para restaurar as dependências e compilar o programa.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-147">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="d9e8c-148">A marca `OutputType` especifica que estamos copilando um executável, em outras palavras, um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-148">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="d9e8c-149">A marca `TargetFramework` especifica qual implementação do .NET estamos direcionando.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-149">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="d9e8c-150">Em um cenário avançado, você pode especificar várias estruturas de destino e compilar para as estruturas especificadas em uma única operação.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-150">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="d9e8c-151">Neste tutorial, compilamos para o .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-151">In this tutorial, we build for .NET Core 2.1.</span></span>

   <span data-ttu-id="d9e8c-152">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-152">`Program.cs`:</span></span>

   <span data-ttu-id="d9e8c-153">O programa é iniciado por `using System`.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-153">The program starts by `using System`.</span></span> <span data-ttu-id="d9e8c-154">Essa declaração significa “colocar tudo no namespace `System` no escopo para este arquivo”.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-154">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="d9e8c-155">O namespace `System` inclui construções básicas, como `string` ou tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-155">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="d9e8c-156">Em seguida, definimos um namespace chamado `Hello`.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-156">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="d9e8c-157">Altere o namespace para o nome desejado.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-157">You can change namespace to anything you want.</span></span> <span data-ttu-id="d9e8c-158">Uma classe chamada `Program` é definida dentro desse namespace, com um método `Main` que usa uma matriz de cadeias de caracteres como argumento.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-158">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="d9e8c-159">Essa matriz contém a lista de argumentos passados quando o programa compilado é chamado.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-159">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="d9e8c-160">Em nosso exemplo, o programa grava apenas “Olá, Mundo!”</span><span class="sxs-lookup"><span data-stu-id="d9e8c-160">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="d9e8c-161">no console.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-161">to the console.</span></span>

   <span data-ttu-id="d9e8c-162">**dotnet new** executa o comando [`dotnet restore`](../tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="d9e8c-162">**dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="d9e8c-163">**Dotnet restore** restaura a árvore de dependências com uma chamada ao [NuGet](https://www.nuget.org/) (gerenciador de pacotes do .NET).</span><span class="sxs-lookup"><span data-stu-id="d9e8c-163">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="d9e8c-164">O NuGet executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-164">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="d9e8c-165">analisa o arquivo *Hello.csproj*.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-165">analyzes the *Hello.csproj* file.</span></span>
   * <span data-ttu-id="d9e8c-166">baixa as dependências de arquivo (ou as captura do cache do computador).</span><span class="sxs-lookup"><span data-stu-id="d9e8c-166">downloads the file dependencies (or grabs from your machine cache).</span></span>
   * <span data-ttu-id="d9e8c-167">grava o arquivo *obj/project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-167">writes the *obj/project.assets.json* file.</span></span>

   <span data-ttu-id="d9e8c-168">O arquivo *project.assets.json* é um conjunto completo do gráfico de dependências do NuGet, das resoluções de associação e de outros metadados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-168">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="d9e8c-169">Esse arquivo obrigatório é usado por outras ferramentas, como [`dotnet build`](../tools/dotnet-build.md) e [`dotnet run`](../tools/dotnet-run.md), para processar o código-fonte corretamente.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-169">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>

2. `$ dotnet run`

   <span data-ttu-id="d9e8c-170">[`dotnet run`](../tools/dotnet-run.md) chama [`dotnet build`](../tools/dotnet-build.md) para confirmar um build bem-sucedido e, em seguida, chama `dotnet <assembly.dll>` para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-170">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>

    ```console
    $ dotnet run

    Hello World!
    ```

    <span data-ttu-id="d9e8c-171">Para cenários avançados, consulte [Implantação de aplicativos .NET Core](../deploying/index.md) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-171">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="d9e8c-172">Colocar o aplicativo .NET Core no Docker</span><span class="sxs-lookup"><span data-stu-id="d9e8c-172">Dockerize the .NET Core application</span></span>

<span data-ttu-id="d9e8c-173">O aplicativo de console Hello .NET Core é executado localmente com êxito.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-173">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="d9e8c-174">Agora vamos dar mais um passo e compilar e executar o aplicativo no Docker.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-174">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="d9e8c-175">Seu primeiro Dockerfile</span><span class="sxs-lookup"><span data-stu-id="d9e8c-175">Your first Dockerfile</span></span>

<span data-ttu-id="d9e8c-176">Abra o editor de texto e vamos começar!</span><span class="sxs-lookup"><span data-stu-id="d9e8c-176">Open your text editor and let's get started!</span></span> <span data-ttu-id="d9e8c-177">Ainda estamos trabalhando no diretório Hello no qual criamos o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-177">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="d9e8c-178">Adicione as instruções do Docker a seguir para [Contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) ou do Linux a um novo arquivo.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-178">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="d9e8c-179">Quando terminar, salve-o na raiz do diretório Hello como um **Dockerfile**, sem extensão (talvez seja necessário definir o tipo de arquivo como `All types (*.*)` ou algo semelhante).</span><span class="sxs-lookup"><span data-stu-id="d9e8c-179">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="d9e8c-180">O Dockerfile contém instruções de build do Docker que são executadas sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-180">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="d9e8c-181">A primeira instrução deve ser [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="d9e8c-181">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="d9e8c-182">Essa instrução inicializa um novo estágio de build e define a imagem Base para as instruções restantes.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-182">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="d9e8c-183">As marcas de vários arcos efetuam pull de contêineres do Windows ou Linux, dependendo do [modo de contêiner](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) do Docker para Windows.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-183">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="d9e8c-184">A Imagem Base de nossa amostra é a imagem 2.1-sdk do repositório microsoft/dotnet.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-184">The Base Image for our sample is the 2.1-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
```

<span data-ttu-id="d9e8c-185">A instrução [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) define o diretório de trabalho para as instruções restantes RUN, CMD, ENTRYPOINT, COPY e ADD do Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-185">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="d9e8c-186">Se o diretório não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-186">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="d9e8c-187">Nesse caso, WORKDIR é definido como o diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-187">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="d9e8c-188">A instrução [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) copia novos arquivos ou diretórios do caminho de origem e adiciona-os ao sistema de arquivos do contêiner de destino.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-188">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="d9e8c-189">Com essa instrução, estamos copiando o arquivo de projeto C# para o contêiner.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-189">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="d9e8c-190">A instrução [**RUN**](https://docs.docker.com/engine/reference/builder/#run) executa os comandos em uma nova camada na parte superior da imagem atual e confirma os resultados.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-190">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="d9e8c-191">A imagem confirmada resultante é usada para a próxima etapa do Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-191">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="d9e8c-192">Estamos executando **dotnet restore** para obter as dependências necessárias do arquivo de projeto C#.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-192">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="d9e8c-193">Essa instrução **COPY** copia o restante dos arquivos em nosso contêiner para novas [camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="d9e8c-193">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="d9e8c-194">Estamos publicando o aplicativo com essa instrução **RUN**.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-194">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="d9e8c-195">O comando [**dotnet publish**](../tools/dotnet-publish.md) compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto resultantes de arquivos em um diretório.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-195">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="d9e8c-196">Nosso aplicativo é publicado com uma configuração **Versão** e uma saída para o diretório padrão.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-196">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="d9e8c-197">A instrução [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) permite que o contêiner seja executado como um executável.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-197">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="d9e8c-198">Agora você tem um Dockerfile que:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-198">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="d9e8c-199">copia o aplicativo para a imagem</span><span class="sxs-lookup"><span data-stu-id="d9e8c-199">copies your app to the image</span></span>
* <span data-ttu-id="d9e8c-200">as dependências do aplicativo para a imagem</span><span class="sxs-lookup"><span data-stu-id="d9e8c-200">your app's dependencies to the image</span></span>
* <span data-ttu-id="d9e8c-201">compila o aplicativo para ser executado como um executável</span><span class="sxs-lookup"><span data-stu-id="d9e8c-201">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-app"></a><span data-ttu-id="d9e8c-202">Compilar e executar o aplicativo Hello .NET Core</span><span class="sxs-lookup"><span data-stu-id="d9e8c-202">Build and run the Hello .NET Core app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="d9e8c-203">Comandos essenciais do Docker</span><span class="sxs-lookup"><span data-stu-id="d9e8c-203">Essential Docker commands</span></span>

<span data-ttu-id="d9e8c-204">Esses comandos do Docker são essenciais:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-204">These Docker commands are essential:</span></span>

* [<span data-ttu-id="d9e8c-205">docker build</span><span class="sxs-lookup"><span data-stu-id="d9e8c-205">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="d9e8c-206">docker run</span><span class="sxs-lookup"><span data-stu-id="d9e8c-206">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="d9e8c-207">docker ps</span><span class="sxs-lookup"><span data-stu-id="d9e8c-207">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="d9e8c-208">docker stop</span><span class="sxs-lookup"><span data-stu-id="d9e8c-208">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="d9e8c-209">docker rm</span><span class="sxs-lookup"><span data-stu-id="d9e8c-209">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="d9e8c-210">docker rmi</span><span class="sxs-lookup"><span data-stu-id="d9e8c-210">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="d9e8c-211">docker image</span><span class="sxs-lookup"><span data-stu-id="d9e8c-211">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="d9e8c-212">Compilar e executar</span><span class="sxs-lookup"><span data-stu-id="d9e8c-212">Build and run</span></span>

<span data-ttu-id="d9e8c-213">Você gravou o Dockerfile; agora o Docker compila o aplicativo e, em seguida, executa o contêiner.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-213">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="d9e8c-214">A saída do comando `docker build` deverá ser semelhante à seguinte saída de console:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-214">The output from the `docker build` command should be similar to the following console output:</span></span>

```console
Sending build context to Docker daemon   173.1kB
Step 1/7 : FROM microsoft/dotnet:2.1-sdk
 ---> 288f8c45f7c2
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 46db075bd98d
Successfully tagged dotnetapp-dev:latest
```

<span data-ttu-id="d9e8c-215">Como você pode ver na saída, o Mecanismo do Docker usou o Dockerfile para compilar nosso contêiner.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-215">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="d9e8c-216">A saída do comando `docker run` deverá ser semelhante à seguinte saída de console:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-216">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="d9e8c-217">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="d9e8c-217">Congratulations!</span></span> <span data-ttu-id="d9e8c-218">Você acabou de:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-218">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d9e8c-219">criar um aplicativo .NET Core local</span><span class="sxs-lookup"><span data-stu-id="d9e8c-219">Created a local .NET Core app</span></span>
> * <span data-ttu-id="d9e8c-220">criar um Dockerfile para criar seu primeiro contêiner</span><span class="sxs-lookup"><span data-stu-id="d9e8c-220">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="d9e8c-221">criar e executar seu aplicativo no Docker</span><span class="sxs-lookup"><span data-stu-id="d9e8c-221">Built and ran your Dockerized app</span></span>

## <a name="next-steps"></a><span data-ttu-id="d9e8c-222">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d9e8c-222">Next steps</span></span>

<span data-ttu-id="d9e8c-223">Estas são algumas das próximas etapas que podem ser realizadas:</span><span class="sxs-lookup"><span data-stu-id="d9e8c-223">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="d9e8c-224">Vídeo de introdução às imagens do Docker do .NET</span><span class="sxs-lookup"><span data-stu-id="d9e8c-224">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="d9e8c-225">Visual Studio, Docker e Instâncias de Contêiner do Azure melhor juntos!</span><span class="sxs-lookup"><span data-stu-id="d9e8c-225">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://medium.com/@AliMazaheri/visual-studio-docker-azure-container-instances-better-together-bf8c2f0419ae)
* [<span data-ttu-id="d9e8c-226">Guias de início rápido do Docker para Azure</span><span class="sxs-lookup"><span data-stu-id="d9e8c-226">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="d9e8c-227">Implantar seu aplicativo no Docker para Azure</span><span class="sxs-lookup"><span data-stu-id="d9e8c-227">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!NOTE]
> <span data-ttu-id="d9e8c-228">Se você não tiver uma assinatura do Azure, [inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) em uma conta gratuita de 30 dias e receba $200 em Créditos do Azure para experimentar qualquer combinação de serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="d9e8c-228">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="d9e8c-229">Imagens do Docker usadas nesta amostra</span><span class="sxs-lookup"><span data-stu-id="d9e8c-229">Docker Images used in this sample</span></span>

<span data-ttu-id="d9e8c-230">As seguintes imagens do Docker são usadas nesta amostra</span><span class="sxs-lookup"><span data-stu-id="d9e8c-230">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.1-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="d9e8c-231">Recursos relacionados</span><span class="sxs-lookup"><span data-stu-id="d9e8c-231">Related resources</span></span>

* [<span data-ttu-id="d9e8c-232">Amostras do Docker do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d9e8c-232">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker/tree/master/samples)
* [<span data-ttu-id="d9e8c-233">Dockerfile em contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="d9e8c-233">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="d9e8c-234">Amostras do Docker do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d9e8c-234">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="d9e8c-235">ASP.NET Core no DockerHub</span><span class="sxs-lookup"><span data-stu-id="d9e8c-235">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="d9e8c-236">Colocar um aplicativo .NET Core no Docker – Tutorial do Docker</span><span class="sxs-lookup"><span data-stu-id="d9e8c-236">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="d9e8c-237">Trabalhar com ferramentas de Docker do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d9e8c-237">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="d9e8c-238">Implantar imagens do Docker do Registro de Contêiner do Azure para Instâncias de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="d9e8c-238">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)