---
title: Especificando a execução do cliente- Comportamento do tempo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: 738aadf93b726569eb59fc281cca2e482bace0bc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645178"
---
# <a name="specifying-client-run-time-behavior"></a>Especificando a execução do cliente- Comportamento do tempo
Os clientes do Windows Communication Foundation (WCF), assim como serviços do Windows Communication Foundation (WCF), podem ser configurados para modificar o comportamento de tempo de execução de acordo com o aplicativo cliente. Três atributos estão disponíveis para especificar o comportamento de tempo de execução do cliente. Objetos de retorno de chamada duplex cliente podem usar o <xref:System.ServiceModel.CallbackBehaviorAttribute> e <xref:System.ServiceModel.Description.CallbackDebugBehavior> atributos para modificar seu comportamento de tempo de execução. O atributo, <xref:System.ServiceModel.Description.ClientViaBehavior>, pode ser usado para separar o destino lógico de destino de rede imediato. Além disso, tipos de retorno de chamada duplex cliente podem usar alguns dos comportamentos no lado do serviço. Para obter mais informações, consulte [especificando comportamento de tempo de execução do serviço](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Usando o CallbackBehaviorAttribute  
 Você pode configurar ou estender o comportamento de execução de uma implementação de contrato de retorno de chamada em um aplicativo cliente usando o <xref:System.ServiceModel.CallbackBehaviorAttribute> classe. Esse atributo executa uma função semelhante para a classe de retorno de chamada como o <xref:System.ServiceModel.ServiceBehaviorAttribute> classe, com exceção de configurações de comportamento e a transação de instanciação.  
  
 O <xref:System.ServiceModel.CallbackBehaviorAttribute> classe deve ser aplicado à classe que implementa o contrato de retorno de chamada. Se aplicado a uma implementação de contrato nonduplex, um <xref:System.InvalidOperationException> exceção é gerada em tempo de execução. O seguinte exemplo de código mostra uma <xref:System.ServiceModel.CallbackBehaviorAttribute> classe em um objeto de retorno de chamada que usa o <xref:System.Threading.SynchronizationContext> objeto para determinar o thread para realizar marshaling para, o <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> propriedade para impor a validação de mensagem e o <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> propriedade para retornar exceções como <xref:System.ServiceModel.FaultException> objetos para o serviço para fins de depuração.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Usando CallbackDebugBehavior para habilitar o fluxo de informações de exceção gerenciada  
 Você pode habilitar o fluxo de informações de exceção gerenciada em um objeto de retorno de chamada do cliente para o serviço para fins de depuração, definindo a <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> propriedade para `true` de arquivos por meio de programação ou de uma configuração de aplicativo.  
  
 Retornando informações de exceção gerenciada serviços podem ser um risco à segurança porque os detalhes da exceção expõem informações sobre o cliente interno implementação que não autorizado a serviços pode usar. Além disso, embora o <xref:System.ServiceModel.Description.CallbackDebugBehavior> propriedades também podem ser definidas programaticamente, ele pode ser fácil esquecer de desabilitar <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> durante a implantação.  
  
 Devido a problemas de segurança envolvida, é altamente recomendável que:  
  
- Usar um arquivo de configuração de aplicativo para definir o valor da <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> propriedade para `true`.  
  
- Você fazer somente em cenários de depuração de controlado.  
  
 O exemplo de código a seguir mostra o arquivo de configuração que instrui o WCF para retornar informações de exceção gerenciada de um cliente objeto de retorno de chamada em mensagens SOAP de um cliente.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>Usando o comportamento de ClientViaBehavior  
 Você pode usar o <xref:System.ServiceModel.Description.ClientViaBehavior> comportamento para especificar o Uniform Resource Identifier para o qual o canal de transporte deve ser criado. Use esse comportamento quando o destino de rede imediato não é o processador pretendido da mensagem. Isso permite que vários saltos conversas quando o aplicativo de chamada não sabe, necessariamente, o destino final ou quando o destino `Via` cabeçalho não é um endereço.  
  
## <a name="see-also"></a>Consulte também

- [Especificando o comportamento em tempo de execução do serviço](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
