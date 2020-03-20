---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: e80fecf508158dcb53f08b75c8f9486c13e403a4
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674793"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
MSMQ deixou cair a mensagem.  
  
## <a name="description"></a>Descrição  
 O rastro indica que uma mensagem MSMQ foi descartada. As mensagens MSMQ podem ser descartadas quando o Windows Communication Foundation (WCF) (usado com o NetMsmqBinding ou o MsmqIntegrationBinding) não puder processá-las. Essas mensagens são referidas como mensagens venenosas.  
  
 Uma mensagem venenosa é `ReceiveErrorHandling` descartada quando a propriedade no NetMsmqBinding ou `Drop`MsmqIntegrationBinding é definida como . Uma mensagem descartada é removida da fila e não pode mais ser recuperável.  
  
 Para obter mais informações sobre quando as mensagens se tornam venenosas e como configurar seu serviço para manuseá-las adequadamente, consulte [Poison-Message Handling](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Confira também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilizando o rastreamento para solucionar problemas em seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e Diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Manuseio de mensagens venenosas](../../feature-details/poison-message-handling.md)
