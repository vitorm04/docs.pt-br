---
title: Criar aplicativos de Docker
description: Encontre aqui uma referência a um guia detalhado sobre a arquitetura de microsserviços, porque esse é um tópico que não é detalhado neste guia.
ms.date: 02/15/2019
ms.openlocfilehash: b8a08658ec6c3df3e1aed596a0240223768dd647
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738459"
---
# <a name="design-docker-applications"></a>Criar aplicativos de Docker

O Capítulo 1 apresentou os conceitos fundamentais sobre contêineres e Docker. Essa informação é o nível básico de informações que você precisa para começar. Entretanto, os aplicativos empresariais podem ser complexos e são compostos de vários serviços e não de um único serviço ou contêiner. Para esses casos de uso opcionais, você precisa saber outras abordagens para design, como a SOA (Arquitetura Orientada a Serviços) e os conceitos de microsserviços mais avançados, bem como os conceitos de orquestração de contêiner. O escopo deste documento não se limita a microsserviços, mas a qualquer ciclo de vida do aplicativo Docker, portanto, ele não explora a arquitetura de microsserviços em profundidade porque você também pode usar contêineres e Docker com SOA regular, tarefas de fundo ou trabalhos, ou mesmo com abordagens de implantação de aplicativos monolíticos.

**Mais informações** Para saber mais sobre aplicativos corporativos e arquitetura de microsserviços em profundidade, leia o guia <https://aka.ms/MicroservicesEbook> [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) que você também pode baixar.

No entanto, antes de entrarmos no ciclo de vida do aplicativo e no DevOps, é importante saber como você pretende projetar e construir seu aplicativo e quais são suas opções de design.

>[!div class="step-by-step"]
>[Próximo](index.md)
>[anterior](common-container-design-principles.md)
