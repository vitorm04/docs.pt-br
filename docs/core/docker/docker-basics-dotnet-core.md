---
title: "Aprenda noções básicas do Docker com o núcleo do .NET"
description: "Um Docker e um Tutorial básico do .NET Core"
keywords: ".NET, o núcleo do .NET, o Docker, o Tutorial"
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
ms.openlocfilehash: 5935f67d7e4ca9c9e8768373e2bcaa9febccfdc5
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2017
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="4e444-104">Aprenda noções básicas do Docker com o núcleo do .NET</span><span class="sxs-lookup"><span data-stu-id="4e444-104">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="4e444-105">Este tutorial ensina Docker contêiner compilar e implantar tarefas para um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4e444-105">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="4e444-106">No decorrer deste tutorial, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="4e444-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="4e444-107">Como criar um Dockerfile</span><span class="sxs-lookup"><span data-stu-id="4e444-107">How to create a Dockerfile</span></span>
> * <span data-ttu-id="4e444-108">Como criar um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4e444-108">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="4e444-109">Como implantar seu aplicativo em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="4e444-109">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="4e444-110">O [plataforma de Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) usa o [mecanismo do Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) para criar e empacotar aplicativos como rapidamente [imagens do Docker](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="4e444-110">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="4e444-111">Essas imagens são escritas no [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) formato a ser implantado e executado um [em camadas contêiner](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="4e444-111">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="4e444-112">.NET core: A maneira mais fácil para começar</span><span class="sxs-lookup"><span data-stu-id="4e444-112">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="4e444-113">Antes de criar a imagem do Docker, é necessário um aplicativo coloca.</span><span class="sxs-lookup"><span data-stu-id="4e444-113">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="4e444-114">Você pode criá-lo no Linux, MacOS ou Windows.</span><span class="sxs-lookup"><span data-stu-id="4e444-114">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="4e444-115">A maneira mais rápida e fácil de fazer isso é usar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4e444-115">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="4e444-116">Se não estiver familiarizado com o conjunto de ferramentas da CLI do .NET Core, leia a [Visão geral do SDK do .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="4e444-116">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="4e444-117">Você pode criar contêineres do Windows e Linux com [multi-arch com base em marcas](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="4e444-117">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="4e444-118">Seu primeiro aplicativo .NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="4e444-118">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="4e444-119">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4e444-119">Prerequisites</span></span>

<span data-ttu-id="4e444-120">Para concluir este tutorial:</span><span class="sxs-lookup"><span data-stu-id="4e444-120">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="4e444-121">.NET core SDK 2.0</span><span class="sxs-lookup"><span data-stu-id="4e444-121">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="4e444-122">Instalar [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="4e444-122">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="4e444-123">Consulte [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 2.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 2.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="4e444-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="4e444-124">Instale o editor de código favorito, se ainda não tiver uma.</span><span class="sxs-lookup"><span data-stu-id="4e444-124">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="4e444-125">É necessário instalar um editor de código?</span><span class="sxs-lookup"><span data-stu-id="4e444-125">Need to install a code editor?</span></span> <span data-ttu-id="4e444-126">Tente [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="4e444-126">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="4e444-127">Instalar o cliente do Docker</span><span class="sxs-lookup"><span data-stu-id="4e444-127">Installing Docker Client</span></span>

<span data-ttu-id="4e444-128">Instalar [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) ou posterior do cliente do Docker.</span><span class="sxs-lookup"><span data-stu-id="4e444-128">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="4e444-129">O cliente do Docker pode ser instalado em:</span><span class="sxs-lookup"><span data-stu-id="4e444-129">The Docker client can be installed in:</span></span>

* <span data-ttu-id="4e444-130">Distribuições do Linux</span><span class="sxs-lookup"><span data-stu-id="4e444-130">Linux distributions</span></span>

   * [<span data-ttu-id="4e444-131">CentOS</span><span class="sxs-lookup"><span data-stu-id="4e444-131">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="4e444-132">Debian</span><span class="sxs-lookup"><span data-stu-id="4e444-132">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="4e444-133">Fedora</span><span class="sxs-lookup"><span data-stu-id="4e444-133">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="4e444-134">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="4e444-134">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="4e444-135">macOS</span><span class="sxs-lookup"><span data-stu-id="4e444-135">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="4e444-136">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="4e444-136">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="4e444-137">Criar um aplicativo de console .NET Core 2.0 para Dockerization</span><span class="sxs-lookup"><span data-stu-id="4e444-137">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="4e444-138">Abra um prompt de comando e crie uma pasta chamada *Hello*.</span><span class="sxs-lookup"><span data-stu-id="4e444-138">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="4e444-139">Navegue até a pasta que você criou e digite os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="4e444-139">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="4e444-140">Vejamos um breve passo a passo:</span><span class="sxs-lookup"><span data-stu-id="4e444-140">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="4e444-141">[`dotnet new`](../tools/dotnet-new.md) cria um arquivo de projeto `Hello.csproj` atualizado com as dependências necessárias para criar um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="4e444-141">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="4e444-142">Ele também cria um `Program.cs`, um arquivo básico que contém o ponto de entrada para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e444-142">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="4e444-143">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="4e444-143">`Hello.csproj`:</span></span>

   <span data-ttu-id="4e444-144">O arquivo de projeto especifica tudo o que é necessário para restaurar as dependências e compilar o programa.</span><span class="sxs-lookup"><span data-stu-id="4e444-144">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="4e444-145">A marca `OutputType` especifica que estamos copilando um executável, em outras palavras, um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="4e444-145">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="4e444-146">A marca `TargetFramework` especifica qual implementação do .NET estamos direcionando.</span><span class="sxs-lookup"><span data-stu-id="4e444-146">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="4e444-147">Em um cenário avançado, você pode especificar várias estruturas de destino e criar estruturas especificado em uma única operação.</span><span class="sxs-lookup"><span data-stu-id="4e444-147">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="4e444-148">Neste tutorial, vamos criar para .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="4e444-148">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="4e444-149">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="4e444-149">`Program.cs`:</span></span>

   <span data-ttu-id="4e444-150">O programa será iniciado por `using System`.</span><span class="sxs-lookup"><span data-stu-id="4e444-150">The program starts by `using System`.</span></span> <span data-ttu-id="4e444-151">Essa declaração significa, "colocar tudo no `System` namespace no escopo para esse arquivo."</span><span class="sxs-lookup"><span data-stu-id="4e444-151">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="4e444-152">O namespace `System` inclui construções básicas, como `string` ou tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="4e444-152">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="4e444-153">Em seguida, definimos um namespace chamado `Hello`.</span><span class="sxs-lookup"><span data-stu-id="4e444-153">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="4e444-154">Você pode alterar o namespace em que quiser.</span><span class="sxs-lookup"><span data-stu-id="4e444-154">You can change namespace to anything you want.</span></span> <span data-ttu-id="4e444-155">Uma classe chamada `Program` é definida dentro desse namespace, com um método `Main` que usa uma matriz de cadeias de caracteres como argumento.</span><span class="sxs-lookup"><span data-stu-id="4e444-155">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="4e444-156">Essa matriz contém a lista de argumentos passados quando o programa compilado é chamado.</span><span class="sxs-lookup"><span data-stu-id="4e444-156">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="4e444-157">Em nosso exemplo, o programa só grava "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="4e444-157">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="4e444-158">no console.</span><span class="sxs-lookup"><span data-stu-id="4e444-158">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="4e444-159">No núcleo do .NET 2. x, **dotnet novo** executa o [ `dotnet restore` ](../tools/dotnet-restore.md) comando.</span><span class="sxs-lookup"><span data-stu-id="4e444-159">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="4e444-160">**Restauração dotnet** restaura a árvore de dependências com um [NuGet](https://www.nuget.org/)chamada (Gerenciador de pacotes do .NET).</span><span class="sxs-lookup"><span data-stu-id="4e444-160">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="4e444-161">O NuGet executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="4e444-161">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="4e444-162">analisa o *Hello.csproj* arquivo</span><span class="sxs-lookup"><span data-stu-id="4e444-162">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="4e444-163">baixa o arquivo dependências (ou captura do seu cache de máquina)</span><span class="sxs-lookup"><span data-stu-id="4e444-163">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="4e444-164">grava o *obj/project.assets.json* arquivo</span><span class="sxs-lookup"><span data-stu-id="4e444-164">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="4e444-165">O *project.assets.json* arquivo é um conjunto completo de como o gráfico de dependências do NuGet, resoluções de associação e outros metadados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e444-165">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="4e444-166">Isso necessário arquivo é usado por outras ferramentas, como [ `dotnet build` ](../tools/dotnet-build.md) e [ `dotnet run` ](../tools/dotnet-run.md), processar corretamente o código-fonte.</span><span class="sxs-lookup"><span data-stu-id="4e444-166">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="4e444-167">[`dotnet run`](../tools/dotnet-run.md)chamadas [ `dotnet build` ](../tools/dotnet-build.md) para confirmar uma compilação bem-sucedida e, em seguida, chama `dotnet <assembly.dll>` para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e444-167">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="4e444-168">Para cenários avançados, consulte [implantação de aplicativos .NET Core](../deploying/index.md) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="4e444-168">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="4e444-169">Dockerize o aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="4e444-169">Dockerize the .NET Core application</span></span>

<span data-ttu-id="4e444-170">O aplicativo de console Hello .NET Core com êxito é executado localmente.</span><span class="sxs-lookup"><span data-stu-id="4e444-170">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="4e444-171">Agora vamos dar um passo adicional e compilar e executar o aplicativo no Docker.</span><span class="sxs-lookup"><span data-stu-id="4e444-171">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="4e444-172">Sua primeira Dockerfile</span><span class="sxs-lookup"><span data-stu-id="4e444-172">Your first Dockerfile</span></span>

<span data-ttu-id="4e444-173">Abra o editor de texto e vamos começar!</span><span class="sxs-lookup"><span data-stu-id="4e444-173">Open your text editor and let's get started!</span></span> <span data-ttu-id="4e444-174">Ainda estamos trabalhando do diretório Olá que criamos o aplicativo no.</span><span class="sxs-lookup"><span data-stu-id="4e444-174">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="4e444-175">Adicione as seguintes instruções de Docker para o Linux ou [contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) para um novo arquivo.</span><span class="sxs-lookup"><span data-stu-id="4e444-175">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="4e444-176">Quando terminar, salve-o na raiz do seu diretório Hello como **Dockerfile**, sem extensão (talvez seja necessário definir o tipo de arquivo `All types (*.*)` ou algo semelhante).</span><span class="sxs-lookup"><span data-stu-id="4e444-176">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

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

<span data-ttu-id="4e444-177">O Dockerfile contém instruções de build do Docker que são executados sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="4e444-177">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="4e444-178">A primeira instrução deve ser [ **FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="4e444-178">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="4e444-179">Essa instrução inicia uma nova fase de compilação e define a imagem de Base para as instruções restantes.</span><span class="sxs-lookup"><span data-stu-id="4e444-179">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="4e444-180">As marcas várias arch pull contêineres do Windows ou Linux dependendo do Docker para Windows [modo contêiner](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span><span class="sxs-lookup"><span data-stu-id="4e444-180">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="4e444-181">A imagem Base para nossa amostra é a imagem do sdk 2.0 do repositório microsoft/dotnet,</span><span class="sxs-lookup"><span data-stu-id="4e444-181">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="4e444-182">O [ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instrução define o diretório de trabalho para qualquer restantes executar CMD, ENTRYPOINT, cópia e adicionar Dockerfile instruções.</span><span class="sxs-lookup"><span data-stu-id="4e444-182">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="4e444-183">Se a pasta não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="4e444-183">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="4e444-184">Nesse caso, WORKDIR é definido para o diretório de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e444-184">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="4e444-185">O [ **cópia** ](https://docs.docker.com/engine/reference/builder/#copy) instrução copia novos arquivos ou diretórios do caminho de origem e adiciona-os no sistema de arquivos do contêiner de destino.</span><span class="sxs-lookup"><span data-stu-id="4e444-185">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="4e444-186">Com essa instrução, podemos está copiando o arquivo de projeto c# para o contêiner.</span><span class="sxs-lookup"><span data-stu-id="4e444-186">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="4e444-187">O [ **executar** ](https://docs.docker.com/engine/reference/builder/#run) instrução executa os comandos em uma nova camada na parte superior da imagem atual e confirme os resultados.</span><span class="sxs-lookup"><span data-stu-id="4e444-187">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="4e444-188">A imagem confirmada resultante é usada para a próxima etapa no Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="4e444-188">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="4e444-189">Estamos executando **restauração dotnet** para obter as dependências necessárias de arquivo de projeto c#.</span><span class="sxs-lookup"><span data-stu-id="4e444-189">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="4e444-190">Isso **cópia** instrução copia o restante dos arquivos em nosso contêiner em novos [camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="4e444-190">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="4e444-191">Estamos publicando o aplicativo com essa **executar** instrução.</span><span class="sxs-lookup"><span data-stu-id="4e444-191">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="4e444-192">O [ **dotnet publicar** ](../tools/dotnet-publish.md) comando compila o aplicativo lê por meio de suas dependências especificadas no arquivo de projeto e publica o conjunto resultante de arquivos para um diretório.</span><span class="sxs-lookup"><span data-stu-id="4e444-192">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="4e444-193">Nosso aplicativo é publicado com uma **versão** configuração e saída para o diretório padrão.</span><span class="sxs-lookup"><span data-stu-id="4e444-193">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="4e444-194">O [ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instrução permite que o contêiner ser executado como um executável.</span><span class="sxs-lookup"><span data-stu-id="4e444-194">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="4e444-195">Agora você tem um Dockerfile que:</span><span class="sxs-lookup"><span data-stu-id="4e444-195">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="4e444-196">Copia a imagem do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4e444-196">copies your app to the image</span></span>
* <span data-ttu-id="4e444-197">dependências do aplicativo para a imagem</span><span class="sxs-lookup"><span data-stu-id="4e444-197">your app's dependencies to the image</span></span>
* <span data-ttu-id="4e444-198">cria o aplicativo para ser executado como um executável</span><span class="sxs-lookup"><span data-stu-id="4e444-198">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="4e444-199">Compilar e executar o aplicativo Hello .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4e444-199">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="4e444-200">Comandos essenciais</span><span class="sxs-lookup"><span data-stu-id="4e444-200">Essential Docker commands</span></span>

<span data-ttu-id="4e444-201">Esses comandos do Docker são essenciais:</span><span class="sxs-lookup"><span data-stu-id="4e444-201">These Docker commands are essential:</span></span>

* [<span data-ttu-id="4e444-202">build do docker</span><span class="sxs-lookup"><span data-stu-id="4e444-202">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="4e444-203">execução de docker</span><span class="sxs-lookup"><span data-stu-id="4e444-203">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="4e444-204">docker ps</span><span class="sxs-lookup"><span data-stu-id="4e444-204">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="4e444-205">parada de docker</span><span class="sxs-lookup"><span data-stu-id="4e444-205">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="4e444-206">docker rm</span><span class="sxs-lookup"><span data-stu-id="4e444-206">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="4e444-207">docker rmi</span><span class="sxs-lookup"><span data-stu-id="4e444-207">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="4e444-208">imagem do docker</span><span class="sxs-lookup"><span data-stu-id="4e444-208">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="4e444-209">Compilar e executar</span><span class="sxs-lookup"><span data-stu-id="4e444-209">Build and run</span></span>

<span data-ttu-id="4e444-210">Você gravou o dockerfile; Agora Docker compila seu aplicativo e, em seguida, executa o contêiner.</span><span class="sxs-lookup"><span data-stu-id="4e444-210">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="4e444-211">A saída de `docker build` comando deve ser semelhante à seguinte saída de console:</span><span class="sxs-lookup"><span data-stu-id="4e444-211">The output from the `docker build` command should be similar to the following console output:</span></span>

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

<span data-ttu-id="4e444-212">Como você pode ver na saída, o mecanismo do Docker usado Dockerfile para compilar nosso contêiner.</span><span class="sxs-lookup"><span data-stu-id="4e444-212">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="4e444-213">A saída de `docker run` comando deve ser semelhante à seguinte saída de console:</span><span class="sxs-lookup"><span data-stu-id="4e444-213">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="4e444-214">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="4e444-214">Congratulations!</span></span> <span data-ttu-id="4e444-215">Você tem apenas:</span><span class="sxs-lookup"><span data-stu-id="4e444-215">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="4e444-216">Criou um aplicativo .NET Core local</span><span class="sxs-lookup"><span data-stu-id="4e444-216">Created a local .NET Core app</span></span>
> * <span data-ttu-id="4e444-217">Criado um Dockerfile para criar o primeiro contêiner</span><span class="sxs-lookup"><span data-stu-id="4e444-217">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="4e444-218">Criado e executou seu aplicativo Dockerized</span><span class="sxs-lookup"><span data-stu-id="4e444-218">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="4e444-219">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4e444-219">Next Steps</span></span>

<span data-ttu-id="4e444-220">Aqui estão algumas das próximas etapas que você pode executar:</span><span class="sxs-lookup"><span data-stu-id="4e444-220">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="4e444-221">Introdução ao .NET Docker imagens vídeo</span><span class="sxs-lookup"><span data-stu-id="4e444-221">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="4e444-222">Visual Studio, o Docker e as instâncias de contêiner do Azure melhor juntos!</span><span class="sxs-lookup"><span data-stu-id="4e444-222">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="4e444-223">Docker para guias de início rápido do Azure</span><span class="sxs-lookup"><span data-stu-id="4e444-223">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="4e444-224">Implantar seu aplicativo no Docker do Azure</span><span class="sxs-lookup"><span data-stu-id="4e444-224">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="4e444-225">Se você não tiver uma assinatura do Azure, [Inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) para uma conta gratuita de 30 dias e get US $200 em créditos do Azure para testar qualquer combinação de serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="4e444-225">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="4e444-226">Imagens do docker usadas neste exemplo</span><span class="sxs-lookup"><span data-stu-id="4e444-226">Docker Images used in this sample</span></span>

<span data-ttu-id="4e444-227">As seguintes imagens do Docker são usadas neste exemplo</span><span class="sxs-lookup"><span data-stu-id="4e444-227">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="4e444-228">Recursos relacionados</span><span class="sxs-lookup"><span data-stu-id="4e444-228">Related Resources</span></span>

* [<span data-ttu-id="4e444-229">Amostras do .NET core Docker</span><span class="sxs-lookup"><span data-stu-id="4e444-229">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="4e444-230">Dockerfile em contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="4e444-230">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="4e444-231">Amostras do .NET framework Docker</span><span class="sxs-lookup"><span data-stu-id="4e444-231">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="4e444-232">ASP.NET Core em DockerHub</span><span class="sxs-lookup"><span data-stu-id="4e444-232">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="4e444-233">Dockerize um aplicativo .NET Core - Tutorial de Docker</span><span class="sxs-lookup"><span data-stu-id="4e444-233">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="4e444-234">Trabalhando com ferramentas de Docker do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4e444-234">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="4e444-235">Implantação de imagens do Docker do registro do contêiner do Azure para instâncias de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="4e444-235">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)