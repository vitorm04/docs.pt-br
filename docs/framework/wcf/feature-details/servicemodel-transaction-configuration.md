---
title: Configuração de transação de ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: d5bb81c618e3b27df32763948dbe56c9b37995e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188963"
---
# <a name="servicemodel-transaction-configuration"></a>Configuração de transação de ServiceModel
Windows Communication Foundation (WCF) oferece três atributos para configurar transações para um serviço: `transactionFlow`, `transactionProtocol`, e `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Configurando transactionFlow  
 A maioria das associações predefinidas que contêm o WCF fornece o `transactionFlow` e `transactionProtocol` atributos, para que você possa configurar a associação para aceitar as transações de entrada para um ponto de extremidade específico usando um protocolo de fluxo de transação específica. Além disso, você pode usar o `transactionFlow` elemento e seu `transactionProtocol` atributo para criar sua própria associação personalizada. Para obter mais informações sobre como definir os elementos de configuração, consulte [ \<associação >](../../../../docs/framework/misc/binding.md) e [esquema de configuração do WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 O `transactionFlow` atributo especifica se o fluxo de transações está habilitado para pontos de extremidade de serviço que usam a associação.  
  
## <a name="configuring-transactionprotocol"></a>Configurando transactionProtocol  
 O `transactionProtocol` atributo especifica o protocolo de transação a ser usado com pontos de extremidade de serviço que usam a associação.  
  
 O exemplo a seguir é um exemplo de uma seção de configuração que configura a associação especificada para dar suporte ao fluxo de transações, bem como um, use o protocolo de WS-AtomicTransaction.  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"   
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"   
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a>Configurando transactionTimeout  
 Você pode configurar o `transactionTimeout` atributo para o serviço WCF no `behavior` elemento do arquivo de configuração. O código a seguir demonstra como fazer isso.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 O `transactionTimeout` atributo especifica o período de tempo dentro do qual uma nova transação criada no serviço deve ser concluída. Ele é usado como o <xref:System.Transactions.TransactionScope> tempo limite para qualquer operação que estabelece uma nova transação, e se <xref:System.ServiceModel.OperationBehaviorAttribute> é aplicado, o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> estiver definida como `true`.  
  
 O tempo limite Especifica a duração de tempo desde a criação da transação para a conclusão da fase 1 no protocolo 2PC.  
  
 Se esse atributo é definido dentro de um `service` seção de configuração, você deve aplicar a pelo menos um método de serviço correspondente com <xref:System.ServiceModel.OperationBehaviorAttribute>, no qual o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> estiver definida como `true`.  
  
 Observe que o valor de tempo limite usado é o menor valor entre esse `transactionTimeout` definição de configuração e qualquer <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> propriedade.  
  
## <a name="see-also"></a>Consulte também

- [\<binding>](../../../../docs/framework/misc/binding.md)
- [Esquema de configuração do WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
