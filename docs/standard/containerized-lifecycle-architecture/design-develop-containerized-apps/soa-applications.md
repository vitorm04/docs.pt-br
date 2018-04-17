---
title: Aplicativos de SOA
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 48dc0f038cee8ddc9555881f2143b566df223a04
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="soa-applications"></a>Aplicativos de SOA

SOA foi um termo com uso excessivo e deve muitas coisas diferentes para pessoas diferentes. Mas, no mínimo e um denominador comum, a SOA, ou a orientação de serviço, a média você estrutura a arquitetura do seu aplicativo, decompondo-la em vários serviços (mais comumente, como serviços HTTP) que podem ser classificados em tipos diferentes, como subsistemas ou, em outros casos, como camadas.

Atualmente, você pode implantar esses serviços como contêineres do Docker, que resolve problemas relacionados à implantação, porque todas as dependências são incluídas na imagem do contêiner. No entanto, quando você precisar de expansão SOAs, você pode encontrar desafios se você estiver implantando com base em instâncias únicas. Isso é onde um Docker clustering software ou orchestrator ajudará. Vamos examinar isso mais detalhadamente na próxima seção quando analisamos microservices abordagens.

No final do dia, as soluções de clustering do contêiner são úteis para os dois uma arquitetura SOA tradicional ou uma arquitetura microservices mais avançada no qual cada microsserviço possui seu modelo de dados. E, graças aos vários bancos de dados, você também pode expansão a camada de dados em vez de trabalhar com bancos de dados monolíticos compartilhados pelos serviços de SOA. No entanto, a discussão sobre os dados de divisão é puramente sobre a arquitetura e design.


>[!div class="step-by-step"]
[Anterior] (state-and-data-in-docker-applications.md) [Avançar] (orquestrar-alta-escalabilidade-availability.md)
