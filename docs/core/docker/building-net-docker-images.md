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
ms.workload: dotnetcore
ms.openlocfilehash: cb438957a6519cf503e5bcaf85f2bc82fa18a047
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="95e00-104">Criando imagens do Docker para .NET Core Applications</span><span class="sxs-lookup"><span data-stu-id="95e00-104">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="95e00-105">Neste tutorial, nós nos concentramos em como usar o .NET Core no Docker.</span><span class="sxs-lookup"><span data-stu-id="95e00-105">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="95e00-106">Primeiro, exploramos diferentes imagens do Docker oferecidas e mantidas pela Microsoft, bem como casos de uso.</span><span class="sxs-lookup"><span data-stu-id="95e00-106">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="95e00-107">Em seguida, aprendemos a criar e colocar um aplicativo ASP.NET Core no Docker.</span><span class="sxs-lookup"><span data-stu-id="95e00-107">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="95e00-108">Durante este tutorial, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="95e00-108">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="95e00-109">Saiba mais sobre as imagens do Docker no Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="95e00-109">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="95e00-110">Obter um aplicativo ASP.NET Core de exemplo para colocá-lo no Docker</span><span class="sxs-lookup"><span data-stu-id="95e00-110">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="95e00-111">Executar o aplicativo ASP.NET de exemplo localmente</span><span class="sxs-lookup"><span data-stu-id="95e00-111">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="95e00-112">Compilar e executar a amostra com o Docker para contêineres do Linux</span><span class="sxs-lookup"><span data-stu-id="95e00-112">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="95e00-113">Compilar e executar a amostra com o Docker para contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="95e00-113">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="95e00-114">Otimizações de imagem de Docker</span><span class="sxs-lookup"><span data-stu-id="95e00-114">Docker Image Optimizations</span></span>

<span data-ttu-id="95e00-115">Ao criar imagens do Docker para desenvolvedores, nos concentramos em três cenários principais:</span><span class="sxs-lookup"><span data-stu-id="95e00-115">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="95e00-116">Imagens usadas para desenvolver aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="95e00-116">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="95e00-117">Imagens usadas para compilar aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="95e00-117">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="95e00-118">Imagens usadas para executar aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="95e00-118">Images used to run .NET Core apps</span></span>

<span data-ttu-id="95e00-119">Por que três imagens?</span><span class="sxs-lookup"><span data-stu-id="95e00-119">Why three images?</span></span>
<span data-ttu-id="95e00-120">Ao desenvolver, compilar e executar aplicativos em contêineres, temos prioridades diferentes.</span><span class="sxs-lookup"><span data-stu-id="95e00-120">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="95e00-121">**Desenvolvimento:** a prioridade enfoca em iterar alterações rapidamente e na capacidade de depurar as alterações.</span><span class="sxs-lookup"><span data-stu-id="95e00-121">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="95e00-122">O tamanho da imagem não é tão importante. Em vez disso, você pode fazer alterações no código e observá-las rapidamente?</span><span class="sxs-lookup"><span data-stu-id="95e00-122">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="95e00-123">**Build:** essa imagem contém tudo o que é necessário para compilar o aplicativo, que inclui o compilador e outras dependências para otimizar os binários.</span><span class="sxs-lookup"><span data-stu-id="95e00-123">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="95e00-124">Use a imagem de build para criar os ativos colocados em uma imagem de produção.</span><span class="sxs-lookup"><span data-stu-id="95e00-124">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="95e00-125">A imagem de build será usada para a integração contínua ou em um ambiente de build.</span><span class="sxs-lookup"><span data-stu-id="95e00-125">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="95e00-126">Essa abordagem permite que um agente de build compile o aplicativo (com todas as dependências necessárias) em uma instância de imagem de build.</span><span class="sxs-lookup"><span data-stu-id="95e00-126">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="95e00-127">O agente de build precisa saber apenas como executar essa imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="95e00-127">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="95e00-128">**Produção:** em quanto tempo você pode implantar e iniciar a imagem?</span><span class="sxs-lookup"><span data-stu-id="95e00-128">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="95e00-129">Essa imagem é pequena e, portanto, o desempenho de rede do Registro do Docker para os hosts do Docker é otimizado.</span><span class="sxs-lookup"><span data-stu-id="95e00-129">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="95e00-130">O conteúdo está pronto para ser executado e habilitar o tempo mais rápido possível da execução do Docker até o processamento de resultados.</span><span class="sxs-lookup"><span data-stu-id="95e00-130">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="95e00-131">A compilação de código dinâmico não é necessária no modelo do Docker.</span><span class="sxs-lookup"><span data-stu-id="95e00-131">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="95e00-132">O conteúdo colocado nesta imagem ficaria limitado aos binários e conteúdos necessários para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95e00-132">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="95e00-133">Por exemplo, a saída `dotnet publish` contém:</span><span class="sxs-lookup"><span data-stu-id="95e00-133">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="95e00-134">os binários compilados</span><span class="sxs-lookup"><span data-stu-id="95e00-134">the compiled binaries</span></span>
    * <span data-ttu-id="95e00-135">arquivos .js e .css</span><span class="sxs-lookup"><span data-stu-id="95e00-135">.js and .css files</span></span>


