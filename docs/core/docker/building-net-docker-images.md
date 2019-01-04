---
title: Visão geral das imagens do Docker
description: Saiba como usar as imagens publicadas do Docker do .NET Core no Registro do Docker. Você também aprenderá a efetuar pull de imagens e compilar suas próprias imagens.
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: dd8c6c500dc2177768e6cba0c1e303950e20d4f3
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656031"
---
# <a name="learn-about-docker-images-for-net-core"></a><span data-ttu-id="c506f-104">Saiba mais sobre imagens do Docker para .NET Core</span><span class="sxs-lookup"><span data-stu-id="c506f-104">Learn about Docker images for .NET Core</span></span>

<span data-ttu-id="c506f-105">Neste tutorial, nós nos concentramos em como usar o .NET Core no Docker.</span><span class="sxs-lookup"><span data-stu-id="c506f-105">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="c506f-106">Primeiro, exploramos diferentes imagens do Docker oferecidas e mantidas pela Microsoft, bem como casos de uso.</span><span class="sxs-lookup"><span data-stu-id="c506f-106">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="c506f-107">Em seguida, aprendemos a criar e colocar um aplicativo ASP.NET Core no Docker.</span><span class="sxs-lookup"><span data-stu-id="c506f-107">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="c506f-108">Durante este tutorial, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="c506f-108">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="c506f-109">Saiba mais sobre as imagens do Docker no Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="c506f-109">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="c506f-110">Obter um aplicativo ASP.NET Core de exemplo para colocá-lo no Docker</span><span class="sxs-lookup"><span data-stu-id="c506f-110">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="c506f-111">Executar o aplicativo ASP.NET de exemplo localmente</span><span class="sxs-lookup"><span data-stu-id="c506f-111">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="c506f-112">Compilar e executar a amostra com o Docker para contêineres do Linux</span><span class="sxs-lookup"><span data-stu-id="c506f-112">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="c506f-113">Compilar e executar a amostra com o Docker para contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="c506f-113">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="c506f-114">Otimizações de imagem de Docker</span><span class="sxs-lookup"><span data-stu-id="c506f-114">Docker Image Optimizations</span></span>

<span data-ttu-id="c506f-115">Ao criar imagens do Docker para desenvolvedores, nos concentramos em três cenários principais:</span><span class="sxs-lookup"><span data-stu-id="c506f-115">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="c506f-116">Imagens usadas para desenvolver aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="c506f-116">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="c506f-117">Imagens usadas para compilar aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="c506f-117">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="c506f-118">Imagens usadas para executar aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="c506f-118">Images used to run .NET Core apps</span></span>

<span data-ttu-id="c506f-119">Por que três imagens?</span><span class="sxs-lookup"><span data-stu-id="c506f-119">Why three images?</span></span>
<span data-ttu-id="c506f-120">Ao desenvolver, compilar e executar aplicativos em contêineres, temos prioridades diferentes.</span><span class="sxs-lookup"><span data-stu-id="c506f-120">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="c506f-121">**Desenvolvimento:**  A prioridade tem como foco a rápida iteração de alterações e a capacidade de depurá-las.</span><span class="sxs-lookup"><span data-stu-id="c506f-121">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="c506f-122">O tamanho da imagem não é tão importante. Em vez disso, você pode fazer alterações no código e observá-las rapidamente?</span><span class="sxs-lookup"><span data-stu-id="c506f-122">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="c506f-123">**Build:** Essa imagem contém tudo o que é necessário para compilar o aplicativo, que inclui o compilador e outras dependências para otimizar os binários.</span><span class="sxs-lookup"><span data-stu-id="c506f-123">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="c506f-124">Use a imagem de build para criar os ativos colocados em uma imagem de produção.</span><span class="sxs-lookup"><span data-stu-id="c506f-124">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="c506f-125">A imagem de build será usada para a integração contínua ou em um ambiente de build.</span><span class="sxs-lookup"><span data-stu-id="c506f-125">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="c506f-126">Essa abordagem permite que um agente de build compile o aplicativo (com todas as dependências necessárias) em uma instância de imagem de build.</span><span class="sxs-lookup"><span data-stu-id="c506f-126">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="c506f-127">O agente de build precisa saber apenas como executar essa imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="c506f-127">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="c506f-128">**Produção:** Em quanto tempo você pode implantar e iniciar a imagem?</span><span class="sxs-lookup"><span data-stu-id="c506f-128">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="c506f-129">Essa imagem é pequena e, portanto, o desempenho de rede do Registro do Docker para os hosts do Docker é otimizado.</span><span class="sxs-lookup"><span data-stu-id="c506f-129">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="c506f-130">O conteúdo está pronto para ser executado e habilitar o tempo mais rápido possível da execução do Docker até o processamento de resultados.</span><span class="sxs-lookup"><span data-stu-id="c506f-130">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="c506f-131">A compilação de código dinâmico não é necessária no modelo do Docker.</span><span class="sxs-lookup"><span data-stu-id="c506f-131">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="c506f-132">O conteúdo colocado nesta imagem ficaria limitado aos binários e conteúdos necessários para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c506f-132">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="c506f-133">Por exemplo, a saída `dotnet publish` contém:</span><span class="sxs-lookup"><span data-stu-id="c506f-133">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="c506f-134">os binários compilados</span><span class="sxs-lookup"><span data-stu-id="c506f-134">the compiled binaries</span></span>
    * <span data-ttu-id="c506f-135">arquivos .js e .css</span><span class="sxs-lookup"><span data-stu-id="c506f-135">.js and .css files</span></span>


