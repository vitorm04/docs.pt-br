---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: d56bbf145c85902d8e5f1fd21f760633121da6da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939211"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Não é possível mover ou excluir a mensagem.  
  
## <a name="description"></a>Descrição  
 O rastreamento indica que ocorreu uma falha ao tentar mover, excluir ou rejeitar uma mensagem MSMQ.  
  
 Mensagens MSMQ são utilizadas pelo Windows Communication Foundation (WCF) (quando usado com o NetMsmqBinding ou o MsmqIntegrationBinding). Este rastreamento está relacionado ao valor escolhido o `ReceiveErrorHandling` propriedade no NetMsmqBinding ou MsmqIntegrationBinding.  
  
 Esse rastreamento não é uma indicação de uma falha geral no sistema. No entanto, ele indica que o escolhido suspeitas falhou para uma mensagem de disposição de mensagem. Ver [tratamento de mensagens suspeitas](https://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens se tornarão suspeitas e como configurar seu serviço para tratá-las adequadamente.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
