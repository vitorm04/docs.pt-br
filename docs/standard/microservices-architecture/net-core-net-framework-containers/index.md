---
title: Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 0f6689468eda1dd1b12c24927e650b2b01381274
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104436"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="e1ffd-103">Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="e1ffd-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="e1ffd-104">Há duas implementações com suporte para criar aplicativos do Docker em contêineres do servidor com o .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) e [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="e1ffd-104">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="e1ffd-105">Eles compartilham muitos componentes do .NET Standard e você pode compartilhar o código entre os dois.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-105">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="e1ffd-106">No entanto, há diferenças fundamentais entre eles e a implementação a ser usada dependerá do que você deseja realizar.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-106">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="e1ffd-107">Esta seção fornece orientações sobre quando escolher cada implementação.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-107">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e1ffd-108">[Anterior](../container-docker-introduction/docker-containers-images-registries.md)
[Próximo](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="e1ffd-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
