---
title: "Arquitetura orientada a serviços"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Arquitetura orientada a serviços"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 970ff86c77100077d4c7710c0a697d1745d35819
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="b182f-104">Arquitetura orientada a serviços</span><span class="sxs-lookup"><span data-stu-id="b182f-104">Service-oriented architecture</span></span> 

<span data-ttu-id="b182f-105">Arquitetura orientada a serviços (SOA) era um termo com uso excessivo e objetivo coisas diferentes para pessoas diferentes.</span><span class="sxs-lookup"><span data-stu-id="b182f-105">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="b182f-106">Mas como um denominador comum, SOA significa que a estrutura de seu aplicativo, decompondo-la em vários serviços (mais comumente, como serviços HTTP) que podem ser classificados como tipos diferentes, como camadas ou subsistemas.</span><span class="sxs-lookup"><span data-stu-id="b182f-106">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="b182f-107">Esses serviços podem agora ser implantados como contêineres do Docker, que resolve problemas de implantação, como todas as dependências estão incluídas na imagem do contêiner.</span><span class="sxs-lookup"><span data-stu-id="b182f-107">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="b182f-108">No entanto, quando você precisa de expansão aplicativos SOA, você pode ter escalabilidade e desafios de disponibilidade, se você estiver implantando com base em hosts de Docker único.</span><span class="sxs-lookup"><span data-stu-id="b182f-108">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you are deploying based on single Docker hosts.</span></span> <span data-ttu-id="b182f-109">Isso é onde Docker clustering software ou um orquestrador ajudará, conforme explicado nas seções posteriores onde descrevemos abordagens de implantação para microservices.</span><span class="sxs-lookup"><span data-stu-id="b182f-109">This is where Docker clustering software or an orchestrator will help you out, as explained in later sections where we describe deployment approaches for microservices.</span></span>

<span data-ttu-id="b182f-110">Contêineres do docker são úteis (mas não obrigatório) para as arquiteturas tradicionais e orientada a serviços e as arquiteturas de microservices mais avançadas.</span><span class="sxs-lookup"><span data-stu-id="b182f-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="b182f-111">Microservices derivam de SOA, mas SOA é diferente da arquitetura de microservices.</span><span class="sxs-lookup"><span data-stu-id="b182f-111">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="b182f-112">Recursos como agentes centrais grandes, orchestrators centrais no nível da organização e o [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) comuns em SOA.</span><span class="sxs-lookup"><span data-stu-id="b182f-112">Features like big central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="b182f-113">Mas, na maioria dos casos, esses são os padrões na comunidade de microsserviço.</span><span class="sxs-lookup"><span data-stu-id="b182f-113">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="b182f-114">Na verdade, algumas pessoas argumentam que "a arquitetura de microsserviço é feita de SOA."</span><span class="sxs-lookup"><span data-stu-id="b182f-114">In fact, some people argue that “The microservice architecture is SOA done right.”</span></span>

<span data-ttu-id="b182f-115">Este guia se concentra em microservices, como uma abordagem SOA é menos prescritiva do que os requisitos e as técnicas usadas em uma arquitetura de microsserviço.</span><span class="sxs-lookup"><span data-stu-id="b182f-115">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="b182f-116">Se você sabe como criar um aplicativo baseado em microsserviço, você também saber como criar um aplicativo de mais simples e orientada a serviços.</span><span class="sxs-lookup"><span data-stu-id="b182f-116">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="b182f-117">[Anterior] (docker-aplicativo-estado-data.md) [Avançar] (microservices architecture.md)</span><span class="sxs-lookup"><span data-stu-id="b182f-117">[Previous] (docker-application-state-data.md) [Next] (microservices-architecture.md)</span></span>
