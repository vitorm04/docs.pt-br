---
title: Para qual sistema operacional direcionar com os contêineres do .NET
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Para qual sistema operacional direcionar com os contêineres do .NET
ms.date: 01/07/2019
ms.openlocfilehash: 7380889374e69ca4d3c981a401af703c19263de5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039685"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="113ea-103">Para qual sistema operacional direcionar com os contêineres do .NET</span><span class="sxs-lookup"><span data-stu-id="113ea-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="113ea-104">Dada a diversidade de sistemas operacionais compatíveis com o Docker e as diferenças entre o .NET Framework e o .NET Core, você deve direcionar um sistema operacional e versões específicos dependendo da estrutura que você está usando.</span><span class="sxs-lookup"><span data-stu-id="113ea-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="113ea-105">Para o Windows, é possível usar o Windows Server Core ou o Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="113ea-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="113ea-106">Essas versões do Windows oferecem características diferentes (IIS no Windows Server Core versus um servidor Web auto-hospedado como Kestrel no Nano Server) que podem ser exigidas pelo .NET Framework ou pelo .NET Core, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="113ea-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="113ea-107">Para Linux, várias distribuições estão disponíveis e há compatibilidade com elas nas imagens oficiais do .NET Docker (como Debian).</span><span class="sxs-lookup"><span data-stu-id="113ea-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="113ea-108">Na Figure 3-1, é possível ver a possível versão do sistema operacional dependendo do .NET Framework usado.</span><span class="sxs-lookup"><span data-stu-id="113ea-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![Ao implantar aplicativos .NET Framework herdados, é necessário definir o Windows Server Core como destino, compatível com aplicativos herdados e o IIS e com uma imagem maior.](./media/image1.png)

<span data-ttu-id="113ea-113">**Figura 3-1.**</span><span class="sxs-lookup"><span data-stu-id="113ea-113">**Figure 3-1.**</span></span> <span data-ttu-id="113ea-114">Sistemas operacionais a serem direcionados dependendo das versões do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="113ea-114">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="113ea-115">Também é possível criar sua própria imagem do Docker em casos em que você deseja usar uma distribuição diferente do Linux ou em que você quer uma imagem com versões não fornecidas pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="113ea-115">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="113ea-116">Por exemplo, você pode criar uma imagem com o ASP.NET Core em execução no .NET Framework tradicional e no Windows Server Core, que é um cenário não tão comum para Docker.</span><span class="sxs-lookup"><span data-stu-id="113ea-116">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="113ea-117">Ao adicionar o nome de imagem ao seu arquivo Dockerfile, é possível selecionar o sistema operacional e a versão dependendo da marcação usada, como nos seguintes exemplos:</span><span class="sxs-lookup"><span data-stu-id="113ea-117">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

| <span data-ttu-id="113ea-118">Image</span><span class="sxs-lookup"><span data-stu-id="113ea-118">Image</span></span> | <span data-ttu-id="113ea-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="113ea-119">Comments</span></span> |
|-------|----------|
| <span data-ttu-id="113ea-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span><span class="sxs-lookup"><span data-stu-id="113ea-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span></span> | <span data-ttu-id="113ea-121">.NET Core 2.2 de várias arquiteturas: Dá suporte ao Linux e ao Windows Nano Server dependendo do host do Docker.</span><span class="sxs-lookup"><span data-stu-id="113ea-121">.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> |
| <span data-ttu-id="113ea-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span><span class="sxs-lookup"><span data-stu-id="113ea-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span></span> | <span data-ttu-id="113ea-123">ASP.NET Core 2.2 de várias arquiteturas: Dá suporte ao Linux e ao Windows Nano Server dependendo do host do Docker.</span><span class="sxs-lookup"><span data-stu-id="113ea-123">ASP.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> <br/> <span data-ttu-id="113ea-124">A imagem aspnetcore tem algumas otimizações para ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="113ea-124">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span> |
| <span data-ttu-id="113ea-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span><span class="sxs-lookup"><span data-stu-id="113ea-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span></span> | <span data-ttu-id="113ea-126">.NET Core 2.2 somente em tempo de execução na distribuição do Linux Alpine</span><span class="sxs-lookup"><span data-stu-id="113ea-126">.NET Core 2.2 runtime-only on Linux Alpine distro</span></span> |
| <span data-ttu-id="113ea-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span><span class="sxs-lookup"><span data-stu-id="113ea-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span></span> | <span data-ttu-id="113ea-128">.NET Core 2.2 somente em tempo de execução no Windows Nano Server (Windows Server versão 1803)</span><span class="sxs-lookup"><span data-stu-id="113ea-128">.NET Core 2.2 runtime-only on Windows Nano Server (Windows Server version 1803)</span></span> |

> [!div class="step-by-step"]
> <span data-ttu-id="113ea-129">[Anterior](container-framework-choice-factors.md)
> [Próximo](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="113ea-129">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
