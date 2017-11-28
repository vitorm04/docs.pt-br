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
ms.openlocfilehash: f7a5fee26f4d138ae22f3551a25a674b22a2f6d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="c14cf-104">Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="c14cf-104">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="c14cf-105">Há duas implementações com suporte para criar aplicativos do Docker em contêineres do servidor com o .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) e [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="c14cf-105">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="c14cf-106">Eles compartilham muitos componentes do .NET Standard e você pode compartilhar o código entre os dois.</span><span class="sxs-lookup"><span data-stu-id="c14cf-106">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="c14cf-107">No entanto, há diferenças fundamentais entre eles e a implementação a ser usada dependerá do que você deseja realizar.</span><span class="sxs-lookup"><span data-stu-id="c14cf-107">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="c14cf-108">Esta seção fornece orientações sobre quando escolher cada implementação.</span><span class="sxs-lookup"><span data-stu-id="c14cf-108">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c14cf-109">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="c14cf-109">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
