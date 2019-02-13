---
title: Criar aplicativos de Docker
description: Encontre aqui uma referência a um guia detalhado sobre a arquitetura de microsserviços, porque esse é um tópico que ele não é detalhado neste guia.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: f31421cab7d2072441999231adfbe771a3f9a0f5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220199"
---
# <a name="design-docker-applications"></a><span data-ttu-id="d9d41-103">Criar aplicativos de Docker</span><span class="sxs-lookup"><span data-stu-id="d9d41-103">Design Docker applications</span></span>

<span data-ttu-id="d9d41-104">Capítulo 1 apresentou os conceitos fundamentais sobre contêineres e Docker.</span><span class="sxs-lookup"><span data-stu-id="d9d41-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="d9d41-105">Essa informação é o nível básico de informações que você precisa para começar a usar.</span><span class="sxs-lookup"><span data-stu-id="d9d41-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="d9d41-106">Mas, aplicativos corporativos podem ser complexos e compostos de vários serviços, em vez de um único serviço ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="d9d41-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="d9d41-107">Para esses casos de uso opcional, você precisa saber outras abordagens para design, como o SOA (arquitetura) e os conceitos de microsserviços mais avançados e o contêiner de conceitos de orquestração.</span><span class="sxs-lookup"><span data-stu-id="d9d41-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="d9d41-108">O escopo deste documento não é limitado aos microsserviços, mas para qualquer ciclo de vida do aplicativo Docker, portanto, ele não explorar a arquitetura de microsserviços em camadas porque você também pode usar o Docker e contêineres com trabalhos, tarefas em segundo plano ou são regular ou até mesmo com abordagens de implantação do aplicativo monolítico.</span><span class="sxs-lookup"><span data-stu-id="d9d41-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="d9d41-109">No entanto, antes de entrarmos no ciclo de vida do aplicativo e DevOps, é importante saber como você pretende design e construir seu aplicativo e quais são suas opções de design.</span><span class="sxs-lookup"><span data-stu-id="d9d41-109">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d9d41-110">[Anterior](index.md)
>[Próximo](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="d9d41-110">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>