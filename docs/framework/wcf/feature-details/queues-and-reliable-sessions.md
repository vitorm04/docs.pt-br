---
title: "Sessões confiáveis e filas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9b2ad869e8127bcaf513bee82e3175b35349d922
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="queues-and-reliable-sessions"></a>Sessões confiáveis e filas
Sessões confiáveis e filas são o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] recursos que implementam o sistema de mensagens confiável. Os tópicos contidos nesta seção discutem o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recursos de mensagens confiáveis.  
  
 Mensagens confiáveis são como uma fonte confiável de mensagens (chamada de origem) transfere mensagens de forma confiável em um destino de mensagens confiável (chamado de destino).  
  
 Sistema de mensagens confiável tem os seguintes aspectos principais:  
  
-   Garantias de transferência de mensagens enviadas de uma fonte para um destino, independentemente de falha de transferência de mensagem ou falhas de transporte.  
  
-   Separação de origem e destino de um do outro, que fornece falha independente e recuperação de origem e de destino como bem como confiável transferência e a entrega de mensagens, mesmo que a origem ou destino está indisponível.  
  
 Mensagens confiáveis com frequência ocorre às custas de alta latência. Latência é o tempo necessário alcançar o destino da origem da mensagem. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], portanto, fornece os seguintes tipos de mensagens confiáveis:  
  
-   [Sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions.md), que oferecem transferência confiável sem o custo de alta latência  
  
-   [As filas no WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md), que oferecem transferências confiáveis e separação entre a origem e o destino.  
  
## <a name="reliable-sessions"></a>Sessões confiáveis  
 Sessões confiáveis fornecem transferência confiável de ponta a ponta de mensagens entre uma origem e um destino usando o protocolo WS-ReliableMessaging, independentemente do número ou tipo de intermediários que separam os pontos de extremidade de mensagens (origem e destino). Isso inclui qualquer intermediários de transporte que não usam SOAP (por exemplo, proxies HTTP) ou intermediários que usam SOAP (por exemplo, roteadores baseados em SOAP ou pontes) que são necessários para mensagens entre os pontos de extremidade. Sessões confiáveis usam uma janela de transferência na memória para falhas de nível de mensagem SOAP máscara e restabelecer conexões no caso de falhas de transporte.  
  
 Sessões confiáveis fornecem transferências de mensagens confiável de baixa latência. Eles fornecem para mensagens SOAP através de qualquer proxies ou intermediários, equivalente ao qual TCP permite pacotes por pontes IP. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]sessões confiáveis, consulte [sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Filas  
 As filas no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornecer ambas as transferências confiáveis de mensagens e separação entre fontes e destinos às custas de alta latência. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]comunicação em fila é criada sobre enfileiramento de mensagens (também conhecido como MSMQ).  
  
 MSMQ é enviado como uma opção com Windows que é executado como um serviço NT. Ele captura mensagens de transmissão em uma fila de transmissão em nome da fonte e entrega para uma fila de destino. A fila de destino aceita mensagens em nome de destino para envio posterior sempre que o destino de solicitações de mensagens. Os gerenciadores de fila MSMQ implementam um protocolo de transferência de mensagens confiáveis para que as mensagens não serão perdidas durante a transmissão. O protocolo pode ser nativo ou baseado em SOAP, como confiável de mensagens protocolo SRMP (Soap).  
  
 A separação, juntamente com as transferências de mensagens confiáveis entre as filas, permite que os aplicativos que são acoplados de forma flexível para se comunicar de forma confiável. Ao contrário das sessões confiáveis, a origem e destino não precisa estar em execução ao mesmo tempo. Implicitamente, isso permite cenários onde as filas são, na verdade, usadas como um mecanismo de nivelamento de carga quando há uma incompatibilidade entre a taxa de produção de mensagem, a origem e a taxa de consumo de mensagem pelo destino. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]as filas, consulte [filas no WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Consulte também  
 [Filas no WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [Visão geral de sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
