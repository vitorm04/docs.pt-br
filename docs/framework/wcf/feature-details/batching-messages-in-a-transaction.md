---
title: Mensagens de lote em uma transação
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: be9661525c960ae558d21b05781007b81b8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185447"
---
# <a name="batching-messages-in-a-transaction"></a>Mensagens de lote em uma transação
Os aplicativos enfileirados usam transações para garantir a correção e a entrega confiável das mensagens. As transações, no entanto, são operações caras e podem reduzir drasticamente o throughput de mensagens. Uma maneira de melhorar o throughput de mensagens é ter um aplicativo lido e processar várias mensagens dentro de uma única transação. A troca é entre desempenho e recuperação: à medida que o número de mensagens em um lote aumenta, também aumenta a quantidade de trabalho de recuperação que é necessário se as transações forem revertidas. É importante notar a diferença entre o loteamento de mensagens em uma transação e sessões. Uma *sessão* é um agrupamento de mensagens relacionadas que são processadas por um único aplicativo e comprometidas como uma única unidade. As sessões são geralmente usadas quando um grupo de mensagens relacionadas deve ser processada em conjunto. Um exemplo disso é um site de compras online. Os lotes são *usados* para processar várias mensagens não relacionadas de uma forma que aumenta o throughput de mensagens. Para obter mais informações sobre as sessões, consulte [Agrupamento de Mensagens Enfileiradas em uma Sessão](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md). As mensagens em um lote também são processadas por um único aplicativo e comprometidas como uma única unidade, mas pode não haver relação entre as mensagens no lote. O loteamento de mensagens em uma transação é uma otimização que não altera a forma como o aplicativo é executado.  
  
## <a name="entering-batching-mode"></a>Entrando no modo de loteamento  
 O <xref:System.ServiceModel.Description.TransactedBatchingBehavior> comportamento do ponto final controla o loteamento. Adicionar esse comportamento de ponto final a um ponto final de serviço diz ao Windows Communication Foundation (WCF) para em lote de mensagens em uma transação. Nem todas as mensagens exigem uma transação, portanto, apenas as mensagens que requerem uma `TransactionScopeRequired`  =  `true` `TransactionAutoComplete`  =  `true` transação são colocadas em um lote, e apenas mensagens enviadas de operações marcadas com e são consideradas para um lote. Se todas as operações do `TransactionScopeRequired`  =  `false` `TransactionAutoComplete`  =  `false`contrato de serviço forem marcadas com e , então o modo de loteamento nunca será inserido.  
  
## <a name="committing-a-transaction"></a>Confirmando uma transação  
 Uma transação em lote é cometida com base no seguinte:  
  
- `MaxBatchSize`. Uma propriedade <xref:System.ServiceModel.Description.TransactedBatchingBehavior> do comportamento. Esta propriedade determina o número máximo de mensagens que são colocadas em um lote. Quando esse número é atingido, o lote é comprometido. Este é o valor não é um limite rigoroso, é possível cometer um lote antes de receber esse número de mensagens.  
  
- `Transaction Timeout`. Depois que 80% do tempo de saída da transação é decorrido, o lote é comprometido e um novo lote é criado. Isso significa que se 20% ou menos do tempo dado para uma transação ser concluída, o lote será comprometido.  
  
- `TransactionScopeRequired`. Ao processar um lote de mensagens, se `TransactionScopeRequired`  =  `false`o WCF encontrar um que tenha, ele compromete o `TransactionScopeRequired`  =  `true` `TransactionAutoComplete`  =  `true`lote e reabre um novo lote no recebimento da primeira mensagem com e .  
  
- Se não houver mais mensagens na fila, o lote atual `MaxBatchSize` será comprometido, mesmo que o lote não tenha sido atingido ou 80% do tempo de intervalo da transação não tenha transcorrido.  
  
## <a name="leaving-batching-mode"></a>Deixando o modo de loteamento  
 Se uma mensagem em um lote fizer com que a transação aborte, ocorrerão as seguintes etapas:  
  
1. Todo o lote de mensagens é revertido.  
  
2. As mensagens são lidas uma de cada vez até que o número de mensagens lidas exceda o dobro do tamanho máximo do lote.  
  
3. O modo de lote é reinserido.  
  
## <a name="choosing-the-batch-size"></a>Escolhendo o tamanho do lote  
 O tamanho de um lote depende do aplicativo. O método empírico é a melhor maneira de chegar a um tamanho de lote ideal para a aplicação. É importante lembrar ao escolher um tamanho de lote para escolher o tamanho de acordo com o modelo real de implantação do seu aplicativo. Por exemplo, ao implantar o aplicativo, se você precisar de um servidor SQL em uma máquina remota e uma transação que abrange a fila e o servidor SQL, então o tamanho do lote é melhor determinado executando essa configuração exata.  
  
## <a name="concurrency-and-batching"></a>Simultâneo e Loteamento  
 Para aumentar o throughput, você também pode ter muitos lotes executados simultaneamente. Ao `ConcurrencyMode.Multiple` `ServiceBehaviorAttribute`configurar, você habilita o loteamento simultâneo.  
  
 *O estrangulamento do* serviço é um comportamento de serviço que é usado para indicar quantas chamadas simultâneas máximas podem ser feitas no serviço. Quando usado com loteamento, isso é interpretado como quantos lotes simultâneos podem ser executados. Se o estrangulamento do serviço não estiver definido, o WCF será padrão das chamadas máximas simultâneas para 16. Assim, se o comportamento de loteamento foi adicionado por padrão, um máximo de 16 lotes podem estar ativos ao mesmo tempo. É melhor ajustar o serviço de estrangulamento e loteamento com base na sua capacidade. Por exemplo, se a fila tiver 100 mensagens e um lote de 20 for desejado, ter as chamadas simultâneas máximas definidas para 16 não é útil porque, dependendo do throughput, 16 transações podem estar ativas, semelhante a não ter o lote ligado. Portanto, ao ajustar o desempenho, não possuem loteamento simultâneo ou possuem loteamento simultâneo com o tamanho correto do acelerador de serviço.  
  
## <a name="batching-and-multiple-endpoints"></a>Loteamento e vários pontos finais  
 Um ponto final é composto por um endereço e um contrato. Pode haver vários pontos finais que compartilham a mesma vinculação. É possível que dois pontos finais compartilhem a mesma vinculação e ouçam uri (Uniform Resource Identifier, identificador de recursos uniformes) ou endereço de fila. Se dois pontos finais estiverem sendo lidos na mesma fila e o comportamento de loteamento transacionado for adicionado a ambos os pontos finais, pode surgir um conflito nos tamanhos de lote especificados. Isso é resolvido implementando o lote usando o tamanho mínimo do lote especificado entre os dois comportamentos de lote ação transacionada. Neste cenário, se um dos pontos finais não especificar o lote amento transacionado, ambos os pontos finais não usariam o loteamento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir `TransactedBatchingBehavior` mostra como especificar o arquivo em uma configuração.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 O exemplo a seguir <xref:System.ServiceModel.Description.TransactedBatchingBehavior> mostra como especificar o código em.  
  
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
  
## <a name="see-also"></a>Confira também

- [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