<span data-ttu-id="c506f-136">O motivo para incluir a saída do comando `dotnet publish` na imagem de produção é manter o tamanho mínimo.</span><span class="sxs-lookup"><span data-stu-id="c506f-136">The reason to include the `dotnet publish` command output in your production image is to keep its size to a minimum.</span></span>

<span data-ttu-id="c506f-137">Algumas imagens do .NET Core compartilham camadas entre marcas diferentes e, portanto, baixar a última marca é um processo relativamente leve.</span><span class="sxs-lookup"><span data-stu-id="c506f-137">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="c506f-138">Se você já tiver uma versão mais antiga no computador, essa arquitetura diminuirá o espaço em disco necessário.</span><span class="sxs-lookup"><span data-stu-id="c506f-138">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="c506f-139">Quando vários aplicativos usam imagens comuns no mesmo computador, a memória é compartilhada entre as imagens comuns.</span><span class="sxs-lookup"><span data-stu-id="c506f-139">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="c506f-140">As imagens devem ser as mesmas para serem compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="c506f-140">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="c506f-141">Variações de imagem do Docker</span><span class="sxs-lookup"><span data-stu-id="c506f-141">Docker image variations</span></span>

<span data-ttu-id="c506f-142">Para atingir as metas descritas acima, fornecemos variantes de imagem em [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="c506f-142">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="c506f-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) Essa imagem contém o SDK do .NET Core, que inclui o .NET Core e a CLI (Ferramentas de Linha de Comando).</span><span class="sxs-lookup"><span data-stu-id="c506f-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="c506f-144">Essa imagem é mapeada para o **cenário de desenvolvimento**.</span><span class="sxs-lookup"><span data-stu-id="c506f-144">This image maps to the **development scenario**.</span></span> <span data-ttu-id="c506f-145">Use essa imagem para o desenvolvimento, depuração e teste de unidade local.</span><span class="sxs-lookup"><span data-stu-id="c506f-145">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="c506f-146">Essa imagem também pode ser usada para cenários **de build**.</span><span class="sxs-lookup"><span data-stu-id="c506f-146">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="c506f-147">O uso de `microsoft/dotnet:sdk` sempre fornece a última versão.</span><span class="sxs-lookup"><span data-stu-id="c506f-147">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="c506f-148">Caso não tenha certeza sobre suas necessidades, é recomendável usar a imagem `microsoft/dotnet:<version>-sdk`.</span><span class="sxs-lookup"><span data-stu-id="c506f-148">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="c506f-149">Como a imagem “de fato”, ela foi projetada para ser usada como um contêiner de descarte (montar o código-fonte e iniciar o contêiner para iniciar o aplicativo) e como a imagem base para criar outras imagens.</span><span class="sxs-lookup"><span data-stu-id="c506f-149">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="c506f-150">`microsoft/dotnet:<version>-runtime`: Essa imagem contém o .NET Core (tempo de execução e bibliotecas) e é otimizada para executar aplicativos .NET Core em **produção**.</span><span class="sxs-lookup"><span data-stu-id="c506f-150">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="c506f-151">Imagens alternativas</span><span class="sxs-lookup"><span data-stu-id="c506f-151">Alternative images</span></span>

<span data-ttu-id="c506f-152">Além dos cenários otimizados de desenvolvimento, build e produção, fornecemos imagens adicionais:</span><span class="sxs-lookup"><span data-stu-id="c506f-152">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="c506f-153">`microsoft/dotnet:<version>-runtime-deps`: A imagem **runtime-deps** contém o sistema operacional com todas as dependências nativas necessárias para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c506f-153">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="c506f-154">Essa imagem destina-se a [aplicativos autossuficientes](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="c506f-154">This image is for [self-contained applications](../deploying/index.md).</span></span>

<span data-ttu-id="c506f-155">Versões mais recentes de cada variante:</span><span class="sxs-lookup"><span data-stu-id="c506f-155">Latest versions of each variant:</span></span>

* <span data-ttu-id="c506f-156">`microsoft/dotnet` ou `microsoft/dotnet:latest` (alias para a imagem do SDK)</span><span class="sxs-lookup"><span data-stu-id="c506f-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="c506f-157">Amostras para explorar</span><span class="sxs-lookup"><span data-stu-id="c506f-157">Samples to explore</span></span>

* <span data-ttu-id="c506f-158">[Este exemplo do Docker no ASP.NET Core](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) demonstra um padrão de prática recomendada para compilação de imagens do Docker para aplicativos ASP.NET Core para produção.</span><span class="sxs-lookup"><span data-stu-id="c506f-158">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="c506f-159">O exemplo funciona com contêineres do Linux e do Windows.</span><span class="sxs-lookup"><span data-stu-id="c506f-159">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="c506f-160">Este exemplo do Docker no .NET Core demonstra um padrão de prática recomendada para [compilação de imagens do Docker para aplicativos .NET Core para produção.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span><span class="sxs-lookup"><span data-stu-id="c506f-160">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span></span>

## <a name="forward-the-request-scheme-and-original-ip-address"></a><span data-ttu-id="c506f-161">Encaminhar o esquema da solicitação e o endereço IP original</span><span class="sxs-lookup"><span data-stu-id="c506f-161">Forward the request scheme and original IP address</span></span>

<span data-ttu-id="c506f-162">Servidores proxy, balanceadores de carga e outros dispositivos de rede geralmente ocultam informações sobre a solicitação antes de elas alcançarem o aplicativo em contêiner:</span><span class="sxs-lookup"><span data-stu-id="c506f-162">Proxy servers, load balancers, and other network appliances often obscure information about a request before it reaches the containerized app:</span></span>

* <span data-ttu-id="c506f-163">Quando solicitações HTTPS são passadas por proxy por HTTP, o esquema original (HTTPS) é perdido e deve ser encaminhado em um cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="c506f-163">When HTTPS requests are proxied over HTTP, the original scheme (HTTPS) is lost and must be forwarded in a header.</span></span>
* <span data-ttu-id="c506f-164">Como um aplicativo recebe uma solicitação do proxy, e não de sua origem verdadeira na Internet ou rede corporativa, o endereço IP do cliente original também deve ser encaminhado em um cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="c506f-164">Because an app receives a request from the proxy and not its true source on the Internet or corporate network, the original client IP address must also be forwarded in a header.</span></span>

<span data-ttu-id="c506f-165">Essas informações podem ser importantes no processamento de solicitações, por exemplo, em redirecionamentos, autenticação, geração de link, avaliação de política e localização geográfica do cliente.</span><span class="sxs-lookup"><span data-stu-id="c506f-165">This information may be important in request processing, for example in redirects, authentication, link generation, policy evaluation, and client geolocation.</span></span>

<span data-ttu-id="c506f-166">Para encaminhar o esquema e o endereço IP original para um aplicativo ASP.NET Core em contêiner, use o Middleware de Cabeçalhos Encaminhados.</span><span class="sxs-lookup"><span data-stu-id="c506f-166">To forward the scheme and original IP address to a containerized ASP.NET Core app, use Forwarded Headers Middleware.</span></span> <span data-ttu-id="c506f-167">Para obter mais informações, veja [Configurar o ASP.NET Core para trabalhar com servidores proxy e balanceadores de carga](/aspnet/core/host-and-deploy/proxy-load-balancer).</span><span class="sxs-lookup"><span data-stu-id="c506f-167">For more information, see [Configure ASP.NET Core to work with proxy servers and load balancers](/aspnet/core/host-and-deploy/proxy-load-balancer).</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="c506f-168">Seu primeiro aplicativo ASP.NET Core do Docker</span><span class="sxs-lookup"><span data-stu-id="c506f-168">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="c506f-169">Para este tutorial, vamos usar um aplicativo de exemplo ASP.NET Core Docker para o aplicativo que desejamos colocar no Docker.</span><span class="sxs-lookup"><span data-stu-id="c506f-169">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="c506f-170">Este aplicativo de exemplo ASP.NET Core Docker demonstra um padrão de melhor prática de compilação de imagens do Docker para aplicativos ASP.NET Core para produção.</span><span class="sxs-lookup"><span data-stu-id="c506f-170">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="c506f-171">O exemplo funciona com contêineres do Linux e do Windows.</span><span class="sxs-lookup"><span data-stu-id="c506f-171">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="c506f-172">O Dockerfile de exemplo cria uma imagem do Docker do aplicativo ASP.NET Core baseada na imagem base do Docker do Tempo de Execução do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c506f-172">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="c506f-173">Ele usa o [recurso de build de vários estágios do Docker](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) para:</span><span class="sxs-lookup"><span data-stu-id="c506f-173">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="c506f-174">compilar a amostra em um contêiner baseado na imagem base **maior** do Docker do Build do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c506f-174">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="c506f-175">copiar o resultado do build final para uma imagem do Docker baseada na imagem base **menor** do Docker do Tempo de Execução do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c506f-175">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!NOTE]
> <span data-ttu-id="c506f-176">A imagem de build contém as ferramentas necessárias para compilar aplicativos, ao contrário da imagem de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c506f-176">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c506f-177">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c506f-177">Prerequisites</span></span>

<span data-ttu-id="c506f-178">Para compilar e executar, instale os seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="c506f-178">To build and run, install the following items:</span></span>

#### <a name="net-core-21-sdk"></a><span data-ttu-id="c506f-179">SDK do .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c506f-179">.NET Core 2.1 SDK</span></span>

* <span data-ttu-id="c506f-180">Instale o [SDK do .NET Core 2.1](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="c506f-180">Install [.NET Core 2.1 SDK](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="c506f-181">Instale seu editor de código favorito, caso ainda não tenha um.</span><span class="sxs-lookup"><span data-stu-id="c506f-181">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="c506f-182">Precisa instalar um editor de código?</span><span class="sxs-lookup"><span data-stu-id="c506f-182">Need to install a code editor?</span></span> <span data-ttu-id="c506f-183">Experimente o [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="c506f-183">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="c506f-184">Instalando o Cliente do Docker</span><span class="sxs-lookup"><span data-stu-id="c506f-184">Installing Docker Client</span></span>

<span data-ttu-id="c506f-185">Instale o [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) ou posterior do cliente do Docker.</span><span class="sxs-lookup"><span data-stu-id="c506f-185">Install [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="c506f-186">O cliente do Docker pode ser instalado em:</span><span class="sxs-lookup"><span data-stu-id="c506f-186">The Docker client can be installed in:</span></span>

* <span data-ttu-id="c506f-187">Distribuições Linux</span><span class="sxs-lookup"><span data-stu-id="c506f-187">Linux distributions</span></span>

   * [<span data-ttu-id="c506f-188">CentOS</span><span class="sxs-lookup"><span data-stu-id="c506f-188">CentOS</span></span>](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [<span data-ttu-id="c506f-189">Debian</span><span class="sxs-lookup"><span data-stu-id="c506f-189">Debian</span></span>](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [<span data-ttu-id="c506f-190">Fedora</span><span class="sxs-lookup"><span data-stu-id="c506f-190">Fedora</span></span>](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [<span data-ttu-id="c506f-191">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c506f-191">Ubuntu</span></span>](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [<span data-ttu-id="c506f-192">macOS</span><span class="sxs-lookup"><span data-stu-id="c506f-192">macOS</span></span>](https://docs.docker.com/docker-for-mac/install/)

* <span data-ttu-id="c506f-193">[Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="c506f-193">[Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="c506f-194">Instalando o Git para o repositório de exemplo</span><span class="sxs-lookup"><span data-stu-id="c506f-194">Installing Git for sample repository</span></span>

* <span data-ttu-id="c506f-195">Instale o [git](https://git-scm.com/download) caso deseje clonar o repositório.</span><span class="sxs-lookup"><span data-stu-id="c506f-195">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="c506f-196">Obtendo o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="c506f-196">Getting the sample application</span></span>

<span data-ttu-id="c506f-197">A maneira mais fácil de obter a amostra é por meio da clonagem do [repositório do Docker do .NET Core](https://github.com/dotnet/dotnet-docker) com o git, usando as seguintes instruções:</span><span class="sxs-lookup"><span data-stu-id="c506f-197">The easiest way to get the sample is by cloning the [.NET Core Docker repository](https://github.com/dotnet/dotnet-docker) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker
```

<span data-ttu-id="c506f-198">Você também pode baixar o repositório (que é pequeno) como um zip no repositório do Docker do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c506f-198">You can also download the repository (it is small) as a zip from the .NET Core Docker repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="c506f-199">Executar o aplicativo ASP.NET localmente</span><span class="sxs-lookup"><span data-stu-id="c506f-199">Run the ASP.NET app locally</span></span>

<span data-ttu-id="c506f-200">Para um ponto de referência, antes de colocarmos o aplicativo em contêineres, primeiro devemos executá-lo localmente.</span><span class="sxs-lookup"><span data-stu-id="c506f-200">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="c506f-201">Compile e execute o aplicativo localmente com o SDK do .NET Core 2.1 usando os seguintes comandos (as instruções pressupõem o uso da raiz do repositório):</span><span class="sxs-lookup"><span data-stu-id="c506f-201">You can build and run the application locally with the .NET Core 2.1 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

<span data-ttu-id="c506f-202">Depois que o aplicativo for iniciado, acesse **http://localhost:5000** no navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="c506f-202">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="c506f-203">Compilar e executar a amostra com o Docker para contêineres do Linux</span><span class="sxs-lookup"><span data-stu-id="c506f-203">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="c506f-204">Compile e execute a amostra no Docker usando contêineres do Linux com os seguintes comandos (as instruções pressupõem o uso da raiz do repositório):</span><span class="sxs-lookup"><span data-stu-id="c506f-204">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> <span data-ttu-id="c506f-205">O argumento `docker run` '-p' mapeia a porta 5000 no computador local para a porta 80 no contêiner (o formato de mapeamento da porta é `host:container`).</span><span class="sxs-lookup"><span data-stu-id="c506f-205">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="c506f-206">Para obter mais informações, consulte a referência [docker run](https://docs.docker.com/engine/reference/commandline/exec/) nos parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c506f-206">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="c506f-207">Depois que o aplicativo for iniciado, acesse **http://localhost:5000** no navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="c506f-207">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="c506f-208">Compilar e executar a amostra com o Docker para contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="c506f-208">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="c506f-209">Compile e execute a amostra no Docker usando contêineres do Windows com os seguintes comandos (as instruções pressupõem o uso da raiz do repositório):</span><span class="sxs-lookup"><span data-stu-id="c506f-209">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="c506f-210">Navegue para o **endereço IP do contêiner** (em vez de `http://localhost`) diretamente no navegador ao usar contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="c506f-210">You must navigate to the **container IP address** (as opposed to `http://localhost`) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="c506f-211">Obtenha o endereço IP do contêiner com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="c506f-211">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="c506f-212">Abra outro prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="c506f-212">Open up another command prompt.</span></span>
* <span data-ttu-id="c506f-213">Execute `docker ps` para ver os contêineres em execução.</span><span class="sxs-lookup"><span data-stu-id="c506f-213">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="c506f-214">O contêiner “aspnetcore_sample” deve estar presente.</span><span class="sxs-lookup"><span data-stu-id="c506f-214">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="c506f-215">Execute `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="c506f-215">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="c506f-216">Copie o endereço IP do contêiner e cole-o no navegador (por exemplo, 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="c506f-216">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!NOTE]
> <span data-ttu-id="c506f-217">O docker exec dá suporte à identificação de contêineres com o nome ou hash.</span><span class="sxs-lookup"><span data-stu-id="c506f-217">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="c506f-218">O nome (aspnetcore_sample) é usado em nosso exemplo.</span><span class="sxs-lookup"><span data-stu-id="c506f-218">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="c506f-219">Consulte o exemplo a seguir de como obter o endereço IP de um contêiner do Windows em execução.</span><span class="sxs-lookup"><span data-stu-id="c506f-219">See the following example of how to get the IP address of a running Windows container.</span></span>

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

> [!NOTE]
> <span data-ttu-id="c506f-220">O docker exec executa um novo comando em um contêiner em execução.</span><span class="sxs-lookup"><span data-stu-id="c506f-220">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="c506f-221">Para obter mais informações, consulte a [referência de docker exec](https://docs.docker.com/engine/reference/commandline/exec/) nos parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c506f-221">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="c506f-222">Produza um aplicativo que está pronto para ser implantado em produção localmente usando o comando [dotnet publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="c506f-222">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> <span data-ttu-id="c506f-223">O argumento de versão -c compila o aplicativo no modo de versão (o padrão é o modo de depuração).</span><span class="sxs-lookup"><span data-stu-id="c506f-223">The -c Release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="c506f-224">Para obter mais informações, consulte a referência [dotnet run](../tools/dotnet-run.md) nos parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c506f-224">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="c506f-225">Execute o aplicativo no **Windows** usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="c506f-225">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="c506f-226">Execute o aplicativo no **Linux** ou **macOS** usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="c506f-226">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="c506f-227">Imagens do Docker usadas nesta amostra</span><span class="sxs-lookup"><span data-stu-id="c506f-227">Docker Images used in this sample</span></span>

<span data-ttu-id="c506f-228">As imagens a seguir do Docker são usadas no dockerfile desta amostra.</span><span class="sxs-lookup"><span data-stu-id="c506f-228">The following Docker images are used in this sample's dockerfile.</span></span>

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

<span data-ttu-id="c506f-229">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="c506f-229">Congratulations!</span></span> <span data-ttu-id="c506f-230">Você acabou de:</span><span class="sxs-lookup"><span data-stu-id="c506f-230">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="c506f-231">Aprender sobre as imagens do Docker no Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="c506f-231">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="c506f-232">Obter um aplicativo ASP.NET Core de exemplo para colocá-lo no Docker</span><span class="sxs-lookup"><span data-stu-id="c506f-232">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="c506f-233">Executar o aplicativo ASP.NET de exemplo localmente</span><span class="sxs-lookup"><span data-stu-id="c506f-233">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="c506f-234">Compilar e executar a amostra com o Docker para contêineres do Linux</span><span class="sxs-lookup"><span data-stu-id="c506f-234">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="c506f-235">Compilar e executar a amostra com o Docker para contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="c506f-235">Built and ran the sample with Docker for Windows containers</span></span>

<span data-ttu-id="c506f-236">**Próximas Etapas**</span><span class="sxs-lookup"><span data-stu-id="c506f-236">**Next Steps**</span></span>

<span data-ttu-id="c506f-237">Estas são algumas das próximas etapas que podem ser realizadas:</span><span class="sxs-lookup"><span data-stu-id="c506f-237">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="c506f-238">Trabalhar com ferramentas de Docker do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c506f-238">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="c506f-239">Implantar imagens do Docker do Registro de Contêiner do Azure para Instâncias de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="c506f-239">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="c506f-240">Depurar com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c506f-240">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="c506f-241">Prática com o Visual Studio para Mac, contêineres e código sem servidor na nuvem</span><span class="sxs-lookup"><span data-stu-id="c506f-241">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="c506f-242">Introdução ao Docker e ao Visual Studio para Mac Lab</span><span class="sxs-lookup"><span data-stu-id="c506f-242">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> <span data-ttu-id="c506f-243">Se você não tiver uma assinatura do Azure, [inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) em uma conta gratuita de 30 dias e receba $200 em Créditos do Azure para experimentar qualquer combinação de serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="c506f-243">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
