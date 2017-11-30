---
title: Criando imagens do Docker do .NET Core
description: "Noções básicas de imagens do Docker e do .NET Core"
keywords: .NET, .NET Core, Docker
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
ms.openlocfilehash: 3ec2d5a58b46e332de41b618f1c3fac663b29bee
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2017
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="6bd9a-104">Criando imagens do Docker para .NET Core Applications</span><span class="sxs-lookup"><span data-stu-id="6bd9a-104">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="6bd9a-105">Neste tutorial, vamos nos concentrar em como usar o .NET Core no Docker.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-105">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="6bd9a-106">Primeiro, exploraremos diferentes imagens do Docker oferecidos e mantido pela Microsoft e casos de uso.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-106">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="6bd9a-107">Em seguida, aprendemos como criar e dockerize um aplicativo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-107">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="6bd9a-108">No decorrer deste tutorial, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-108">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="6bd9a-109">Saiba mais sobre as imagens do Microsoft .NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="6bd9a-109">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="6bd9a-110">Obter um ASP.NET Core Dockerize de aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="6bd9a-110">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="6bd9a-111">Executar o aplicativo de exemplo do ASP.NET localmente</span><span class="sxs-lookup"><span data-stu-id="6bd9a-111">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="6bd9a-112">Compilar e executar o exemplo com o Docker para contêineres do Linux</span><span class="sxs-lookup"><span data-stu-id="6bd9a-112">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="6bd9a-113">Compilar e executar o exemplo com contêineres do Docker para Windows</span><span class="sxs-lookup"><span data-stu-id="6bd9a-113">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="6bd9a-114">Otimizações de imagem de Docker</span><span class="sxs-lookup"><span data-stu-id="6bd9a-114">Docker Image Optimizations</span></span>

<span data-ttu-id="6bd9a-115">Ao criar imagens do Docker para desenvolvedores, nos concentramos em três cenários principais:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-115">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="6bd9a-116">Imagens usadas para desenvolver aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="6bd9a-116">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="6bd9a-117">Imagens usadas para compilar aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="6bd9a-117">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="6bd9a-118">Imagens usadas para executar aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="6bd9a-118">Images used to run .NET Core apps</span></span>

<span data-ttu-id="6bd9a-119">Por que três imagens?</span><span class="sxs-lookup"><span data-stu-id="6bd9a-119">Why three images?</span></span>
<span data-ttu-id="6bd9a-120">Ao desenvolver, compilar e executar aplicativos em contêineres, temos prioridades diferentes.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-120">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="6bd9a-121">**Desenvolvimento:** a prioridade enfoca itera rapidamente as alterações e a capacidade de depurar as alterações.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-121">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="6bd9a-122">O tamanho da imagem não é tão importante, em vez disso, você pode fazer alterações no seu código e vê-los rapidamente?</span><span class="sxs-lookup"><span data-stu-id="6bd9a-122">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="6bd9a-123">**Compilação:** essa imagem contém todos os componentes necessários para compilar seu aplicativo, que inclui o compilador e qualquer outra dependência de otimizar os binários.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-123">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="6bd9a-124">Você pode usar a imagem de compilação para criar os ativos que você coloca em uma imagem de produção.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-124">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="6bd9a-125">A imagem de compilação seria usada para a integração contínua, ou em um ambiente de compilação.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-125">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="6bd9a-126">Essa abordagem permite que um agente de compilação Compilar e criar o aplicativo (com todas as dependências necessárias) em uma instância de imagem de compilação.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-126">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="6bd9a-127">O agente de build precisa saber apenas como executar essa imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-127">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="6bd9a-128">**Produção:** rapidez você pode implantar e iniciar sua imagem?</span><span class="sxs-lookup"><span data-stu-id="6bd9a-128">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="6bd9a-129">Esta imagem é pequena para otimização de desempenho de rede de seu registro de Docker para seus hosts de Docker.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-129">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="6bd9a-130">O conteúdo está pronto para ser executado e habilitar o tempo mais rápido possível da execução do Docker até o processamento de resultados.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-130">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="6bd9a-131">Compilação de código dinâmico não é necessária no modelo do Docker.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-131">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="6bd9a-132">O conteúdo colocado nesta imagem ficaria limitado aos binários e conteúdos necessários para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-132">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="6bd9a-133">Por exemplo, o `dotnet publish` saída contém:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-133">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="6bd9a-134">os binários compilados</span><span class="sxs-lookup"><span data-stu-id="6bd9a-134">the compiled binaries</span></span>
    * <span data-ttu-id="6bd9a-135">arquivos. CSS e. js</span><span class="sxs-lookup"><span data-stu-id="6bd9a-135">.js and .css files</span></span>


