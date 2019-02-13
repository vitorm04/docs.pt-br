---
title: Aplicativos de SOA
description: Tenha em mente que os contêineres também podem ser uma opção de implantação útil para aplicativos de SOA.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 4fd39e075c5730cf7fddb0138cdb5267a914c91f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221258"
---
# <a name="soa-applications"></a>Aplicativos de SOA

SOA era um termo usado de maneira exagerado e significava tantas coisas diferentes para pessoas diferentes. Mas, pelo menos e como um denominador comum, a SOA, ou a orientação por serviços, a média, você estrutura da arquitetura de seu aplicativo decompondo-o em vários serviços (mais comumente, como serviços HTTP) que podem ser classificados em diferentes tipos como subsistemas ou, em outros casos, como camadas.

Hoje, você pode implantar esses serviços como contêineres do Docker, que resolve problemas relacionados à implantação, porque todas as dependências são incluídas na imagem de contêiner. No entanto, quando você precisar SOAs de escalabilidade horizontal, você pode encontrar desafios se você estiver implantando com base em instâncias únicas. Isso é onde um Docker softwares de clustering ou orquestrador ajudará. Vamos examinar isso mais detalhadamente na próxima seção quando examinamos as abordagens de microsserviços.

No final do dia, as soluções de clustering de contêiner são úteis para os dois uma arquitetura SOA tradicional ou para uma arquitetura de microsserviços mais avançada em que cada microsserviço tem seu modelo de dados. E, graças aos vários bancos de dados, você também pode expandir a camada de dados em vez de trabalhar com bancos de dados monolíticos compartilhados pelos serviços de SOA. No entanto, a discussão sobre dividindo os dados é puramente sobre arquitetura e design.

>[!div class="step-by-step"]
>[Anterior](state-and-data-in-docker-applications.md)
>[Próximo](orchestrate-high-scalability-availability.md)