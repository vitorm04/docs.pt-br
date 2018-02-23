---
title: Implementando novas tentativas com retirada exponencial
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando novas tentativas com retirada exponencial"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7ed97b750d6e3f2aa5def72e90e070a49a7c0e63
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-retries-with-exponential-backoff"></a><span data-ttu-id="b33ae-104">Implementando novas tentativas com retirada exponencial</span><span class="sxs-lookup"><span data-stu-id="b33ae-104">Implementing retries with exponential backoff</span></span>

<span data-ttu-id="b33ae-105">[*Novas tentativas com retirada exponencial*](https://docs.microsoft.com/azure/architecture/patterns/retry) é uma técnica que tentará repetir uma operação, com um tempo de espera que aumenta exponencialmente, até que a contagem de repetição máxima tenha sido atingida (a [retirada exponencial](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="b33ae-105">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="b33ae-106">Essa técnica adota o fato de que recursos de nuvem podem estar temporariamente não disponíveis por mais de alguns segundos por qualquer motivo.</span><span class="sxs-lookup"><span data-stu-id="b33ae-106">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="b33ae-107">Por exemplo, um orquestrador pode estar movendo um contêiner para outro nó em um cluster para balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="b33ae-107">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="b33ae-108">Durante esse tempo, algumas solicitações podem falhar.</span><span class="sxs-lookup"><span data-stu-id="b33ae-108">During that time, some requests might fail.</span></span> <span data-ttu-id="b33ae-109">Outro exemplo poderia ser um banco de dados como o SQL Azure, em que um banco de dados pode ser movido para outro servidor para balanceamento de carga, fazendo o banco de dados ficar não disponível por alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="b33ae-109">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="b33ae-110">Há muitas abordagens para implementar a lógica de repetições com retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="b33ae-110">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="b33ae-111">[Anterior] (partial-failure-strategies.md) [Próximo] (implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="b33ae-111">[Previous] (partial-failure-strategies.md) [Next] (implement-resilient-entity-framework-core-sql-connections.md)</span></span>
