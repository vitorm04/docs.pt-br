---
title: Configuração de transação de ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: e8c8c9ebff259ccd991768afb8cdf9925a66aad0
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141618"
---
# <a name="servicemodel-transaction-configuration"></a>Configuração de transação de ServiceModel
Windows Communication Foundation (WCF) fornece três atributos para configurar transações para um serviço: `transactionFlow`, `transactionProtocol`e `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Configurando o transactionFlow  
 A maioria das associações predefinidas que o WCF fornece contém os atributos `transactionFlow` e `transactionProtocol`, para que você possa configurar a associação para aceitar transações de entrada para um ponto de extremidade específico usando um protocolo de fluxo de transação específico. Além disso, você pode usar o elemento `transactionFlow` e seu atributo `transactionProtocol` para criar sua própria associação personalizada. Para obter mais informações sobre como definir os elementos de configuração, consulte [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) e o [esquema de configuração do WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 O atributo `transactionFlow` especifica se o fluxo de transações está habilitado para pontos de extremidade de serviço que usam a associação.  
  
## <a name="configuring-transactionprotocol"></a>Configurando o transactionProtocol  
 O atributo `transactionProtocol` especifica o protocolo de transação a ser usado com pontos de extremidade de serviço que usam a associação.  
  
 Veja a seguir um exemplo de uma seção de configuração que configura a associação especificada para dar suporte ao fluxo de transações, bem como a usar o protocolo WS-AtomicTransaction.  
  
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
  
## <a name="configuring-transactiontimeout"></a>Configurando o transactionTimeout  
 Você pode configurar o atributo `transactionTimeout` para o serviço WCF no elemento `behavior` do arquivo de configuração. O código a seguir demonstra como fazer isso.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 O atributo `transactionTimeout` especifica o período de tempo no qual uma nova transação criada no serviço deve ser concluída. Ele é usado como o tempo limite de <xref:System.Transactions.TransactionScope> para qualquer operação que estabelece uma nova transação e, se <xref:System.ServiceModel.OperationBehaviorAttribute> for aplicado, a propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> será definida como `true`.  
  
 O tempo limite especifica a duração do tempo desde a criação da transação até a conclusão da fase 1 no protocolo de confirmação de duas fases.  
  
 Se esse atributo for definido em uma seção de configuração de `service`, você deverá aplicar pelo menos um método do serviço correspondente com <xref:System.ServiceModel.OperationBehaviorAttribute>, no qual a propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> está definida como `true`.  
  
 Observe que o valor de tempo limite usado é o valor menor entre esse `transactionTimeout` definição de configuração e qualquer propriedade de <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.  
  
## <a name="see-also"></a>Consulte também

- [> de associação de \<](../../configure-apps/file-schema/wcf/bindings.md)
- [Esquema de configuração do WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
