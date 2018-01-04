---
title: "Como fazer intercâmbio de mensagens em fila com pontos de extremidade do WCF"
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
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 975c5ea5d5b3ab81d37b713e84f273e4c2c1c0b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Como fazer intercâmbio de mensagens em fila com pontos de extremidade do WCF
Filas Certifique-se de que o sistema de mensagens confiável pode ocorrer entre um cliente e um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de serviço, mesmo se o serviço não está disponível no momento da comunicação. Os procedimentos a seguir mostram como garantir a comunicação durável entre um cliente e um serviço usando o padrão na fila associação ao implementar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.  
  
 Esta seção explica como usar <xref:System.ServiceModel.NetMsmqBinding> para comunicação em fila entre um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente e um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Para usar o enfileiramento de mensagens em um serviço WCF  
  
1.  Definir um contrato de serviço usando uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute>. Marcar as operações na interface que fazem parte do contrato de serviço com o <xref:System.ServiceModel.OperationContractAttribute> e especificá-los como unidirecional porque nenhuma resposta para o método é retornada. O código a seguir fornece um contrato de serviço de exemplo e sua definição de operação.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  Quando o contrato de serviço passa tipos definidos pelo usuário, você deve definir os contratos de dados para esses tipos. O código a seguir mostra dois contratos de dados, `PurchaseOrder` e `PurchaseOrderLineItem`. Esses dois tipos definem os dados que são enviados para o serviço. (Observe que as classes que definem esse contrato de dados também definem um número de métodos. Esses métodos não são considerados parte do contrato de dados. Somente os membros que são declarados com o `DataMember` atributo fazem parte do contrato de dados.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  Implemente os métodos do contrato de serviço definidos na interface em uma classe.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Observe o <xref:System.ServiceModel.OperationBehaviorAttribute> colocadas no `SubmitPurchaseOrder` método. Especifica que esta operação deve ser chamada dentro de uma transação e que a transação seja concluída automaticamente quando o método é concluído.  
  
4.  Criar uma fila transacional usando <xref:System.Messaging>. Você pode optar por criar a fila usando o Microsoft Management Console (MMC) do serviço de enfileiramento de mensagens da Microsoft (MSMQ) em vez disso. Nesse caso, certifique-se de que criar uma fila transacional.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  Definir um <xref:System.ServiceModel.Description.ServiceEndpoint> na configuração que especifica o endereço do serviço e usa o padrão de <xref:System.ServiceModel.NetMsmqBinding> associação. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuração, consulte [Configurando o Windows Communication Foundation aplicativos](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
  
  
6.  Criar um host para o `OrderProcessing` serviço usando <xref:System.ServiceModel.ServiceHost> que lê mensagens da fila e processa-os. Abra o host de serviço para disponibilizar o serviço. Exiba uma mensagem que informa o usuário pressione qualquer tecla para encerrar o serviço. Chamar `ReadLine` de espera para a chave a ser pressionado e, em seguida, feche o serviço.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>Para criar um cliente para o serviço na fila  
  
1.  O exemplo a seguir mostra como executar o aplicativo de hospedagem e use a ferramenta Svcutil.exe para criar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente.  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  Definir um <xref:System.ServiceModel.Description.ServiceEndpoint> na configuração que especifica o endereço e usa o padrão de <xref:System.ServiceModel.NetMsmqBinding> associação, conforme mostrado no exemplo a seguir.  
  
  
  
3.  Criar um escopo de transação para gravar na fila transacional, a chamada a `SubmitPurchaseOrder` operação e fechar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram o código de serviço, aplicativo de hospedagem, arquivo App. config e incluídos neste exemplo de código do cliente.  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [Associação transacionada do MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Windows Communication Foundation para Enfileiramento de Mensagens](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalando o Enfileiramento de Mensagens (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Exemplos de associação de integração de serviço de enfileiramento de mensagem](http://msdn.microsoft.com/en-us/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Enfileiramento de mensagens para o Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Segurança de mensagem através do enfileiramento de mensagem](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
