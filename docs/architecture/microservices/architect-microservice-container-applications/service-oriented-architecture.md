---
title: Arquitetura orientada a serviço
description: Aprenda as diferenças fundamentais entre microsserviços e uma arquitetura SOA.
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68674923"
---
# <a name="service-oriented-architecture"></a>Arquitetura orientada a serviço

A SOA (arquitetura orientada a serviço) era um termo usado de maneira exagerada e significava diferentes coisas para diferentes pessoas. Mas, como um denominador comum, a SOA significa que você estrutura seu aplicativo o decompondo em vários serviços (mais comumente, como serviços HTTP) que podem ser classificados como diferentes tipos como subsistemas ou camadas.

Agora esses serviços podem ser implantados como contêineres do Docker, que resolve problemas de implantação, porque todas as dependências estão incluídas na imagem de contêiner. No entanto, quando você precisa expandir aplicativos SOA, talvez você tenha desafios de escalabilidade e de disponibilidade se estiver implantando com base em hosts únicos do Docker. É aí que o software de clustering do Docker ou um orquestrador pode ajudar você, conforme explicado nas seções posteriores, em que são descritas as abordagens de implantação para microsserviços.

Os contêineres do Docker são úteis (mas não necessários) para arquiteturas tradicionais orientadas a serviço e para as arquiteturas de microsserviços mais avançadas.

Os microsserviços derivam da SOA, mas a SOA é diferente da arquitetura de microsserviços. Recursos como agentes centrais grandes, orquestradores centrais no nível da organização e o [ESB (Enterprise Service Bus)](https://en.wikipedia.org/wiki/Enterprise_service_bus) são comuns na SOA. Mas, na maioria dos casos, esses são os antipadrões na comunidade de microsserviços. Na verdade, algumas pessoas argumentam que "A arquitetura de microsserviço é a SOA feita da maneira certa".

Este guia se concentra em microsserviços, porque uma abordagem SOA é menos prescritiva do que os requisitos e as técnicas usados em uma arquitetura de microsserviço. Se você souber como criar um aplicativo baseado em microsserviço, também saberá como criar um aplicativo mais simples orientado a serviços.

>[!div class="step-by-step"]
>[Próximo](docker-application-state-data.md)
>[anterior](microservices-architecture.md)
