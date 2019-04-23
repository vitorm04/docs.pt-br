---
title: Mensagens de lote em uma transação
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: 2d820087973e689514a0a19a7adc912f49e9d0a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310519"
---
# <a name="batching-messages-in-a-transaction"></a>Mensagens de lote em uma transação
Aplicativos em fila usam transações para garantir a correção e entrega confiável de mensagens. Transações, no entanto, são operações caras e podem reduzir drasticamente a taxa de transferência de mensagem. Uma maneira para melhorar a taxa de transferência de mensagem é ter um aplicativo de ler e processar várias mensagens em uma única transação. A compensação está entre desempenho e recuperação: conforme aumenta o número de mensagens em um lote, aumenta a quantidade de trabalho de recuperação que necessário se as transações serão revertidas. É importante observar a diferença entre o envio em lote de mensagens em uma transação e sessões. Um *sessão* é um agrupamento de mensagens relacionadas que são processados por um único aplicativo e confirmado como uma única unidade. Sessões geralmente são usadas quando um grupo de mensagens relacionadas deve ser processado em conjunto. Um exemplo disso é um site de compra online. *Lotes* são usados para processar vários, não relacionados a mensagens de forma que a taxa de transferência de mensagem aumenta. Para obter mais informações sobre as sessões, consulte [mensagens na fila de agrupamento em uma sessão](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md). Mensagens em um lote também são processadas por um único aplicativo e confirmadas como uma única unidade, mas não pode haver nenhuma relação entre as mensagens no lote. Mensagens em lote em uma transação são uma otimização que não são alterados como o aplicativo é executado.  
  
## <a name="entering-batching-mode"></a>Inserir o modo de lote  
 O <xref:System.ServiceModel.Description.TransactedBatchingBehavior> controles de comportamento de ponto de extremidade envio em lote. Adicionar esse comportamento de ponto de extremidade para um ponto de extremidade de serviço informa ao Windows Communication Foundation (WCF) para mensagens em lote em uma transação. Nem todas as mensagens exigem uma transação, portanto, apenas as mensagens que exigem uma transação são colocadas em um lote, e apenas as mensagens enviadas de operações marcadas com `TransactionScopeRequired`  =  `true` e `TransactionAutoComplete`  =  `true` são consideradas para um lote. Se todas as operações no contrato de serviço são marcadas com `TransactionScopeRequired`  =  `false` e `TransactionAutoComplete`  =  `false`, em seguida, o modo de lote nunca é inserido.  
  
## <a name="committing-a-transaction"></a>Confirmar uma transação  
 Uma transação em lote é confirmada com base no seguinte:  
  
-   `MaxBatchSize`. Uma propriedade do <xref:System.ServiceModel.Description.TransactedBatchingBehavior> comportamento. Essa propriedade determina o número máximo de mensagens que são colocados em um lote. Quando esse número for atingido, o lote será confirmado. Esse é o valor não é um limite estrito, é possível confirmar um lote antes de receber esse número de mensagens.  
  
-   `Transaction Timeout`. Depois de decorrido 80 por cento do tempo de limite da transação, o lote será confirmado e um novo lote é criado. Isso significa que se 20 por cento ou menos do tempo fornecido para a conclusão de uma transação permanece, o lote será confirmado.  
  
-   `TransactionScopeRequired`. Ao processar um lote de mensagens, se WCF encontrar um que tenha `TransactionScopeRequired`  =  `false`, ele confirma o lote e reabre um novo lote após o recebimento da primeira mensagem com `TransactionScopeRequired`  =  `true` e `TransactionAutoComplete`  = `true`.  
  
-   Se mais nenhuma mensagem existe na fila e, em seguida, o lote atual for confirmado, mesmo se o `MaxBatchSize` não tiver sido atingida ou 80 por cento do tempo de limite da transação ainda não tiver decorrido.  
  
## <a name="leaving-batching-mode"></a>Sair do modo de lote  
 Se uma mensagem em um lote faz com que a transação seja anulada, ocorrem as seguintes etapas:  
  
1. Todo o lote de mensagens é revertido.  
  
2. As mensagens são lidas uma de cada vez até que o número de mensagens lidas excede duas vezes o tamanho máximo de lote.  
  
3. Modo de lote é inserido novamente.  
  
## <a name="choosing-the-batch-size"></a>Escolhendo o tamanho do lote  
 O tamanho de um lote é dependente de aplicativo. O método empírico é a melhor maneira de chegar a um tamanho de lote ideal para o aplicativo. É importante lembrar-se ao escolher um tamanho de lote para escolher o tamanho de acordo com o modelo de implantação real do seu aplicativo. Por exemplo, ao implantar o aplicativo, se você precisar de um SQL server em um computador remoto e uma transação que abrange a fila e o SQL server, em seguida, o tamanho do lote é melhor determinado executando essa configuração exata.  
  
## <a name="concurrency-and-batching"></a>Simultaneidade e o envio em lote  
 Para aumentar a taxa de transferência, você também pode ter muitos lotes executados simultaneamente. Definindo `ConcurrencyMode.Multiple` em `ServiceBehaviorAttribute`, habilitar o envio em lote simultâneas.  
  
 *Limitação de serviço* é um comportamento de serviço que é usado para indicar o número máximo de chamadas simultâneas pode ser feito no serviço. Quando usado com o envio em lote, isso é interpretado como a muitos lotes simultâneos podem ser executados. Se a limitação do serviço não for definido, o WCF padrão é o máximo de chamadas simultâneas para 16. Assim, se o comportamento de lote foram adicionado por padrão, um máximo de 16 lotes pode ser ativo ao mesmo tempo. É melhor ajustar a limitação do serviço e o envio em lote com base em sua capacidade. Por exemplo, se a fila tem 100 mensagens e um lote de 20 for desejado, ter o máximo de chamadas simultâneas definidas como 16 não é útil porque, dependendo da taxa de transferência, 16 transações pode ser o Active Directory, semelhante a não ter o envio em lote ativado. Portanto, quando ajustar o desempenho, ou não ter o envio em lote simultâneas ou tenha simultâneas envio em lote com o tamanho de limitação de serviço correto.  
  
## <a name="batching-and-multiple-endpoints"></a>Envio em lote e vários pontos de extremidade  
 Um ponto de extremidade é composto de um endereço e um contrato. Pode haver vários pontos de extremidade que compartilham a mesma associação. É possível que dois pontos de extremidade compartilharem a mesma ligação e ouvir o identificador de recurso uniforme (URI) ou o endereço da fila. Se dois pontos de extremidade estão lendo a mesma fila e transacionado comportamento de lote é adicionado a ambos os pontos de extremidade, um conflito no lote tamanhos especificados podem surgir. Isso é resolvido com a implementação de envio em lote usando o tamanho de lote mínimo especificado entre os dois comportamentos de envio em lote transacionados. Nesse cenário, se um dos pontos de extremidade não especificar o lote transacionado, em seguida, ambos os pontos de extremidade não usaria envio em lote.  
  
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

- [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
