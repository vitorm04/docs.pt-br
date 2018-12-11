---
title: Aplicativos de SOA
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 7f88daaf0787cf780e7ab9602f35ae4e6ab8308c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155308"
---
# <a name="soa-applications"></a>Aplicativos de SOA

SOA era um termo usado de maneira exagerado e significava tantas coisas diferentes para pessoas diferentes. Mas, pelo menos e como um denominador comum, a SOA, ou a orientação por serviços, a média, você estrutura da arquitetura de seu aplicativo decompondo-o em vários serviços (mais comumente, como serviços HTTP) que podem ser classificados em diferentes tipos como subsistemas ou, em outros casos, como camadas.

Hoje, você pode implantar esses serviços como contêineres do Docker, que resolve problemas relacionados à implantação, porque todas as dependências são incluídas na imagem de contêiner. No entanto, quando você precisar SOAs de escalabilidade horizontal, você pode encontrar desafios se você estiver implantando com base em instâncias únicas. Isso é onde um Docker softwares de clustering ou orquestrador ajudará. Vamos examinar isso mais detalhadamente na próxima seção quando examinamos as abordagens de microsserviços.

No final do dia, as soluções de clustering de contêiner são úteis para os dois uma arquitetura SOA tradicional ou para uma arquitetura de microsserviços mais avançada em que cada microsserviço tem seu modelo de dados. E, graças aos vários bancos de dados, você também pode expandir a camada de dados em vez de trabalhar com bancos de dados monolíticos compartilhados pelos serviços de SOA. No entanto, a discussão sobre dividindo os dados é puramente sobre arquitetura e design.

>[!div class="step-by-step"]
>[Anterior](state-and-data-in-docker-applications.md)
>[Próximo](orchestrate-high-scalability-availability.md)