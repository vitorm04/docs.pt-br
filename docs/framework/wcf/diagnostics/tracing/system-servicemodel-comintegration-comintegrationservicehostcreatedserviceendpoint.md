---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: f89dd1373d67714046f8cb958582c3a5dea04456
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674784"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Não é possível mover ou excluir mensagem.  
  
## <a name="description"></a>Descrição  
 O rastreamento indica que ocorreu uma falha ao tentar mover, excluir ou rejeitar uma mensagem MSMQ.  
  
 As mensagens MSMQ são empregadas pela Windows Communication Foundation (WCF) (quando usadas com o NetMsmqBinding ou o MsmqIntegrationBinding). Este traço está relacionado com `ReceiveErrorHandling` o valor escolhido da propriedade no NetMsmqBinding ou MsmqIntegrationBinding.  
  
 Este traço não indica uma falha geral do sistema. No entanto, indica que a disposição da mensagem venenosa escolhida falhou para uma mensagem. Para obter mais informações sobre quando as mensagens se tornam venenosas e como configurar seu serviço para manuseá-las adequadamente, consulte [Poison-Message Handling](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Confira também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilizando o rastreamento para solucionar problemas em seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e Diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
