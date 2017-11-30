---
title: "Arquitetura orientada a serviços"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Arquitetura orientada a serviços"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 970ff86c77100077d4c7710c0a697d1745d35819
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="service-oriented-architecture"></a>Arquitetura orientada a serviços 

Arquitetura orientada a serviços (SOA) era um termo com uso excessivo e objetivo coisas diferentes para pessoas diferentes. Mas como um denominador comum, SOA significa que a estrutura de seu aplicativo, decompondo-la em vários serviços (mais comumente, como serviços HTTP) que podem ser classificados como tipos diferentes, como camadas ou subsistemas.

Esses serviços podem agora ser implantados como contêineres do Docker, que resolve problemas de implantação, como todas as dependências estão incluídas na imagem do contêiner. No entanto, quando você precisa de expansão aplicativos SOA, você pode ter escalabilidade e desafios de disponibilidade, se você estiver implantando com base em hosts de Docker único. Isso é onde Docker clustering software ou um orquestrador ajudará, conforme explicado nas seções posteriores onde descrevemos abordagens de implantação para microservices.

Contêineres do docker são úteis (mas não obrigatório) para as arquiteturas tradicionais e orientada a serviços e as arquiteturas de microservices mais avançadas.

Microservices derivam de SOA, mas SOA é diferente da arquitetura de microservices. Recursos como agentes centrais grandes, orchestrators centrais no nível da organização e o [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) comuns em SOA. Mas, na maioria dos casos, esses são os padrões na comunidade de microsserviço. Na verdade, algumas pessoas argumentam que "a arquitetura de microsserviço é feita de SOA."

Este guia se concentra em microservices, como uma abordagem SOA é menos prescritiva do que os requisitos e as técnicas usadas em uma arquitetura de microsserviço. Se você sabe como criar um aplicativo baseado em microsserviço, você também saber como criar um aplicativo de mais simples e orientada a serviços.




>[!div class="step-by-step"]
[Anterior] (docker-aplicativo-estado-data.md) [Avançar] (microservices architecture.md)
