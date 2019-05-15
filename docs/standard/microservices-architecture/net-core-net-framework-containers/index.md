---
title: Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker
ms.date: 09/11/2018
ms.openlocfilehash: 771d23cf4610e5778f0a144386754ce10d6ae144
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639015"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="c8b6b-103">Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="c8b6b-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="c8b6b-104">Há suporte para duas estruturas para criar aplicativos do Docker em contêineres no lado do servidor com o .NET: [.NET Framework e .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="c8b6b-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="c8b6b-105">Eles compartilham muitos componentes da plataforma .NET e você pode compartilhar o código entre os dois.</span><span class="sxs-lookup"><span data-stu-id="c8b6b-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="c8b6b-106">No entanto, há diferenças fundamentais entre eles e a estrutura a ser usada dependerá do que você deseja realizar.</span><span class="sxs-lookup"><span data-stu-id="c8b6b-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="c8b6b-107">Esta seção fornece orientações sobre quando escolher cada estrutura.</span><span class="sxs-lookup"><span data-stu-id="c8b6b-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c8b6b-108">[Anterior](../container-docker-introduction/docker-containers-images-registries.md)
>[Próximo](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="c8b6b-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
