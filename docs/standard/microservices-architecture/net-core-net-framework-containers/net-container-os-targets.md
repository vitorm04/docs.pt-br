---
title: "Qual sistema operacional de destino com contêineres do .NET"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Qual sistema operacional de destino com contêineres do .NET"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 828ccb5e7a76f9419e80793b6cb3a6ba24f358cf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="bf152-104">Qual sistema operacional de destino com contêineres do .NET</span><span class="sxs-lookup"><span data-stu-id="bf152-104">What OS to target with .NET containers</span></span>

<span data-ttu-id="bf152-105">Dada a diversidade de sistemas operacionais com suporte pelo Docker e as diferenças entre o .NET Framework e o .NET Core, você deve ter como destino um sistema operacional específico e versões específicas, dependendo da estrutura que você está usando.</span><span class="sxs-lookup"><span data-stu-id="bf152-105">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span> 

<span data-ttu-id="bf152-106">Para Windows, você pode usar o Windows Server Core ou Nano Server do Windows.</span><span class="sxs-lookup"><span data-stu-id="bf152-106">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="bf152-107">Essas versões do Windows fornecem características diferentes (IIS no Windows Server Core em comparação com um servidor de web auto-hospedado como Kestrel no Nano Server) que podem ser necessários para o .NET Framework ou .NET Core, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="bf152-107">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span> 

<span data-ttu-id="bf152-108">Para o Linux, várias distribuições estão disponíveis e com suporte oficial imagens Docker .NET (como Debian).</span><span class="sxs-lookup"><span data-stu-id="bf152-108">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="bf152-109">Figura 3-1, você verá a versão do SO possíveis dependendo do .NET framework usada.</span><span class="sxs-lookup"><span data-stu-id="bf152-109">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![](./media/image1.png)

<span data-ttu-id="bf152-110">**Figura 3-1.**</span><span class="sxs-lookup"><span data-stu-id="bf152-110">**Figure 3-1.**</span></span> <span data-ttu-id="bf152-111">Sistemas operacionais para o destino dependendo de versões do .NET framework</span><span class="sxs-lookup"><span data-stu-id="bf152-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="bf152-112">Você também pode criar sua própria imagem do Docker em casos em que você deseja usar uma distribuição de Linux diferente ou onde quer uma imagem com as versões não fornecidas pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bf152-112">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="bf152-113">Por exemplo, você pode criar uma imagem com o ASP.NET Core em execução no .NET Framework e Windows Server Core, que é um cenário não tão comuns para Docker tradicional.</span><span class="sxs-lookup"><span data-stu-id="bf152-113">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="bf152-114">Quando você adiciona o nome da imagem ao seu arquivo de Dockerfile, você pode selecionar o sistema operacional e versão de acordo com a marca que você usa, como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="bf152-114">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

-   <span data-ttu-id="bf152-115">Microsoft /**dotnet:2.0.0-tempo de execução-jessie**</span><span class="sxs-lookup"><span data-stu-id="bf152-115">microsoft/**dotnet:2.0.0-runtime-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

-   <span data-ttu-id="bf152-116">Microsoft /**dotnet:2.0.0-tempo de execução-nanoserver-1709**</span><span class="sxs-lookup"><span data-stu-id="bf152-116">microsoft/**dotnet:2.0.0-runtime-nanoserver-1709**</span></span> 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   <span data-ttu-id="bf152-117">Microsoft /**aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="bf152-117">microsoft/**aspnetcore:2.0**</span></span>
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
<span data-ttu-id="bf152-118">[Anterior] (contêiner-estrutura-escolha-factors.md) [Avançar] (oficial-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="bf152-118">[Previous] (container-framework-choice-factors.md) [Next] (official-net-docker-images.md)</span></span>
