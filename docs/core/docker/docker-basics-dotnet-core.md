---
title: "Aprenda noções básicas do Docker com o .NET Core"
description: "Um tutorial básico do Docker e do .NET Core"
keywords: NET, .NET Core, Docker, Tutorial
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.workload: dotnetcore
ms.openlocfilehash: 79ded2ce5de5100c18301127a2654f8791b8ed76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="7ecd7-104">Aprenda noções básicas do Docker com o .NET Core</span><span class="sxs-lookup"><span data-stu-id="7ecd7-104">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="7ecd7-105">Este tutorial ensina as tarefas de build e implantação de contêiner do Docker para um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-105">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="7ecd7-106">Durante este tutorial, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="7ecd7-107">Como criar um Dockerfile</span><span class="sxs-lookup"><span data-stu-id="7ecd7-107">How to create a Dockerfile</span></span>
> * <span data-ttu-id="7ecd7-108">Como criar um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-108">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="7ecd7-109">Como implantar seu aplicativo em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-109">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="7ecd7-110">A [plataforma Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) usa o [Mecanismo do Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) para criar e empacotar aplicativos com agilidade [imagens do Docker](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="7ecd7-110">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="7ecd7-111">Essas imagens são gravadas no formato [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) para serem implantadas e executadas em um [contêiner em camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="7ecd7-111">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="7ecd7-112">.NET Core: a maneira mais fácil para começar a usar</span><span class="sxs-lookup"><span data-stu-id="7ecd7-112">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="7ecd7-113">Antes de criar a imagem do Docker, é necessário ter um aplicativo para colocá-lo em contêiner.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-113">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="7ecd7-114">Crie-o no Linux, MacOS ou Windows.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-114">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="7ecd7-115">A maneira mais rápida e fácil de fazer isso é usando o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-115">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="7ecd7-116">Se não estiver familiarizado com o conjunto de ferramentas da CLI do .NET Core, leia a [Visão geral do SDK do .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ecd7-116">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="7ecd7-117">Criar contêineres do Windows e Linux com [marcas baseadas em vários arcos](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="7ecd7-117">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="7ecd7-118">Seu primeiro aplicativo .NET Core do Docker</span><span class="sxs-lookup"><span data-stu-id="7ecd7-118">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7ecd7-119">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7ecd7-119">Prerequisites</span></span>

<span data-ttu-id="7ecd7-120">Para concluir este tutorial:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-120">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="7ecd7-121">SDK do .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="7ecd7-121">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="7ecd7-122">Instale o [SDK do .NET Core 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="7ecd7-122">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="7ecd7-123">Consulte [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 2.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 2.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="7ecd7-124">Instale seu editor de código favorito, caso ainda não tenha um.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-124">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="7ecd7-125">Precisa instalar um editor de código?</span><span class="sxs-lookup"><span data-stu-id="7ecd7-125">Need to install a code editor?</span></span> <span data-ttu-id="7ecd7-126">Experimente o [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="7ecd7-126">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="7ecd7-127">Instalando o Cliente do Docker</span><span class="sxs-lookup"><span data-stu-id="7ecd7-127">Installing Docker Client</span></span>

<span data-ttu-id="7ecd7-128">Instale o [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) ou posterior do cliente do Docker.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-128">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="7ecd7-129">O cliente do Docker pode ser instalado em:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-129">The Docker client can be installed in:</span></span>

* <span data-ttu-id="7ecd7-130">Distribuições Linux</span><span class="sxs-lookup"><span data-stu-id="7ecd7-130">Linux distributions</span></span>

   * [<span data-ttu-id="7ecd7-131">CentOS</span><span class="sxs-lookup"><span data-stu-id="7ecd7-131">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="7ecd7-132">Debian</span><span class="sxs-lookup"><span data-stu-id="7ecd7-132">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="7ecd7-133">Fedora</span><span class="sxs-lookup"><span data-stu-id="7ecd7-133">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="7ecd7-134">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7ecd7-134">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="7ecd7-135">macOS</span><span class="sxs-lookup"><span data-stu-id="7ecd7-135">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="7ecd7-136">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="7ecd7-136">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="7ecd7-137">Criar um aplicativo de console .NET Core 2.0 para colocá-lo no Docker</span><span class="sxs-lookup"><span data-stu-id="7ecd7-137">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="7ecd7-138">Abra um prompt de comando e crie uma pasta chamada *Hello*.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-138">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="7ecd7-139">Navegue para a pasta criada e digite os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-139">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="7ecd7-140">Vejamos um breve passo a passo:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-140">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="7ecd7-141">[`dotnet new`](../tools/dotnet-new.md) cria um arquivo de projeto `Hello.csproj` atualizado com as dependências necessárias para criar um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-141">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="7ecd7-142">Ele também cria um `Program.cs`, um arquivo básico que contém o ponto de entrada para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-142">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="7ecd7-143">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-143">`Hello.csproj`:</span></span>

   <span data-ttu-id="7ecd7-144">O arquivo de projeto especifica tudo o que é necessário para restaurar as dependências e compilar o programa.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-144">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="7ecd7-145">A marca `OutputType` especifica que estamos copilando um executável, em outras palavras, um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-145">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="7ecd7-146">A marca `TargetFramework` especifica qual implementação do .NET estamos direcionando.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-146">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="7ecd7-147">Em um cenário avançado, você pode especificar várias estruturas de destino e compilar para as estruturas especificadas em uma única operação.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-147">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="7ecd7-148">Neste tutorial, compilamos para o .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-148">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="7ecd7-149">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-149">`Program.cs`:</span></span>

   <span data-ttu-id="7ecd7-150">O programa é iniciado por `using System`.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-150">The program starts by `using System`.</span></span> <span data-ttu-id="7ecd7-151">Essa declaração significa “colocar tudo no namespace `System` no escopo para este arquivo”.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-151">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="7ecd7-152">O namespace `System` inclui construções básicas, como `string` ou tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-152">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="7ecd7-153">Em seguida, definimos um namespace chamado `Hello`.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-153">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="7ecd7-154">Altere o namespace para o nome desejado.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-154">You can change namespace to anything you want.</span></span> <span data-ttu-id="7ecd7-155">Uma classe chamada `Program` é definida dentro desse namespace, com um método `Main` que usa uma matriz de cadeias de caracteres como argumento.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-155">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="7ecd7-156">Essa matriz contém a lista de argumentos passados quando o programa compilado é chamado.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-156">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="7ecd7-157">Em nosso exemplo, o programa grava apenas “Olá, Mundo!”</span><span class="sxs-lookup"><span data-stu-id="7ecd7-157">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="7ecd7-158">no console.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-158">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="7ecd7-159">No .NET Core 2.x, **dotnet new** executa o comando [`dotnet restore`](../tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="7ecd7-159">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="7ecd7-160">**Dotnet restore** restaura a árvore de dependências com uma chamada ao [NuGet](https://www.nuget.org/) (gerenciador de pacotes do .NET).</span><span class="sxs-lookup"><span data-stu-id="7ecd7-160">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="7ecd7-161">O NuGet executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-161">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="7ecd7-162">analisa o arquivo *Hello.csproj*</span><span class="sxs-lookup"><span data-stu-id="7ecd7-162">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="7ecd7-163">baixa as dependências de arquivo (ou captura-as do cache do computador)</span><span class="sxs-lookup"><span data-stu-id="7ecd7-163">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="7ecd7-164">grava o arquivo *obj/project.assets.json*</span><span class="sxs-lookup"><span data-stu-id="7ecd7-164">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="7ecd7-165">O arquivo *project.assets.json* é um conjunto completo do gráfico de dependências do NuGet, das resoluções de associação e de outros metadados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-165">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="7ecd7-166">Esse arquivo obrigatório é usado por outras ferramentas, como [`dotnet build`](../tools/dotnet-build.md) e [`dotnet run`](../tools/dotnet-run.md), para processar o código-fonte corretamente.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-166">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="7ecd7-167">[`dotnet run`](../tools/dotnet-run.md) chama [`dotnet build`](../tools/dotnet-build.md) para confirmar um build bem-sucedido e, em seguida, chama `dotnet <assembly.dll>` para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-167">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="7ecd7-168">Para cenários avançados, consulte [Implantação de aplicativos .NET Core](../deploying/index.md) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-168">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="7ecd7-169">Colocar o aplicativo .NET Core no Docker</span><span class="sxs-lookup"><span data-stu-id="7ecd7-169">Dockerize the .NET Core application</span></span>

<span data-ttu-id="7ecd7-170">O aplicativo de console Hello .NET Core é executado localmente com êxito.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-170">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="7ecd7-171">Agora vamos dar mais um passo e compilar e executar o aplicativo no Docker.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-171">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="7ecd7-172">Seu primeiro Dockerfile</span><span class="sxs-lookup"><span data-stu-id="7ecd7-172">Your first Dockerfile</span></span>

<span data-ttu-id="7ecd7-173">Abra o editor de texto e vamos começar!</span><span class="sxs-lookup"><span data-stu-id="7ecd7-173">Open your text editor and let's get started!</span></span> <span data-ttu-id="7ecd7-174">Ainda estamos trabalhando no diretório Hello no qual criamos o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-174">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="7ecd7-175">Adicione as instruções do Docker a seguir para [Contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) ou do Linux a um novo arquivo.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-175">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="7ecd7-176">Quando terminar, salve-o na raiz do diretório Hello como um **Dockerfile**, sem extensão (talvez seja necessário definir o tipo de arquivo como `All types (*.*)` ou algo semelhante).</span><span class="sxs-lookup"><span data-stu-id="7ecd7-176">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="7ecd7-177">O Dockerfile contém instruções de build do Docker que são executadas sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-177">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="7ecd7-178">A primeira instrução deve ser [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="7ecd7-178">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="7ecd7-179">Essa instrução inicializa um novo estágio de build e define a imagem Base para as instruções restantes.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-179">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="7ecd7-180">As marcas de vários arcos efetuam pull de contêineres do Windows ou Linux, dependendo do [modo de contêiner](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) do Docker para Windows.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-180">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="7ecd7-181">A imagem Base de nossa amostra é a imagem 2.0-sdk do repositório microsoft/dotnet.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-181">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="7ecd7-182">A instrução [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) define o diretório de trabalho para as instruções restantes RUN, CMD, ENTRYPOINT, COPY e ADD do Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-182">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="7ecd7-183">Se o diretório não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-183">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="7ecd7-184">Nesse caso, WORKDIR é definido como o diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-184">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="7ecd7-185">A instrução [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) copia novos arquivos ou diretórios do caminho de origem e adiciona-os ao sistema de arquivos do contêiner de destino.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-185">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="7ecd7-186">Com essa instrução, estamos copiando o arquivo de projeto C# para o contêiner.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-186">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="7ecd7-187">A instrução [**RUN**](https://docs.docker.com/engine/reference/builder/#run) executa os comandos em uma nova camada na parte superior da imagem atual e confirma os resultados.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-187">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="7ecd7-188">A imagem confirmada resultante é usada para a próxima etapa do Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-188">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="7ecd7-189">Estamos executando **dotnet restore** para obter as dependências necessárias do arquivo de projeto C#.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-189">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="7ecd7-190">Essa instrução **COPY** copia o restante dos arquivos em nosso contêiner para novas [camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="7ecd7-190">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="7ecd7-191">Estamos publicando o aplicativo com essa instrução **RUN**.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-191">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="7ecd7-192">O comando [**dotnet publish**](../tools/dotnet-publish.md) compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto resultantes de arquivos em um diretório.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-192">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="7ecd7-193">Nosso aplicativo é publicado com uma configuração **Versão** e uma saída para o diretório padrão.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-193">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="7ecd7-194">A instrução [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) permite que o contêiner seja executado como um executável.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-194">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="7ecd7-195">Agora você tem um Dockerfile que:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-195">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="7ecd7-196">copia o aplicativo para a imagem</span><span class="sxs-lookup"><span data-stu-id="7ecd7-196">copies your app to the image</span></span>
* <span data-ttu-id="7ecd7-197">as dependências do aplicativo para a imagem</span><span class="sxs-lookup"><span data-stu-id="7ecd7-197">your app's dependencies to the image</span></span>
* <span data-ttu-id="7ecd7-198">compila o aplicativo para ser executado como um executável</span><span class="sxs-lookup"><span data-stu-id="7ecd7-198">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="7ecd7-199">Compilar e executar o aplicativo Hello .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="7ecd7-199">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="7ecd7-200">Comandos essenciais do Docker</span><span class="sxs-lookup"><span data-stu-id="7ecd7-200">Essential Docker commands</span></span>

<span data-ttu-id="7ecd7-201">Esses comandos do Docker são essenciais:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-201">These Docker commands are essential:</span></span>

* [<span data-ttu-id="7ecd7-202">docker build</span><span class="sxs-lookup"><span data-stu-id="7ecd7-202">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="7ecd7-203">docker run</span><span class="sxs-lookup"><span data-stu-id="7ecd7-203">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="7ecd7-204">docker ps</span><span class="sxs-lookup"><span data-stu-id="7ecd7-204">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="7ecd7-205">docker stop</span><span class="sxs-lookup"><span data-stu-id="7ecd7-205">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="7ecd7-206">docker rm</span><span class="sxs-lookup"><span data-stu-id="7ecd7-206">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="7ecd7-207">docker rmi</span><span class="sxs-lookup"><span data-stu-id="7ecd7-207">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="7ecd7-208">docker image</span><span class="sxs-lookup"><span data-stu-id="7ecd7-208">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="7ecd7-209">Compilar e executar</span><span class="sxs-lookup"><span data-stu-id="7ecd7-209">Build and run</span></span>

<span data-ttu-id="7ecd7-210">Você gravou o Dockerfile; agora o Docker compila o aplicativo e, em seguida, executa o contêiner.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-210">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="7ecd7-211">A saída do comando `docker build` deverá ser semelhante à seguinte saída de console:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-211">The output from the `docker build` command should be similar to the following console output:</span></span>

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
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
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

<span data-ttu-id="7ecd7-212">Como você pode ver na saída, o Mecanismo do Docker usou o Dockerfile para compilar nosso contêiner.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-212">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="7ecd7-213">A saída do comando `docker run` deverá ser semelhante à seguinte saída de console:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-213">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="7ecd7-214">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="7ecd7-214">Congratulations!</span></span> <span data-ttu-id="7ecd7-215">Você acabou de:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-215">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="7ecd7-216">criar um aplicativo .NET Core local</span><span class="sxs-lookup"><span data-stu-id="7ecd7-216">Created a local .NET Core app</span></span>
> * <span data-ttu-id="7ecd7-217">criar um Dockerfile para criar seu primeiro contêiner</span><span class="sxs-lookup"><span data-stu-id="7ecd7-217">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="7ecd7-218">criar e executar seu aplicativo no Docker</span><span class="sxs-lookup"><span data-stu-id="7ecd7-218">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="7ecd7-219">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7ecd7-219">Next Steps</span></span>

<span data-ttu-id="7ecd7-220">Estas são algumas das próximas etapas que podem ser realizadas:</span><span class="sxs-lookup"><span data-stu-id="7ecd7-220">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="7ecd7-221">Vídeo de introdução às imagens do Docker do .NET</span><span class="sxs-lookup"><span data-stu-id="7ecd7-221">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="7ecd7-222">Visual Studio, Docker e Instâncias de Contêiner do Azure melhor juntos!</span><span class="sxs-lookup"><span data-stu-id="7ecd7-222">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="7ecd7-223">Guias de início rápido do Docker para Azure</span><span class="sxs-lookup"><span data-stu-id="7ecd7-223">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="7ecd7-224">Implantar seu aplicativo no Docker para Azure</span><span class="sxs-lookup"><span data-stu-id="7ecd7-224">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="7ecd7-225">Se você não tiver uma assinatura do Azure, [inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) em uma conta gratuita de 30 dias e receba $200 em Créditos do Azure para experimentar qualquer combinação de serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-225">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="7ecd7-226">Imagens do Docker usadas nesta amostra</span><span class="sxs-lookup"><span data-stu-id="7ecd7-226">Docker Images used in this sample</span></span>

<span data-ttu-id="7ecd7-227">As seguintes imagens do Docker são usadas nesta amostra</span><span class="sxs-lookup"><span data-stu-id="7ecd7-227">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="7ecd7-228">Recursos relacionados</span><span class="sxs-lookup"><span data-stu-id="7ecd7-228">Related Resources</span></span>

* [<span data-ttu-id="7ecd7-229">Amostras do Docker do .NET Core</span><span class="sxs-lookup"><span data-stu-id="7ecd7-229">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="7ecd7-230">Dockerfile em contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="7ecd7-230">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="7ecd7-231">Amostras do Docker do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7ecd7-231">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="7ecd7-232">ASP.NET Core no DockerHub</span><span class="sxs-lookup"><span data-stu-id="7ecd7-232">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="7ecd7-233">Colocar um aplicativo .NET Core no Docker – Tutorial do Docker</span><span class="sxs-lookup"><span data-stu-id="7ecd7-233">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="7ecd7-234">Trabalhar com ferramentas de Docker do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7ecd7-234">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="7ecd7-235">Implantar imagens do Docker do Registro de Contêiner do Azure para Instâncias de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="7ecd7-235">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)