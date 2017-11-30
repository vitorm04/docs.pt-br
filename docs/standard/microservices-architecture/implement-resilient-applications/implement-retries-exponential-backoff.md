---
title: "Implementação de novas tentativas com retirada exponencial"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementação de novas tentativas com retirada exponencial"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c8ad8c6363ddff59915efc076161fe6b76074bbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-retries-with-exponential-backoff"></a><span data-ttu-id="73c4a-104">Implementação de novas tentativas com retirada exponencial</span><span class="sxs-lookup"><span data-stu-id="73c4a-104">Implementing retries with exponential backoff</span></span>

<span data-ttu-id="73c4a-105">[*Tentativas de retirada exponencial* ](https://docs.microsoft.com/azure/architecture/patterns/retry) é uma técnica que tentará repetir uma operação, com um tempo de espera aumentando exponencialmente, até um máximo de tentativas foi atingida (o [retirada exponencial](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="73c4a-105">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="73c4a-106">Essa técnica adota o fato de que recursos de nuvem podem estar temporariamente indisponíveis por mais de alguns segundos por qualquer motivo.</span><span class="sxs-lookup"><span data-stu-id="73c4a-106">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="73c4a-107">Por exemplo, um orquestrador pode mover um contêiner para outro nó em um cluster de balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="73c4a-107">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="73c4a-108">Durante esse tempo, algumas solicitações podem falhar.</span><span class="sxs-lookup"><span data-stu-id="73c4a-108">During that time, some requests might fail.</span></span> <span data-ttu-id="73c4a-109">Outro exemplo pode ser um banco de dados como o SQL Azure, onde um banco de dados pode ser movido para outro servidor para balanceamento de carga, fazendo com que o banco de dados ficar indisponível por alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="73c4a-109">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="73c4a-110">Há várias abordagens para implementar a lógica de novas tentativas com retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="73c4a-110">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="73c4a-111">[Anterior] (parcial-falha-strategies.md) [Avançar] (implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="73c4a-111">[Previous] (partial-failure-strategies.md) [Next] (implement-resilient-entity-framework-core-sql-connections.md)</span></span>
