---
title: Agrupamento de mensagens em fila em uma sessão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 231310e5c427f507141e3c144cb02b8e848d4fbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185153"
---
# <a name="grouping-queued-messages-in-a-session"></a>Agrupamento de mensagens em fila em uma sessão
O Windows Communication Foundation (WCF) fornece uma sessão que permite agrupar um conjunto de mensagens relacionadas para processamento por um único aplicativo de recepção. As mensagens que fazem parte de uma sessão devem fazer parte da mesma transação. Como todas as mensagens fazem parte da mesma transação, se uma mensagem não for processada, toda a sessão será revertida. As sessões têm comportamentos semelhantes em relação a filas de letras mortas e filas de veneno. A propriedade Time to Live (TTL) definida em uma vinculação enfileirada configurada para sessões é aplicada à sessão como um todo. Se apenas algumas das mensagens da sessão forem enviadas antes da ttl expirar, toda a sessão será colocada na fila da letra morta. Da mesma forma, quando as mensagens em uma sessão não são enviadas para um aplicativo da fila do aplicativo, toda a sessão é colocada na fila de veneno (se disponível).  
  
## <a name="message-grouping-example"></a>Exemplo de agrupamento de mensagens  
 Um exemplo em que o agrupamento de mensagens é útil ao implementar um aplicativo de processamento de pedidos como um serviço WCF. Por exemplo, um cliente envia um pedido para este aplicativo que contém uma série de itens. Para cada item, o cliente faz uma chamada para o serviço, o que resulta em uma mensagem separada sendo enviada. É possível que o saque A receba o primeiro item, e o servidor B receba o segundo item. Cada vez que um item é adicionado, o servidor processando esse item tem que encontrar a ordem apropriada e adicionar o item a ele, o que é altamente ineficiente. Você ainda se depara com tais ineficiências com apenas um único servidor lidando com todas as solicitações, porque o servidor deve acompanhar todas as ordens que estão sendo processadas e determinar a qual o novo item pertence. O agrupamento de todas as solicitações de uma única ordem simplifica muito a implementação de tal aplicativo. O aplicativo cliente envia todos os itens para um único pedido em uma sessão, então quando o serviço processa o pedido, ele processa toda a sessão de uma só vez. \  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Para configurar um contrato de serviço para usar sessões  
  
1. Defina um contrato de serviço que exija uma sessão. Faça isso <xref:System.ServiceModel.ServiceContractAttribute> com o atributo especificando:  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. Marque as operações no contrato como unidirecional, porque esses métodos não retornam nada. Isso é feito <xref:System.ServiceModel.OperationContractAttribute> com o atributo especificando:  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Implementar o contrato de <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>serviço e especificar um de . Isso instancia o serviço apenas uma vez para cada sessão.  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Cada operação de serviço requer uma transação. Especifique <xref:System.ServiceModel.OperationBehaviorAttribute> isso com o atributo. A operação que conclui a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> transação também deve ser definida como `true`.  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    ```  
  
5. Configure um ponto final que use `NetMsmqBinding` a vinculação fornecida pelo sistema.  
  
6. Crie uma fila transacional usando <xref:System.Messaging>. Você também pode criar a fila usando a Fila de Mensagens (MSMQ) ou MMC. Se você fizer isso, crie uma fila transacional.  
  
7. Crie um host de serviço <xref:System.ServiceModel.ServiceHost>para o serviço usando .  
  
8. Abra o host de serviço para disponibilizar o serviço.  
  
9. Feche o host de serviço.  
  
#### <a name="to-set-up-a-client"></a>Para configurar um cliente  
  
1. Crie um escopo de transação para escrever na fila transacional.  
  
2. Crie o cliente WCF usando a ferramenta [ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
  
3. Coloque o pedido.  
  
4. Feche o cliente WCF.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir `IProcessOrder` fornece o código para o serviço e para um cliente que usa este serviço. Ele mostra como o WCF usa sessões enfileiradas para fornecer o comportamento de agrupamento.  
  
### <a name="code-for-the-service"></a>Código para o Serviço  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>Código para o Cliente  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>Confira também

- [Sessões e filas](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)
