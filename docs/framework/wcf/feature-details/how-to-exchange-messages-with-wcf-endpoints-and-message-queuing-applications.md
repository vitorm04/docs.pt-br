---
title: "Como fazer intercâmbio de mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa6f9d0b9631420013593cb44903b5451549e8c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Como fazer intercâmbio de mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens
Você pode integrar aplicativos existentes do serviço de enfileiramento de mensagens (MSMQ) com [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativos usando a associação de integração do MSMQ para converter as mensagens MSMQ em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagens. Isso permite que você chame em aplicativos de receptor MSMQ de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes, bem como chamar em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços de aplicativos de remetente do MSMQ.  
  
 Nesta seção, explicaremos como usar <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> para comunicação em fila entre (1) um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente e um serviço de aplicativo do MSMQ gravadas usando System. Messaging e (2) um cliente de aplicativo do MSMQ e um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.  
  
 Para obter um exemplo completo que demonstra como chamar um aplicativo receptor MSMQ um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, consulte o [Windows Communication Foundation para enfileiramento](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) exemplo.  
  
 Para obter um exemplo completo que demonstra como chamar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço de um cliente do MSMQ, consulte o [enfileiramento de mensagens para o Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) exemplo.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Para criar um serviço WCF que recebe mensagens de um cliente do MSMQ  
  
1.  Define uma interface que define o contrato de serviço para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que recebe as mensagens na fila de um aplicativo de remetente do MSMQ, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  Implementa a interface e aplique o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo à classe, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  Criar um arquivo de configuração que especifica o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
  
  
4.  Criar uma instância de um <xref:System.ServiceModel.ServiceHost> objeto que usa a associação configurada.  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Para criar um cliente do WCF que envia mensagens a um aplicativo de destinatário do MSMQ  
  
1.  Define uma interface que define o contrato de serviço para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente que envia na fila de mensagens do receptor do MSMQ, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  Definir um cliente de classe que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente usa para chamar o receptor do MSMQ.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  Crie uma configuração que especifica o uso da ligação MsmqIntegrationBinding.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  Criar uma instância da classe do cliente e chame o método definido pelo serviço de recebimento da mensagem.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Como trocar mensagens na fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Windows Communication Foundation para Enfileiramento de Mensagens](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalando o Enfileiramento de Mensagens (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Enfileiramento de mensagens para o Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Segurança de mensagem através do enfileiramento de mensagem](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
