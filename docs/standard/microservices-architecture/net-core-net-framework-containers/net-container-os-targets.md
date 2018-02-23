---
title: "Para qual sistema operacional direcionar com os contêineres do .NET"
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Para qual sistema operacional direcionar com os contêineres do .NET"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ef7a21efa23be3a5181f08066a093abbb915c20f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="5dcc1-104">Para qual sistema operacional direcionar com os contêineres do .NET</span><span class="sxs-lookup"><span data-stu-id="5dcc1-104">What OS to target with .NET containers</span></span>

<span data-ttu-id="5dcc1-105">Dada a diversidade de sistemas operacionais compatíveis com o Docker e as diferenças entre o .NET Framework e o .NET Core, você deve direcionar um sistema operacional e versões específicos dependendo da estrutura que você está usando.</span><span class="sxs-lookup"><span data-stu-id="5dcc1-105">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span> 

<span data-ttu-id="5dcc1-106">Para o Windows, é possível usar o Windows Server Core ou o Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="5dcc1-106">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="5dcc1-107">Essas versões do Windows oferecem características diferentes (IIS no Windows Server Core versus um servidor Web auto-hospedado como Kestrel no Nano Server) que podem ser exigidas pelo .NET Framework ou pelo .NET Core, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5dcc1-107">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span> 

<span data-ttu-id="5dcc1-108">Para Linux, várias distribuições estão disponíveis e há compatibilidade com elas nas imagens oficiais do .NET Docker (como Debian).</span><span class="sxs-lookup"><span data-stu-id="5dcc1-108">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="5dcc1-109">Na Figure 3-1, é possível ver a possível versão do sistema operacional dependendo do .NET Framework usado.</span><span class="sxs-lookup"><span data-stu-id="5dcc1-109">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![](./media/image1.png)

<span data-ttu-id="5dcc1-110">**Figura 3-1.**</span><span class="sxs-lookup"><span data-stu-id="5dcc1-110">**Figure 3-1.**</span></span> <span data-ttu-id="5dcc1-111">Sistemas operacionais a serem direcionados dependendo das versões do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5dcc1-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="5dcc1-112">Também é possível criar sua própria imagem do Docker em casos em que você deseja usar uma distribuição diferente do Linux ou em que você quer uma imagem com versões não fornecidas pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5dcc1-112">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="5dcc1-113">Por exemplo, você pode criar uma imagem com o ASP.NET Core em execução no .NET Framework tradicional e no Windows Server Core, que é um cenário não tão comum para Docker.</span><span class="sxs-lookup"><span data-stu-id="5dcc1-113">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="5dcc1-114">Ao adicionar o nome de imagem ao seu arquivo Dockerfile, é possível selecionar o sistema operacional e a versão dependendo da marcação usada, como nos seguintes exemplos:</span><span class="sxs-lookup"><span data-stu-id="5dcc1-114">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

-   <span data-ttu-id="5dcc1-115">microsoft/**dotnet:2.0.0-runtime-jessie**</span><span class="sxs-lookup"><span data-stu-id="5dcc1-115">microsoft/**dotnet:2.0.0-runtime-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

-   <span data-ttu-id="5dcc1-116">microsoft/**dotnet:2.0.0-runtime-nanoserver-1709**</span><span class="sxs-lookup"><span data-stu-id="5dcc1-116">microsoft/**dotnet:2.0.0-runtime-nanoserver-1709**</span></span> 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   <span data-ttu-id="5dcc1-117">microsoft/**aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="5dcc1-117">microsoft/**aspnetcore:2.0**</span></span>
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
<span data-ttu-id="5dcc1-118">[Anterior] (container-framework-choice-factors.md) [Próximo] (official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="5dcc1-118">[Previous] (container-framework-choice-factors.md) [Next] (official-net-docker-images.md)</span></span>
