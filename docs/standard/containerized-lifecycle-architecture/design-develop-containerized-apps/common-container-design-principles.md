---
title: "Noções básicas de criação de contêiner comum"
description: "Ciclo de vida de aplicativo de Docker em contêineres com ferramentas e plataformas da Microsoft"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: d7186ae3b768384fe5c6b269578de8db5ef6064c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="common-container-design-principles"></a>Noções básicas de criação de contêiner comum

Em frente de obter no processo de desenvolvimento, há alguns conceitos básicos, vale a pena mencionar em relação a como você pode usar contêineres.

## <a name="container-equals-a-process"></a>Contêiner é igual a um processo

No modelo de contêiner, um contêiner representa um único processo. Definindo um contêiner como um limite de processo, você começar a criar os primitivos usados para escala, ou em lotes de lançamento, processos. Quando você executa um contêiner do Docker, você verá um [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definição. Isso define o processo e o tempo de vida do contêiner. Quando o processo for concluído, o ciclo de vida do contêiner será encerrada. Há processos de longa execução, como servidores web e processos de curta duração, como trabalhos de lote, que podem ter sido implementados como o Microsoft Azure [WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/). Se o processo falhar, o contêiner é encerrado e o orquestrador assume. Se o orchestrator instruído para manter a cinco instâncias em execução e um falhar, o orchestrator criará outro contêiner para substituir o processo com falha. Em um trabalho em lotes, o processo é iniciado com parâmetros. Quando o processo é concluído, o trabalho é concluído.

Você pode encontrar um cenário no qual você deseja que vários processos em execução em um único contêiner. Em qualquer documento de arquitetura, nunca há um "nunca", nem sempre há um "sempre". Para cenários que exigem vários processos, um padrão comum é usar [Supervisor](http://supervisord.org/).


>[!div class="step-by-step"]
[Anterior] (design-docker-applications.md) [Avançar] (monolítico applications.md)
