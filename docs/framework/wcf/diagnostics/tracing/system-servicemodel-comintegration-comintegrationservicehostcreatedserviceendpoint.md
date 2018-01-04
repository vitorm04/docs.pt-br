---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87eac8f0e3949ac47c7bb2915a87043bdc205b8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Não é possível mover ou excluir a mensagem.  
  
## <a name="description"></a>Descrição  
 O rastreamento indica que ocorreu uma falha ao tentar mover, excluir ou rejeitar uma mensagem MSMQ.  
  
 Mensagens MSMQ são usadas pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (quando usado com o NetMsmqBinding ou MsmqIntegrationBinding). Este rastreamento está relacionado ao valor escolhido o `ReceiveErrorHandling` propriedade no NetMsmqBinding ou MsmqIntegrationBinding.  
  
 Este rastreamento não é uma indicação de uma falha geral no sistema. No entanto, ele indica escolhido suspeitas disposição de mensagem falhou para uma mensagem. Consulte [manipulação de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens são suspeitas e como configurar seu serviço para tratar de maneira adequada.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
