---
title: Tratando falha parcial
description: Saiba como tratar falhas parciais normalmente. Um microsserviço pode não estar totalmente funcional, mas ainda conseguir realizar algum trabalho útil.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 16b6237f79d6b4bc2bc9152ba6eb023ffbd3899f
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362698"
---
# <a name="handle-partial-failure"></a>Tratar falhas parciais

Em sistemas distribuídos como aplicativos baseados em microsserviços, há um risco de falha parcial sempre presente. Por exemplo, um único microsserviço/contêiner pode falhar ou pode não estar disponível para responder por um curto período, ou um único servidor ou VM pode falhar. Como clientes e serviços são processos separados, um serviço pode não ser capaz de responder de forma oportuna a uma solicitação do cliente. O serviço pode estar sobrecarregado e respondendo a solicitações de maneira muito lenta ou pode simplesmente não estar acessível durante um curto período devido a problemas de rede.

Por exemplo, considere a página de detalhes Ordem do aplicativo de exemplo eShopOnContainers. Se o microsserviço de ordenação não estiver respondendo quando o usuário tentar enviar uma ordem, uma implementação incorreta do processo do cliente (o aplicativo Web MVC) – por exemplo, se o código do cliente usasse RPCs síncronos sem tempo limite – bloqueará threads indefinidamente que estão aguardando uma resposta. Além de criar uma experiência de usuário ruim, toda espera sem resposta consome ou bloqueia um thread, e os threads são extremamente valiosos em aplicativos altamente escalonáveis. Se houver muitos threads bloqueados, o tempo de execução do aplicativo poderá eventualmente ficar sem threads. Nesse caso, o aplicativo poderá ficar globalmente sem resposta, em vez de apenas parcialmente sem resposta, como mostra a Figura 8-1.

![Diagrama ilustrando o parágrafo anterior](./media/image1.png)

**Figura 8-1**. Falhas parciais devido a dependências que afetam a disponibilidade do thread de serviço

Em um aplicativo grande baseado em microsserviços, falhas parciais poderão ser amplificadas, principalmente se a maioria da interação interna dos microsserviços for baseada em chamadas HTTP síncronas (o que é considerado um antipadrão). Pense em um sistema que recebe milhões de chamadas de entrada por dia. Se o sistema tiver um design ruim baseado em longas cadeias de chamadas HTTP síncronas, essas chamadas de entrada poderão resultar em muito mais milhões de chamadas de saída (vamos supor uma razão de 1:4) a dezenas de microsserviços internos como dependências síncronas. Essa situação é mostrada na Figura 8-2, principalmente a dependência \#3.

![Um design incorreto de microsserviço de aplicativo Web que depende de uma cadeia de dependências em outros microsserviços](./media/image2.png)

**Figura 8-2**. O impacto de ter um design incorreto com longas cadeias de solicitações HTTP

A falha intermitente é garantida em um sistema distribuído e baseado em nuvem, mesmo quando cada dependência têm uma disponibilidade excelente. Esse um fato que você precisa considerar.

Se você não criar nem implementar técnicas para garantir a tolerância a falhas, até mesmo pequenos tempos de inatividade poderão ser amplificados. Por exemplo, 50 dependências, cada uma com 99,99% de disponibilidade, poderia resultar em várias horas de tempo de inatividade por mês devido a esse efeito de ondulação. Quando uma dependência de microsserviço falhar ao manipular um alto volume de solicitações, essa falha poderá saturar rapidamente todos os threads de solicitação disponíveis em cada serviço e causar uma pane em todo o aplicativo.

![As falhas parciais podem ser gravemente amplificadas pelas dependências encadeadas](./media/image3.png)

**Figura 8-3**. Falha parcial amplificada por microsserviços com longas cadeias de chamadas HTTP síncronas

Para minimizar esse problema, na seção [A integração assíncrona do microsserviço impõe a autonomia do microsserviço](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy), esse guia indica o uso da comunicação assíncrona entre os microsserviços internos.

Além disso, é essencial que você crie seus aplicativos cliente e microsserviços para lidar com falhas parciais, ou seja, crie microsserviços e aplicativos cliente resilientes.

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](partial-failure-strategies.md)