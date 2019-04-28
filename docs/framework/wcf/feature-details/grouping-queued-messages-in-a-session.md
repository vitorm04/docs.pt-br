---
title: Agrupamento de mensagens em fila em uma sessão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 37f0874ea99ee928e49a54a3e6a05ea4ef06f84e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855914"
---
# <a name="grouping-queued-messages-in-a-session"></a>Agrupamento de mensagens em fila em uma sessão
Windows Communication Foundation (WCF) oferece uma sessão que lhe permite agrupar um conjunto de mensagens relacionadas juntas para processamento por um único aplicativo de recebimento. As mensagens que fazem parte de uma sessão devem ser parte da mesma transação. Como todas as mensagens fazem parte da mesma transação, se uma mensagem falhar ao ser processada toda a sessão será revertida. As sessões têm comportamentos semelhantes em relação a filas e filas suspeitas. O tempo para a propriedade de vida (TTL) definida em uma associação enfileirada configurada para sessões é aplicado à sessão como um todo. Se apenas algumas das mensagens da sessão são enviadas antes que o TTL expire, toda a sessão é colocada na fila de inatividade. Da mesma forma, quando mensagens em uma sessão não conseguir ser enviadas para um aplicativo da fila de aplicativos, toda a sessão é colocada na fila de mensagens suspeitas (se disponível).  
  
## <a name="message-grouping-example"></a>Exemplo de agrupamento de mensagem  
 Um exemplo em que o agrupamento de mensagens é útil é ao implementar um aplicativo de processamento de pedidos como um serviço WCF. Por exemplo, um cliente envia um pedido para este aplicativo que contém um número de itens. Para cada item, o cliente faz uma chamada para o serviço, o que resulta em uma mensagem separada que está sendo enviada. É possível para que serve a receber o primeiro item e o servidor B para receber o segundo item. Cada vez que um item é adicionado, o servidor de processamento desse item tem que localizar o pedido apropriado e adicione o item a ele, que é muito ineficiente. Você ainda encontrar essas ineficiências com apenas um único servidor manipular todas as solicitações, porque o servidor deve manter o controle de todos os pedidos sendo processados no momento e determinar qual o novo item pertence. Todas as solicitações para uma única ordem de agrupamento bastante simplifica a implementação de um aplicativo desse tipo. O aplicativo cliente envia todos os itens de uma única ordem em uma sessão, portanto, quando o serviço processa o pedido, ele processa toda a sessão ao mesmo tempo. \  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Para configurar um contrato de serviço para usar sessões  
  
1. Defina um contrato de serviço que requer uma sessão. Fazer isso com o <xref:System.ServiceModel.OperationContractAttribute> de atributos e ao especificar:  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2. Marca as operações no contrato como unidirecional, pois esses métodos não retorna nada. Isso é feito com o <xref:System.ServiceModel.OperationContractAttribute> de atributos e ao especificar:  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Implementar o contrato de serviço e especificar uma `InstanceContextMode` de `PerSession`. Esse código instancia o serviço apenas uma vez para cada sessão.  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Cada operação de serviço exige uma transação. Especifique isso com o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo. A operação que conclui a transação também deve definir `TransactionAutoComplete` para `true`.  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. Configurar um ponto de extremidade que usa o sistema forneceu `NetMsmqBinding` associação.  
  
6. Criar uma fila transacional usando <xref:System.Messaging>. Você também pode criar a fila usando o serviço de enfileiramento de mensagens (MSMQ) ou o MMC. Se você fizer isso, crie uma fila transacional.  
  
7. Criar um host de serviço para o serviço usando <xref:System.ServiceModel.ServiceHost>.  
  
8. Abra o host de serviço para disponibilizar o serviço.  
  
9. Feche o host de serviço.  
  
#### <a name="to-set-up-a-client"></a>Para configurar um cliente  
  
1. Crie um escopo de transação para gravar na fila transacional.  
  
2. Criar o cliente WCF usando o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta.  
  
3. Fazer o pedido.  
  
4. Feche o cliente do WCF.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir fornece o código para o `IProcessOrder` de serviço e para um cliente que usa esse serviço. Ele mostra como o WCF usa sessões na fila para fornecer o comportamento de agrupamento.  
  
### <a name="code-for-the-service"></a>Código do serviço  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>Código do cliente  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>Consulte também

- [Sessões e filas](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)
