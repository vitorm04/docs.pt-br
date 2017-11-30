---
title: Tratamento de falha parcial
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Tratamento de falha parcial"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b7d16acf3de2d395da70e8f46e59c129dec24f71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="handling-partial-failure"></a>Tratamento de falha parcial

Em sistemas distribuídos como aplicativos baseados em microservices, há um risco de sempre presente de falha parcial. Por exemplo, um único microsserviço/contêiner pode falhar ou pode não estar disponível para responder por um curto período, ou um único servidor ou VM pode falhar. Como clientes e serviços são processos separados, um serviço pode não ser capaz de responder de forma oportuna de uma solicitação do cliente. O serviço pode estar sobrecarregadas e respondendo muito lenta para solicitações, ou pode simplesmente não estar acessível por um curto período devido a problemas de rede.

Por exemplo, considere a página de detalhes da ordem do eShopOnContainers aplicativo de exemplo. Se não estiver respondendo o ordenação microsserviço quando o usuário tentar enviar um pedido, uma implementação incorreta de processo do cliente (o aplicativo da web MVC) — por exemplo, se o código do cliente usar RPCs síncronos sem tempo limite — bloquearia threads indefinidamente aguardando uma resposta. Além de criar uma experiência de usuário incorreto, cada espera sem resposta consome ou bloqueia um thread e threads são extremamente importantes em aplicativos altamente escalonáveis. Se houver muitos threads bloqueados, eventualmente o tempo de execução do aplicativo pode ficar sem threads. Nesse caso, o aplicativo pode se tornar globalmente não responder em vez de apenas parcialmente não responder, como é mostrado na Figura 10-1.

![](./media/image1.png)

**Figura 10-1**. Falhas parciais devido a dependências que afetam a disponibilidade do serviço de thread

Em um aplicativo grande com base em microservices, todas as falhas parciais podem ser aumentadas, especialmente se a maioria da interação microservices interna é baseado em chamadas HTTP síncronas (o que é considerado um antipadrão). Pense em um sistema que recebe milhões de chamadas por dia. Se o sistema tiver um design ruim se baseia em longas cadeias de chamadas síncronas de HTTP, essas chamadas de entrada podem resultar em muitos mais milhões de chamadas de saída (vamos supor que uma taxa de 1:4) a dezenas de microservices interno como dependências síncronas. Essa situação é mostrada na Figura 10-2, especialmente dependência \#3.

![](./media/image2.png)

**Figura 10-2**. O impacto de um design incorreto com longas cadeias de solicitações HTTP

Falha intermitente é praticamente garantido em distribuído e na nuvem de sistema baseado em, mesmo se cada dependência em si tem excelente disponibilidade. Isso deve ser um fato que você precisa considerar.

Se você não criar e implementar técnicas para garantir tolerância a falhas, até mesmo pequenos tempos de inatividade podem ser amplificados. Por exemplo, 50 dependências cada com 99,99% de disponibilidade pode resultar em várias horas de inatividade por mês devido a esse efeito de ondulação. Quando uma dependência de microsserviço Falha ao manipular um alto volume de solicitações, essa falha pode saturar todos os threads de solicitação disponíveis em cada serviço e falhas de todo o aplicativo rapidamente.

![](./media/image3.png)

**Figura 10-3**. Falha parcial ampliada por microservices com longas cadeias de chamadas síncronas de HTTP

Para minimizar esse problema, na seção "*microsserviço assíncrona integração impõe a autonomia do microsserviço*" (no capítulo arquitetura), é recomendável usar a comunicação assíncrona entre interno microservices. Brevemente explicamos mais na próxima seção.

Além disso, é essencial que você criar seus aplicativos de cliente e microservices para lidar com falhas parciais — ou seja, para compilar aplicativos microservices resiliente e cliente.


>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (strategies.md de falha parcial)
