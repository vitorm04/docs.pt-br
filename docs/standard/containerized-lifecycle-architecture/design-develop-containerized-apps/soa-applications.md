---
title: Aplicativos de SOA
description: Tenha em mente que os contêineres também podem ser uma opção de implantação útil para aplicativos de SOA.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 353ba738143b7dcd92c7c75ac27ea6a7370f9da6
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745827"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="90c4c-103">Aplicativos orientados a serviço</span><span class="sxs-lookup"><span data-stu-id="90c4c-103">Service-oriented applications</span></span>

<span data-ttu-id="90c4c-104">Arquitetura orientada a serviços (SOA) era um termo usado em excesso do que significava muitas coisas diferentes para pessoas diferentes.</span><span class="sxs-lookup"><span data-stu-id="90c4c-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="90c4c-105">Mas como um denominador comum, a SOA significa que você estrutura da arquitetura de seu aplicativo decompondo em vários serviços (mais comumente, como serviços HTTP) que podem ser classificados em diferentes tipos como subsistemas ou, em outros casos, como camadas.</span><span class="sxs-lookup"><span data-stu-id="90c4c-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="90c4c-106">Hoje, você pode implantar esses serviços como contêineres do Docker, que resolvem problemas relacionados à implantação, pois todas as dependências estão incluídas na imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="90c4c-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="90c4c-107">No entanto, quando você precisar expandir SOAs, você pode encontrar desafios se você estiver implantando com base em instâncias únicas.</span><span class="sxs-lookup"><span data-stu-id="90c4c-107">However, when you need to scale out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="90c4c-108">Esse desafio pode ser manipulado usando softwares de clustering ou um orquestrador do Docker.</span><span class="sxs-lookup"><span data-stu-id="90c4c-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="90c4c-109">Vamos examinar mais detalhadamente na próxima seção, orquestradores de quando podemos explorar abordagens de microsserviços.</span><span class="sxs-lookup"><span data-stu-id="90c4c-109">We'll look at orchestrators in greater detail in the next section, when we explore microservices approaches.</span></span>

<span data-ttu-id="90c4c-110">Os contêineres do Docker são úteis (mas não necessários) para arquiteturas tradicionais orientadas a serviço e para as arquiteturas de microsserviços mais avançadas.</span><span class="sxs-lookup"><span data-stu-id="90c4c-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="90c4c-111">No final do dia, as soluções de clustering de contêiner são úteis para os dois uma arquitetura SOA tradicional em uma arquitetura de microsserviços mais avançada em que cada microsserviço tem seu modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="90c4c-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="90c4c-112">E, graças aos vários bancos de dados, você também pode escalar horizontalmente a camada de dados em vez de trabalhar com bancos de dados monolíticos compartilhados pelos serviços de SOA.</span><span class="sxs-lookup"><span data-stu-id="90c4c-112">And thanks to multiple databases, you also can scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="90c4c-113">No entanto, a discussão sobre dividindo os dados é puramente sobre arquitetura e design.</span><span class="sxs-lookup"><span data-stu-id="90c4c-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="90c4c-114">[Anterior](state-and-data-in-docker-applications.md)
>[Próximo](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="90c4c-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>