<span data-ttu-id="6bd9a-136">O motivo para incluir o `dotnet publish` saída do comando em sua imagem de produção é manter o ' tamanho mínimo.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-136">The reason to include the `dotnet publish` command output in your production image is to keep its' size to a minimum.</span></span>

<span data-ttu-id="6bd9a-137">Algumas imagens de .NET Core compartilham camadas entre marcas diferentes para que baixar a última marca é um processo relativamente simples.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-137">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="6bd9a-138">Se você já tiver uma versão mais antiga em seu computador, essa arquitetura diminui o espaço em disco necessário.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-138">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="6bd9a-139">Quando vários aplicativos usam imagens comuns no mesmo computador, a memória é compartilhada entre as imagens comuns.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-139">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="6bd9a-140">As imagens devem ser os mesmos para ser compartilhado.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-140">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="6bd9a-141">Variações de imagem do Docker</span><span class="sxs-lookup"><span data-stu-id="6bd9a-141">Docker image variations</span></span>

<span data-ttu-id="6bd9a-142">Para atingir os objetivos descritos acima, fornecemos variantes de imagem em [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="6bd9a-142">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="6bd9a-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Esta imagem contém o SDK de núcleo do .NET, que inclui o .NET Core e ferramentas de linha de comando (CLI).</span><span class="sxs-lookup"><span data-stu-id="6bd9a-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="6bd9a-144">Essa imagem é mapeada para o **cenário de desenvolvimento**.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-144">This image maps to the **development scenario**.</span></span> <span data-ttu-id="6bd9a-145">Você pode usar essa imagem para o local de desenvolvimento, depuração e teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-145">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="6bd9a-146">Essa imagem também pode ser usada para cenários **de build**.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-146">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="6bd9a-147">Usando `microsoft/dotnet:sdk` sempre fornece a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-147">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="6bd9a-148">Se você não tiver certeza sobre as suas necessidades, você deseja usar o `microsoft/dotnet:<version>-sdk` imagem.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-148">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="6bd9a-149">Como a imagem "verdadeiro", ele foi projetado para ser usado como um throw contêiner ausente (montar seu código-fonte e inicie o contêiner para iniciar seu aplicativo) e como a imagem base para criar imagens de.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-149">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="6bd9a-150">`microsoft/dotnet:<version>-runtime`: Esta imagem contém o .NET Core (tempo de execução e bibliotecas) e é otimizada para executar aplicativos .NET Core em **produção**.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-150">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="6bd9a-151">Imagens alternativas</span><span class="sxs-lookup"><span data-stu-id="6bd9a-151">Alternative images</span></span>

<span data-ttu-id="6bd9a-152">Além dos cenários otimizados de desenvolvimento, build e produção, fornecemos imagens adicionais:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-152">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="6bd9a-153">`microsoft/dotnet:<version>-runtime-deps`: O **deps de tempo de execução** imagem contém o sistema operacional com todas as dependências nativo necessárias ao .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-153">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="6bd9a-154">Esta imagem é para [aplicativos independentes](https://docs.microsoft.com/dotnet/core/deploying/index).</span><span class="sxs-lookup"><span data-stu-id="6bd9a-154">This image is for [self-contained applications](https://docs.microsoft.com/dotnet/core/deploying/index).</span></span>

<span data-ttu-id="6bd9a-155">Versões mais recentes de cada variante:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-155">Latest versions of each variant:</span></span>

* <span data-ttu-id="6bd9a-156">`microsoft/dotnet`ou `microsoft/dotnet:latest` (alias para a imagem do SDK)</span><span class="sxs-lookup"><span data-stu-id="6bd9a-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="6bd9a-157">Exemplos para explorar</span><span class="sxs-lookup"><span data-stu-id="6bd9a-157">Samples to explore</span></span>

* <span data-ttu-id="6bd9a-158">[Este exemplo do ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstra um padrão de práticas recomendado para a criação de imagens do Docker para ASP.NET Core aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-158">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="6bd9a-159">O exemplo funciona com contêineres do Linux e Windows.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-159">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="6bd9a-160">.NET Core Docker demonstra um padrão de prática recomendado para [criação de imagens do Docker para aplicativos .NET Core para produção.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="6bd9a-160">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="6bd9a-161">Seu primeiro aplicativo ASP.NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="6bd9a-161">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="6bd9a-162">Para este tutorial, permite usar um aplicativo de exemplo do ASP.NET Core Docker para o aplicativo que desejamos dockerize.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-162">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="6bd9a-163">Este aplicativo de exemplo do ASP.NET Core Docker demonstra um padrão de práticas recomendado para a criação de imagens do Docker para ASP.NET Core aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-163">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="6bd9a-164">O exemplo funciona com contêineres do Linux e Windows.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-164">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="6bd9a-165">O exemplo Dockerfile cria uma imagem de Docker de aplicativo do ASP.NET Core baseada a imagem base do Docker de tempo de execução do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-165">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="6bd9a-166">Ele usa o [vários estágios do Docker build recurso](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) para:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-166">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="6bd9a-167">criar o exemplo em um contêiner com base no **maior** imagem base do ASP.NET Core compilação Docker</span><span class="sxs-lookup"><span data-stu-id="6bd9a-167">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="6bd9a-168">Copia o resultado da compilação final em uma imagem do Docker com base no **menor** imagem base do tempo de execução do ASP.NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="6bd9a-168">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!Note]
> <span data-ttu-id="6bd9a-169">A imagem de compilação contém as ferramentas necessárias para criar aplicativos, enquanto a imagem de tempo de execução, não.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-169">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="6bd9a-170">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6bd9a-170">Prerequisites</span></span>

<span data-ttu-id="6bd9a-171">Para compilar e executar, instale os seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-171">To build and run, install the following items:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="6bd9a-172">.NET core SDK 2.0</span><span class="sxs-lookup"><span data-stu-id="6bd9a-172">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="6bd9a-173">Instalar [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="6bd9a-173">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="6bd9a-174">Instale o editor de código favorito, se ainda não tiver uma.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-174">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="6bd9a-175">É necessário instalar um editor de código?</span><span class="sxs-lookup"><span data-stu-id="6bd9a-175">Need to install a code editor?</span></span> <span data-ttu-id="6bd9a-176">Tente [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="6bd9a-176">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="6bd9a-177">Instalar o cliente do Docker</span><span class="sxs-lookup"><span data-stu-id="6bd9a-177">Installing Docker Client</span></span>

<span data-ttu-id="6bd9a-178">Instalar [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) ou posterior do cliente do Docker.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-178">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="6bd9a-179">O cliente do Docker pode ser instalado em:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-179">The Docker client can be installed in:</span></span>

* <span data-ttu-id="6bd9a-180">Distribuições do Linux</span><span class="sxs-lookup"><span data-stu-id="6bd9a-180">Linux distributions</span></span>

   * [<span data-ttu-id="6bd9a-181">CentOS</span><span class="sxs-lookup"><span data-stu-id="6bd9a-181">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="6bd9a-182">Debian</span><span class="sxs-lookup"><span data-stu-id="6bd9a-182">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="6bd9a-183">Fedora</span><span class="sxs-lookup"><span data-stu-id="6bd9a-183">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="6bd9a-184">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6bd9a-184">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="6bd9a-185">macOS</span><span class="sxs-lookup"><span data-stu-id="6bd9a-185">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="6bd9a-186">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="6bd9a-186">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="6bd9a-187">Instalando o Git para o repositório de exemplo</span><span class="sxs-lookup"><span data-stu-id="6bd9a-187">Installing Git for sample repository</span></span>

* <span data-ttu-id="6bd9a-188">Instalar [git](https://git-scm.com/download) se você deseja clonar o repositório.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-188">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="6bd9a-189">Obtendo o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="6bd9a-189">Getting the sample application</span></span>

<span data-ttu-id="6bd9a-190">A maneira mais fácil de obter o exemplo é por meio da clonagem de [repositório exemplos](https://github.com/dotnet/dotnet-docker-samples) com git, usando as instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-190">The easiest way to get the sample is by cloning the [samples repository](https://github.com/dotnet/dotnet-docker-samples) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

<span data-ttu-id="6bd9a-191">Você também pode baixar o repositório (é pequeno) como um zip do repositório de amostras do .NET Core Docker.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-191">You can also download the repository (it is small) as a zip from the .NET Core Docker samples repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="6bd9a-192">Executar o aplicativo ASP.NET localmente</span><span class="sxs-lookup"><span data-stu-id="6bd9a-192">Run the ASP.NET app locally</span></span>

<span data-ttu-id="6bd9a-193">Para um ponto de referência, antes de colocarmos o aplicativo em contêineres, primeiro devemos executá-lo localmente.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-193">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="6bd9a-194">Você pode criar e executar o aplicativo localmente com o SDK do .NET Core 2.0 usando os comandos a seguir (as instruções presumem que a raiz do repositório):</span><span class="sxs-lookup"><span data-stu-id="6bd9a-194">You can build and run the application locally with the .NET Core 2.0 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
dotnet run
```

<span data-ttu-id="6bd9a-195">Depois que o aplicativo for iniciado, visite **http://localhost:5000/** no navegador da web.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-195">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="6bd9a-196">Compilar e executar o exemplo com o Docker para contêineres do Linux</span><span class="sxs-lookup"><span data-stu-id="6bd9a-196">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="6bd9a-197">Você pode criar e executar o exemplo no Docker usando os contêineres do Linux usando os comandos a seguir (as instruções presumem que a raiz do repositório):</span><span class="sxs-lookup"><span data-stu-id="6bd9a-197">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!Note] <span data-ttu-id="6bd9a-198">O `docker run` '-p' argumento mapas 5000 em seu computador local para a porta 80 no contêiner da porta (o formato de mapeamento de porta é `host:container`).</span><span class="sxs-lookup"><span data-stu-id="6bd9a-198">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="6bd9a-199">Para obter mais informações, consulte o [docker executar](https://docs.docker.com/engine/reference/commandline/exec/) referência nos parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-199">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="6bd9a-200">Depois que o aplicativo for iniciado, visite **http://localhost:5000/** no navegador da web.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-200">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="6bd9a-201">Compilar e executar o exemplo com contêineres do Docker para Windows</span><span class="sxs-lookup"><span data-stu-id="6bd9a-201">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="6bd9a-202">Você pode criar e executar o exemplo no Docker usando contêineres do Windows usando os comandos a seguir (as instruções presumem que a raiz do repositório):</span><span class="sxs-lookup"><span data-stu-id="6bd9a-202">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="6bd9a-203">Navegue até o **endereço IP de contêiner** (em vez de http://localhost) em seu navegador diretamente ao usar contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-203">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="6bd9a-204">Você pode obter o endereço IP do seu contêiner com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-204">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="6bd9a-205">Abra o prompt de comando do outro.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-205">Open up another command prompt.</span></span>
* <span data-ttu-id="6bd9a-206">Execute `docker ps` para ver os contêineres em execução.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-206">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="6bd9a-207">O contêiner "aspnetcore_sample" deve existir.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-207">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="6bd9a-208">Execute `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-208">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="6bd9a-209">Copie o endereço IP de contêiner e cole no navegador (por exemplo, 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="6bd9a-209">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!Note]
> <span data-ttu-id="6bd9a-210">A execução do docker oferece suporte à identificação contêineres com o nome ou hash.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-210">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="6bd9a-211">O nome (aspnetcore_sample) é usado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-211">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="6bd9a-212">Consulte o seguinte exemplo de como obter o endereço IP de um contêiner do Windows em execução.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-212">See the following example of how to get the IP address of a running Windows container.</span></span>

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!Note]
> <span data-ttu-id="6bd9a-213">A execução do docker executa um comando de novo em um contêiner em execução.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-213">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="6bd9a-214">Para obter mais informações, consulte o [referência do docker exec](https://docs.docker.com/engine/reference/commandline/exec/) nos parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-214">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="6bd9a-215">Você pode produzir um aplicativo que está pronto para implantar na produção localmente usando o [dotnet publicar](../tools/dotnet-publish.md) comando.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-215">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c release -o published
```

> [!Note]
> <span data-ttu-id="6bd9a-216">O argumento de versão - c cria o aplicativo no modo de liberação (o padrão é o modo de depuração).</span><span class="sxs-lookup"><span data-stu-id="6bd9a-216">The -c release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="6bd9a-217">Para obter mais informações, consulte o [dotnet executar referência](../tools/dotnet-run.md) nos parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-217">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="6bd9a-218">Você pode executar o aplicativo em **Windows** usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-218">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="6bd9a-219">Você pode executar o aplicativo em **Linux** ou **macOS** usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-219">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="6bd9a-220">Imagens do docker usadas neste exemplo</span><span class="sxs-lookup"><span data-stu-id="6bd9a-220">Docker Images used in this sample</span></span>

<span data-ttu-id="6bd9a-221">As seguintes imagens do Docker são usadas neste exemplo</span><span class="sxs-lookup"><span data-stu-id="6bd9a-221">The following Docker images are used in this sample</span></span>

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

<span data-ttu-id="6bd9a-222">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="6bd9a-222">Congratulations!</span></span> <span data-ttu-id="6bd9a-223">Você tem apenas:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-223">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="6bd9a-224">Aprendeu sobre as imagens do Microsoft .NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="6bd9a-224">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="6bd9a-225">Temos um ASP.NET Core Dockerize de aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="6bd9a-225">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="6bd9a-226">Executar o aplicativo de exemplo do ASP.NET localmente</span><span class="sxs-lookup"><span data-stu-id="6bd9a-226">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="6bd9a-227">Compilado e executado o exemplo com o Docker para contêineres do Linux</span><span class="sxs-lookup"><span data-stu-id="6bd9a-227">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="6bd9a-228">Compilado e executado o exemplo com contêineres do Docker para Windows</span><span class="sxs-lookup"><span data-stu-id="6bd9a-228">Built and ran the sample with Docker for Windows containers</span></span>


<span data-ttu-id="6bd9a-229">**Próximas Etapas**</span><span class="sxs-lookup"><span data-stu-id="6bd9a-229">**Next Steps**</span></span>

<span data-ttu-id="6bd9a-230">Aqui estão algumas das próximas etapas que você pode executar:</span><span class="sxs-lookup"><span data-stu-id="6bd9a-230">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="6bd9a-231">Trabalhando com ferramentas de Docker do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6bd9a-231">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="6bd9a-232">Implantação de imagens do Docker do registro do contêiner do Azure para instâncias de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="6bd9a-232">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="6bd9a-233">Depuração com o código do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6bd9a-233">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="6bd9a-234">Obtendo ponteiros com o Visual Studio para Mac, contêineres e código sem servidor na nuvem</span><span class="sxs-lookup"><span data-stu-id="6bd9a-234">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="6bd9a-235">Introdução ao Docker e o Visual Studio para Mac laboratório</span><span class="sxs-lookup"><span data-stu-id="6bd9a-235">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!Note]
> <span data-ttu-id="6bd9a-236">Se você não tiver uma assinatura do Azure, [Inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) para uma conta gratuita de 30 dias e get US $200 em créditos do Azure para testar qualquer combinação de serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="6bd9a-236">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
