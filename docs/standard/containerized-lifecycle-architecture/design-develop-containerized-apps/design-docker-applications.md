---
title: Criar aplicativos de Docker
description: Encontre aqui uma referência a um guia detalhado sobre a arquitetura de microsserviços, porque esse é um tópico que ele não é detalhado neste guia.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 1d49f7509c0a12edfe375486429147e8fd240b2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799340"
---
# <a name="design-docker-applications"></a>Criar aplicativos de Docker

Capítulo 1 apresentou os conceitos fundamentais sobre contêineres e Docker. Essa informação é o nível básico de informações que você precisa para começar a usar. Mas, aplicativos corporativos podem ser complexos e compostos de vários serviços, em vez de um único serviço ou contêiner. Para esses casos de uso opcional, você precisa saber outras abordagens para design, como o SOA (arquitetura) e os conceitos de microsserviços mais avançados e o contêiner de conceitos de orquestração. O escopo deste documento não é limitado aos microsserviços, mas para qualquer ciclo de vida do aplicativo Docker, portanto, ele não explorar a arquitetura de microsserviços em camadas porque você também pode usar o Docker e contêineres com trabalhos, tarefas em segundo plano ou SOA regular ou até mesmo com abordagens de implantação do aplicativo monolítico.

**Obter mais informações** para saber mais sobre aplicativos empresariais e arquitetura de microsserviços em detalhes, leia o guia [Microsserviços NET: Arquitetura para aplicativos .NET em contêineres](../../microservices-architecture/index.md) que você também pode baixar do <https://aka.ms/MicroservicesEbook>.

No entanto, antes de entrarmos no ciclo de vida do aplicativo e DevOps, é importante saber como você pretende design e construir seu aplicativo e quais são suas opções de design.

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](common-container-design-principles.md)