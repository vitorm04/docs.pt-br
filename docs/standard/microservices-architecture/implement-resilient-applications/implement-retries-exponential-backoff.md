---
title: Implementar repetição com retirada exponencial
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando novas tentativas com retirada exponencial
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: e0758ee8fe28cb45ecd35ad07ddc738c12614973
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148763"
---
# <a name="implement-retries-with-exponential-backoff"></a>Implementar repetição com retirada exponencial

[*Novas tentativas com retirada exponencial*](https://docs.microsoft.com/azure/architecture/patterns/retry) é uma técnica que tentará repetir uma operação, com um tempo de espera que aumenta exponencialmente, até que a contagem de repetição máxima tenha sido atingida (a [retirada exponencial](https://en.wikipedia.org/wiki/Exponential_backoff)). Essa técnica adota o fato de que recursos de nuvem podem estar temporariamente não disponíveis por mais de alguns segundos por qualquer motivo. Por exemplo, um orquestrador pode estar movendo um contêiner para outro nó em um cluster para balanceamento de carga. Durante esse tempo, algumas solicitações podem falhar. Outro exemplo poderia ser um banco de dados como o SQL Azure, em que um banco de dados pode ser movido para outro servidor para balanceamento de carga, fazendo o banco de dados ficar não disponível por alguns segundos.

Há muitas abordagens para implementar a lógica de repetições com retirada exponencial.

>[!div class="step-by-step"]
>[Anterior](partial-failure-strategies.md)
>[Próximo](implement-resilient-entity-framework-core-sql-connections.md)