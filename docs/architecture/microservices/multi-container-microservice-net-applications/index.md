---
title: Projetando e desenvolvendo aplicativos .NET baseados em microsserviço e em vários contêineres
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Entender a arquitetura externa para projetar e desenvolver aplicativos .NET baseados em microsserviço e em vários contêineres.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70296622"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Projetando e desenvolvendo aplicativos .NET baseados em microsserviço e em vários contêineres

*Desenvolver aplicações de microserviço em contêiner significa que você está construindo aplicações de vários contêineres. No entanto, um aplicativo de vários contêineres também pode ser mais simples — por exemplo, um aplicativo de três níveis — e pode não ser construído usando uma arquitetura de microserviço.*

Anteriormente, fizemos a pergunta "O Docker é necessário ao criar uma arquitetura de microsserviço?" A resposta é claramente não. O Docker é um habilitador e pode fornecer benefícios significativos, mas os contêineres e o Docker não são um requisito rígido para os microsserviços. Por exemplo, você pode criar um aplicativo baseado em microsserviços com ou sem o Docker ao usar o Azure Service Fabric, que dá suporte a microsserviços executados como processos simples ou como contêineres do Docker.

No entanto, se você souber como projetar e desenvolver um aplicativo baseado em microsserviços que também seja baseado em contêineres do Docker, será possível projetar e desenvolver qualquer outro modelo de aplicativo mais simples. Por exemplo, você pode projetar um aplicativo de três camadas que também exija uma abordagem de vários contêineres. Por esse motivo e como as arquiteturas de microsserviço são uma tendência importante no campo dos contêineres, esta seção concentra-se em uma implementação de arquitetura de microsserviço que usa contêineres do Docker.

>[!div class="step-by-step"]
>[Próximo](../docker-application-development-process/docker-app-development-workflow.md)
>[anterior](microservice-application-design.md)
