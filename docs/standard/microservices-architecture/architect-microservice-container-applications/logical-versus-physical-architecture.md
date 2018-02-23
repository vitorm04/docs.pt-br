---
title: "Arquitetura lógica versus arquitetura física"
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Arquitetura lógica versus arquitetura física"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b08a5b8fb8f9df8a9a0a821fa85f1f6a94fce2d3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="logical-architecture-versus-physical-architecture"></a>Arquitetura lógica versus arquitetura física

Neste momento, é útil parar e discutir a diferença entre arquitetura lógica e arquitetura física, e como isso se aplica ao design de aplicativos baseados em microsserviços.

Para começar, criar microsserviços não requer o uso de nenhuma tecnologia específica. Por exemplo, os contêineres do Docker não são obrigatórios para criar uma arquitetura baseada em microsserviço. Essas microsserviços também podem ser executados como processos simples. Os microsserviços são uma arquitetura lógica.

Além disso, mesmo quando um microsserviço puder ser implementado fisicamente como um único serviço, processo ou contêiner (para simplificar, essa é a abordagem usada na versão inicial de [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)), essa paridade entre microsserviço de negócios e serviço ou contêiner físico não será necessariamente obrigatória em todos os casos quando você criar um aplicativo grande e complexo composto por muitas dezenas ou até mesmo centenas de serviços.

Este é o local em que há uma diferença entre a arquitetura lógica e a arquitetura física de um aplicativo. A arquitetura lógica e os limites de lógicos de um sistema não necessariamente mapeiam individualmente para a arquitetura física ou de implantação. Isso pode acontecer, mas geralmente não acontece.

Embora você possa ter identificado determinados microsserviços de negócios ou Contextos limitados, isso não significa que a melhor maneira de implementá-los seja sempre criando um único serviço (como uma API Web ASP.NET) ou um único contêiner do Docker para cada microsserviço de negócios. Ter uma regra que diz que cada microsserviço de negócios deve ser implementado usando um único serviço ou contêiner é rígido demais.

Portanto, um microsserviço de negócios ou um Contexto limitado é uma arquitetura lógica que pode coincidir (ou não) com a arquitetura física. O ponto importante é que um microsserviço de negócios ou Contexto limitado deve ser autônomo, permitindo que o controle de versão, a implantação e a colocação em escala do código e do estado sejam feitas de maneira independente.

Como mostra a Figura 4-8, o microsserviço de negócios de catálogo pode ser composto por vários serviços ou processos. Eles podem ser vários serviços de API Web ASP.NET ou qualquer outro tipo de serviços que usam HTTP ou qualquer outro protocolo. Mais importante, os serviços podem compartilhar os mesmos dados, desde que esses serviços sejam coesos em relação ao mesmo domínio de negócios.

![](./media/image8.png)

**Figura 4-8**. Microsserviço de negócios com vários serviços físicos

Os serviços no exemplo compartilham o mesmo modelo de dados, porque o serviço de API Web tem como alvo os mesmos dados que o Serviço de Pesquisa. Portanto, na implementação física do microsserviço de negócios, você está dividindo essa funcionalidade para poder escalar ou reduzir verticalmente cada um desses serviços internos, conforme necessário. Talvez o serviço de API Web geralmente precise de mais instâncias do que o Serviço de Pesquisa ou vice-versa.)

Em resumo, a arquitetura lógica de microsserviços nem sempre precisa coincidir com a arquitetura de implantação física. Neste guia, sempre que mencionamos um microsserviço, queremos dizer um microsserviço lógico ou de negócios que pôde mapear para um ou mais serviços. Na maioria dos casos, esse será um único serviço, mas pode ser mais.


>[!div class="step-by-step"]
[Anterior] (data-sovereignty-per-microservice.md) [Próximo] (distributed-data-management.md)
