---
title: Serviços confiáveis
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
ms.openlocfilehash: a617100e46d4bcafb9325efa99c255f2f8ee5981
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216763"
---
# <a name="reliable-services"></a>Serviços confiáveis
Sessões confiáveis e filas são os recursos do Windows Communication Foundation (WCF) que implementam o sistema de mensagens confiável. Este tópico explica os recursos de mensagens confiáveis do WCF.  
  
 *Mensagens confiáveis* é como uma fonte confiável de mensagens (chamado de *código-fonte*) transfere mensagens de forma confiável para um destino de sistema de mensagens confiável (chamado o *destino*).  
  
 Sistema de mensagens confiável executa as seguintes funções:  
  
-   Transfere garantias para as mensagens enviadas de uma fonte para um destino, independentemente das falhas de transporte ou transferência de mensagem.  
  
-   Separa o código-fonte e o destino uns dos outros. Isso fornece falha independente e recuperação do código-fonte e o destino, bem como transferência confiável e entrega de mensagens, mesmo quando a origem ou destino está indisponível.  
  
 Mensagens confiáveis com frequência vem às custas de alta latência. *Latência* é o tempo necessário para a mensagem alcançar o destino da origem. WCF, portanto, fornece os seguintes tipos de sistema de mensagens confiável:  
  
-   [Sessões confiáveis](../../../docs/framework/wcf/feature-details/reliable-sessions.md), que oferece uma transferência confiável sem o custo de alta latência.  
  
-   [As filas no WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md), que oferece transferências confiáveis e a separação entre a origem e destino.  
  
## <a name="reliable-sessions"></a>Sessões confiáveis  
 Sessões confiáveis fornecem transferência confiável de ponta a ponta de mensagens entre uma origem e um destino usando o protocolo WS-confiável de mensagens, independentemente do número ou tipo de intermediários que separam os pontos de extremidade de mensagens (origem e destino). Isso inclui qualquer intermediário de transporte que não usa SOAP (por exemplo, proxies HTTP) ou intermediários que usam o SOAP (por exemplo, roteadores baseados em SOAP ou pontes) que são necessários para que as mensagens fluam entre os pontos de extremidade. Sessões confiáveis usam uma janela de transferência na memória para falhas de nível de mensagem SOAP máscara e restabelecer as conexões no caso de falhas de transporte.  
  
 Sessões confiáveis fornecem transferências de mensagens confiáveis de baixa latência. Eles fornecem para mensagens SOAP sobre quaisquer proxies ou intermediários, equivalente ao qual o TCP fornece para pacotes em pontes IP. Para obter mais informações sobre as sessões confiáveis, consulte [sessões confiáveis](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Filas  
 As filas no WCF fornecem ambas as transferências de confiáveis de mensagens e a separação entre origens e destinos às custas de alta latência. WCF em fila comunicação baseia-se na parte superior Message Queuing (MSMQ).  
  
 MSMQ é fornecido como um componente opcional do Windows. O serviço MSMQ é executado como um serviço do Windows. Ele captura mensagens para transmissão em uma fila de transmissão em nome de origem e a entrega para uma fila de destino. A fila de destino aceita mensagens em nome de destino para entrega posterior sempre que o destino solicita as mensagens. Os gerenciadores de MSMQ implementam um protocolo de transferência de mensagens confiável, de modo que as mensagens não são perdidas durante a transmissão. O protocolo pode ser nativo ou um protocolo baseado em SOAP chamado Reliable Messaging protocolo SRMP (SOAP).  
  
 A separação, juntamente com as transferências de mensagens confiável entre as filas, permite que os aplicativos que são flexíveis para se comunicar de forma confiável. Ao contrário de sessões confiáveis, a origem e destino não precisa estar em execução ao mesmo tempo. Implicitamente, isso possibilita cenários em que filas são, na verdade, usadas como um mecanismo de nivelamento de carga quando a taxa da origem de produção de mensagem e a taxa do destino do consumo de mensagem não coincidem. Para obter mais informações sobre filas, consulte [filas no WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de sessões confiáveis](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
- [Enfileiramento no WCF](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
