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
# <a name="implementing-retries-with-exponential-backoff"></a>Implementação de novas tentativas com retirada exponencial

[*Tentativas de retirada exponencial* ](https://docs.microsoft.com/azure/architecture/patterns/retry) é uma técnica que tentará repetir uma operação, com um tempo de espera aumentando exponencialmente, até um máximo de tentativas foi atingida (o [retirada exponencial](https://en.wikipedia.org/wiki/Exponential_backoff)). Essa técnica adota o fato de que recursos de nuvem podem estar temporariamente indisponíveis por mais de alguns segundos por qualquer motivo. Por exemplo, um orquestrador pode mover um contêiner para outro nó em um cluster de balanceamento de carga. Durante esse tempo, algumas solicitações podem falhar. Outro exemplo pode ser um banco de dados como o SQL Azure, onde um banco de dados pode ser movido para outro servidor para balanceamento de carga, fazendo com que o banco de dados ficar indisponível por alguns segundos.

Há várias abordagens para implementar a lógica de novas tentativas com retirada exponencial.


>[!div class="step-by-step"]
[Anterior] (parcial-falha-strategies.md) [Avançar] (implement-resilient-entity-framework-core-sql-connections.md)
