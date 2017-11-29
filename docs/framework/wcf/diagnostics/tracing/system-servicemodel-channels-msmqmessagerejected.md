---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecbbd8bc0e798388f994432ea2d3f25396f7de97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ rejeitou a mensagem.  
  
## <a name="description"></a>Descrição  
 Este rastreamento indica que uma mensagem MSMQ foi rejeitada.  
  
 As mensagens MSMQ podem ser rejeitada quando [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (usado com o NetMsmqBinding ou MsmqIntegrationBinding) não pode processá-los. Essas mensagens são denominadas mensagens suspeitas. Uma mensagem suspeita é rejeitada quando o `ReceiveErrorHandling` no NetMsmqBinding ou MsmqIntegrationBinding estiver definida como `Reject`. Uma mensagem rejeitada é fornecida para o remetente [fila de mensagens mortas](http://go.microsoft.com/fwlink/?LinkID=99544).  
  
 Consulte [manipulação de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens são suspeitas e como configurar seu serviço para tratar de maneira adequada.  
  
 Consulte [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) para obter mais detalhes sobre o que significa que uma mensagem rejeitada no MSMQ.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas de seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)  
 [Tratamento de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)
