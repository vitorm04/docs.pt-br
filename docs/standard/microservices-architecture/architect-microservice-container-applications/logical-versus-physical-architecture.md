---
title: Arquitetura lógica versus arquitetura física
description: Entenda as diferenças entre arquiteturas lógica e física.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: e8ed375899637d06db8eb9b12a0e1cb0c05591f9
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129916"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Arquitetura lógica versus arquitetura física

Neste momento, é útil parar e discutir a diferença entre as arquiteturas lógica e física, além de como isso se aplica ao design de aplicativos baseados em microsserviços.

Para começar, a criação de microsserviços não exige o uso de nenhuma tecnologia específica. Por exemplo, os contêineres do Docker não são obrigatórios para criar uma arquitetura baseada em microsserviço. Essas microsserviços também podem ser executados como processos simples. Os microsserviços são uma arquitetura lógica.

Além disso, mesmo quando um microsserviço puder ser implementado fisicamente como um único serviço, processo ou contêiner (para simplificar, essa é a abordagem usada na versão inicial de [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), essa paridade entre microsserviço empresarial e serviço ou contêiner físico não será necessariamente obrigatória em todos os casos quando você criar um aplicativo grande e complexo composto por muitas dezenas ou até mesmo centenas de serviços.

É aqui em que há uma diferença entre a arquitetura lógica e a arquitetura física de um aplicativo. A arquitetura lógica e os limites de lógicos de um sistema não necessariamente mapeiam individualmente para a arquitetura física ou de implantação. Isso pode acontecer, mas geralmente não acontece.

Embora você possa ter identificado determinados microsserviços empresariais ou Contextos Limitados, isso não significa que a melhor maneira de implementá-los seja sempre criando um único serviço (como uma ASP.NET Web API) ou um único contêiner do Docker para cada microsserviço empresarial. Ter uma regra que diz que cada microsserviço de negócios deve ser implementado usando um único serviço ou contêiner é rígido demais.

Portanto, um microsserviço de negócios ou um Contexto limitado é uma arquitetura lógica que pode coincidir (ou não) com a arquitetura física. O ponto importante é que um microsserviço de negócios ou Contexto limitado deve ser autônomo, permitindo que o controle de versão, a implantação e a colocação em escala do código e do estado sejam feitas de maneira independente.

Como mostra a Figura 4-8, o microsserviço de negócios de catálogo pode ser composto por vários serviços ou processos. Eles podem ser vários serviços do ASP.NET Web API ou qualquer outro tipo de serviços que usam HTTP ou qualquer outro protocolo. Mais importante, os serviços podem compartilhar os mesmos dados, desde que esses serviços sejam coesos em relação ao mesmo domínio de negócios.

![Diagrama do microsserviço empresarial de Catálogo, que contém um serviço de API, um serviço de pesquisa e um Banco de Dados do SQL Server.](./media/image8.png)

**Figura 4-8**. Microsserviço de negócios com vários serviços físicos

Os serviços no exemplo compartilham o mesmo modelo de dados, porque o serviço de API Web tem como alvo os mesmos dados que o Serviço de Pesquisa. Portanto, na implementação física do microsserviço empresarial, você está dividindo essa funcionalidade para poder escalar ou reduzir verticalmente cada um desses serviços internos, conforme necessário. Talvez o serviço de API Web geralmente precise de mais instâncias do que o Serviço de Pesquisa ou vice-versa.

Em resumo, a arquitetura lógica de microsserviços nem sempre precisa coincidir com a arquitetura de implantação física. Neste guia, sempre que mencionamos um microsserviço, queremos dizer um microsserviço lógico ou empresarial que pode ser mapeado para um ou mais serviços (físicos). Na maioria dos casos, esse será um único serviço, mas pode ser mais.

>[!div class="step-by-step"]
>[Anterior](data-sovereignty-per-microservice.md)
>[Próximo](distributed-data-management.md)