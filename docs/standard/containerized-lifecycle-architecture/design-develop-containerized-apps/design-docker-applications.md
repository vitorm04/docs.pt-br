---
title: Criar aplicativos de Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 6525e5f80ebb0551e4f85904a467d862aa4133ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="design-docker-applications"></a><span data-ttu-id="fed64-103">Criar aplicativos de Docker</span><span class="sxs-lookup"><span data-stu-id="fed64-103">Design Docker applications</span></span>

<span data-ttu-id="fed64-104">Capítulo 1 introduziu os conceitos fundamentais sobre contêineres e o Docker.</span><span class="sxs-lookup"><span data-stu-id="fed64-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="fed64-105">Essa informação é o nível básico de informações que você precisa para começar.</span><span class="sxs-lookup"><span data-stu-id="fed64-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="fed64-106">Mas, aplicativos corporativos podem ser complexos e composta por vários serviços, em vez de um único serviço ou um contêiner.</span><span class="sxs-lookup"><span data-stu-id="fed64-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="fed64-107">Nos casos de uso opcional, você precisa saber outras abordagens de design, como arquitetura orientada a serviços (SOA) e a microservices conceitos mais avançados e o contêiner conceitos de orquestração.</span><span class="sxs-lookup"><span data-stu-id="fed64-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="fed64-108">O escopo deste documento não está limitado a microservices, mas para qualquer ciclo de vida do aplicativo Docker, portanto, ele não explorar microservices arquitetura em camadas porque você também pode usar contêineres e Docker com são normal, tarefas em segundo plano ou trabalhos, ou até mesmo com abordagens de implantação de aplicativo monolítico.</span><span class="sxs-lookup"><span data-stu-id="fed64-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="fed64-109">No entanto, antes de entrar no ciclo de vida do aplicativo e DevOps, é importante saber como você vai design e construir o aplicativo e quais são suas opções de design.</span><span class="sxs-lookup"><span data-stu-id="fed64-109">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="fed64-110">[Anterior] (index.md) [Avançar] (comum-contêiner-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="fed64-110">[Previous] (index.md) [Next] (common-container-design-principles.md)</span></span>
