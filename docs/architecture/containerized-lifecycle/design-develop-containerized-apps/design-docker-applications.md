---
title: Criar aplicativos de Docker
description: Encontre aqui uma referência a um guia detalhado sobre a arquitetura de microsserviços, porque esse é um tópico que não é detalhado neste guia.
ms.date: 08/06/2020
ms.openlocfilehash: b63d4344abb358a393587bdacf91f6091b531af0
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915982"
---
# <a name="design-docker-applications"></a><span data-ttu-id="f5485-103">Criar aplicativos de Docker</span><span class="sxs-lookup"><span data-stu-id="f5485-103">Design Docker applications</span></span>

<span data-ttu-id="f5485-104">O Capítulo 1 apresentou os conceitos fundamentais sobre contêineres e Docker.</span><span class="sxs-lookup"><span data-stu-id="f5485-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="f5485-105">Essa informação é o nível básico de informações que você precisa para começar.</span><span class="sxs-lookup"><span data-stu-id="f5485-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="f5485-106">Entretanto, os aplicativos empresariais podem ser complexos e são compostos de vários serviços e não de um único serviço ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="f5485-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="f5485-107">Para esses casos de uso opcionais, você precisa saber outras abordagens para design, como a SOA (Arquitetura Orientada a Serviços) e os conceitos de microsserviços mais avançados, bem como os conceitos de orquestração de contêiner.</span><span class="sxs-lookup"><span data-stu-id="f5485-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="f5485-108">O escopo deste documento não está limitado aos microserviços, mas a qualquer ciclo de vida do aplicativo Docker, portanto, ele não explora a arquitetura de microserviços em detalhes, pois você também pode usar contêineres e Docker com tarefas SOA, em segundo plano ou trabalhos regulares, ou mesmo com abordagens de implantação de aplicativo monolítico.</span><span class="sxs-lookup"><span data-stu-id="f5485-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you can also use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="f5485-109">**Mais informações** Para saber mais sobre as arquiteturas de aplicativos empresariais e de microserviço em detalhes, leia o guia [microserviços: arquitetura para aplicativos .net em contêineres](../../microservices/index.md) dos quais você também pode baixar <https://aka.ms/MicroservicesEbook> .</span><span class="sxs-lookup"><span data-stu-id="f5485-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="f5485-110">No entanto, antes de entrar no ciclo de vida do aplicativo e DevOps, é importante saber como você pretende criar e construir seu aplicativo e quais são suas opções de design.</span><span class="sxs-lookup"><span data-stu-id="f5485-110">However, before you get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f5485-111">[Anterior](index.md) 
> [Avançar](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="f5485-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
