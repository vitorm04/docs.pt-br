---
title: Para qual sistema operacional direcionar com os contêineres do .NET
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Para qual sistema operacional direcionar com os contêineres do .NET
ms.date: 01/07/2019
ms.openlocfilehash: 8bcfa0212f84c575a63f76e05edec1e511cadc36
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772012"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="def7a-103">Para qual sistema operacional direcionar com os contêineres do .NET</span><span class="sxs-lookup"><span data-stu-id="def7a-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="def7a-104">Dada a diversidade de sistemas operacionais compatíveis com o Docker e as diferenças entre o .NET Framework e o .NET Core, você deve direcionar um sistema operacional e versões específicos dependendo da estrutura que você está usando.</span><span class="sxs-lookup"><span data-stu-id="def7a-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="def7a-105">Para o Windows, é possível usar o Windows Server Core ou o Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="def7a-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="def7a-106">Essas versões do Windows oferecem características diferentes (IIS no Windows Server Core versus um servidor Web auto-hospedado como Kestrel no Nano Server) que podem ser exigidas pelo .NET Framework ou pelo .NET Core, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="def7a-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="def7a-107">Para Linux, várias distribuições estão disponíveis e há compatibilidade com elas nas imagens oficiais do .NET Docker (como Debian).</span><span class="sxs-lookup"><span data-stu-id="def7a-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="def7a-108">Na Figure 3-1, é possível ver a possível versão do sistema operacional dependendo do .NET Framework usado.</span><span class="sxs-lookup"><span data-stu-id="def7a-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![Ao implantar aplicativos .NET Framework herdados, é necessário definir o Windows Server Core como destino, compatível com aplicativos herdados e o IIS e com uma imagem maior.](./media/image1.png)

<span data-ttu-id="def7a-113">**Figura 3-1.**</span><span class="sxs-lookup"><span data-stu-id="def7a-113">**Figure 3-1.**</span></span> <span data-ttu-id="def7a-114">Sistemas operacionais a serem direcionados dependendo das versões do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="def7a-114">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="def7a-115">Também é possível criar sua própria imagem do Docker em casos em que você deseja usar uma distribuição diferente do Linux ou em que você quer uma imagem com versões não fornecidas pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="def7a-115">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="def7a-116">Por exemplo, você pode criar uma imagem com o ASP.NET Core em execução no .NET Framework tradicional e no Windows Server Core, que é um cenário não tão comum para Docker.</span><span class="sxs-lookup"><span data-stu-id="def7a-116">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="def7a-117">Ao usar imagens do Windows Server Core, você pode achar que algumas DLLs estão ausentes, quando comparadas com imagens completas do Windows.</span><span class="sxs-lookup"><span data-stu-id="def7a-117">When using Windows Server Core images, you might find that some DLLs are missing, when compared to full Windows images.</span></span> <span data-ttu-id="def7a-118">Você pode resolver esse problema criando uma imagem personalizada de núcleo do servidor, adicionando os arquivos ausentes no momento da compilação da imagem, conforme mencionado neste [Comentário do GitHub](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).</span><span class="sxs-lookup"><span data-stu-id="def7a-118">You might be able to solve this problem by creating a custom Server Core image, adding the missing files at image build time, as mentioned in this [GitHub comment](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).</span></span>

<span data-ttu-id="def7a-119">Ao adicionar o nome de imagem ao seu arquivo Dockerfile, é possível selecionar o sistema operacional e a versão dependendo da marcação usada, como nos seguintes exemplos:</span><span class="sxs-lookup"><span data-stu-id="def7a-119">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

| <span data-ttu-id="def7a-120">Image</span><span class="sxs-lookup"><span data-stu-id="def7a-120">Image</span></span> | <span data-ttu-id="def7a-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="def7a-121">Comments</span></span> |
|-------|----------|
| <span data-ttu-id="def7a-122">mcr.microsoft.com/dotnet/core/runtime:2.2</span><span class="sxs-lookup"><span data-stu-id="def7a-122">mcr.microsoft.com/dotnet/core/runtime:2.2</span></span> | <span data-ttu-id="def7a-123">.NET Core 2,2 multiarquiteturas: dá suporte ao Linux e ao Windows nano Server dependendo do host do Docker.</span><span class="sxs-lookup"><span data-stu-id="def7a-123">.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> |
| <span data-ttu-id="def7a-124">mcr.microsoft.com/dotnet/core/aspnet:2.2</span><span class="sxs-lookup"><span data-stu-id="def7a-124">mcr.microsoft.com/dotnet/core/aspnet:2.2</span></span> | <span data-ttu-id="def7a-125">ASP.NET Core várias arquiteturas 2,2: dá suporte ao Linux e ao Windows nano Server dependendo do host do Docker.</span><span class="sxs-lookup"><span data-stu-id="def7a-125">ASP.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> <br/> <span data-ttu-id="def7a-126">A imagem aspnetcore tem algumas otimizações para ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="def7a-126">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span> |
| <span data-ttu-id="def7a-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span><span class="sxs-lookup"><span data-stu-id="def7a-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span></span> | <span data-ttu-id="def7a-128">.NET Core 2.2 somente em runtime na distribuição do Linux Alpine</span><span class="sxs-lookup"><span data-stu-id="def7a-128">.NET Core 2.2 runtime-only on Linux Alpine distro</span></span> |
| <span data-ttu-id="def7a-129">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span><span class="sxs-lookup"><span data-stu-id="def7a-129">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span></span> | <span data-ttu-id="def7a-130">.NET Core 2.2 somente em runtime no Windows Nano Server (Windows Server versão 1803)</span><span class="sxs-lookup"><span data-stu-id="def7a-130">.NET Core 2.2 runtime-only on Windows Nano Server (Windows Server version 1803)</span></span> |

## <a name="additional-resources"></a><span data-ttu-id="def7a-131">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="def7a-131">Additional resources</span></span>

- <span data-ttu-id="def7a-132">**BitmapDecoder falha devido a falta de WindowsCodecsExt. dll (problema do GitHub)**</span><span class="sxs-lookup"><span data-stu-id="def7a-132">**BitmapDecoder fails due to missing WindowsCodecsExt.dll (GitHub issue)**</span></span>  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> <span data-ttu-id="def7a-133">[Anterior](container-framework-choice-factors.md)
> [Próximo](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="def7a-133">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
