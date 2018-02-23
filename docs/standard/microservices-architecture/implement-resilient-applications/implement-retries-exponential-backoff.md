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
# <a name="implementing-retries-with-exponential-backoff"></a>Implementando novas tentativas com retirada exponencial

[*Novas tentativas com retirada exponencial*](https://docs.microsoft.com/azure/architecture/patterns/retry) é uma técnica que tentará repetir uma operação, com um tempo de espera que aumenta exponencialmente, até que a contagem de repetição máxima tenha sido atingida (a [retirada exponencial](https://en.wikipedia.org/wiki/Exponential_backoff)). Essa técnica adota o fato de que recursos de nuvem podem estar temporariamente não disponíveis por mais de alguns segundos por qualquer motivo. Por exemplo, um orquestrador pode estar movendo um contêiner para outro nó em um cluster para balanceamento de carga. Durante esse tempo, algumas solicitações podem falhar. Outro exemplo poderia ser um banco de dados como o SQL Azure, em que um banco de dados pode ser movido para outro servidor para balanceamento de carga, fazendo o banco de dados ficar não disponível por alguns segundos.

Há muitas abordagens para implementar a lógica de repetições com retirada exponencial.


>[!div class="step-by-step"]
[Anterior] (partial-failure-strategies.md) [Próximo] (implement-resilient-entity-framework-core-sql-connections.md)
