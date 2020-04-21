---
title: Criar aplicativos de Docker
description: Encontre aqui uma referência a um guia detalhado sobre a arquitetura de microsserviços, porque esse é um tópico que não é detalhado neste guia.
ms.date: 02/15/2019
ms.openlocfilehash: b8a08658ec6c3df3e1aed596a0240223768dd647
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738459"
---
# <a name="design-docker-applications"></a><span data-ttu-id="a15e5-103">Criar aplicativos de Docker</span><span class="sxs-lookup"><span data-stu-id="a15e5-103">Design Docker applications</span></span>

<span data-ttu-id="a15e5-104">O Capítulo 1 apresentou os conceitos fundamentais sobre contêineres e Docker.</span><span class="sxs-lookup"><span data-stu-id="a15e5-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="a15e5-105">Essa informação é o nível básico de informações que você precisa para começar.</span><span class="sxs-lookup"><span data-stu-id="a15e5-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="a15e5-106">Entretanto, os aplicativos empresariais podem ser complexos e são compostos de vários serviços e não de um único serviço ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="a15e5-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="a15e5-107">Para esses casos de uso opcionais, você precisa saber outras abordagens para design, como a SOA (Arquitetura Orientada a Serviços) e os conceitos de microsserviços mais avançados, bem como os conceitos de orquestração de contêiner.</span><span class="sxs-lookup"><span data-stu-id="a15e5-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="a15e5-108">O escopo deste documento não se limita a microsserviços, mas a qualquer ciclo de vida do aplicativo Docker, portanto, ele não explora a arquitetura de microsserviços em profundidade porque você também pode usar contêineres e Docker com SOA regular, tarefas de fundo ou trabalhos, ou mesmo com abordagens de implantação de aplicativos monolíticos.</span><span class="sxs-lookup"><span data-stu-id="a15e5-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you can also use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="a15e5-109">**Mais informações** Para saber mais sobre aplicativos corporativos e arquitetura de microsserviços em profundidade, leia o guia <https://aka.ms/MicroservicesEbook> [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) que você também pode baixar.</span><span class="sxs-lookup"><span data-stu-id="a15e5-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="a15e5-110">No entanto, antes de entrarmos no ciclo de vida do aplicativo e no DevOps, é importante saber como você pretende projetar e construir seu aplicativo e quais são suas opções de design.</span><span class="sxs-lookup"><span data-stu-id="a15e5-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a15e5-111">[Próximo](index.md)
>[anterior](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="a15e5-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
