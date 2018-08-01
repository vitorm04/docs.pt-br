---
title: Implementar repetição com retirada exponencial
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando novas tentativas com retirada exponencial
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: a5ab15299ecb501691c26bbc6d377e22a38ee51e
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874358"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="6a80d-103">Implementar repetição com retirada exponencial</span><span class="sxs-lookup"><span data-stu-id="6a80d-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="6a80d-104">[*Novas tentativas com retirada exponencial*](https://docs.microsoft.com/azure/architecture/patterns/retry) é uma técnica que tentará repetir uma operação, com um tempo de espera que aumenta exponencialmente, até que a contagem de repetição máxima tenha sido atingida (a [retirada exponencial](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="6a80d-104">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="6a80d-105">Essa técnica adota o fato de que recursos de nuvem podem estar temporariamente não disponíveis por mais de alguns segundos por qualquer motivo.</span><span class="sxs-lookup"><span data-stu-id="6a80d-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="6a80d-106">Por exemplo, um orquestrador pode estar movendo um contêiner para outro nó em um cluster para balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="6a80d-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="6a80d-107">Durante esse tempo, algumas solicitações podem falhar.</span><span class="sxs-lookup"><span data-stu-id="6a80d-107">During that time, some requests might fail.</span></span> <span data-ttu-id="6a80d-108">Outro exemplo poderia ser um banco de dados como o SQL Azure, em que um banco de dados pode ser movido para outro servidor para balanceamento de carga, fazendo o banco de dados ficar não disponível por alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="6a80d-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="6a80d-109">Há muitas abordagens para implementar a lógica de repetições com retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="6a80d-109">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="6a80d-110">[Anterior](partial-failure-strategies.md)
[Próximo](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="6a80d-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
