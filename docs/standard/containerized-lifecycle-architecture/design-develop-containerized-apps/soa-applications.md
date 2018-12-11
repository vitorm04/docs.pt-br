---
title: Aplicativos de SOA
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 7f88daaf0787cf780e7ab9602f35ae4e6ab8308c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155308"
---
# <a name="soa-applications"></a><span data-ttu-id="2566e-103">Aplicativos de SOA</span><span class="sxs-lookup"><span data-stu-id="2566e-103">SOA applications</span></span>

<span data-ttu-id="2566e-104">SOA era um termo usado de maneira exagerado e significava tantas coisas diferentes para pessoas diferentes.</span><span class="sxs-lookup"><span data-stu-id="2566e-104">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="2566e-105">Mas, pelo menos e como um denominador comum, a SOA, ou a orientação por serviços, a média, você estrutura da arquitetura de seu aplicativo decompondo-o em vários serviços (mais comumente, como serviços HTTP) que podem ser classificados em diferentes tipos como subsistemas ou, em outros casos, como camadas.</span><span class="sxs-lookup"><span data-stu-id="2566e-105">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="2566e-106">Hoje, você pode implantar esses serviços como contêineres do Docker, que resolve problemas relacionados à implantação, porque todas as dependências são incluídas na imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="2566e-106">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="2566e-107">No entanto, quando você precisar SOAs de escalabilidade horizontal, você pode encontrar desafios se você estiver implantando com base em instâncias únicas.</span><span class="sxs-lookup"><span data-stu-id="2566e-107">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="2566e-108">Isso é onde um Docker softwares de clustering ou orquestrador ajudará.</span><span class="sxs-lookup"><span data-stu-id="2566e-108">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="2566e-109">Vamos examinar isso mais detalhadamente na próxima seção quando examinamos as abordagens de microsserviços.</span><span class="sxs-lookup"><span data-stu-id="2566e-109">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="2566e-110">No final do dia, as soluções de clustering de contêiner são úteis para os dois uma arquitetura SOA tradicional ou para uma arquitetura de microsserviços mais avançada em que cada microsserviço tem seu modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="2566e-110">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="2566e-111">E, graças aos vários bancos de dados, você também pode expandir a camada de dados em vez de trabalhar com bancos de dados monolíticos compartilhados pelos serviços de SOA.</span><span class="sxs-lookup"><span data-stu-id="2566e-111">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="2566e-112">No entanto, a discussão sobre dividindo os dados é puramente sobre arquitetura e design.</span><span class="sxs-lookup"><span data-stu-id="2566e-112">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2566e-113">[Anterior](state-and-data-in-docker-applications.md)
>[Próximo](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="2566e-113">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>