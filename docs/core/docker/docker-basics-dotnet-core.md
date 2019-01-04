---
title: Colocar um aplicativo em contêiner com o Docker
description: Este tutorial ensina como criar um aplicativo básico do .NET Core e a colocá-lo em contêiner com o Docker.
ms.date: 10/11/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: eed72553576f4154fe63b2e5cf035a781afe4b7c
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169580"
---
# <a name="how-to-containerize-a-net-core-application"></a><span data-ttu-id="d38ea-103">Como colocar em contêiner um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="d38ea-103">How to containerize a .NET Core application</span></span>

<span data-ttu-id="d38ea-104">Este tutorial ensina as tarefas de build e implantação de contêiner do Docker para um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d38ea-104">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="d38ea-105">A [plataforma Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) usa o [Mecanismo do Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) para criar e empacotar aplicativos com agilidade [imagens do Docker](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="d38ea-105">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="d38ea-106">Essas imagens são gravadas no formato [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) para serem implantadas e executadas em um [contêiner em camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="d38ea-106">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="d38ea-107">Durante este tutorial, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="d38ea-107">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="d38ea-108">Como criar um Dockerfile</span><span class="sxs-lookup"><span data-stu-id="d38ea-108">How to create a Dockerfile</span></span>
> * <span data-ttu-id="d38ea-109">Como criar um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d38ea-109">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="d38ea-110">Como implantar seu aplicativo em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="d38ea-110">How to deploy your app into a Docker container.</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="d38ea-111">.NET Core: A maneira mais fácil para começar</span><span class="sxs-lookup"><span data-stu-id="d38ea-111">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="d38ea-112">Antes de criar a imagem do Docker, é necessário ter um aplicativo para colocá-lo em contêiner.</span><span class="sxs-lookup"><span data-stu-id="d38ea-112">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="d38ea-113">Crie-o no Linux, MacOS ou Windows.</span><span class="sxs-lookup"><span data-stu-id="d38ea-113">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="d38ea-114">A maneira mais rápida e fácil de fazer isso é usando o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d38ea-114">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="d38ea-115">Se não estiver familiarizado com o conjunto de ferramentas da CLI do .NET Core, leia a [Visão geral do SDK do .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="d38ea-115">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="d38ea-116">Criar contêineres do Windows e Linux com [marcas baseadas em vários arcos](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="d38ea-116">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="d38ea-117">Seu primeiro aplicativo .NET Core do Docker</span><span class="sxs-lookup"><span data-stu-id="d38ea-117">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d38ea-118">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d38ea-118">Prerequisites</span></span>

<span data-ttu-id="d38ea-119">Para concluir este tutorial:</span><span class="sxs-lookup"><span data-stu-id="d38ea-119">To complete this tutorial:</span></span>

#### <a name="net-core-sdk"></a><span data-ttu-id="d38ea-120">SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d38ea-120">.NET Core SDK</span></span>

* <span data-ttu-id="d38ea-121">Instale o [SDK do .NET Core 2.1](https://www.microsoft.com/net/download) ou posterior.</span><span class="sxs-lookup"><span data-stu-id="d38ea-121">Install [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later.</span></span>

<span data-ttu-id="d38ea-122">Consulte [Versões de sistema operacional compatíveis com .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) para obter a lista completa de sistemas operacionais compatíveis com .NET Core 2.1, versões de sistema operacional não compatíveis e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="d38ea-122">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="d38ea-123">Instale seu editor de código favorito, caso ainda não tenha um.</span><span class="sxs-lookup"><span data-stu-id="d38ea-123">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="d38ea-124">Precisa instalar um editor de código?</span><span class="sxs-lookup"><span data-stu-id="d38ea-124">Need to install a code editor?</span></span> <span data-ttu-id="d38ea-125">Experimente o [Visual Studio Code](https://code.visualstudio.com/download)!</span><span class="sxs-lookup"><span data-stu-id="d38ea-125">Try [Visual Studio Code](https://code.visualstudio.com/download)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="d38ea-126">Instalando o Cliente do Docker</span><span class="sxs-lookup"><span data-stu-id="d38ea-126">Installing Docker Client</span></span>

<span data-ttu-id="d38ea-127">Instale o [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) ou cliente do Docker posterior.</span><span class="sxs-lookup"><span data-stu-id="d38ea-127">Install [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="d38ea-128">O cliente do Docker pode ser instalado em:</span><span class="sxs-lookup"><span data-stu-id="d38ea-128">The Docker client can be installed in:</span></span>

* <span data-ttu-id="d38ea-129">Distribuições Linux</span><span class="sxs-lookup"><span data-stu-id="d38ea-129">Linux distributions</span></span>

   * [<span data-ttu-id="d38ea-130">CentOS</span><span class="sxs-lookup"><span data-stu-id="d38ea-130">CentOS</span></span>](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [<span data-ttu-id="d38ea-131">Debian</span><span class="sxs-lookup"><span data-stu-id="d38ea-131">Debian</span></span>](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [<span data-ttu-id="d38ea-132">Fedora</span><span class="sxs-lookup"><span data-stu-id="d38ea-132">Fedora</span></span>](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [<span data-ttu-id="d38ea-133">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d38ea-133">Ubuntu</span></span>](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [<span data-ttu-id="d38ea-134">macOS</span><span class="sxs-lookup"><span data-stu-id="d38ea-134">macOS</span></span>](https://docs.docker.com/docker-for-mac/install/)

* <span data-ttu-id="d38ea-135">[Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="d38ea-135">[Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

### <a name="create-a-net-core-21-console-app-for-dockerization"></a><span data-ttu-id="d38ea-136">Criar um aplicativo de console .NET Core 2.1 para colocá-lo no Docker</span><span class="sxs-lookup"><span data-stu-id="d38ea-136">Create a .NET Core 2.1 console app for Dockerization</span></span>

<span data-ttu-id="d38ea-137">Abra um prompt de comando e crie uma pasta chamada *Hello*.</span><span class="sxs-lookup"><span data-stu-id="d38ea-137">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="d38ea-138">Navegue para a pasta criada e digite os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d38ea-138">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="d38ea-139">Vejamos um breve passo a passo:</span><span class="sxs-lookup"><span data-stu-id="d38ea-139">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="d38ea-140">[`dotnet new`](../tools/dotnet-new.md) cria um arquivo de projeto `Hello.csproj` atualizado com as dependências necessárias para criar um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="d38ea-140">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="d38ea-141">Ele também cria um `Program.cs`, um arquivo básico que contém o ponto de entrada para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d38ea-141">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="d38ea-142">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="d38ea-142">`Hello.csproj`:</span></span>

   <span data-ttu-id="d38ea-143">O arquivo de projeto especifica tudo o que é necessário para restaurar as dependências e compilar o programa.</span><span class="sxs-lookup"><span data-stu-id="d38ea-143">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="d38ea-144">A marca `OutputType` especifica que estamos copilando um executável, em outras palavras, um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="d38ea-144">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="d38ea-145">A marca `TargetFramework` especifica qual implementação do .NET estamos direcionando.</span><span class="sxs-lookup"><span data-stu-id="d38ea-145">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="d38ea-146">Em um cenário avançado, você pode especificar várias estruturas de destino e compilar para as estruturas especificadas em uma única operação.</span><span class="sxs-lookup"><span data-stu-id="d38ea-146">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="d38ea-147">Neste tutorial, compilamos para o .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="d38ea-147">In this tutorial, we build for .NET Core 2.1.</span></span>

   <span data-ttu-id="d38ea-148">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="d38ea-148">`Program.cs`:</span></span>

   <span data-ttu-id="d38ea-149">O programa é iniciado por `using System`.</span><span class="sxs-lookup"><span data-stu-id="d38ea-149">The program starts by `using System`.</span></span> <span data-ttu-id="d38ea-150">Essa declaração significa “colocar tudo no namespace `System` no escopo para este arquivo”.</span><span class="sxs-lookup"><span data-stu-id="d38ea-150">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="d38ea-151">O namespace `System` inclui construções básicas, como `string` ou tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="d38ea-151">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="d38ea-152">Em seguida, definimos um namespace chamado `Hello`.</span><span class="sxs-lookup"><span data-stu-id="d38ea-152">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="d38ea-153">Altere o namespace para o nome desejado.</span><span class="sxs-lookup"><span data-stu-id="d38ea-153">You can change namespace to anything you want.</span></span> <span data-ttu-id="d38ea-154">Uma classe chamada `Program` é definida dentro desse namespace, com um método `Main` que usa uma matriz de cadeias de caracteres como argumento.</span><span class="sxs-lookup"><span data-stu-id="d38ea-154">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="d38ea-155">Essa matriz contém a lista de argumentos passados quando o programa compilado é chamado.</span><span class="sxs-lookup"><span data-stu-id="d38ea-155">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="d38ea-156">Em nosso exemplo, o programa grava apenas “Olá, Mundo!”</span><span class="sxs-lookup"><span data-stu-id="d38ea-156">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="d38ea-157">no console.</span><span class="sxs-lookup"><span data-stu-id="d38ea-157">to the console.</span></span>

   <span data-ttu-id="d38ea-158">**dotnet new** executa o comando [`dotnet restore`](../tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="d38ea-158">**dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="d38ea-159">**Dotnet restore** restaura a árvore de dependências com uma chamada ao [NuGet](https://www.nuget.org/) (gerenciador de pacotes do .NET).</span><span class="sxs-lookup"><span data-stu-id="d38ea-159">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="d38ea-160">O NuGet executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="d38ea-160">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="d38ea-161">analisa o arquivo *Hello.csproj*.</span><span class="sxs-lookup"><span data-stu-id="d38ea-161">analyzes the *Hello.csproj* file.</span></span>
   * <span data-ttu-id="d38ea-162">baixa as dependências de arquivo (ou as captura do cache do computador).</span><span class="sxs-lookup"><span data-stu-id="d38ea-162">downloads the file dependencies (or grabs from your machine cache).</span></span>
   * <span data-ttu-id="d38ea-163">grava o arquivo *obj/project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="d38ea-163">writes the *obj/project.assets.json* file.</span></span>

   <span data-ttu-id="d38ea-164">O arquivo *project.assets.json* é um conjunto completo do gráfico de dependências do NuGet, das resoluções de associação e de outros metadados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d38ea-164">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="d38ea-165">Esse arquivo obrigatório é usado por outras ferramentas, como [`dotnet build`](../tools/dotnet-build.md) e [`dotnet run`](../tools/dotnet-run.md), para processar o código-fonte corretamente.</span><span class="sxs-lookup"><span data-stu-id="d38ea-165">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>

2. `$ dotnet run`

   <span data-ttu-id="d38ea-166">[`dotnet run`](../tools/dotnet-run.md) chama [`dotnet build`](../tools/dotnet-build.md) para confirmar um build bem-sucedido e, em seguida, chama `dotnet <assembly.dll>` para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d38ea-166">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>

    ```console
    $ dotnet run

    Hello World!
    ```

    <span data-ttu-id="d38ea-167">Para cenários avançados, consulte [Implantação de aplicativos .NET Core](../deploying/index.md) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="d38ea-167">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="d38ea-168">Colocar o aplicativo .NET Core no Docker</span><span class="sxs-lookup"><span data-stu-id="d38ea-168">Dockerize the .NET Core application</span></span>

<span data-ttu-id="d38ea-169">O aplicativo de console Hello .NET Core é executado localmente com êxito.</span><span class="sxs-lookup"><span data-stu-id="d38ea-169">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="d38ea-170">Agora vamos dar mais um passo e compilar e executar o aplicativo no Docker.</span><span class="sxs-lookup"><span data-stu-id="d38ea-170">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="d38ea-171">Seu primeiro Dockerfile</span><span class="sxs-lookup"><span data-stu-id="d38ea-171">Your first Dockerfile</span></span>

<span data-ttu-id="d38ea-172">Abra o editor de texto e vamos começar!</span><span class="sxs-lookup"><span data-stu-id="d38ea-172">Open your text editor and let's get started!</span></span> <span data-ttu-id="d38ea-173">Ainda estamos trabalhando no diretório Hello no qual criamos o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d38ea-173">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="d38ea-174">Adicione as instruções do Docker a seguir para [Contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) ou do Linux a um novo arquivo.</span><span class="sxs-lookup"><span data-stu-id="d38ea-174">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="d38ea-175">Quando terminar, salve-o na raiz do diretório Hello como um **Dockerfile**, sem extensão (talvez seja necessário definir o tipo de arquivo como `All types (*.*)` ou algo semelhante).</span><span class="sxs-lookup"><span data-stu-id="d38ea-175">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

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

<span data-ttu-id="d38ea-176">O Dockerfile contém instruções de build do Docker que são executadas sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="d38ea-176">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="d38ea-177">A primeira instrução deve ser [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="d38ea-177">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="d38ea-178">Essa instrução inicializa um novo estágio de build e define a imagem Base para as instruções restantes.</span><span class="sxs-lookup"><span data-stu-id="d38ea-178">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="d38ea-179">As marcas de vários arcos efetuam pull de contêineres do Windows ou Linux, dependendo do [modo de contêiner](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) do Docker para Windows.</span><span class="sxs-lookup"><span data-stu-id="d38ea-179">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="d38ea-180">A Imagem Base de nossa amostra é a imagem 2.1-sdk do repositório microsoft/dotnet.</span><span class="sxs-lookup"><span data-stu-id="d38ea-180">The Base Image for our sample is the 2.1-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
```

<span data-ttu-id="d38ea-181">A instrução [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) define o diretório de trabalho para as instruções restantes RUN, CMD, ENTRYPOINT, COPY e ADD do Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d38ea-181">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="d38ea-182">Se o diretório não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="d38ea-182">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="d38ea-183">Nesse caso, WORKDIR é definido como o diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d38ea-183">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="d38ea-184">A instrução [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) copia novos arquivos ou diretórios do caminho de origem e adiciona-os ao sistema de arquivos do contêiner de destino.</span><span class="sxs-lookup"><span data-stu-id="d38ea-184">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="d38ea-185">Com essa instrução, estamos copiando o arquivo de projeto C# para o contêiner.</span><span class="sxs-lookup"><span data-stu-id="d38ea-185">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="d38ea-186">A instrução [**RUN**](https://docs.docker.com/engine/reference/builder/#run) executa os comandos em uma nova camada na parte superior da imagem atual e confirma os resultados.</span><span class="sxs-lookup"><span data-stu-id="d38ea-186">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="d38ea-187">A imagem confirmada resultante é usada para a próxima etapa do Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d38ea-187">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="d38ea-188">Estamos executando **dotnet restore** para obter as dependências necessárias do arquivo de projeto C#.</span><span class="sxs-lookup"><span data-stu-id="d38ea-188">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="d38ea-189">Essa instrução **COPY** copia o restante dos arquivos em nosso contêiner para novas [camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="d38ea-189">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="d38ea-190">Estamos publicando o aplicativo com essa instrução **RUN**.</span><span class="sxs-lookup"><span data-stu-id="d38ea-190">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="d38ea-191">O comando [**dotnet publish**](../tools/dotnet-publish.md) compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto resultantes de arquivos em um diretório.</span><span class="sxs-lookup"><span data-stu-id="d38ea-191">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="d38ea-192">Nosso aplicativo é publicado com uma configuração **Versão** e uma saída para o diretório padrão.</span><span class="sxs-lookup"><span data-stu-id="d38ea-192">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="d38ea-193">A instrução [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) permite que o contêiner seja executado como um executável.</span><span class="sxs-lookup"><span data-stu-id="d38ea-193">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="d38ea-194">Agora você tem um Dockerfile que:</span><span class="sxs-lookup"><span data-stu-id="d38ea-194">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="d38ea-195">copia o aplicativo para a imagem</span><span class="sxs-lookup"><span data-stu-id="d38ea-195">copies your app to the image</span></span>
* <span data-ttu-id="d38ea-196">as dependências do aplicativo para a imagem</span><span class="sxs-lookup"><span data-stu-id="d38ea-196">your app's dependencies to the image</span></span>
* <span data-ttu-id="d38ea-197">compila o aplicativo para ser executado como um executável</span><span class="sxs-lookup"><span data-stu-id="d38ea-197">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-app"></a><span data-ttu-id="d38ea-198">Compilar e executar o aplicativo Hello .NET Core</span><span class="sxs-lookup"><span data-stu-id="d38ea-198">Build and run the Hello .NET Core app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="d38ea-199">Comandos essenciais do Docker</span><span class="sxs-lookup"><span data-stu-id="d38ea-199">Essential Docker commands</span></span>

<span data-ttu-id="d38ea-200">Esses comandos do Docker são essenciais:</span><span class="sxs-lookup"><span data-stu-id="d38ea-200">These Docker commands are essential:</span></span>

* [<span data-ttu-id="d38ea-201">docker build</span><span class="sxs-lookup"><span data-stu-id="d38ea-201">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="d38ea-202">docker run</span><span class="sxs-lookup"><span data-stu-id="d38ea-202">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="d38ea-203">docker ps</span><span class="sxs-lookup"><span data-stu-id="d38ea-203">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="d38ea-204">docker stop</span><span class="sxs-lookup"><span data-stu-id="d38ea-204">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="d38ea-205">docker rm</span><span class="sxs-lookup"><span data-stu-id="d38ea-205">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="d38ea-206">docker rmi</span><span class="sxs-lookup"><span data-stu-id="d38ea-206">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="d38ea-207">docker image</span><span class="sxs-lookup"><span data-stu-id="d38ea-207">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="d38ea-208">Compilar e executar</span><span class="sxs-lookup"><span data-stu-id="d38ea-208">Build and run</span></span>

<span data-ttu-id="d38ea-209">Você gravou o Dockerfile; agora o Docker compila o aplicativo e, em seguida, executa o contêiner.</span><span class="sxs-lookup"><span data-stu-id="d38ea-209">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="d38ea-210">A saída do comando `docker build` deverá ser semelhante à seguinte saída de console:</span><span class="sxs-lookup"><span data-stu-id="d38ea-210">The output from the `docker build` command should be similar to the following console output:</span></span>

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

<span data-ttu-id="d38ea-211">Como você pode ver na saída, o Mecanismo do Docker usou o Dockerfile para compilar nosso contêiner.</span><span class="sxs-lookup"><span data-stu-id="d38ea-211">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="d38ea-212">A saída do comando `docker run` deverá ser semelhante à seguinte saída de console:</span><span class="sxs-lookup"><span data-stu-id="d38ea-212">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="d38ea-213">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="d38ea-213">Congratulations!</span></span> <span data-ttu-id="d38ea-214">Você acabou de:</span><span class="sxs-lookup"><span data-stu-id="d38ea-214">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d38ea-215">criar um aplicativo .NET Core local</span><span class="sxs-lookup"><span data-stu-id="d38ea-215">Created a local .NET Core app</span></span>
> * <span data-ttu-id="d38ea-216">criar um Dockerfile para criar seu primeiro contêiner</span><span class="sxs-lookup"><span data-stu-id="d38ea-216">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="d38ea-217">criar e executar seu aplicativo no Docker</span><span class="sxs-lookup"><span data-stu-id="d38ea-217">Built and ran your Dockerized app</span></span>

## <a name="next-steps"></a><span data-ttu-id="d38ea-218">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d38ea-218">Next steps</span></span>

<span data-ttu-id="d38ea-219">Estas são algumas das próximas etapas que podem ser realizadas:</span><span class="sxs-lookup"><span data-stu-id="d38ea-219">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="d38ea-220">Vídeo de introdução às imagens do Docker do .NET</span><span class="sxs-lookup"><span data-stu-id="d38ea-220">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="d38ea-221">Visual Studio, Docker e Instâncias de Contêiner do Azure melhor juntos!</span><span class="sxs-lookup"><span data-stu-id="d38ea-221">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://medium.com/@AliMazaheri/visual-studio-docker-azure-container-instances-better-together-bf8c2f0419ae)
* [<span data-ttu-id="d38ea-222">Guias de início rápido do Docker para Azure</span><span class="sxs-lookup"><span data-stu-id="d38ea-222">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="d38ea-223">Implantar seu aplicativo no Docker para Azure</span><span class="sxs-lookup"><span data-stu-id="d38ea-223">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="d38ea-224">Se você não tiver uma assinatura do Azure, [inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) em uma conta gratuita de 30 dias e receba $200 em Créditos do Azure para experimentar qualquer combinação de serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="d38ea-224">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="d38ea-225">Imagens do Docker usadas nesta amostra</span><span class="sxs-lookup"><span data-stu-id="d38ea-225">Docker Images used in this sample</span></span>

<span data-ttu-id="d38ea-226">As seguintes imagens do Docker são usadas nesta amostra</span><span class="sxs-lookup"><span data-stu-id="d38ea-226">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.1-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="d38ea-227">Recursos relacionados</span><span class="sxs-lookup"><span data-stu-id="d38ea-227">Related resources</span></span>

* [<span data-ttu-id="d38ea-228">Amostras do Docker do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d38ea-228">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker/tree/master/samples)
* [<span data-ttu-id="d38ea-229">Dockerfile em contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="d38ea-229">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="d38ea-230">Amostras do Docker do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d38ea-230">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="d38ea-231">ASP.NET Core no DockerHub</span><span class="sxs-lookup"><span data-stu-id="d38ea-231">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="d38ea-232">Colocar um aplicativo .NET Core no Docker – Tutorial do Docker</span><span class="sxs-lookup"><span data-stu-id="d38ea-232">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="d38ea-233">Trabalhar com ferramentas de Docker do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d38ea-233">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="d38ea-234">Implantar imagens do Docker do Registro de Contêiner do Azure para Instâncias de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="d38ea-234">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)