---
title: Serviços unidirecionais
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: 03efc27f2ba54ca22f03e3ece84770fe0dcadbb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="one-way-services"></a>Serviços unidirecionais
O comportamento padrão de uma operação de serviço é o padrão de solicitação-resposta. Em um padrão de solicitação-resposta, o cliente aguarda a mensagem de resposta, mesmo se a operação de serviço é representada no código como um `void` método. Com uma operação unidirecional, somente uma mensagem é transmitida. O receptor não envia uma mensagem de resposta, nem o remetente esperado um.  
  
 Use o padrão de design unidirecional:  
  
-   Quando o cliente deve chamar as operações e não é afetado pelo resultado da operação no nível da operação.  
  
-   Ao usar o <xref:System.ServiceModel.NetMsmqBinding> ou <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> classe. (Para obter mais informações sobre esse cenário, consulte [filas no WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).)  
  
 Quando uma operação é unidirecional, não há nenhuma mensagem de resposta para transmitir informações de erro para o cliente. Você pode detectar condições de erro usando recursos de associação subjacente, como sessões confiáveis, ou criando um contrato de serviço duplex que usa duas operações unidirecionais — um contrato unidirecional do cliente para o serviço para chamar a operação de serviço e outro unidirecional entre o cliente e o serviço de contrato de forma que o serviço pode enviar falhas de backup para o cliente usando um retorno de chamada que implementa o cliente.  
  
 Para criar um contrato de serviço unidirecional, definir o contrato de serviço, aplicar o <xref:System.ServiceModel.OperationContractAttribute> de classe para cada operação e defina o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade `true`, conforme mostrado no código de exemplo a seguir.  
  
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
 É importante observar que embora alguns aplicativos unidirecionais retornam assim que os dados de saída são gravados para a conexão de rede, em diversos cenários de implementação de uma associação ou de um serviço pode causar um cliente WCF bloquear usando operações unidirecionais. Em aplicativos de cliente do WCF, o objeto de cliente do WCF não retorna até que os dados de saída foram gravados para a conexão de rede. Isso é verdadeiro para todos os padrões de troca de mensagens, incluindo operações unidirecionais; Isso significa que qualquer problema ao gravar que os dados para o transporte impede que o cliente retornando. Dependendo do problema, o resultado seria uma exceção ou um atraso no envio de mensagens para o serviço.  
  
 Por exemplo, se o transporte não é possível localizar o ponto de extremidade, um <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> exceção sem muito atraso. No entanto, também é possível que o serviço é não é possível ler os dados na rede por algum motivo, o que impede que o transporte de cliente a operação de envio de retorno. Nesses casos, se o <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> período em que o transporte de cliente associação for excedida, um <xref:System.TimeoutException?displayProperty=nameWithType> é lançada, mas não até que o período de tempo limite foi excedido. Também é possível acionar muitas mensagens em um serviço que o serviço não pode processá-las após um certo ponto. Nesse caso, também, os blocos de cliente unidirecional até que o serviço pode processar as mensagens ou até que uma exceção é lançada.  
  
 Outra variação é a situação na qual o serviço <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> está definida como <xref:System.ServiceModel.ConcurrencyMode.Single> e a associação usa sessões. Nesse caso, o dispatcher impõe ordenação de mensagens de entrada (um requisito de sessões), que impede que as mensagens subsequentes sejam lidas fora da rede até que o serviço processou a mensagem anterior para a sessão. Novamente, os blocos de cliente, mas se uma exceção ocorre depende se o serviço é capaz de processar os dados de espera antes das configurações de tempo limite no cliente.  
  
 Você pode reduzir alguns desse problema, inserindo um buffer entre o objeto de cliente e a operação de envio de transporte de cliente. Por exemplo, usando chamadas assíncronas ou uma fila de mensagens na memória pode habilitar o objeto cliente retornar rapidamente. Ambas as abordagens podem aumentar a funcionalidade, mas o tamanho do pool de threads e a fila de mensagens ainda Imponha limites.  
  
 É recomendável, em vez disso, que você examine os vários controles no serviço, bem como no cliente e, em seguida, testar os cenários de aplicativo para determinar a melhor configuração em ambos os lados. Por exemplo, se o uso de sessões está bloqueando o processamento de mensagens em seu serviço, você pode definir o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade <xref:System.ServiceModel.InstanceContextMode.PerCall> para que cada mensagem pode ser processada por uma instância de serviço diferente e definir o <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> para <xref:System.ServiceModel.ConcurrencyMode.Multiple> para permitir que mais de um thread enviar mensagens de cada vez. Outra abordagem é aumentar as cotas de leitura das ligações de serviço e cliente.  
  
## <a name="see-also"></a>Consulte também  
 [Unidirecional](../../../../docs/framework/wcf/samples/one-way.md)
