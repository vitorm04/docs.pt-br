---
title: Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: e71739b06275d4ee786d246004930d7b66fbc72b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019601"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="594b4-103">Escolhendo entre o .NET Core e do .NET Framework para contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="594b4-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="594b4-104">Há suporte para duas estruturas para criar aplicativos do Docker em contêineres no lado do servidor com o .NET: [.NET Framework e .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="594b4-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="594b4-105">Eles compartilham muitos componentes da plataforma .NET e você pode compartilhar o código entre os dois.</span><span class="sxs-lookup"><span data-stu-id="594b4-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="594b4-106">No entanto, há diferenças fundamentais entre eles e a estrutura a ser usada dependerá do que você deseja realizar.</span><span class="sxs-lookup"><span data-stu-id="594b4-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="594b4-107">Esta seção fornece orientações sobre quando escolher cada estrutura.</span><span class="sxs-lookup"><span data-stu-id="594b4-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="594b4-108">[Anterior](../container-docker-introduction/docker-containers-images-registries.md)
>[Próximo](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="594b4-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>