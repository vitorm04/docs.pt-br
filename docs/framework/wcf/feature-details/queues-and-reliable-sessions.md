---
title: Sessões confiáveis e filas
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: 2f79e1eac469dc1d9d775cbca0f06046f10dfb20
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642903"
---
# <a name="queues-and-reliable-sessions"></a>Sessões confiáveis e filas
Sessões confiáveis e filas são os recursos do Windows Communication Foundation (WCF) que implementam o sistema de mensagens confiável. Os tópicos contidos nesta seção abordam os recursos de mensagens confiáveis do WCF.  
  
 Sistema de mensagens confiável é como uma fonte confiável de mensagens (chamada de código-fonte) transfere mensagens de forma confiável para um destino de sistema de mensagens confiável (chamado de destino).  
  
 Sistema de mensagens confiável tem os seguintes aspectos principais:  
  
-   Garantias de transferência de mensagens enviadas de uma fonte para um destino, independentemente de falhas de transporte ou de falha de transferência de mensagem.  
  
-   Separação da origem e o destino de um do outro, que fornece falha independente e a recuperação de origem e o destino como bem tão confiável de transferência e a entrega de mensagens, mesmo que a origem ou destino está indisponível.  
  
 Mensagens confiáveis com frequência vem às custas de alta latência. Latência é o tempo necessário para a mensagem alcançar o destino da origem. WCF, portanto, fornece os seguintes tipos de sistema de mensagens confiável:  
  
-   [Sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions.md), que oferecem transferência confiável sem o custo de alta latência  
  
-   [As filas no WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md), que oferecem transferências confiáveis e a separação entre a origem e destino.  
  
## <a name="reliable-sessions"></a>Sessões confiáveis  
 Sessões confiáveis fornecem transferência confiável de ponta a ponta de mensagens entre uma origem e um destino usando o protocolo WS-ReliableMessaging independentemente do número ou tipo de intermediários que separam os pontos de extremidade de mensagens (origem e destino). Isso inclui qualquer intermediário de transporte que não usa SOAP (por exemplo, proxies HTTP) ou intermediários que usam o SOAP (por exemplo, roteadores baseados em SOAP ou pontes) que são necessários para que as mensagens fluam entre os pontos de extremidade. Sessões confiáveis usam uma janela de transferência na memória para falhas de nível de mensagem SOAP máscara e restabelecer as conexões no caso de falhas de transporte.  
  
 Sessões confiáveis fornecem transferências de mensagens confiáveis de baixa latência. Eles fornecem para mensagens SOAP sobre quaisquer proxies ou intermediários, equivalente ao qual o TCP fornece para pacotes em pontes IP. Para obter mais informações sobre as sessões confiáveis, consulte [sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Filas  
 As filas no WCF fornecem ambas as transferências de confiáveis de mensagens e a separação entre origens e destinos às custas de alta latência. WCF em fila comunicação se baseia no enfileiramento de mensagens (também conhecido como MSMQ).  
  
 MSMQ é fornecido como uma opção com Windows que é executado como um serviço NT. Ele captura mensagens para transmissão em uma fila de transmissão em nome de origem e a entrega para uma fila de destino. A fila de destino aceita mensagens em nome de destino para entrega posterior sempre que o destino solicita para mensagens. Os gerenciadores de fila do MSMQ implementam um protocolo de transferência de mensagens confiável, de modo que as mensagens não são perdidas durante a transmissão. O protocolo pode ser baseado em SOAP, como Reliable Messaging protocolo SRMP (Soap) ou nativo.  
  
 A separação, juntamente com as transferências de mensagens confiável entre as filas, permite que os aplicativos que são flexíveis para se comunicar de forma confiável. Ao contrário de sessões confiáveis, a origem e destino não precisa estar em execução ao mesmo tempo. Implicitamente, isso possibilita cenários em que filas são, na verdade, usadas como um mecanismo de nivelamento de carga quando há uma incompatibilidade entre a taxa de produção de mensagem pela fonte e a taxa de consumo de mensagem pelo destino. Para obter mais informações sobre filas, consulte [filas no WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Consulte também
- [Filas no WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
- [Visão geral de sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
