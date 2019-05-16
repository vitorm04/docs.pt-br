---
title: Noções básicas de criação de contêiner comum
description: Aprenda a um princípio fundamental do design de contêiner BOM, é que um contêiner deve hospedar apenas um processo.
ms.date: 02/15/2019
ms.openlocfilehash: 69f3ff6c9303f0c4082695d861a8c90031295b6a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644802"
---
# <a name="common-container-design-principles"></a>Noções básicas de criação de contêiner comum

Em frente de Introdução ao processo de desenvolvimento, há alguns conceitos básicos, vale a pena mencionar em relação a como você pode usar contêineres.

## <a name="container-equals-a-process"></a>Contêiner é igual a um processo

No modelo de contêiner, um contêiner representa um único processo. Definindo um contêiner como um limite de processo, você começar a criar os primitivos usados para escala, ou em lotes-off, processos. Quando você executar um contêiner do Docker, você verá uma [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definição. Isso define o processo e o tempo de vida do contêiner. Quando o processo for concluído, encerra o ciclo de vida do contêiner. Há processos de longa execução, como servidores web e os processos de curta duração, como trabalhos de lote, que podem ter sido implementados como o Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/). Se o processo falhar, o contêiner é encerrado e o orquestrador assume. Se o orquestrador foi instruído para manter cinco instâncias em execução e uma falhar, o orchestrator criará outro contêiner para substituir o processo com falha. Em um trabalho em lotes, o processo é iniciado com parâmetros. Quando o processo é concluído, o trabalho é concluído.

Você pode encontrar um cenário no qual você deseja que vários processos em execução em um único contêiner. Em qualquer documento de arquitetura, nunca há um "nunca", nem sempre há um "sempre". Para cenários que exigem vários processos, um padrão comum é usar [Supervisor](http://supervisord.org/).

>[!div class="step-by-step"]
>[Anterior](design-docker-applications.md)
>[Próximo](monolithic-applications.md)
