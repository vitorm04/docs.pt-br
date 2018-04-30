---
title: Serviços confiáveis
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9cbaef77f4dce609d36ba4b679d8c569b648fa5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="reliable-services"></a>Serviços confiáveis
Sessões confiáveis e filas são o [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] recursos que implementam o sistema de mensagens confiável. Este tópico explica os recursos de mensagens confiáveis de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 *Mensagens confiáveis* é como uma fonte confiável de mensagens (chamado de *fonte*) transfere mensagens de forma confiável em um destino de mensagens confiável (chamado de *destino*).  
  
 Mensagens confiáveis executa as seguintes funções:  
  
-   Transfere garantias para mensagens enviadas de uma fonte para um destino independentemente das falhas de transferência ou o transporte de mensagens.  
  
-   Separa a origem e o destino do outro. Isso fornece falha independente e recuperação de origem e de destino, bem como transferência confiável e a entrega de mensagens, mesmo quando a origem ou destino está indisponível.  
  
 Mensagens confiáveis com frequência ocorre às custas de alta latência. *Latência* é o tempo necessário alcançar o destino da origem da mensagem. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], portanto, fornece os seguintes tipos de mensagens confiáveis:  
  
-   [Sessões confiáveis](../../../docs/framework/wcf/feature-details/reliable-sessions.md), que oferece transferência confiável sem o custo de alta latência.  
  
-   [As filas no WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md), que oferece transferências confiáveis e separação entre a origem e o destino.  
  
## <a name="reliable-sessions"></a>Sessões confiáveis  
 Sessões confiáveis fornecem transferência confiável de ponta a ponta de mensagens entre uma origem e um destino usando o protocolo WS-confiável de mensagens, independentemente do número ou tipo de intermediários que separam os pontos de extremidade de mensagens (origem e destino). Isso inclui qualquer intermediários de transporte que não usam SOAP (por exemplo, proxies HTTP) ou intermediários que usam SOAP (por exemplo, roteadores baseados em SOAP ou pontes) que são necessários para mensagens entre os pontos de extremidade. Sessões confiáveis usam uma janela de transferência na memória para falhas de nível de mensagem SOAP máscara e restabelecer conexões no caso de falhas de transporte.  
  
 Sessões confiáveis fornecem transferências de mensagens confiável de baixa latência. Eles fornecem para mensagens SOAP através de qualquer proxies ou intermediários, equivalente ao qual TCP permite pacotes por pontes IP. Para obter mais informações sobre sessões confiáveis, consulte [sessões confiáveis](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Filas  
 As filas no [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] fornecer ambas as transferências confiáveis de mensagens e separação entre fontes e destinos às custas de alta latência. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comunicação em fila é criada sobre o enfileiramento de mensagens (MSMQ).  
  
 MSMQ é fornecido como um componente opcional do Windows. O serviço do MSMQ é executado como um serviço do Windows. Ele captura mensagens de transmissão em uma fila de transmissão em nome da fonte e entrega para uma fila de destino. A fila de destino aceita mensagens em nome de destino para envio posterior sempre que o destino de solicitações de mensagens. Os gerenciadores de MSMQ implementam um protocolo de transferência de mensagens confiáveis para que as mensagens não serão perdidas durante a transmissão. O protocolo pode ser nativo ou um protocolo baseado em SOAP, chamado de protocolo de mensagens confiável SOAP (SRMP).  
  
 A separação, juntamente com as transferências de mensagens confiáveis entre as filas, permite que os aplicativos que são acoplados de forma flexível para se comunicar de forma confiável. Ao contrário das sessões confiáveis, a origem e destino não precisa estar em execução ao mesmo tempo. Implicitamente, isso permite cenários onde filas são, na verdade, usadas como um mecanismo nivelamento de carga quando a taxa da fonte de produção de mensagem e a taxa de destino do consumo de mensagem não coincidem. Para obter mais informações sobre as filas, consulte [filas no WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de sessões confiáveis](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)  
 [Enfileiramento no WCF](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
