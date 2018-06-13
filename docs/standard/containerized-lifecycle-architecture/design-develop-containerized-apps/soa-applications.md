---
title: Aplicativos de SOA
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 37313c4eb437b6b7a362456a7d1ee3b3aecb6020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569407"
---
# <a name="soa-applications"></a><span data-ttu-id="db190-103">Aplicativos de SOA</span><span class="sxs-lookup"><span data-stu-id="db190-103">SOA applications</span></span>

<span data-ttu-id="db190-104">SOA foi um termo com uso excessivo e deve muitas coisas diferentes para pessoas diferentes.</span><span class="sxs-lookup"><span data-stu-id="db190-104">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="db190-105">Mas, no mínimo e um denominador comum, a SOA, ou a orientação de serviço, a média você estrutura a arquitetura do seu aplicativo, decompondo-la em vários serviços (mais comumente, como serviços HTTP) que podem ser classificados em tipos diferentes, como subsistemas ou, em outros casos, como camadas.</span><span class="sxs-lookup"><span data-stu-id="db190-105">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="db190-106">Atualmente, você pode implantar esses serviços como contêineres do Docker, que resolve problemas relacionados à implantação, porque todas as dependências são incluídas na imagem do contêiner.</span><span class="sxs-lookup"><span data-stu-id="db190-106">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="db190-107">No entanto, quando você precisar de expansão SOAs, você pode encontrar desafios se você estiver implantando com base em instâncias únicas.</span><span class="sxs-lookup"><span data-stu-id="db190-107">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="db190-108">Isso é onde um Docker clustering software ou orchestrator ajudará.</span><span class="sxs-lookup"><span data-stu-id="db190-108">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="db190-109">Vamos examinar isso mais detalhadamente na próxima seção quando analisamos microservices abordagens.</span><span class="sxs-lookup"><span data-stu-id="db190-109">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="db190-110">No final do dia, as soluções de clustering do contêiner são úteis para os dois uma arquitetura SOA tradicional ou uma arquitetura microservices mais avançada no qual cada microsserviço possui seu modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="db190-110">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="db190-111">E, graças aos vários bancos de dados, você também pode expansão a camada de dados em vez de trabalhar com bancos de dados monolíticos compartilhados pelos serviços de SOA.</span><span class="sxs-lookup"><span data-stu-id="db190-111">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="db190-112">No entanto, a discussão sobre os dados de divisão é puramente sobre a arquitetura e design.</span><span class="sxs-lookup"><span data-stu-id="db190-112">However, the discussion about splitting the data is purely about architecture and design.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="db190-113">[Anterior] (state-and-data-in-docker-applications.md) [Avançar] (orquestrar-alta-escalabilidade-availability.md)</span><span class="sxs-lookup"><span data-stu-id="db190-113">[Previous] (state-and-data-in-docker-applications.md) [Next] (orchestrate-high-scalability-availability.md)</span></span>
