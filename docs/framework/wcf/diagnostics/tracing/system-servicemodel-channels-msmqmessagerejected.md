---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674768"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
A MSMQ rejeitou a mensagem.  
  
## <a name="description"></a>Descrição  
 Este rastreamento indica que uma mensagem MSMQ foi rejeitada.  
  
 As mensagens MSMQ podem ser rejeitadas quando o Windows Communication Foundation (WCF) (usado com o NetMsmqBinding ou o MsmqIntegrationBinding) não puder processá-las. Essas mensagens são referidas como mensagens venenosas. Uma mensagem venenosa é `ReceiveErrorHandling` rejeitada quando a propriedade no NetMsmqBinding ou `Reject`MsmqIntegrationBinding é definida como . Uma mensagem rejeitada é entregue de volta à fila de [letras mortas](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)do remetente .  
  
 Para obter mais informações sobre quando as mensagens se tornam venenosas e como configurar seu serviço para manuseá-las adequadamente, consulte [Poison-Message Handling](../../feature-details/poison-message-handling.md).  
  
 Para obter mais informações sobre o que significa uma mensagem rejeitada no MSMQ, consulte [MQMarkMessageReject .](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))  
  
## <a name="see-also"></a>Confira também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilizando o rastreamento para solucionar problemas em seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e Diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Manuseio de mensagens venenosas](../../feature-details/poison-message-handling.md)
- [MQMarkMessageRejeitado](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
