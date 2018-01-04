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
ms.workload: dotnet
ms.openlocfilehash: 650f34c37917a7f7ce407df1a3af42d177593c33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="281c2-102">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="281c2-102">ServiceModel Transaction Configuration</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="281c2-103">fornece três atributos para configurar transações para um serviço: `transactionFlow`, `transactionProtocol`, e `transactionTimeout`.</span><span class="sxs-lookup"><span data-stu-id="281c2-103"> provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="281c2-104">Configurando transactionFlow</span><span class="sxs-lookup"><span data-stu-id="281c2-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="281c2-105">A maioria das associações predefinidas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece contêm o `transactionFlow` e `transactionProtocol` atributos, para que você possa configurar a associação para aceitar as transações de entrada para um ponto de extremidade específico usando um protocolo de fluxo de transação específica.</span><span class="sxs-lookup"><span data-stu-id="281c2-105">Most of the predefined bindings [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="281c2-106">Além disso, você pode usar o `transactionFlow` elemento e seu `transactionProtocol` atributo para criar sua própria associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="281c2-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="281c2-107">definir os elementos de configuração, consulte [ \<associação >](../../../../docs/framework/misc/binding.md) e [esquema de configuração do WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="281c2-107"> setting the configuration elements, see [\<binding>](../../../../docs/framework/misc/binding.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="281c2-108">O `transactionFlow` atributo especifica se o fluxo de transações está habilitado para pontos de extremidade de serviço que usam a associação.</span><span class="sxs-lookup"><span data-stu-id="281c2-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="281c2-109">Configurando transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="281c2-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="281c2-110">O `transactionProtocol` atributo especifica o protocolo de transação a ser usado com pontos de extremidade de serviço que usam a associação.</span><span class="sxs-lookup"><span data-stu-id="281c2-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="281c2-111">Este é um exemplo de uma seção de configuração que configura a associação especificada para dar suporte ao fluxo de transações, bem como um uso do protocolo WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="281c2-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="281c2-112">Configurando transactionTimeout</span><span class="sxs-lookup"><span data-stu-id="281c2-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="281c2-113">Você pode configurar o `transactionTimeout` atributo seu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço o `behavior` elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="281c2-113">You can configure the `transactionTimeout` attribute for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="281c2-114">O código a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="281c2-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="281c2-115">O `transactionTimeout` atributo especifica o período de tempo dentro do qual deve concluir uma nova transação criada no serviço.</span><span class="sxs-lookup"><span data-stu-id="281c2-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="281c2-116">Ele é usado como o <xref:System.Transactions.TransactionScope> tempo limite para qualquer operação que estabelece uma nova transação, e se <xref:System.ServiceModel.OperationBehaviorAttribute> for aplicada, o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> está definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="281c2-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="281c2-117">O tempo limite Especifica a duração de tempo desde a criação da transação para a conclusão da fase 1 no protocolo de confirmação de duas fases.</span><span class="sxs-lookup"><span data-stu-id="281c2-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="281c2-118">Se esse atributo é definido dentro de um `service` seção de configuração, você deve aplicar pelo menos um método do serviço correspondente com <xref:System.ServiceModel.OperationBehaviorAttribute>, no qual o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> está definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="281c2-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="281c2-119">Observe que o valor de tempo limite usado é o menor valor entre esta `transactionTimeout` configuração e qualquer <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="281c2-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="281c2-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="281c2-120">See Also</span></span>  
 [<span data-ttu-id="281c2-121">\<associação ></span><span class="sxs-lookup"><span data-stu-id="281c2-121">\<binding></span></span>](../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="281c2-122">Esquema de configuração do WCF</span><span class="sxs-lookup"><span data-stu-id="281c2-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
