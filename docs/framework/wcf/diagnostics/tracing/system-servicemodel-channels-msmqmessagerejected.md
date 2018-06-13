---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 2bd64263a2374c10a3514cbed75f9224542051dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33478929"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ rejeitou a mensagem.  
  
## <a name="description"></a>Descrição  
 Este rastreamento indica que uma mensagem MSMQ foi rejeitada.  
  
 Mensagens MSMQ poderá ser rejeitadas quando o Windows Communication Foundation (WCF) (usado com o NetMsmqBinding ou MsmqIntegrationBinding) não pode processá-los. Essas mensagens são denominadas mensagens suspeitas. Uma mensagem suspeita é rejeitada quando o `ReceiveErrorHandling` no NetMsmqBinding ou MsmqIntegrationBinding estiver definida como `Reject`. Uma mensagem rejeitada é fornecida para o remetente [fila de mensagens mortas](http://go.microsoft.com/fwlink/?LinkID=99544).  
  
 Consulte [manipulação de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens são suspeitas e como configurar seu serviço para tratar de maneira adequada.  
  
 Consulte [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) para obter mais detalhes sobre o que significa que uma mensagem rejeitada no MSMQ.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Tratamento de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)
