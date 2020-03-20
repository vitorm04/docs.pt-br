---
title: Configuração de transação de ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 79772d19ddaec041aa1fac936b9951731507b6e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184460"
---
# <a name="servicemodel-transaction-configuration"></a>Configuração de transação de ServiceModel
A Windows Communication Foundation (WCF) fornece três atributos `transactionFlow` `transactionProtocol`para `transactionTimeout`configurar transações para um serviço: , e .  
  
## <a name="configuring-transactionflow"></a>Configurando transactionFlow  
 A maioria das vinculações predefinidas `transactionFlow` `transactionProtocol` que o WCF fornece contém os atributos e os atributos, para que você possa configurar a vinculação para aceitar transações recebidas para um ponto final específico usando um protocolo específico de fluxo de transações. Além disso, você `transactionFlow` pode usar `transactionProtocol` o elemento e seu atributo para construir sua própria vinculação personalizada. Para obter mais informações sobre a configuração dos elementos de [ \<configuração,](../../configure-apps/file-schema/wcf/bindings.md) consulte>de vinculação e [esquema de configuração WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 O `transactionFlow` atributo especifica se o fluxo de transações está habilitado para pontos finais de serviço que usam a vinculação.  
  
## <a name="configuring-transactionprotocol"></a>Configuração de transactionProtocol  
 O `transactionProtocol` atributo especifica o protocolo de transação a ser usado com pontos finais de serviço que usam a vinculação.  
  
 A seguir, um exemplo de uma seção de configuração que configura a vinculação especificada para suportar o fluxo de transações, bem como um uso do protocolo WS-AtomicTransaction.  
  
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
  
## <a name="configuring-transactiontimeout"></a>Configurando transaçãoTimeout  
 Você pode configurar `transactionTimeout` o atributo para `behavior` o serviço WCF no elemento do arquivo de configuração. O código a seguir demonstra como fazer isso.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 O `transactionTimeout` atributo especifica o período de tempo no qual uma nova transação criada no serviço deve ser concluída. É usado como <xref:System.Transactions.TransactionScope> o tempo para qualquer operação que estabeleça <xref:System.ServiceModel.OperationBehaviorAttribute> uma nova transação, e se for aplicado, a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedade é definida como `true`.  
  
 O tempo de intervalo especifica a duração do tempo desde a criação da transação até a conclusão da fase 1 no protocolo de confirmação bifásica.  
  
 Se este atributo `service` estiver definido dentro de uma seção de <xref:System.ServiceModel.OperationBehaviorAttribute>configuração, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> você deve `true`aplicar pelo menos um método do serviço correspondente com , no qual a propriedade está definida para .  
  
 Observe que o valor de tempo de saída `transactionTimeout` usado é <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> o valor menor entre essa configuração e qualquer propriedade.  
  
## <a name="see-also"></a>Confira também

- [\<vinculação>](../../configure-apps/file-schema/wcf/bindings.md)
- [Esquema de configuração wcf](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
