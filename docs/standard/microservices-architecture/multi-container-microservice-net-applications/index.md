---
title: Projetando e desenvolvendo aplicativos .NET baseados em microsserviço e em vários contêineres
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Projetando e desenvolvendo aplicativos .NET baseados em microsserviço e em vários contêineres
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 297a53d6d6d37b1fa4a0e021919c9df86edeca03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571950"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Projetando e desenvolvendo aplicativos .NET baseados em microsserviço e em vários contêineres

*Desenvolver aplicativos de microsserviço em contêineres significa criar aplicativos em vários contêineres. No entanto, um aplicativo em vários contêineres também pode ser mais simples, como um aplicativo de três camadas, e talvez não seja criado usando uma arquitetura de microsserviço.*

Anteriormente, fizemos a pergunta "O Docker é necessário ao criar uma arquitetura de microsserviço?" A resposta é claramente não. O Docker é um habilitador e pode fornecer benefícios significativos, mas os contêineres e o Docker não são um requisito rígido para os microsserviços. Por exemplo, você pode criar um aplicativo baseado em microsserviços com ou sem o Docker ao usar o Azure Service Fabric, que dá suporte a microsserviços executados como processos simples ou como contêineres do Docker.

No entanto, se você souber como projetar e desenvolver um aplicativo baseado em microsserviços que também seja baseado em contêineres do Docker, será possível projetar e desenvolver qualquer outro modelo de aplicativo mais simples. Por exemplo, você pode projetar um aplicativo de três camadas que também exija uma abordagem de vários contêineres. Por esse motivo e como as arquiteturas de microsserviço são uma tendência importante no campo dos contêineres, esta seção concentra-se em uma implementação de arquitetura de microsserviço que usa contêineres do Docker.


>[!div class="step-by-step"]
[Previous] (../containerize-net-framework-applications/index.md) [Next] (microservice-application-design.md)
