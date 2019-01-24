---
title: Serviços unidirecionais
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: ad285b5a0fa37867b1b80b3d7293a976fbd12c61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527790"
---
# <a name="one-way-services"></a>Serviços unidirecionais
O comportamento padrão de uma operação de serviço é o padrão de solicitação-resposta. Em um padrão de solicitação-resposta, o cliente aguarda a mensagem de resposta, mesmo se a operação de serviço é representada no código como um `void` método. Com uma operação unidirecional, apenas uma mensagem é transmitida. O receptor não envia uma mensagem de resposta, nem faz o remetente espera um.  
  
 Use o padrão de design unidirecional:  
  
-   Quando o cliente deve chamar as operações e não é afetado pelo resultado da operação no nível da operação.  
  
-   Ao usar o <xref:System.ServiceModel.NetMsmqBinding> ou o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> classe. (Para obter mais informações sobre esse cenário, consulte [filas no WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).)  
  
 Quando uma operação é unidirecional, não há nenhuma mensagem de resposta para transmitir informações de erro para o cliente. Você pode detectar condições de erro usando os recursos da associação subjacente, como sessões confiáveis, ou criando um contrato de serviço duplex que usa duas operações unidirecionais — um contrato unidirecional do cliente para o serviço para chamar a operação de serviço e outro unidirecional de contrato entre o serviço e o cliente para que o serviço possa enviar falhas back para o cliente usando um retorno de chamada que implementa o cliente.  
  
 Para criar um contrato de serviço unidirecional, definir seu contrato de serviço, se aplicam a <xref:System.ServiceModel.OperationContractAttribute> de classe para cada operação e defina o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade `true`, conforme mostrado no código de exemplo a seguir.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 Para obter um exemplo completo, consulte o [unidirecional](../../../../docs/framework/wcf/samples/one-way.md) exemplo.  
  
## <a name="clients-blocking-with-one-way-operations"></a>Clientes de bloqueio com operações unidirecionais  
 É importante perceber que enquanto alguns aplicativos unidirecionais retornam assim que os dados de saída são gravados para a conexão de rede, em vários cenários de implementação de uma associação ou de um serviço pode fazer com que um cliente WCF para bloquear usando operações unidirecionais. Em aplicativos de cliente do WCF, o objeto de cliente do WCF não retorna até que os dados de saída tem sido gravados para a conexão de rede. Isso é verdadeiro para todos os padrões de troca de mensagem, incluindo operações unidirecionais; Isso significa que qualquer problema ao gravar que os dados para o transporte impede que o cliente retornando. Dependendo do problema, o resultado poderia ser uma exceção ou um atraso no envio de mensagens para o serviço.  
  
 Por exemplo, se o transporte não é possível localizar o ponto de extremidade, um <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> exceção é lançada sem atraso. No entanto, também é possível que o serviço não é possível ler os dados de transmissão, por algum motivo, o que impede que o transporte de cliente a operação de envio de retornar. Nesses casos, se o <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> período em que o transporte de cliente associação for excedida, uma <xref:System.TimeoutException?displayProperty=nameWithType> é lançada — mas não até que o período de tempo limite foi excedido. Também é possível acionar muitas mensagens em um serviço que o serviço não pode processá-las após um determinado ponto. Nesse caso, também, os blocos de cliente unidirecional até que o serviço pode processar as mensagens ou até que uma exceção é lançada.  
  
 Outra variação é a situação na qual o serviço <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> estiver definida como <xref:System.ServiceModel.ConcurrencyMode.Single> e a associação usa sessões. Nesse caso, o dispatcher impõe ordenação de mensagens de entrada (um requisito de sessões), que impede que as mensagens subsequentes sejam lidas fora da rede até que o serviço processou a mensagem anterior para a sessão. Novamente, os blocos de cliente, mas se uma exceção ocorre depende se o serviço é capaz de processar os dados de espera antes das configurações de tempo limite no cliente.  
  
 Você pode atenuar alguns desse problema com a inserção de um buffer entre o objeto de cliente e a operação de envio de transporte de cliente. Por exemplo, usando chamadas assíncronas ou usando uma fila de mensagens na memória pode habilitar o objeto de cliente retornar rapidamente. As duas abordagens podem aumentar a funcionalidade, mas o tamanho do pool de threads e a fila de mensagens ainda impor limites.  
  
 É recomendável, em vez disso, que você examine os vários controles no serviço, bem como no cliente e, em seguida, testar seus cenários de aplicativo para determinar a melhor configuração em ambos os lados. Por exemplo, se o uso de sessões está bloqueando o processamento de mensagens em seu serviço, você pode definir as <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade para <xref:System.ServiceModel.InstanceContextMode.PerCall> para que cada mensagem pode ser processada por uma instância de serviço diferente e definir o <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> para <xref:System.ServiceModel.ConcurrencyMode.Multiple> para permitir que mais de um thread enviar mensagens por vez. Outra abordagem é aumentar as cotas de leitura das associações de serviço e cliente.  
  
## <a name="see-also"></a>Consulte também
- [Unidirecional](../../../../docs/framework/wcf/samples/one-way.md)
