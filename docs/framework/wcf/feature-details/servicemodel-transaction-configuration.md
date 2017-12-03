---
title: "Configuração de transação de ServiceModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef1d8a9e749c06701aa0a187f81b5b345518c07b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="servicemodel-transaction-configuration"></a>Configuração de transação de ServiceModel
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]fornece três atributos para configurar transações para um serviço: `transactionFlow`, `transactionProtocol`, e `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Configurando transactionFlow  
 A maioria das associações predefinidas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece contêm o `transactionFlow` e `transactionProtocol` atributos, para que você possa configurar a associação para aceitar as transações de entrada para um ponto de extremidade específico usando um protocolo de fluxo de transação específica. Além disso, você pode usar o `transactionFlow` elemento e seu `transactionProtocol` atributo para criar sua própria associação personalizada. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]definir os elementos de configuração, consulte [ \<associação >](../../../../docs/framework/misc/binding.md) e [esquema de configuração do WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 O `transactionFlow` atributo especifica se o fluxo de transações está habilitado para pontos de extremidade de serviço que usam a associação.  
  
## <a name="configuring-transactionprotocol"></a>Configurando transactionProtocol  
 O `transactionProtocol` atributo especifica o protocolo de transação a ser usado com pontos de extremidade de serviço que usam a associação.  
  
 Este é um exemplo de uma seção de configuração que configura a associação especificada para dar suporte ao fluxo de transações, bem como um uso do protocolo WS-AtomicTransaction.  
  
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
 Você pode configurar o `transactionTimeout` atributo seu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço o `behavior` elemento do arquivo de configuração. O código a seguir demonstra como fazer isso.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 O `transactionTimeout` atributo especifica o período de tempo dentro do qual deve concluir uma nova transação criada no serviço. Ele é usado como o <xref:System.Transactions.TransactionScope> tempo limite para qualquer operação que estabelece uma nova transação, e se <xref:System.ServiceModel.OperationBehaviorAttribute> for aplicada, o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> está definida como `true`.  
  
 O tempo limite Especifica a duração de tempo desde a criação da transação para a conclusão da fase 1 no protocolo de confirmação de duas fases.  
  
 Se esse atributo é definido dentro de um `service` seção de configuração, você deve aplicar pelo menos um método do serviço correspondente com <xref:System.ServiceModel.OperationBehaviorAttribute>, no qual o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> está definida como `true`.  
  
 Observe que o valor de tempo limite usado é o menor valor entre esta `transactionTimeout` configuração e qualquer <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [\<associação >](../../../../docs/framework/misc/binding.md)  
 [Esquema de configuração do WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
