---
title: Especificando a execução do cliente- Comportamento do tempo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: 075f62526ace1ac49d12e1bdec39d8df4b0a3ff1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321405"
---
# <a name="specifying-client-run-time-behavior"></a>Especificando a execução do cliente- Comportamento do tempo
Os clientes do Windows Communication Foundation (WCF), como os serviços do Windows Communication Foundation (WCF), podem ser configurados para modificar o comportamento de tempo de execução para se adequar ao aplicativo cliente. Três atributos estão disponíveis para especificar o comportamento de tempo de execução do cliente. Os objetos de retorno de chamada do cliente duplex podem usar os atributos <xref:System.ServiceModel.CallbackBehaviorAttribute> e <xref:System.ServiceModel.Description.CallbackDebugBehavior> para modificar o comportamento de tempo de execução. O outro atributo, <xref:System.ServiceModel.Description.ClientViaBehavior>, pode ser usado para separar o destino lógico do destino de rede imediato. Além disso, os tipos de retorno de chamada do cliente duplex podem usar alguns dos comportamentos do lado do serviço. Para obter mais informações, consulte [especificando o comportamento de tempo de execução do serviço](specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Usando o CallbackBehaviorAttribute  
 Você pode configurar ou estender o comportamento de execução de uma implementação de contrato de retorno de chamada em um aplicativo cliente usando a classe <xref:System.ServiceModel.CallbackBehaviorAttribute>. Esse atributo executa uma função semelhante para a classe de retorno de chamada como a classe <xref:System.ServiceModel.ServiceBehaviorAttribute>, com exceção das configurações de transação e comportamento de instanciação.  
  
 A classe <xref:System.ServiceModel.CallbackBehaviorAttribute> deve ser aplicada à classe que implementa o contrato de retorno de chamada. Se aplicado a uma implementação de contrato não duplex, uma exceção <xref:System.InvalidOperationException> será lançada em tempo de execução. O exemplo de código a seguir mostra uma classe <xref:System.ServiceModel.CallbackBehaviorAttribute> em um objeto de retorno de chamada que usa o objeto <xref:System.Threading.SynchronizationContext> para determinar o thread para o qual realizar marshaling, a propriedade <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> para impor a validação de mensagem e a propriedade <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> para retornar exceções como objetos <xref:System.ServiceModel.FaultException> para o serviço para fins de depuração.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Usando o CallbackDebugBehavior para habilitar o fluxo de informações de exceção gerenciada  
 Você pode habilitar o fluxo de informações de exceção gerenciada em um objeto de retorno de chamada de cliente para o serviço para fins de depuração definindo a propriedade <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> como `true` programaticamente ou de um arquivo de configuração de aplicativo.  
  
 Retornar informações de exceção gerenciada aos serviços pode ser um risco de segurança, pois os detalhes da exceção expõem informações sobre a implementação interna do cliente que os serviços não autorizados podem usar. Além disso, embora as propriedades <xref:System.ServiceModel.Description.CallbackDebugBehavior> também possam ser definidas programaticamente, pode ser fácil esquecer de desabilitar <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> durante a implantação.  
  
 Devido aos problemas de segurança envolvidos, é altamente recomendável que:  
  
- Você usa um arquivo de configuração de aplicativo para definir o valor da propriedade <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> como `true`.  
  
- Você só faz isso em cenários de depuração controlados.  
  
 O exemplo de código a seguir mostra um arquivo de configuração de cliente que instrui o WCF a retornar informações de exceção gerenciadas de um objeto de retorno de chamada de cliente em mensagens SOAP.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>Usando o comportamento ClientViaBehavior  
 Você pode usar o comportamento <xref:System.ServiceModel.Description.ClientViaBehavior> para especificar o Uniform Resource Identifier para o qual o canal de transporte deve ser criado. Use esse comportamento quando o destino de rede imediato não for o processador pretendido da mensagem. Isso permite conversas de salto múltiplo quando o aplicativo de chamada não conhece necessariamente o destino final ou quando o cabeçalho `Via` de destino não é um endereço.  
  
## <a name="see-also"></a>Consulte também

- [Especificando o comportamento em tempo de execução do serviço](specifying-service-run-time-behavior.md)
