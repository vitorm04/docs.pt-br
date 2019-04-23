---
title: 'Como: fazer intercâmbio de mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 7463f9cfc37c2bf4f271f6e59896a7d77f3f65cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310298"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Como: fazer intercâmbio de mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens
Você pode integrar os aplicativos existentes do serviço de enfileiramento de mensagens (MSMQ) com aplicativos do Windows Communication Foundation (WCF) usando a associação de integração de MSMQ para converter mensagens do MSMQ em mensagens do WCF. Isso permite que você chamar aplicativos de destinatário MSMQ de clientes do WCF, bem como chamar serviços WCF de aplicativos de remetente do MSMQ.  
  
 Nesta seção, vamos explicar como usar <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> para comunicação em fila entre (1) um cliente WCF e um serviço de aplicativo do MSMQ gravadas usando System. Messaging e (2) um cliente de aplicativo do MSMQ e um serviço WCF.  
  
 Para obter um exemplo completo que demonstra como chamar um aplicativo de receptor MSMQ de um cliente do WCF, consulte o [Windows Communication Foundation para enfileiramento de mensagens](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) exemplo.  
  
 Para obter um exemplo completo que demonstra como chamar um serviço WCF de um cliente do MSMQ, consulte a [enfileiramento de mensagens para o Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) exemplo.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Para criar um serviço WCF que recebe mensagens de um cliente do MSMQ  
  
1. Defina uma interface que define o contrato de serviço para o serviço WCF que recebe mensagens na fila de um aplicativo de remetente do MSMQ, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. Implementar a interface e aplique o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo à classe, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. Criar um arquivo de configuração que especifica o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  

4. Criar uma instância de um <xref:System.ServiceModel.ServiceHost> objeto que usa a associação configurada.  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Para criar um cliente do WCF que envia mensagens para um aplicativo de receptor MSMQ  
  
1. Defina uma interface que define o contrato de serviço para o cliente do WCF que envia mensagens para o destinatário MSMQ, na fila, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. Defina uma classe de cliente que o cliente do WCF usa para chamar o destinatário MSMQ.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. Crie uma configuração que especifica o uso da associação MsmqIntegrationBinding.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. Criar uma instância da classe do cliente e chamar o método definido pelo serviço de recebimento da mensagem.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Como: Troca de mensagens na fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Windows Communication Foundation para Enfileiramento de Mensagens](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [Instalando o Enfileiramento de Mensagens (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Enfileiramento de mensagens para o Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [Segurança de mensagem através do enfileiramento de mensagem](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
