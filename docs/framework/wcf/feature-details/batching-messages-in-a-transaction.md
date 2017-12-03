---
title: "Mensagens de lote em uma transação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d9effe9b44a8e6f786103162930852de80ab4f8d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="batching-messages-in-a-transaction"></a>Mensagens de lote em uma transação
Na fila de aplicativos usam transações para garantir a correção e a entrega confiável de mensagens. Transações, no entanto, são operações caras e podem reduzir drasticamente a taxa de transferência de mensagem. Uma maneira de melhorar a taxa de transferência de mensagem é ter um aplicativo de ler e processar várias mensagens em uma única transação. É a compensação entre desempenho e a recuperação: à medida que aumenta o número de mensagens em um lote, aumenta a quantidade de trabalho de recuperação que necessárias se as transações são revertidas. É importante observar a diferença entre mensagens de lote em uma transação e sessões. Um *sessão* é um agrupamento de mensagens relacionadas que são processados por um único aplicativo e confirmado como uma única unidade. Sessões geralmente são usadas quando um grupo de mensagens relacionadas deve ser processado em conjunto. Um exemplo disso é um site de compra online. *Lotes* são usados para processar vários, não relacionados a mensagens de forma que a taxa de transferência de mensagem aumenta. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]sessões, consulte [mensagens na fila de agrupamento em uma sessão](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md). Mensagens em um lote também são processadas por um único aplicativo e confirmadas como uma única unidade, mas não pode haver nenhuma relação entre as mensagens no lote. Mensagens de lote em uma transação são uma otimização que não seja alterado como o aplicativo é executado.  
  
## <a name="entering-batching-mode"></a>Inserir o modo de lote  
 O <xref:System.ServiceModel.Description.TransactedBatchingBehavior> controles de comportamento de ponto de extremidade envio em lote. Adicionar esse comportamento de ponto de extremidade para um ponto de extremidade de serviço informa [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para mensagens em lote em uma transação. Nem todas as mensagens necessitam de uma transação, de forma que apenas as mensagens que requerem uma transação são colocadas em um lote, e apenas as mensagens enviadas com as operações marcadas com `TransactionScopeRequired`  =  `true` e `TransactionAutoComplete`  =  `true` são considerado para um lote. Se todas as operações no contrato de serviço são marcadas com `TransactionScopeRequired`  =  `false` e `TransactionAutoComplete`  =  `false`, em seguida, o modo de lote nunca é inserido.  
  
## <a name="committing-a-transaction"></a>Confirmar uma transação  
 Uma transação em lote é confirmada com base no seguinte:  
  
-   `MaxBatchSize`. Uma propriedade do <xref:System.ServiceModel.Description.TransactedBatchingBehavior> comportamento. Essa propriedade determina o número máximo de mensagens que são colocados em um lote. Quando esse número for atingido, o lote será confirmado. Este é o valor não é um limite estrito, é possível confirmar um lote antes de receber esse número de mensagens.  
  
-   `Transaction Timeout`. Depois de decorrido 80 por cento do tempo-limite da transação, o lote será confirmado e é criado um novo lote. Isso significa que se 20 por cento ou menos de tempo fornecido para a conclusão de uma transação permanece, o lote será confirmado.  
  
-   `TransactionScopeRequired`. Durante o processamento de um lote de mensagens, se [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] encontrar um que tenha `TransactionScopeRequired`  =  `false`, ele confirma o lote e reabre um novo lote no recebimento da primeira mensagem com `TransactionScopeRequired`  =  `true` e `TransactionAutoComplete` = `true`.  
  
-   Se não mais houver mensagens na fila, o lote atual for confirmado, mesmo se o `MaxBatchSize` não foi atingido ou 80 por cento do tempo-limite da transação ainda não tiver decorrido.  
  
## <a name="leaving-batching-mode"></a>Deixar o modo de lote  
 Se uma mensagem em um lote faz com que a transação seja anulada, ocorrem as seguintes etapas:  
  
1.  Todo o lote de mensagens é revertido.  
  
2.  As mensagens são lidas um de cada vez até que o número de mensagens ler excede duas vezes o tamanho máximo de lote.  
  
3.  Modo de lote é inserido novamente.  
  
## <a name="choosing-the-batch-size"></a>Escolher o tamanho do lote  
 O tamanho do lote depende do aplicativo. O método empírico é a melhor maneira de chegar a um tamanho de lote ideal para o aplicativo. É importante lembrar-se ao escolher um tamanho de lote para escolher o tamanho de acordo com o modelo de implantação real do seu aplicativo. Por exemplo, ao implantar o aplicativo, se você precisar de um SQL server em um computador remoto e uma transação que abrange a fila e o SQL server, em seguida, o tamanho do lote é melhor determinado executando essa configuração exata.  
  
## <a name="concurrency-and-batching"></a>Simultaneidade e envio em lote  
 Para aumentar a taxa de transferência, você também pode ter muitos lotes executados simultaneamente. Definindo `ConcurrencyMode.Multiple` em `ServiceBehaviorAttribute`, habilitar o processamento em lotes simultâneos.  
  
 *Limitação de serviço* é um comportamento de serviço que é usado para indicar o número máximo de chamadas simultâneas pode ser feito no serviço. Quando usado com o envio em lote, isso é interpretado como muitos lotes simultâneos podem ser executados. Se a limitação de serviço não for definida, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] padrão é o máximo de chamadas simultâneas para 16. Portanto, se o comportamento de lote foram adicionado por padrão, um máximo de 16 lotes pode ser ativo ao mesmo tempo. É aconselhável ajustar a limitação de serviço e envio em lote com base na sua capacidade. Por exemplo, se a fila tem 100 mensagens e um lote de 20 for desejado, com o máximo de chamadas simultâneas definido como 16 não é útil porque, dependendo da taxa de transferência, 16 transações podem ser ativo, semelhante a não ter o envio em lote ativado. Portanto, quando ajustar o desempenho, ou não ter o processamento em lotes simultâneos ou tenha lotes simultâneos com o tamanho de limitação de serviço correta.  
  
## <a name="batching-and-multiple-endpoints"></a>Envio em lote e vários pontos de extremidade  
 Um ponto de extremidade é composto de um endereço e um contrato. Pode haver vários pontos de extremidade que compartilham a mesma associação. É possível que dois pontos de extremidade compartilhar a mesma associação e escutar identificador de recurso uniforme (URI) ou o endereço da fila. Se dois pontos de extremidade estão lendo da mesma fila e transacionado comportamento de lote é adicionado a ambos os pontos de extremidade, um conflito no lote tamanhos especificados podem surgir. Isto pode ser resolvido com a implementação de envio em lote usando o tamanho do lote mínimo especificado entre os dois comportamentos de envio em lote transacionados. Nesse cenário, se um dos pontos de extremidade não especificar o lote transacionado, em seguida, os pontos de extremidade não usaria envio em lote.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar o `TransactedBatchingBehavior` em um arquivo de configuração.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 O exemplo a seguir mostra como especificar o <xref:System.ServiceModel.Description.TransactedBatchingBehavior> no código.  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
     ServiceEndpoint sep = ServiceHost.AddServiceEndpoint(typeof(IOrderProcessor), new NetMsmqBinding(), "net.msmq://localhost/private/ServiceModelSamplesTransacted");
     sep.Behaviors.Add(new TransactedBatchingBehavior(100));
     
     // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();
  
    // The service can now be accessed.
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.WriteLine();
    Console.ReadLine();
  
    // Close the ServiceHostB to shut down the service.
    serviceHost.Close();
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
