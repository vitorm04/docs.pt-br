---
title: "Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker"
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 60d21de06262a14f9be6a1a5ce80edf15ddf1b59
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="04472-104">Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="04472-104">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="04472-105">Há duas implementações com suporte para criar aplicativos do Docker em contêineres do servidor com o .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) e [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="04472-105">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="04472-106">Eles compartilham muitos componentes do .NET Standard e você pode compartilhar o código entre os dois.</span><span class="sxs-lookup"><span data-stu-id="04472-106">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="04472-107">No entanto, há diferenças fundamentais entre eles e a implementação a ser usada dependerá do que você deseja realizar.</span><span class="sxs-lookup"><span data-stu-id="04472-107">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="04472-108">Esta seção fornece orientações sobre quando escolher cada implementação.</span><span class="sxs-lookup"><span data-stu-id="04472-108">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="04472-109">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="04472-109">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
