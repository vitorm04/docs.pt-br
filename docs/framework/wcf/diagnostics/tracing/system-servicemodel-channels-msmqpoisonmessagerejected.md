---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 7dc1e4120caae7c4a592067f5e77ed4f56e82e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Mensagem de inviabilização recusada.  
  
## <a name="description"></a>Descrição  
 O rastreamento indica que uma mensagem suspeita foi encontrada e subsequentemente rejeitada. Isso ocorre quando o `ReceiveErrorHandling` no NetMsmqBinding ou MsmqIntegrationBinding estiver definida como `Reject`. Uma mensagem rejeitada é fornecida para o remetente [fila de mensagens mortas](http://go.microsoft.com/fwlink/?LinkId=99544).  
  
 Consulte [manipulação de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkId=99546) para obter mais detalhes sobre quando as mensagens são suspeitas e como configurar seu serviço para tratar de maneira adequada. Consulte [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) para obter mais detalhes sobre o que significa que uma mensagem rejeitada no MSMQ.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Tratamento de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)
