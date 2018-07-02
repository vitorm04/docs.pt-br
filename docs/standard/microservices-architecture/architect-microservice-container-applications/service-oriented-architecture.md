---
title: Arquitetura orientada a serviço
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Arquitetura orientada a serviço
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 67560cc93b3d147be36a691af440bb78f2315557
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104998"
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="e55f3-103">Arquitetura orientada a serviço</span><span class="sxs-lookup"><span data-stu-id="e55f3-103">Service-oriented architecture</span></span> 

<span data-ttu-id="e55f3-104">A SOA (arquitetura orientada a serviço) era um termo usado de maneira exagerada e significava diferentes coisas para diferentes pessoas.</span><span class="sxs-lookup"><span data-stu-id="e55f3-104">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="e55f3-105">Mas, como um denominador comum, a SOA significa que você estrutura seu aplicativo o decompondo em vários serviços (mais comumente, como serviços HTTP) que podem ser classificados como diferentes tipos como subsistemas ou camadas.</span><span class="sxs-lookup"><span data-stu-id="e55f3-105">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="e55f3-106">Agora esses serviços podem ser implantados como contêineres do Docker, que resolve problemas de implantação, porque todas as dependências estão incluídas na imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="e55f3-106">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="e55f3-107">No entanto, quando você precisa expandir aplicativos SOA, talvez você tenha desafios de escalabilidade e de disponibilidade se estiver implantando com base em hosts únicos do Docker.</span><span class="sxs-lookup"><span data-stu-id="e55f3-107">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you are deploying based on single Docker hosts.</span></span> <span data-ttu-id="e55f3-108">É aí que o software de clustering do Docker ou um orquestrador ajudará você, conforme explicado nas seções posteriores, em que descrevemos abordagens de implantação para microsserviços.</span><span class="sxs-lookup"><span data-stu-id="e55f3-108">This is where Docker clustering software or an orchestrator will help you out, as explained in later sections where we describe deployment approaches for microservices.</span></span>

<span data-ttu-id="e55f3-109">Os contêineres do Docker são úteis (mas não necessários) para arquiteturas tradicionais orientadas a serviço e para as arquiteturas de microsserviços mais avançadas.</span><span class="sxs-lookup"><span data-stu-id="e55f3-109">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="e55f3-110">Os microsserviços derivam da SOA, mas a SOA é diferente da arquitetura de microsserviços.</span><span class="sxs-lookup"><span data-stu-id="e55f3-110">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="e55f3-111">Recursos como agentes centrais grandes, orquestradores centrais no nível da organização e o [ESB (Enterprise Service Bus)](https://en.wikipedia.org/wiki/Enterprise_service_bus) são comuns na SOA.</span><span class="sxs-lookup"><span data-stu-id="e55f3-111">Features like big central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="e55f3-112">Mas, na maioria dos casos, esses são os antipadrões na comunidade de microsserviços.</span><span class="sxs-lookup"><span data-stu-id="e55f3-112">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="e55f3-113">Na verdade, algumas pessoas argumentam que "A arquitetura de microsserviço é SOA feita da maneira certa".</span><span class="sxs-lookup"><span data-stu-id="e55f3-113">In fact, some people argue that “The microservice architecture is SOA done right.”</span></span>

<span data-ttu-id="e55f3-114">Este guia se concentra em microsserviços, porque uma abordagem SOA é menos prescritiva do que os requisitos e as técnicas usados em uma arquitetura de microsserviço.</span><span class="sxs-lookup"><span data-stu-id="e55f3-114">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="e55f3-115">Se você souber como criar um aplicativo baseado em microsserviço, também saberá como criar um aplicativo mais simples orientado a serviços.</span><span class="sxs-lookup"><span data-stu-id="e55f3-115">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="e55f3-116">[Anterior](docker-application-state-data.md)
[Próximo](microservices-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="e55f3-116">[Previous](docker-application-state-data.md)
[Next](microservices-architecture.md)</span></span>
