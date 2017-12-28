---
title: "Introdução ao .NET e ao Docker"
description: "Noções básicas do Docker e do .NET Core"
keywords: .NET, .NET Core, Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.openlocfilehash: ce02033a7994d48494b4e627f1ed8f1dea4caadb
ms.sourcegitcommit: 5bfcb8d341239df251351f318038d31cdc9159d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="69970-104">Introdução ao .NET e ao Docker</span><span class="sxs-lookup"><span data-stu-id="69970-104">Introduction to .NET and Docker</span></span>

<span data-ttu-id="69970-105">Este artigo fornece uma introdução e uma base conceitual para trabalhar com o .NET no Docker.</span><span class="sxs-lookup"><span data-stu-id="69970-105">This article provides an introduction and conceptual background to working with .NET on Docker.</span></span>

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a><span data-ttu-id="69970-106">Docker: empacotar seus aplicativos para implantar e executar em qualquer lugar</span><span class="sxs-lookup"><span data-stu-id="69970-106">Docker: Packaging your apps to deploy and run anywhere</span></span>

<span data-ttu-id="69970-107">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) é uma plataforma aberta que permite aos desenvolvedores e administradores compilar [imagens](https://docs.docker.com/glossary/?term=image), enviar e executar aplicativos distribuídos em um ambiente isolado de forma flexível chamado de [contêiner](https://www.docker.com/what-container).</span><span class="sxs-lookup"><span data-stu-id="69970-107">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) is an open platform that enables developers and administrators to build [images](https://docs.docker.com/glossary/?term=image), ship, and run distributed applications in a loosely isolated environment called a [container](https://www.docker.com/what-container).</span></span> <span data-ttu-id="69970-108">Essa abordagem permite um gerenciamento eficiente do ciclo de vida do aplicativo entre ambientes de desenvolvimento, garantia de qualidade e produção.</span><span class="sxs-lookup"><span data-stu-id="69970-108">This approach enables efficient application lifecycle management between development, QA, and production environments.</span></span>
 
<span data-ttu-id="69970-109">A [plataforma do Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) usa o [Mecanismo do Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) para compilar e empacotar rapidamente aplicativos como [imagens do Docker](https://docs.docker.com/glossary/?term=image) criadas usando arquivos escritos no formato [Dockerfile ](https://docs.docker.com/glossary/?term=Dockerfile) que, depois, são implantados e executados em um [contêiner de camadas ](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="69970-109">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image) created using files written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format that then is deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="69970-110">Você pode criar suas próprias [imagens em camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) como dockerfiles, ou usar imagens existentes de um [registro](https://docs.docker.com/glossary/?term=registry), como [Hub do Docker](https://docs.docker.com/glossary/?term=Docker%20Hub).</span><span class="sxs-lookup"><span data-stu-id="69970-110">You can either create your own [layered images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) as dockerfiles or use existing ones from a [registry](https://docs.docker.com/glossary/?term=registry), like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span></span>

<span data-ttu-id="69970-111">A [relação entre contêineres, imagens e registros do Docker](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) é um conceito importante ao [arquitetar e compilar aplicativos ou microsserviços em contêineres](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span><span class="sxs-lookup"><span data-stu-id="69970-111">The [relationship between Docker containers, images, and registries](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) is an important concept when [architecting and building containerized applications or microservices](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span></span> <span data-ttu-id="69970-112">Essa abordagem reduz bastante o tempo entre o desenvolvimento e a implantação.</span><span class="sxs-lookup"><span data-stu-id="69970-112">This approach greatly shortens the time between development and deployment.</span></span>

### <a name="further-reading-and-watching"></a><span data-ttu-id="69970-113">Leituras (e vídeos) adicionais</span><span class="sxs-lookup"><span data-stu-id="69970-113">Further reading (and watching)</span></span>

* [<span data-ttu-id="69970-114">Contêineres baseados em Windows: desenvolvimento de aplicativos modernos com controle de nível empresarial.</span><span class="sxs-lookup"><span data-stu-id="69970-114">Windows-based containers: Modern app development with enterprise-grade control.</span></span>](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [<span data-ttu-id="69970-115">Visão geral do docker</span><span class="sxs-lookup"><span data-stu-id="69970-115">Docker overview</span></span>](https://docs.docker.com/engine/docker-overview/)
* [<span data-ttu-id="69970-116">Dockerfile em contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="69970-116">Dockerfile on Windows Containers</span></span>](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile.md)
* [<span data-ttu-id="69970-117">Práticas recomendadas para escrever Dockerfiles</span><span class="sxs-lookup"><span data-stu-id="69970-117">Best practices for writing Dockerfiles</span></span>](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [<span data-ttu-id="69970-118">Compilar Imagens do Docker para aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="69970-118">Building Docker Images for .NET Core applications</span></span>](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a><span data-ttu-id="69970-119">Obter imagens do .NET Docker</span><span class="sxs-lookup"><span data-stu-id="69970-119">Getting .NET Docker Images</span></span>

<span data-ttu-id="69970-120">As imagens oficiais do .NET Docker são criadas e otimizadas pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="69970-120">The Official .NET Docker images are created and optimized by Microsoft.</span></span> <span data-ttu-id="69970-121">Elas ficam publicamente disponíveis nos repositórios da Microsoft no Hub do Docker.</span><span class="sxs-lookup"><span data-stu-id="69970-121">They are publicly available in the Microsoft repositories on Docker Hub.</span></span> <span data-ttu-id="69970-122">Cada repositório pode conter várias imagens, dependendo das versões do .NET e das versões do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="69970-122">Each repository can contain multiple images, depending on .NET versions, and on OS versions.</span></span> <span data-ttu-id="69970-123">A maioria dos repositórios de imagens fornecem muitas opções de marcação para ajudar você a selecionar uma versão específica do framework e um sistema operacional (distribuição Linux ou versão do Windows).</span><span class="sxs-lookup"><span data-stu-id="69970-123">Most image repos provide extensive tagging to help you select both a specific framework version and an OS (Linux distro or Windows version).</span></span>

## <a name="scenario-based-guidance"></a><span data-ttu-id="69970-124">Orientação baseada em cenário</span><span class="sxs-lookup"><span data-stu-id="69970-124">Scenario Based Guidance</span></span>

<span data-ttu-id="69970-125">A intenção da Microsoft para repositórios do .NET é ter repositórios granulares e focados, que representam um cenário ou carga de trabalho específica.</span><span class="sxs-lookup"><span data-stu-id="69970-125">Microsoft’s intent for .NET repositories is to have granular and focused repos, which represent a specific scenario or workload.</span></span>

<span data-ttu-id="69970-126">As imagens `microsoft/aspnetcore` são otimizadas para aplicativos do ASP.NET Core no Docker, assim os contêineres podem ser iniciados com mais rapidez.</span><span class="sxs-lookup"><span data-stu-id="69970-126">The `microsoft/aspnetcore` images are optimized for ASP.NET Core apps on Docker, so containers can start faster.</span></span>

<span data-ttu-id="69970-127">As imagens do .NET Core (`microsoft/dotnet`) servem para aplicativos de console com base no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69970-127">The .NET Core images (`microsoft/dotnet`) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="69970-128">Por exemplo, processos em lote, Azure WebJobs e outros cenários do console devem usar imagens otimizadas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69970-128">For example, batch processes, Azure WebJobs, and other console scenarios should use optimized .NET Core images.</span></span>

<span data-ttu-id="69970-129">O cenário horizontal mais óbvio para o uso de aplicativos .NET e de Docker é para implantação de produção e hospedagem.</span><span class="sxs-lookup"><span data-stu-id="69970-129">The most obvious horizontal scenario for using Docker and .NET applications is for production deployment and hosting.</span></span> <span data-ttu-id="69970-130">Acontece que produção é apenas um cenário, e os outros são igualmente úteis.</span><span class="sxs-lookup"><span data-stu-id="69970-130">It turns out that production is just one scenario and the other ones are equally useful.</span></span> <span data-ttu-id="69970-131">Esses cenários não são específicos ao .NET, mas devem ser aplicados à maioria das plataformas de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="69970-131">These scenarios are not specific to .NET, but should apply to most developer platforms.</span></span>

* <span data-ttu-id="69970-132">**Instalação de baixa fricção** — Você pode experimentar o .NET sem uma instalação local.</span><span class="sxs-lookup"><span data-stu-id="69970-132">**Low friction install** — You can try out .NET without a local install.</span></span> <span data-ttu-id="69970-133">Basta baixar uma imagem do Docker com o .NET nele.</span><span class="sxs-lookup"><span data-stu-id="69970-133">Just download a Docker image with .NET in it.</span></span>

* <span data-ttu-id="69970-134">**Desenvolver em um contêiner**: você pode desenvolver em um ambiente consistente, tornando os ambientes de desenvolvimento e produção semelhantes (evitando problemas como estado global em computadores de desenvolvedor).</span><span class="sxs-lookup"><span data-stu-id="69970-134">**Develop in a container** — You can develop in a consistent environment, making development and production environments similar (avoiding issues like global state on developer machines).</span></span> <span data-ttu-id="69970-135">As Ferramentas do Visual Studio para Docker permitem até que você inicie um contêiner diretamente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="69970-135">Visual Studio Tools for Docker even enable you to start a container directly from Visual Studio.</span></span>

* <span data-ttu-id="69970-136">**Testar em um contêiner**: você pode testar em um contêiner, reduzindo falhas devido a ambientes configurados incorretamente ou a outras alterações deixadas para trás do último teste.</span><span class="sxs-lookup"><span data-stu-id="69970-136">**Test in a container** — You can test in a container, reducing failures due to incorrectly configured environments or other changes left behind from the last test.</span></span>

* <span data-ttu-id="69970-137">**Compilar um contêiner**: você pode compilar o código em um contêiner, evitando a necessidade de configurar corretamente as máquinas de compilação compartilhadas com vários ambientes, mas, em vez disso, mudar para uma abordagem "BYOC" (traga seu próprio contêiner).</span><span class="sxs-lookup"><span data-stu-id="69970-137">**Build in a container** — You can build code in a container, avoiding the need to correctly configure shared build machines for multiple environments but instead move to a “BYOC” (bring your own container) approach.</span></span>

* <span data-ttu-id="69970-138">**Implantação em todos os ambientes**: você pode implantar uma imagem em todos os seus ambientes.</span><span class="sxs-lookup"><span data-stu-id="69970-138">**Deployment in all environments** — You can deploy an image through all of your environments.</span></span> <span data-ttu-id="69970-139">Essa abordagem reduz falhas devido a diferenças de configuração, normalmente alterando o comportamento da imagem por meio da configuração externa (por exemplo, variáveis de ambiente injetadas).</span><span class="sxs-lookup"><span data-stu-id="69970-139">This approach reduces failures due to configuration differences, typically changing the image behavior via external configuration (for example, injected environment variables).</span></span>

<span data-ttu-id="69970-140">[Orientação geral](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) para decidir entre o .NET Core e o .NET Framework para desenvolvimento de contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="69970-140">[General guidance](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) for deciding between .NET Core and .NET Framework for Docker container development.</span></span>

### <a name="common-docker-development-scenarios"></a><span data-ttu-id="69970-141">Cenários comuns de desenvolvimento do Docker</span><span class="sxs-lookup"><span data-stu-id="69970-141">Common Docker development scenarios</span></span>

#### <a name="net-core"></a><span data-ttu-id="69970-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="69970-142">.NET Core</span></span>

<span data-ttu-id="69970-143">**Recursos do .NET Core**</span><span class="sxs-lookup"><span data-stu-id="69970-143">**.NET Core resources**</span></span>

 <span data-ttu-id="69970-144">Escolha os exemplos do .NET Core que se ajustam aos cenários de seu interesse.</span><span class="sxs-lookup"><span data-stu-id="69970-144">Pick the .NET Core samples that fit your scenarios of interest.</span></span> <span data-ttu-id="69970-145">Todas as instruções de exemplo descrevem como direcionar imagens do Docker para Windows ou do Linux a partir de hosts do Windows, Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="69970-145">All sample instructions describe how to target Windows or Linux Docker images from Windows, Linux, or macOS hosts.</span></span>

<span data-ttu-id="69970-146">Os exemplos usam o .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="69970-146">The samples use .NET Core 2.0.</span></span> <span data-ttu-id="69970-147">Eles usam a [compilação de vários estágios](https://github.com/dotnet/announcements/issues/18) do Docker e [marcas de vários arcos](https://github.com/dotnet/announcements/issues/14), quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="69970-147">They use Docker [multi-stage build](https://github.com/dotnet/announcements/issues/18) and [multi-arch tags](https://github.com/dotnet/announcements/issues/14) where appropriate.</span></span>

* [<span data-ttu-id="69970-148">Imagens do .NET Core no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-148">.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="69970-149">Colocar no docker um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="69970-149">Dockerize a .NET Core application</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)

* <span data-ttu-id="69970-150">Este exemplo de Docker no .NET Core demonstra como [usar o Docker em seu processo de desenvolvimento do .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span><span class="sxs-lookup"><span data-stu-id="69970-150">This .NET Core Docker sample demonstrates how to [use Docker in your .NET Core development process](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span></span> <span data-ttu-id="69970-151">O exemplo funciona com contêineres do Linux e do Windows.</span><span class="sxs-lookup"><span data-stu-id="69970-151">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="69970-152">Este exemplo do Docker no .NET Core demonstra um padrão de prática recomendada para [compilação de imagens do Docker para aplicativos .NET Core para produção.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="69970-152">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span> <span data-ttu-id="69970-153">O exemplo funciona com contêineres do Linux e do Windows.</span><span class="sxs-lookup"><span data-stu-id="69970-153">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="69970-154">Este [exemplo do Docker no .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstra um padrão de prática recomendada para compilação de imagens do Docker para [aplicativos .NET Core autossuficientes](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="69970-154">This [.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstrates a best practice pattern for building Docker images for [self-contained .NET Core applications](../deploying/index.md).</span></span> <span data-ttu-id="69970-155">Usado para o menor contêiner de produção sem um benefício do [compartilhamento de imagens base entre contêineres](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span><span class="sxs-lookup"><span data-stu-id="69970-155">Used for the smallest production container without a benefit from [sharing base images between containers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span></span> <span data-ttu-id="69970-156">No entanto, camadas inferiores do Docker podem ser compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="69970-156">However, lower Docker layers could be shared.</span></span>

#### <a name="arm32--raspberry-pi"></a><span data-ttu-id="69970-157">ARM32 / Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="69970-157">ARM32 / Raspberry Pi</span></span>

* [<span data-ttu-id="69970-158">Anúncio de compilações ARM32 do tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="69970-158">.NET Core Runtime ARM32 builds announcement</span></span>](https://github.com/dotnet/announcements/issues/29)

* [<span data-ttu-id="69970-159">Imagens do .NET Core para ARM32 / Raspberry Pi no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-159">ARM32 / Raspberry Pi .NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="69970-160">Exemplos do Docker do .NET Core ARM32 / Raspberry Pi no GitHub</span><span class="sxs-lookup"><span data-stu-id="69970-160">ARM32 / Raspberry Pi .NET Core Docker Samples on GitHub</span></span>](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a><span data-ttu-id="69970-161">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="69970-161">.NET Framework</span></span>

* [<span data-ttu-id="69970-162">Imagens do .NET framework no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-162">.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet-framework/)

<span data-ttu-id="69970-163">Este repositório contém exemplos que demonstram várias configurações do Docker do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69970-163">This repo contain samples that demonstrate various .NET Framework Docker configurations.</span></span> <span data-ttu-id="69970-164">Use essas imagens como a base de suas próprias imagens do Docker.</span><span class="sxs-lookup"><span data-stu-id="69970-164">You can use these images as the basis of your own Docker images.</span></span>

<span data-ttu-id="69970-165">**.NET Framework 4.7**</span><span class="sxs-lookup"><span data-stu-id="69970-165">**.NET Framework 4.7**</span></span>

<span data-ttu-id="69970-166">O [exemplo dotnet-framework:4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstra o uso de "hello world" básico do [.NET Framework 4.7](../../framework/whats-new/index.md#v47).</span><span class="sxs-lookup"><span data-stu-id="69970-166">[The [dotnet-framework:4.7 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstrates basic "hello world" usage of the [.NET Framework 4.7](../../framework/whats-new/index.md#v47).</span></span> <span data-ttu-id="69970-167">Ele mostra como você pode compilar e implantar o aplicativo dependendo da [imagem do docker para .NET Framework 4.7](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="69970-167">It shows you how you can build and deploy the app relying on the [.NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).</span></span>

<span data-ttu-id="69970-168">**.NET Framework 4.6.2**</span><span class="sxs-lookup"><span data-stu-id="69970-168">**.NET Framework 4.6.2**</span></span>

<span data-ttu-id="69970-169">O [exemplo dotnet-framework:4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstra o uso de "hello world" básico do [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span><span class="sxs-lookup"><span data-stu-id="69970-169">The [dotnet-framework:4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstrates basic "hello world" usage of the [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span></span> <span data-ttu-id="69970-170">Ele mostra como você pode compilar e implantar o aplicativo dependendo da [imagem do docker para .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).</span><span class="sxs-lookup"><span data-stu-id="69970-170">It shows you how you can build and deploy the app relying on the [.NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).</span></span>

<span data-ttu-id="69970-171">**.NET Framework 3.5**</span><span class="sxs-lookup"><span data-stu-id="69970-171">**.NET Framework 3.5**</span></span>

 <span data-ttu-id="69970-172">O [exemplo dotnet-framework:3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstra o uso de "hello world" básico do [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5).</span><span class="sxs-lookup"><span data-stu-id="69970-172">The [dotnet-framework:3.5 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstrates basic "hello world" usage of [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5).</span></span> <span data-ttu-id="69970-173">Ele mostra como você pode compilar e implantar um projeto dependendo do .NET Framework 3.5 no Docker.</span><span class="sxs-lookup"><span data-stu-id="69970-173">It shows you how you can build and deploy a project relying on .NET Framework 3.5 in Docker.</span></span>

#### <a name="aspnet-core"></a><span data-ttu-id="69970-174">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="69970-174">ASP.NET Core</span></span>

* <span data-ttu-id="69970-175">[Este exemplo do Docker no ASP.NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstra um padrão de prática recomendada para compilação de imagens do Docker para aplicativos ASP.NET Core para produção.</span><span class="sxs-lookup"><span data-stu-id="69970-175">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="69970-176">O exemplo funciona com contêineres do Linux e do Windows.</span><span class="sxs-lookup"><span data-stu-id="69970-176">The sample works with both Linux and Windows containers.</span></span>

* [<span data-ttu-id="69970-177">Imagens do ASP.NET Core no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-177">ASP.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [<span data-ttu-id="69970-178">Imagens do ASP.NET Core no GitHub</span><span class="sxs-lookup"><span data-stu-id="69970-178">ASP.NET Core images on GitHub</span></span>](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a><span data-ttu-id="69970-179">ASP.NET Framework</span><span class="sxs-lookup"><span data-stu-id="69970-179">ASP.NET Framework</span></span>

* [<span data-ttu-id="69970-180">Imagens do ASP.NET Framework no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-180">ASP.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnet/)

* [<span data-ttu-id="69970-181">Exemplo de aplicativo Web Forms do ASP.NET no .NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="69970-181">ASP.NET Web Forms app on .NET Framework 4.6.2 sample</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a><span data-ttu-id="69970-182">Windows Communication Framework (WCF)</span><span class="sxs-lookup"><span data-stu-id="69970-182">Windows Communication Framework (WCF)</span></span>

* [<span data-ttu-id="69970-183">Imagens do Windows Communication Framework (WCF) no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-183">Windows Communication Framework (WCF) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/wcf/)

* [<span data-ttu-id="69970-184">Imagens do Windows Communication Framework (WCF) no GitHub</span><span class="sxs-lookup"><span data-stu-id="69970-184">Windows Communication Framework (WCF) images on GitHub</span></span>](https://github.com/microsoft/iis-docker)

* [<span data-ttu-id="69970-185">Exemplos de Docker do Windows Communication Framework (WCF) usando o .NET Full Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="69970-185">Windows Communication Framework (WCF) Docker samples using .NET Full Framework 4.6.2</span></span>](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a><span data-ttu-id="69970-186">Internet Information Server (IIS)</span><span class="sxs-lookup"><span data-stu-id="69970-186">Internet Information Server (IIS)</span></span>

* [<span data-ttu-id="69970-187">Imagens do Internet Information Server (IIS) no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-187">Internet Information Server (IIS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/iis/)

* [<span data-ttu-id="69970-188">Imagens do Internet Information Server (IIS) no GitHub</span><span class="sxs-lookup"><span data-stu-id="69970-188">Internet Information Server (IIS) images on GitHub</span></span>](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a><span data-ttu-id="69970-189">Interagir com outras imagens de contêiner de pilha da Microsoft</span><span class="sxs-lookup"><span data-stu-id="69970-189">Interact with other Microsoft stack container images</span></span>

#### <a name="microsoft-sql-server"></a><span data-ttu-id="69970-190">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="69970-190">Microsoft SQL Server</span></span>

* [<span data-ttu-id="69970-191">Executar o Microsoft SQL Server para imagem de contêiner do Linux 2017 com o Início Rápido do Docker</span><span class="sxs-lookup"><span data-stu-id="69970-191">Run the Microsoft SQL Server for Linux 2017 container image with Docker Quickstart</span></span>](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [<span data-ttu-id="69970-192">Microsoft SQL Server para imagens do Linux no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-192">Microsoft SQL Server for Linux images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="69970-193">Microsoft SQL Server para imagens de contêiner do Windows no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-193">Microsoft SQL Server for Windows Containers images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="69970-194">Imagens do Microsoft SQL Server Express Edition para contêineres do Windows no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-194">Microsoft SQL Server Express Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [<span data-ttu-id="69970-195">Imagens do Microsoft SQL Server Developer Edition para contêineres do Windows no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-195">Microsoft SQL Server Developer Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a><span data-ttu-id="69970-196">Agente do VSTS (Visual Studio Team Services)</span><span class="sxs-lookup"><span data-stu-id="69970-196">Visual Studio Team Services (VSTS) agent</span></span>

* [<span data-ttu-id="69970-197">Imagens de agente VSTS (Visual Studio Team Services) no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-197">Visual Studio Team Services (VSTS) agent images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="69970-198">Imagens de agente VSTS (Visual Studio Team Services) no GitHub</span><span class="sxs-lookup"><span data-stu-id="69970-198">Visual Studio Team Services (VSTS) agent images on GitHub</span></span>](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a><span data-ttu-id="69970-199">Agente do OMS (Operations Management Suite) para Linux</span><span class="sxs-lookup"><span data-stu-id="69970-199">Operations Management Suite (OMS) Linux agent</span></span>

* [<span data-ttu-id="69970-200">Visão geral do agente do OMS (Operations Management Suite) para Linux</span><span class="sxs-lookup"><span data-stu-id="69970-200">Operations Management Suite (OMS) Linux agent overview</span></span>](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [<span data-ttu-id="69970-201">Imagens do OMS (Operations Management Suite) no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-201">Operations Management Suite (OMS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="69970-202">Imagens do OMS (Operations Management Suite) no GitHub</span><span class="sxs-lookup"><span data-stu-id="69970-202">Operations Management Suite (OMS) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a><span data-ttu-id="69970-203">CLI (Interface de linha de comando) do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="69970-203">Microsoft Azure Command Line Interface (CLI)</span></span>

* [<span data-ttu-id="69970-204">Imagens da CLI (Interface de linha de comando) do Microsoft Azure no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-204">Microsoft Azure Command Line Interface (CLI) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cli/) 

* [<span data-ttu-id="69970-205">Imagens da CLI (Interface de linha de comando) do Microsoft Azure no GitHub</span><span class="sxs-lookup"><span data-stu-id="69970-205">Microsoft Azure Command-Line Interface (CLI) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

> [!NOTE]
> <span data-ttu-id="69970-206">Se você não tiver uma assinatura do Azure, [inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) em uma conta gratuita de 30 dias e receba $200 em Créditos do Azure para experimentar qualquer combinação de serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="69970-206">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a><span data-ttu-id="69970-207">Emulador do Microsoft Azure Cosmos DB (apenas Contêineres do Windows)</span><span class="sxs-lookup"><span data-stu-id="69970-207">Microsoft Azure Cosmos DB Emulator (Windows Containers only)</span></span>

* [<span data-ttu-id="69970-208">Imagens do Emulador do Microsoft Azure Cosmos DB no DockerHub</span><span class="sxs-lookup"><span data-stu-id="69970-208">Microsoft Azure Cosmos DB Emulator images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [<span data-ttu-id="69970-209">Usar o Emulador do Azure Cosmos DB para desenvolvimento e teste local</span><span class="sxs-lookup"><span data-stu-id="69970-209">Use the Azure Cosmos DB Emulator for local development and testing</span></span>](/azure/cosmos-db/local-emulator.md#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a><span data-ttu-id="69970-210">Exploração do ecossistema de desenvolvimento avançado do Docker</span><span class="sxs-lookup"><span data-stu-id="69970-210">Exploring the rich Docker development ecosystem</span></span>

<span data-ttu-id="69970-211">Agora que você aprendeu sobre a plataforma do Docker e imagens diferentes do Docker, a próxima etapa é explorar o ecossistema avançado do Docker.</span><span class="sxs-lookup"><span data-stu-id="69970-211">Now that you have learned about the Docker platform and different Docker images, the next step is to explore the rich Docker ecosystem.</span></span> <span data-ttu-id="69970-212">Os links a seguir mostram como as ferramentas da Microsoft complementam o desenvolvimento de contêiner.</span><span class="sxs-lookup"><span data-stu-id="69970-212">The following links show you how the Microsoft tools complement container development.</span></span>

* [<span data-ttu-id="69970-213">Usar o .NET e o Docker juntos</span><span class="sxs-lookup"><span data-stu-id="69970-213">Using .NET and Docker together</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [<span data-ttu-id="69970-214">Projetar e desenvolver aplicativos .NET baseados em microsserviço e em vários contêineres</span><span class="sxs-lookup"><span data-stu-id="69970-214">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [<span data-ttu-id="69970-215">Extensão do Docker do Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69970-215">Visual Studio Code Docker extension</span></span>](https://code.visualstudio.com/docs/languages/dockerfile)
* [<span data-ttu-id="69970-216">Saiba como usar o Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="69970-216">Learn how to use Azure Service Fabric</span></span>](/azure/service-fabric/index.md)
* [<span data-ttu-id="69970-217">Exemplo de introdução ao Service Fabric</span><span class="sxs-lookup"><span data-stu-id="69970-217">Service Fabric Getting Started Sample</span></span>](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [<span data-ttu-id="69970-218">Benefícios dos contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="69970-218">Benefits of Windows Containers</span></span>](/virtualization/windowscontainers/about/index.md#video-overview)
* [<span data-ttu-id="69970-219">Trabalhar com ferramentas de Docker do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="69970-219">Working with Visual Studio Docker Tools</span></span>](/aspnet/core/publishing/visual-studio-tools-for-docker/index.md)
* [<span data-ttu-id="69970-220">Implantar imagens do Docker do Registro de Contêiner do Azure para Instâncias de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="69970-220">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="69970-221">Depurar com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69970-221">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [<span data-ttu-id="69970-222">Prática com o Visual Studio para Mac, contêineres e código sem servidor na nuvem</span><span class="sxs-lookup"><span data-stu-id="69970-222">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="69970-223">Introdução ao Docker e ao Visual Studio para Mac Lab</span><span class="sxs-lookup"><span data-stu-id="69970-223">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a><span data-ttu-id="69970-224">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="69970-224">Next Steps</span></span>

* [<span data-ttu-id="69970-225">Aprenda noções básicas do Docker com o .NET Core</span><span class="sxs-lookup"><span data-stu-id="69970-225">Learn Docker Basics with .NET Core</span></span>](docker-basics-dotnet-core.md)
* <span data-ttu-id="69970-226">[Compilar imagens do Docker do .NET Core](building-net-docker-images.md)
\\</span><span class="sxs-lookup"><span data-stu-id="69970-226">[Building .NET Core Docker Images](building-net-docker-images.md)
\\</span></span>