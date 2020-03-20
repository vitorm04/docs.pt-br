---
title: Especificando a execução do cliente- Comportamento do tempo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: f9c22d25bedc36b3515538a8785b488aaa547990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143233"
---
# <a name="specifying-client-run-time-behavior"></a>Especificando a execução do cliente- Comportamento do tempo
Os clientes da Windows Communication Foundation (WCF), como os serviços da Windows Communication Foundation (WCF), podem ser configurados para modificar o comportamento de tempo de execução para se adequar ao aplicativo cliente. Três atributos estão disponíveis para especificar o comportamento de tempo de execução do cliente. Objetos de retorno de <xref:System.ServiceModel.CallbackBehaviorAttribute> chamada <xref:System.ServiceModel.Description.CallbackDebugBehavior> do cliente Duplex podem usar os atributos e atributos para modificar seu comportamento de tempo de execução. O outro <xref:System.ServiceModel.Description.ClientViaBehavior>atributo, pode ser usado para separar o destino lógico do destino imediato da rede. Além disso, os tipos de retorno de chamada do cliente duplex podem usar alguns dos comportamentos do lado do serviço. Para obter mais informações, consulte [Especificando o comportamento em tempo de execução do serviço](specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Usando o CallbackBehaviorAttribute  
 Você pode configurar ou estender o comportamento de execução de uma <xref:System.ServiceModel.CallbackBehaviorAttribute> implementação de contrato de retorno de chamada em um aplicativo cliente usando a classe. Este atributo executa uma função semelhante <xref:System.ServiceModel.ServiceBehaviorAttribute> para a classe de retorno de chamada como a classe, com exceção do comportamento de instancing e configurações de transação.  
  
 A <xref:System.ServiceModel.CallbackBehaviorAttribute> classe deve ser aplicada à classe que implementa o contrato de retorno de chamada. Se aplicado a uma implementação de <xref:System.InvalidOperationException> contrato não duplex, uma exceção é lançada em tempo de execução. O exemplo de <xref:System.ServiceModel.CallbackBehaviorAttribute> código a seguir mostra uma <xref:System.Threading.SynchronizationContext> classe em um objeto de <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> retorno de chamada que <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> usa o objeto <xref:System.ServiceModel.FaultException> para determinar o segmento a ser marshal, a propriedade para impor a validação de mensagens e a propriedade para retornar exceções como objetos ao serviço para fins de depuração.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Usando callbackDebugBehavior para ativar o fluxo de informações de exceção gerenciadas  
 Você pode habilitar o fluxo de informações de exceção gerenciadas em um objeto <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> de `true` retorno de chamada do cliente de volta ao serviço para fins de depuração, definindo a propriedade para programaticamente ou a partir de um arquivo de configuração de aplicativo.  
  
 Devolver informações gerenciadas de exceção aos serviços pode ser um risco à segurança, pois detalhes de exceção expõem informações sobre a implementação interna do cliente que serviços não autorizados poderiam usar. Além disso, <xref:System.ServiceModel.Description.CallbackDebugBehavior> embora as propriedades também possam ser definidas programáticamente, pode ser fácil esquecer de desativar <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> ao implantar.  
  
 Devido aos problemas de segurança envolvidos, é fortemente recomendável que:  
  
- Você usa um arquivo de configuração <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> de `true`aplicativo para definir o valor da propriedade para .  
  
- Você faz isso apenas em cenários controlados de depuração.  
  
 O exemplo de código a seguir mostra um arquivo de configuração do cliente que instrui o WCF a retornar informações de exceção gerenciadas de um objeto de retorno de chamada do cliente em mensagens SOAP.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  

## <a name="using-the-clientviabehavior-behavior"></a>Usando o comportamento do ClientViaBehavior  
 Você pode <xref:System.ServiceModel.Description.ClientViaBehavior> usar o comportamento para especificar o Identificador de Recursos Uniformes para o qual o canal de transporte deve ser criado. Use esse comportamento quando o destino imediato da rede não for o processador pretendido da mensagem. Isso permite conversas de vários saltos quando o aplicativo de chamada não `Via` sabe necessariamente o destino final ou quando o cabeçalho de destino não é um endereço.  
  
## <a name="see-also"></a>Confira também

- [Especificando o comportamento em tempo de execução do serviço](specifying-service-run-time-behavior.md)