<span data-ttu-id="95e00-136">O motivo para incluir a saída do comando `dotnet publish` na imagem de produção é manter o tamanho mínimo.</span><span class="sxs-lookup"><span data-stu-id="95e00-136">The reason to include the `dotnet publish` command output in your production image is to keep its' size to a minimum.</span></span>

<span data-ttu-id="95e00-137">Algumas imagens do .NET Core compartilham camadas entre marcas diferentes e, portanto, baixar a última marca é um processo relativamente leve.</span><span class="sxs-lookup"><span data-stu-id="95e00-137">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="95e00-138">Se você já tiver uma versão mais antiga no computador, essa arquitetura diminuirá o espaço em disco necessário.</span><span class="sxs-lookup"><span data-stu-id="95e00-138">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="95e00-139">Quando vários aplicativos usam imagens comuns no mesmo computador, a memória é compartilhada entre as imagens comuns.</span><span class="sxs-lookup"><span data-stu-id="95e00-139">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="95e00-140">As imagens devem ser as mesmas para serem compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="95e00-140">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="95e00-141">Variações de imagem do Docker</span><span class="sxs-lookup"><span data-stu-id="95e00-141">Docker image variations</span></span>

<span data-ttu-id="95e00-142">Para atingir as metas descritas acima, fornecemos variantes de imagem em [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="95e00-142">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="95e00-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Essa imagem contém o SDK do .NET Core, que inclui o .NET Core e a CLI (Ferramentas de Linha de Comando).</span><span class="sxs-lookup"><span data-stu-id="95e00-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="95e00-144">Essa imagem é mapeada para o **cenário de desenvolvimento**.</span><span class="sxs-lookup"><span data-stu-id="95e00-144">This image maps to the **development scenario**.</span></span> <span data-ttu-id="95e00-145">Use essa imagem para o desenvolvimento, depuração e teste de unidade local.</span><span class="sxs-lookup"><span data-stu-id="95e00-145">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="95e00-146">Essa imagem também pode ser usada para cenários **de build**.</span><span class="sxs-lookup"><span data-stu-id="95e00-146">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="95e00-147">O uso de `microsoft/dotnet:sdk` sempre fornece a última versão.</span><span class="sxs-lookup"><span data-stu-id="95e00-147">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="95e00-148">Caso não tenha certeza sobre suas necessidades, é recomendável usar a imagem `microsoft/dotnet:<version>-sdk`.</span><span class="sxs-lookup"><span data-stu-id="95e00-148">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="95e00-149">Como a imagem “de fato”, ela foi projetada para ser usada como um contêiner de descarte (montar o código-fonte e iniciar o contêiner para iniciar o aplicativo) e como a imagem base para criar outras imagens.</span><span class="sxs-lookup"><span data-stu-id="95e00-149">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="95e00-150">`microsoft/dotnet:<version>-runtime`: essa imagem contém o .NET Core (tempo de execução e bibliotecas) e é otimizada para executar aplicativos .NET Core em **produção**.</span><span class="sxs-lookup"><span data-stu-id="95e00-150">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="95e00-151">Imagens alternativas</span><span class="sxs-lookup"><span data-stu-id="95e00-151">Alternative images</span></span>

<span data-ttu-id="95e00-152">Além dos cenários otimizados de desenvolvimento, build e produção, fornecemos imagens adicionais:</span><span class="sxs-lookup"><span data-stu-id="95e00-152">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="95e00-153">`microsoft/dotnet:<version>-runtime-deps`: a imagem **runtime-deps** contém o sistema operacional com todas as dependências nativas exigidas pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95e00-153">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="95e00-154">Essa imagem destina-se a [aplicativos autossuficientes](https://docs.microsoft.com/dotnet/core/deploying/index).</span><span class="sxs-lookup"><span data-stu-id="95e00-154">This image is for [self-contained applications](https://docs.microsoft.com/dotnet/core/deploying/index).</span></span>

<span data-ttu-id="95e00-155">Versões mais recentes de cada variante:</span><span class="sxs-lookup"><span data-stu-id="95e00-155">Latest versions of each variant:</span></span>

* <span data-ttu-id="95e00-156">`microsoft/dotnet` ou `microsoft/dotnet:latest` (alias para a imagem do SDK)</span><span class="sxs-lookup"><span data-stu-id="95e00-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="95e00-157">Amostras para explorar</span><span class="sxs-lookup"><span data-stu-id="95e00-157">Samples to explore</span></span>

* <span data-ttu-id="95e00-158">[Este exemplo do Docker no ASP.NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstra um padrão de prática recomendada para compilação de imagens do Docker para aplicativos ASP.NET Core para produção.</span><span class="sxs-lookup"><span data-stu-id="95e00-158">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="95e00-159">O exemplo funciona com contêineres do Linux e do Windows.</span><span class="sxs-lookup"><span data-stu-id="95e00-159">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="95e00-160">Este exemplo do Docker no .NET Core demonstra um padrão de prática recomendada para [compilação de imagens do Docker para aplicativos .NET Core para produção.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="95e00-160">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="95e00-161">Seu primeiro aplicativo ASP.NET Core do Docker</span><span class="sxs-lookup"><span data-stu-id="95e00-161">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="95e00-162">Para este tutorial, vamos usar um aplicativo de exemplo ASP.NET Core Docker para o aplicativo que desejamos colocar no Docker.</span><span class="sxs-lookup"><span data-stu-id="95e00-162">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="95e00-163">Este aplicativo de exemplo ASP.NET Core Docker demonstra um padrão de melhor prática de compilação de imagens do Docker para aplicativos ASP.NET Core para produção.</span><span class="sxs-lookup"><span data-stu-id="95e00-163">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="95e00-164">O exemplo funciona com contêineres do Linux e do Windows.</span><span class="sxs-lookup"><span data-stu-id="95e00-164">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="95e00-165">O Dockerfile de exemplo cria uma imagem do Docker do aplicativo ASP.NET Core baseada na imagem base do Docker do Tempo de Execução do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="95e00-165">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="95e00-166">Ele usa o [recurso de build de vários estágios do Docker](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) para:</span><span class="sxs-lookup"><span data-stu-id="95e00-166">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="95e00-167">compilar a amostra em um contêiner baseado na imagem base **maior** do Docker do Build do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="95e00-167">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="95e00-168">copiar o resultado do build final para uma imagem do Docker baseada na imagem base **menor** do Docker do Tempo de Execução do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="95e00-168">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!Note]
> <span data-ttu-id="95e00-169">A imagem de build contém as ferramentas necessárias para compilar aplicativos, ao contrário da imagem de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="95e00-169">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="95e00-170">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="95e00-170">Prerequisites</span></span>

<span data-ttu-id="95e00-171">Para compilar e executar, instale os seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="95e00-171">To build and run, install the following items:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="95e00-172">SDK do .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="95e00-172">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="95e00-173">Instale o [SDK do .NET Core 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="95e00-173">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="95e00-174">Instale seu editor de código favorito, caso ainda não tenha um.</span><span class="sxs-lookup"><span data-stu-id="95e00-174">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="95e00-175">Precisa instalar um editor de código?</span><span class="sxs-lookup"><span data-stu-id="95e00-175">Need to install a code editor?</span></span> <span data-ttu-id="95e00-176">Experimente o [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="95e00-176">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="95e00-177">Instalando o Cliente do Docker</span><span class="sxs-lookup"><span data-stu-id="95e00-177">Installing Docker Client</span></span>

<span data-ttu-id="95e00-178">Instale o [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) ou posterior do cliente do Docker.</span><span class="sxs-lookup"><span data-stu-id="95e00-178">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="95e00-179">O cliente do Docker pode ser instalado em:</span><span class="sxs-lookup"><span data-stu-id="95e00-179">The Docker client can be installed in:</span></span>

* <span data-ttu-id="95e00-180">Distribuições Linux</span><span class="sxs-lookup"><span data-stu-id="95e00-180">Linux distributions</span></span>

   * [<span data-ttu-id="95e00-181">CentOS</span><span class="sxs-lookup"><span data-stu-id="95e00-181">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="95e00-182">Debian</span><span class="sxs-lookup"><span data-stu-id="95e00-182">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="95e00-183">Fedora</span><span class="sxs-lookup"><span data-stu-id="95e00-183">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="95e00-184">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="95e00-184">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="95e00-185">macOS</span><span class="sxs-lookup"><span data-stu-id="95e00-185">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="95e00-186">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="95e00-186">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="95e00-187">Instalando o Git para o repositório de exemplo</span><span class="sxs-lookup"><span data-stu-id="95e00-187">Installing Git for sample repository</span></span>

* <span data-ttu-id="95e00-188">Instale o [git](https://git-scm.com/download) caso deseje clonar o repositório.</span><span class="sxs-lookup"><span data-stu-id="95e00-188">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="95e00-189">Obtendo o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="95e00-189">Getting the sample application</span></span>

<span data-ttu-id="95e00-190">A maneira mais fácil de obter a amostra é por meio da clonagem do [repositório de amostras](https://github.com/dotnet/dotnet-docker-samples) com o git, usando as seguintes instruções:</span><span class="sxs-lookup"><span data-stu-id="95e00-190">The easiest way to get the sample is by cloning the [samples repository](https://github.com/dotnet/dotnet-docker-samples) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

<span data-ttu-id="95e00-191">Também baixe o repositório (ele é pequeno) como um zip no repositório de amostras do Docker do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95e00-191">You can also download the repository (it is small) as a zip from the .NET Core Docker samples repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="95e00-192">Executar o aplicativo ASP.NET localmente</span><span class="sxs-lookup"><span data-stu-id="95e00-192">Run the ASP.NET app locally</span></span>

<span data-ttu-id="95e00-193">Para um ponto de referência, antes de colocarmos o aplicativo em contêineres, primeiro devemos executá-lo localmente.</span><span class="sxs-lookup"><span data-stu-id="95e00-193">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="95e00-194">Compile e execute o aplicativo localmente com o SDK do .NET Core 2.0 usando os seguintes comandos (as instruções pressupõem o uso da raiz do repositório):</span><span class="sxs-lookup"><span data-stu-id="95e00-194">You can build and run the application locally with the .NET Core 2.0 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
dotnet run
```

<span data-ttu-id="95e00-195">Depois que o aplicativo for iniciado, visite **http://localhost:5000** no navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="95e00-195">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="95e00-196">Compilar e executar a amostra com o Docker para contêineres do Linux</span><span class="sxs-lookup"><span data-stu-id="95e00-196">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="95e00-197">Compile e execute a amostra no Docker usando contêineres do Linux com os seguintes comandos (as instruções pressupõem o uso da raiz do repositório):</span><span class="sxs-lookup"><span data-stu-id="95e00-197">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!Note] <span data-ttu-id="95e00-198">O argumento `docker run` '-p' mapeia a porta 5000 no computador local para a porta 80 no contêiner (o formato de mapeamento da porta é `host:container`).</span><span class="sxs-lookup"><span data-stu-id="95e00-198">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="95e00-199">Para obter mais informações, consulte a referência [docker run](https://docs.docker.com/engine/reference/commandline/exec/) nos parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="95e00-199">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="95e00-200">Depois que o aplicativo for iniciado, visite **http://localhost:5000** no navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="95e00-200">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="95e00-201">Compilar e executar a amostra com o Docker para contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="95e00-201">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="95e00-202">Compile e execute a amostra no Docker usando contêineres do Windows com os seguintes comandos (as instruções pressupõem o uso da raiz do repositório):</span><span class="sxs-lookup"><span data-stu-id="95e00-202">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="95e00-203">Navegue para o **endereço IP do contêiner** (em vez de http://localhost) no navegador diretamente ao usar contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="95e00-203">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="95e00-204">Obtenha o endereço IP do contêiner com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="95e00-204">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="95e00-205">Abra outro prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="95e00-205">Open up another command prompt.</span></span>
* <span data-ttu-id="95e00-206">Execute `docker ps` para ver os contêineres em execução.</span><span class="sxs-lookup"><span data-stu-id="95e00-206">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="95e00-207">O contêiner “aspnetcore_sample” deve estar presente.</span><span class="sxs-lookup"><span data-stu-id="95e00-207">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="95e00-208">Execute `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="95e00-208">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="95e00-209">Copie o endereço IP do contêiner e cole-o no navegador (por exemplo, 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="95e00-209">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!Note]
> <span data-ttu-id="95e00-210">O docker exec dá suporte à identificação de contêineres com o nome ou hash.</span><span class="sxs-lookup"><span data-stu-id="95e00-210">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="95e00-211">O nome (aspnetcore_sample) é usado em nosso exemplo.</span><span class="sxs-lookup"><span data-stu-id="95e00-211">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="95e00-212">Consulte o exemplo a seguir de como obter o endereço IP de um contêiner do Windows em execução.</span><span class="sxs-lookup"><span data-stu-id="95e00-212">See the following example of how to get the IP address of a running Windows container.</span></span>

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
> <span data-ttu-id="95e00-213">O docker exec executa um novo comando em um contêiner em execução.</span><span class="sxs-lookup"><span data-stu-id="95e00-213">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="95e00-214">Para obter mais informações, consulte a [referência de docker exec](https://docs.docker.com/engine/reference/commandline/exec/) nos parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="95e00-214">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="95e00-215">Produza um aplicativo que está pronto para ser implantado em produção localmente usando o comando [dotnet publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="95e00-215">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c release -o published
```

> [!Note]
> <span data-ttu-id="95e00-216">O argumento de versão -c compila o aplicativo no modo de versão (o padrão é o modo de depuração).</span><span class="sxs-lookup"><span data-stu-id="95e00-216">The -c release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="95e00-217">Para obter mais informações, consulte a referência [dotnet run](../tools/dotnet-run.md) nos parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="95e00-217">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="95e00-218">Execute o aplicativo no **Windows** usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="95e00-218">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="95e00-219">Execute o aplicativo no **Linux** ou **macOS** usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="95e00-219">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="95e00-220">Imagens do Docker usadas nesta amostra</span><span class="sxs-lookup"><span data-stu-id="95e00-220">Docker Images used in this sample</span></span>

<span data-ttu-id="95e00-221">As seguintes imagens do Docker são usadas nesta amostra</span><span class="sxs-lookup"><span data-stu-id="95e00-221">The following Docker images are used in this sample</span></span>

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

<span data-ttu-id="95e00-222">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="95e00-222">Congratulations!</span></span> <span data-ttu-id="95e00-223">Você acabou de:</span><span class="sxs-lookup"><span data-stu-id="95e00-223">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="95e00-224">Aprender sobre as imagens do Docker no Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="95e00-224">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="95e00-225">Obter um aplicativo ASP.NET Core de exemplo para colocá-lo no Docker</span><span class="sxs-lookup"><span data-stu-id="95e00-225">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="95e00-226">Executar o aplicativo ASP.NET de exemplo localmente</span><span class="sxs-lookup"><span data-stu-id="95e00-226">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="95e00-227">Compilar e executar a amostra com o Docker para contêineres do Linux</span><span class="sxs-lookup"><span data-stu-id="95e00-227">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="95e00-228">Compilar e executar a amostra com o Docker para contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="95e00-228">Built and ran the sample with Docker for Windows containers</span></span>


<span data-ttu-id="95e00-229">**Próximas Etapas**</span><span class="sxs-lookup"><span data-stu-id="95e00-229">**Next Steps**</span></span>

<span data-ttu-id="95e00-230">Estas são algumas das próximas etapas que podem ser realizadas:</span><span class="sxs-lookup"><span data-stu-id="95e00-230">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="95e00-231">Trabalhar com ferramentas de Docker do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="95e00-231">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="95e00-232">Implantar imagens do Docker do Registro de Contêiner do Azure para Instâncias de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="95e00-232">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="95e00-233">Depurar com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="95e00-233">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="95e00-234">Prática com o Visual Studio para Mac, contêineres e código sem servidor na nuvem</span><span class="sxs-lookup"><span data-stu-id="95e00-234">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="95e00-235">Introdução ao Docker e ao Visual Studio para Mac Lab</span><span class="sxs-lookup"><span data-stu-id="95e00-235">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!Note]
> <span data-ttu-id="95e00-236">Se você não tiver uma assinatura do Azure, [inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) em uma conta gratuita de 30 dias e receba $200 em Créditos do Azure para experimentar qualquer combinação de serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="95e00-236">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
