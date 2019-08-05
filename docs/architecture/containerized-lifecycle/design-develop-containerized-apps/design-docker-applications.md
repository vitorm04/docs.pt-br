---
title: Criar aplicativos de Docker
description: Encontre aqui uma referência a um guia detalhado sobre a arquitetura de microsserviços, porque esse é um tópico que não é detalhado neste guia.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674033"
---
# <a name="design-docker-applications"></a><span data-ttu-id="2b905-103">Criar aplicativos de Docker</span><span class="sxs-lookup"><span data-stu-id="2b905-103">Design Docker applications</span></span>

<span data-ttu-id="2b905-104">O Capítulo 1 apresentou os conceitos fundamentais sobre contêineres e Docker.</span><span class="sxs-lookup"><span data-stu-id="2b905-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="2b905-105">Essa informação é o nível básico de informações que você precisa para começar.</span><span class="sxs-lookup"><span data-stu-id="2b905-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="2b905-106">Entretanto, os aplicativos empresariais podem ser complexos e são compostos de vários serviços e não de um único serviço ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="2b905-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="2b905-107">Para esses casos de uso opcionais, você precisa saber outras abordagens para design, como a SOA (Arquitetura Orientada a Serviços) e os conceitos de microsserviços mais avançados, bem como os conceitos de orquestração de contêiner.</span><span class="sxs-lookup"><span data-stu-id="2b905-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="2b905-108">O escopo deste documento não é limitado aos microsserviços, mas para qualquer ciclo de vida do aplicativo Docker, portanto, ele não explora a arquitetura de microsserviços de modo aprofundado porque você também pode usar o Docker e os contêineres com trabalhos ou tarefas em segundo plano, SOA regular ou até mesmo com abordagens de implantação de aplicativo monolítico.</span><span class="sxs-lookup"><span data-stu-id="2b905-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="2b905-109">**Mais informações** Para saber mais sobre aplicativos empresariais e arquitetura de microsserviços em detalhes, leia o guia [Microsserviços NET: arquitetura para aplicativos .NET em contêineres](../../microservices/index.md) que você também pode baixar no <https://aka.ms/MicroservicesEbook>.</span><span class="sxs-lookup"><span data-stu-id="2b905-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="2b905-110">No entanto, antes de entrarmos no ciclo de vida do aplicativo e no DevOps, é importante saber como você pretende projetar e construir seu aplicativo e quais são suas opções de design.</span><span class="sxs-lookup"><span data-stu-id="2b905-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2b905-111">[Anterior](index.md)
>[Próximo](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="2b905-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
