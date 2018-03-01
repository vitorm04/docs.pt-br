---
title: "Agrupamento de mensagens em fila em uma sessão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aba045456d61b5ad687f1030dca3c26b083cdb58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="grouping-queued-messages-in-a-session"></a>Agrupamento de mensagens em fila em uma sessão
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Fornece uma sessão que permite agrupar um conjunto de mensagens relacionadas juntas para processamento por um único aplicativo. As mensagens que fazem parte de uma sessão devem ser parte da mesma transação. Como todas as mensagens fazem parte da mesma transação, se uma mensagem falhar ao ser processada toda a sessão será revertida. Sessões têm comportamento semelhante em relação a filas de mensagens mortas e suspeitas. O tempo para a propriedade de vida (TTL) definida em uma associação enfileirada configurada para sessões é aplicado à sessão como um todo. Se apenas algumas das mensagens na sessão são enviadas antes que o TTL expire, toda a sessão é colocada na fila de mensagens mortas. Da mesma forma, quando as mensagens em uma sessão não ser enviada a um aplicativo da fila de aplicativos, toda a sessão é colocada na fila de suspeitas (se disponível).  
  
## <a name="message-grouping-example"></a>Exemplo de agrupamento de mensagem  
 Um exemplo de onde o agrupamento de mensagens é útil é ao implementar um aplicativo de processamento de pedido como um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço. Por exemplo, um cliente envia uma ordem para este aplicativo que contém um número de itens. Para cada item, o cliente faz uma chamada para o serviço, o que resulta em uma mensagem separada que está sendo enviada. É possível para que servem a receber o primeiro item e o servidor B para receber o segundo item. Cada vez que um item é adicionado, o servidor está processando o item tem que localizar o pedido apropriado e adicione o item a ele, que é altamente ineficiente. Você ainda tiver essas ineficiências com um único servidor tratar todas as solicitações, porque o servidor deve manter o controle de todos os pedidos sendo processados no momento e determinar qual o novo item pertence. Todas as solicitações de uma única ordem de agrupamento bastante simplifica a implementação de tal aplicativo. O aplicativo cliente envia todos os itens de uma única ordem em uma sessão, para que quando o serviço processa o pedido, ele processa toda a sessão de uma vez. \  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Para configurar um contrato de serviço para usar sessões  
  
1.  Defina um contrato de serviço que exige uma sessão. Fazer isso com o <xref:System.ServiceModel.OperationContractAttribute> de atributo e especificando por:  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  Marca as operações no contrato como unidirecional, pois esses métodos não retorna nada. Isso é feito com o <xref:System.ServiceModel.OperationContractAttribute> de atributo e especificando por:  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  Implementar o contrato de serviço e especifique um `InstanceContextMode` de `PerSession`. Isso cria uma instância de serviço somente uma vez para cada sessão.  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  Cada operação de serviço exige uma transação. Especificar com o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo. A operação que conclui a transação também deve definir `TransactionAutoComplete` para `true`.  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  Configurar um ponto de extremidade que usa o fornecida pelo sistema `NetMsmqBinding` associação.  
  
6.  Criar uma fila transacional usando <xref:System.Messaging>. Você também pode criar a fila usando o serviço de enfileiramento de mensagens (MSMQ) ou o MMC. Se você fizer isso, crie uma fila transacional.  
  
7.  Criar um host de serviço para o serviço usando <xref:System.ServiceModel.ServiceHost>.  
  
8.  Abra o host de serviço para disponibilizar o serviço.  
  
9. Feche o host de serviço.  
  
#### <a name="to-set-up-a-client"></a>Para configurar um cliente  
  
1.  Crie um escopo de transação para gravar na fila transacional.  
  
2.  Criar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta.  
  
3.  Faz o pedido.  
  
4.  Fechar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir fornece o código para o `IProcessOrder` de serviço e para um cliente que usa este serviço. Ele mostra como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa na fila de sessões para fornecer o comportamento do agrupamento.  
  
### <a name="code-for-the-service"></a>Código do serviço  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a>Código do cliente  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a>Consulte também  
 [Sessões e filas](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)
