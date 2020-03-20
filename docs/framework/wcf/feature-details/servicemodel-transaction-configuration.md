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
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="52dda-102">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="52dda-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="52dda-103">A Windows Communication Foundation (WCF) fornece três atributos `transactionFlow` `transactionProtocol`para `transactionTimeout`configurar transações para um serviço: , e .</span><span class="sxs-lookup"><span data-stu-id="52dda-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="52dda-104">Configurando transactionFlow</span><span class="sxs-lookup"><span data-stu-id="52dda-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="52dda-105">A maioria das vinculações predefinidas `transactionFlow` `transactionProtocol` que o WCF fornece contém os atributos e os atributos, para que você possa configurar a vinculação para aceitar transações recebidas para um ponto final específico usando um protocolo específico de fluxo de transações.</span><span class="sxs-lookup"><span data-stu-id="52dda-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="52dda-106">Além disso, você `transactionFlow` pode usar `transactionProtocol` o elemento e seu atributo para construir sua própria vinculação personalizada.</span><span class="sxs-lookup"><span data-stu-id="52dda-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="52dda-107">Para obter mais informações sobre a configuração dos elementos de [ \<configuração,](../../configure-apps/file-schema/wcf/bindings.md) consulte>de vinculação e [esquema de configuração WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="52dda-107">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="52dda-108">O `transactionFlow` atributo especifica se o fluxo de transações está habilitado para pontos finais de serviço que usam a vinculação.</span><span class="sxs-lookup"><span data-stu-id="52dda-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="52dda-109">Configuração de transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="52dda-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="52dda-110">O `transactionProtocol` atributo especifica o protocolo de transação a ser usado com pontos finais de serviço que usam a vinculação.</span><span class="sxs-lookup"><span data-stu-id="52dda-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="52dda-111">A seguir, um exemplo de uma seção de configuração que configura a vinculação especificada para suportar o fluxo de transações, bem como um uso do protocolo WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="52dda-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="52dda-112">Configurando transaçãoTimeout</span><span class="sxs-lookup"><span data-stu-id="52dda-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="52dda-113">Você pode configurar `transactionTimeout` o atributo para `behavior` o serviço WCF no elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="52dda-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="52dda-114">O código a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="52dda-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="52dda-115">O `transactionTimeout` atributo especifica o período de tempo no qual uma nova transação criada no serviço deve ser concluída.</span><span class="sxs-lookup"><span data-stu-id="52dda-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="52dda-116">É usado como <xref:System.Transactions.TransactionScope> o tempo para qualquer operação que estabeleça <xref:System.ServiceModel.OperationBehaviorAttribute> uma nova transação, e se for aplicado, a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedade é definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="52dda-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="52dda-117">O tempo de intervalo especifica a duração do tempo desde a criação da transação até a conclusão da fase 1 no protocolo de confirmação bifásica.</span><span class="sxs-lookup"><span data-stu-id="52dda-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="52dda-118">Se este atributo `service` estiver definido dentro de uma seção de <xref:System.ServiceModel.OperationBehaviorAttribute>configuração, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> você deve `true`aplicar pelo menos um método do serviço correspondente com , no qual a propriedade está definida para .</span><span class="sxs-lookup"><span data-stu-id="52dda-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="52dda-119">Observe que o valor de tempo de saída `transactionTimeout` usado é <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> o valor menor entre essa configuração e qualquer propriedade.</span><span class="sxs-lookup"><span data-stu-id="52dda-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52dda-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="52dda-120">See also</span></span>

- [<span data-ttu-id="52dda-121">\<vinculação></span><span class="sxs-lookup"><span data-stu-id="52dda-121">\<binding></span></span>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="52dda-122">Esquema de configuração wcf</span><span class="sxs-lookup"><span data-stu-id="52dda-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
