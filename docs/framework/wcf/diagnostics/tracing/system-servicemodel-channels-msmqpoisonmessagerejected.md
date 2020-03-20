---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 6b0e6e3ebcf5d414e9dbbcecd09ba2e8bb3ddd3a
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674811"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Mensagem venenosa rejeitada.  
  
## <a name="description"></a>Descrição  

 O rastro indica que uma mensagem venenosa foi encontrada e posteriormente rejeitada. Isso ocorre `ReceiveErrorHandling` quando a propriedade no NetMsmqBinding ou MsmqIntegrationBinding é definida como `Reject`. Uma mensagem rejeitada é entregue de volta à fila de [letras mortas](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)do remetente .  
  
 Para obter mais informações sobre quando as mensagens se tornam venenosas e como configurar seu serviço para manuseá-las adequadamente, consulte [Poison-Message Handling](../../feature-details/poison-message-handling.md). Para obter mais informações sobre o que significa uma mensagem rejeitada no MSMQ, consulte [MQMarkMessageReject .](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))  
  
## <a name="see-also"></a>Confira também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilizando o rastreamento para solucionar problemas em seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e Diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Manuseio de mensagens venenosas](../../feature-details/poison-message-handling.md)
- [MQMarkMessageRejeitado](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
