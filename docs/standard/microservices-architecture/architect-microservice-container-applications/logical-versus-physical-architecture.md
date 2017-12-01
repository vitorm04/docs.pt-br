---
title: "Arquitetura lógica versus arquitetura física"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Arquitetura lógica versus arquitetura física"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 635774a8fcd0cf1c0ede6a73c604071f538a37fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="logical-architecture-versus-physical-architecture"></a>Arquitetura lógica versus arquitetura física

É útil neste momento parar e discutir a diferença entre a arquitetura lógica e arquitetura física e como isso se aplica ao design de aplicativos baseados em microsserviço.

Para começar, criar microservices não requer o uso de qualquer tecnologia específica. Por exemplo, contêineres do Docker não são obrigatórios para criar uma arquitetura de microsserviço. Essas microservices também pode ser executados como processos simples. Microservices é uma arquitetura lógica.

Além disso, mesmo quando um microsserviço poderia ser fisicamente implementado como um único serviço, o processo ou o contêiner (para simplificar, que é a abordagem usada na versão inicial do [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)), essa semelhança entre microsserviço de negócios e física de serviço ou um contêiner não é necessariamente necessário em todos os casos quando você compila um aplicativo grande e complexo composto de muitas dúzias ou até mesmo centenas de serviços.

Este é o local onde houver uma diferença entre a arquitetura lógica e a arquitetura física de um aplicativo. A arquitetura lógica e os limites de lógicos de um sistema não necessariamente mapeiam individualmente para a arquitetura física ou de implantação. Isso pode acontecer, mas geralmente não.

Embora pode identificar certos microservices de negócios ou contextos limitada, isso não significa que a melhor maneira de implementá-las sempre é criando um serviço (por exemplo, uma API Web do ASP.NET) ou um único contêiner de Docker para cada microsserviço de negócios. Ter uma regra que cada microsserviço de negócios precisa ser implementada usando um único serviço ou contêiner é muito rígido.

Portanto, um microsserviço de negócios ou contexto associado é uma arquitetura lógica pode coincidir (ou não) com a arquitetura física. O ponto importante é que um microsserviço de negócios ou contexto associado deve ser autônomo, permitindo que o código de estado seja independentemente com controle de versão, implantado e expandida.

Como mostra a Figura 4-8, o microsserviço de negócios de catálogo pode ser composto de vários serviços ou processos. Eles podem ser vários serviços de API da Web ASP.NET ou qualquer outro tipo de serviços usando HTTP ou qualquer outro protocolo. Mais importante, os serviços podem compartilhar os mesmos dados, como esses serviços são coesos em relação ao mesmo domínio de negócios.

![](./media/image8.png)

**Figura 4-8**. Microsserviço de negócios com vários serviços físicos

Os serviços no exemplo a compartilham o mesmo modelo de dados porque o serviço de API da Web tem como alvo os mesmos dados que o serviço de pesquisa. Portanto, na implementação física de microsserviço de negócios, você esteja dividindo essa funcionalidade para que você pode dimensionar cada um desses serviços interno para cima ou para baixo conforme necessário. Talvez o serviço de API da Web geralmente precisa mais instâncias que o serviço de pesquisa, ou vice-versa.)

Em resumo, a arquitetura lógica de microservices sempre precisa coincidir com a arquitetura de implantação física. Neste guia, sempre que vamos mencionar um microsserviço, queremos dizer uma empresa ou microsserviço lógico que foi mapeado para um ou mais serviços. Na maioria dos casos, esse será um único serviço, mas pode ser mais.


>[!div class="step-by-step"]
[Anterior] (dados-Soberania-por-microservice.md) [Avançar] (distributed-data-management.md)
