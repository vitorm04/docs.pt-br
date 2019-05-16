---
title: Aplicativos de SOA
description: Tenha em mente que os contêineres também podem ser uma opção de implantação útil para aplicativos de SOA.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644758"
---
# <a name="service-oriented-applications"></a>Aplicativos orientados a serviço

Arquitetura orientada a serviços (SOA) era um termo usado em excesso do que significava muitas coisas diferentes para pessoas diferentes. Mas como um denominador comum, a SOA significa que você estrutura da arquitetura de seu aplicativo decompondo em vários serviços (mais comumente, como serviços HTTP) que podem ser classificados em diferentes tipos como subsistemas ou, em outros casos, como camadas.

Hoje, você pode implantar esses serviços como contêineres do Docker, que resolvem problemas relacionados à implantação, pois todas as dependências estão incluídas na imagem de contêiner. No entanto, quando você precisar expandir SOAs, você pode encontrar desafios se você estiver implantando com base em instâncias únicas. Esse desafio pode ser manipulado usando softwares de clustering ou um orquestrador do Docker. Vamos examinar mais detalhadamente na próxima seção, orquestradores de quando podemos explorar abordagens de microsserviços.

Os contêineres do Docker são úteis (mas não necessários) para arquiteturas tradicionais orientadas a serviço e para as arquiteturas de microsserviços mais avançadas.

No final do dia, as soluções de clustering de contêiner são úteis para os dois uma arquitetura SOA tradicional em uma arquitetura de microsserviços mais avançada em que cada microsserviço tem seu modelo de dados. E, graças aos vários bancos de dados, você também pode escalar horizontalmente a camada de dados em vez de trabalhar com bancos de dados monolíticos compartilhados pelos serviços de SOA. No entanto, a discussão sobre dividindo os dados é puramente sobre arquitetura e design.

>[!div class="step-by-step"]
>[Anterior](state-and-data-in-docker-applications.md)
>[Próximo](orchestrate-high-scalability-availability.md)
