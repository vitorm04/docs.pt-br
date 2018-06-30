---
title: Projetando e desenvolvendo aplicativos .NET baseados em microsserviço e em vários contêineres
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Projetando e desenvolvendo aplicativos .NET baseados em microsserviço e em vários contêineres
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 13abff090d42c5d59476612942560c126836dbb0
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104472"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Projetando e desenvolvendo aplicativos .NET baseados em microsserviço e em vários contêineres

*Desenvolver aplicativos de microsserviço em contêineres significa criar aplicativos em vários contêineres. No entanto, um aplicativo em vários contêineres também pode ser mais simples, como um aplicativo de três camadas, e talvez não seja criado usando uma arquitetura de microsserviço.*

Anteriormente, fizemos a pergunta "O Docker é necessário ao criar uma arquitetura de microsserviço?" A resposta é claramente não. O Docker é um habilitador e pode fornecer benefícios significativos, mas os contêineres e o Docker não são um requisito rígido para os microsserviços. Por exemplo, você pode criar um aplicativo baseado em microsserviços com ou sem o Docker ao usar o Azure Service Fabric, que dá suporte a microsserviços executados como processos simples ou como contêineres do Docker.

No entanto, se você souber como projetar e desenvolver um aplicativo baseado em microsserviços que também seja baseado em contêineres do Docker, será possível projetar e desenvolver qualquer outro modelo de aplicativo mais simples. Por exemplo, você pode projetar um aplicativo de três camadas que também exija uma abordagem de vários contêineres. Por esse motivo e como as arquiteturas de microsserviço são uma tendência importante no campo dos contêineres, esta seção concentra-se em uma implementação de arquitetura de microsserviço que usa contêineres do Docker.


>[!div class="step-by-step"]
[Anterior](../containerize-net-framework-applications/index.md)
[Próximo](microservice-application-design.md)
