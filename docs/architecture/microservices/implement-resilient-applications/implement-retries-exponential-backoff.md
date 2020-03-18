---
title: Implementar repetição com retirada exponencial
description: Saiba como implementar repetições com retirada exponencial.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68674533"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="ddca3-103">Implementar repetição com retirada exponencial</span><span class="sxs-lookup"><span data-stu-id="ddca3-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="ddca3-104">[*Repetições com retirada exponencial*](/azure/architecture/patterns/retry) é uma técnica que repete uma operação, com um tempo de espera aumentando exponencialmente, até que uma contagem máxima de repetições seja atingida (a [retirada exponencial](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="ddca3-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="ddca3-105">Essa técnica adota o fato de que recursos de nuvem podem estar temporariamente não disponíveis por mais de alguns segundos por qualquer motivo.</span><span class="sxs-lookup"><span data-stu-id="ddca3-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="ddca3-106">Por exemplo, um orquestrador pode estar movendo um contêiner para outro nó em um cluster para balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="ddca3-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="ddca3-107">Durante esse tempo, algumas solicitações podem falhar.</span><span class="sxs-lookup"><span data-stu-id="ddca3-107">During that time, some requests might fail.</span></span> <span data-ttu-id="ddca3-108">Outro exemplo poderia ser um banco de dados como o SQL Azure, em que um banco de dados pode ser movido para outro servidor para balanceamento de carga, fazendo o banco de dados ficar não disponível por alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="ddca3-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="ddca3-109">Há muitas abordagens para implementar a lógica de repetições com retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="ddca3-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ddca3-110">[Próximo](partial-failure-strategies.md)
>[anterior](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="ddca3-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
