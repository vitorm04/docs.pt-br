---
title: Tratando falha parcial
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Tratando falha parcial
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 957a0b1b8b4d217fac591db54e4ee053098bc7da
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105189"
---
# <a name="handling-partial-failure"></a>Tratando falha parcial

Em sistemas distribuídos como aplicativos baseados em microsserviços, há um risco de falha parcial sempre presente. Por exemplo, um único microsserviço/contêiner pode falhar ou pode não estar disponível para responder por um curto período, ou um único servidor ou VM pode falhar. Como clientes e serviços são processos separados, um serviço pode não ser capaz de responder de forma oportuna a uma solicitação do cliente. O serviço pode estar sobrecarregado e respondendo a solicitações de maneira extremamente lenta ou pode simplesmente não estar acessível durante um curto período devido a problemas de rede.

Por exemplo, considere a página de detalhes Ordem do aplicativo de exemplo eShopOnContainers. Se o microsserviço de ordenação não estiver respondendo quando o usuário tentar enviar uma ordem, uma implementação incorreta do processo do cliente (o aplicativo Web MVC) – por exemplo, se o código do cliente usasse RPCs síncronos sem tempo limite – bloqueará threads indefinidamente que estão aguardando uma resposta. Além de criar uma experiência de usuário incorreta, toda espera sem resposta consome ou bloqueia um thread, e os threads são extremamente valiosos em aplicativos altamente escalonáveis. Se houver muitos threads bloqueados, o tempo de execução do aplicativo poderá eventualmente ficar sem threads. Nesse caso, o aplicativo poderá se ficar globalmente sem resposta, em vez de apenas parcialmente sem resposta, conforme mostrado na Figura 10-1.

![](./media/image1.png)

**Figura 10-1**. Falhas parciais devido a dependências que afetam a disponibilidade do thread de serviço

Em um aplicativo grande baseado em microsserviços, falhas parciais poderão ser amplificadas, principalmente se a maioria da interação interna dos microsserviços for baseada em chamadas HTTP síncronas (o que é considerado um antipadrão). Pense em um sistema que recebe milhões de chamadas de entrada por dia. Se o sistema tiver um design ruim baseado em longas cadeias de chamadas HTTP síncronas, essas chamadas de entrada poderão resultar em muitos mais milhões de chamadas de saída (vamos supor uma razão de 1:4) a dezenas de microsserviços internos como dependências síncronas. Essa situação é mostrada na Figura 10-2, principalmente dependência \#3.

![](./media/image2.png)

**Figura 10-2**. O impacto de ter um design incorreto com longas cadeias de solicitações HTTP

A falha intermitente será praticamente garantida em um sistema distribuído e baseado na nuvem, mesmo se cada dependência em si tiver excelente disponibilidade. Isso deve ser um fato que você precisa considerar.

Se você não criar nem implementar técnicas para garantir a tolerância a falhas, até mesmo pequenos tempos de inatividade poderão ser amplificados. Por exemplo, 50 dependências, cada uma com 99,99% de disponibilidade, poderia resultar em várias horas de tempo de inatividade por mês devido a esse efeito de ondulação. Quando uma dependência de microsserviço falhar ao manipular um alto volume de solicitações, essa falha poderá saturar rapidamente todos os threads de solicitação disponíveis em cada serviço e causar uma pane em todo o aplicativo.

![](./media/image3.png)

**Figura 10-3**. Falha parcial amplificada por microsserviços com longas cadeias de chamadas HTTP síncronas

Para minimizar esse problema, na seção "*A integração do microsserviço assíncrono impõe a autonomia do microsserviço*" (no capítulo de arquitetura), é recomendável usar a comunicação assíncrona entre microsserviços internos. Explicaremos mais resumidamente na próxima seção.

Além disso, é essencial que você crie seus aplicativos cliente e microsserviços para lidar com falhas parciais — ou seja, para criar microsserviços resilientes e aplicativos cliente.


>[!div class="step-by-step"]
[Anterior](index.md)
[Próximo](partial-failure-strategies.md)
