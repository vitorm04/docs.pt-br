---
title: Implementar repetição com retirada exponencial
description: Saiba como implementar repetições com retirada exponencial.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 421a4535888f432974c764b238c06b5b323aefb3
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362074"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="8a82a-103">Implementar repetição com retirada exponencial</span><span class="sxs-lookup"><span data-stu-id="8a82a-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="8a82a-104">[*Repetições com retirada exponencial*](/azure/architecture/patterns/retry) é uma técnica que repete uma operação, com um tempo de espera aumentando exponencialmente, até que uma contagem máxima de repetições seja atingida (a [retirada exponencial](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="8a82a-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="8a82a-105">Essa técnica adota o fato de que recursos de nuvem podem estar temporariamente não disponíveis por mais de alguns segundos por qualquer motivo.</span><span class="sxs-lookup"><span data-stu-id="8a82a-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="8a82a-106">Por exemplo, um orquestrador pode estar movendo um contêiner para outro nó em um cluster para balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="8a82a-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="8a82a-107">Durante esse tempo, algumas solicitações podem falhar.</span><span class="sxs-lookup"><span data-stu-id="8a82a-107">During that time, some requests might fail.</span></span> <span data-ttu-id="8a82a-108">Outro exemplo poderia ser um banco de dados como o SQL Azure, em que um banco de dados pode ser movido para outro servidor para balanceamento de carga, fazendo o banco de dados ficar não disponível por alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="8a82a-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="8a82a-109">Há muitas abordagens para implementar a lógica de repetições com retirada exponencial.</span><span class="sxs-lookup"><span data-stu-id="8a82a-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8a82a-110">[Anterior](partial-failure-strategies.md)
>[Próximo](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="8a82a-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>