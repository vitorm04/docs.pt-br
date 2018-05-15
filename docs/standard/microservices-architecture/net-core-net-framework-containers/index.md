---
title: Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: b483214e7bd039a71ae642aa26e69d63222af8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="3d85f-103">Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="3d85f-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="3d85f-104">Há duas implementações com suporte para criar aplicativos do Docker em contêineres do servidor com o .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) e [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="3d85f-104">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="3d85f-105">Eles compartilham muitos componentes do .NET Standard e você pode compartilhar o código entre os dois.</span><span class="sxs-lookup"><span data-stu-id="3d85f-105">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="3d85f-106">No entanto, há diferenças fundamentais entre eles e a implementação a ser usada dependerá do que você deseja realizar.</span><span class="sxs-lookup"><span data-stu-id="3d85f-106">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="3d85f-107">Esta seção fornece orientações sobre quando escolher cada implementação.</span><span class="sxs-lookup"><span data-stu-id="3d85f-107">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="3d85f-108">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="3d85f-108">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
