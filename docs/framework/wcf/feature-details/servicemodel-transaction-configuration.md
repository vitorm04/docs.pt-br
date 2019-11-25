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
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="54f7d-102">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="54f7d-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="54f7d-103">Windows Communication Foundation (WCF) fornece três atributos para configurar transações para um serviço: `transactionFlow`, `transactionProtocol`e `transactionTimeout`.</span><span class="sxs-lookup"><span data-stu-id="54f7d-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="54f7d-104">Configurando o transactionFlow</span><span class="sxs-lookup"><span data-stu-id="54f7d-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="54f7d-105">A maioria das associações predefinidas que o WCF fornece contém os atributos `transactionFlow` e `transactionProtocol`, para que você possa configurar a associação para aceitar transações de entrada para um ponto de extremidade específico usando um protocolo de fluxo de transação específico.</span><span class="sxs-lookup"><span data-stu-id="54f7d-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="54f7d-106">Além disso, você pode usar o elemento `transactionFlow` e seu atributo `transactionProtocol` para criar sua própria associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="54f7d-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="54f7d-107">Para obter mais informações sobre como definir os elementos de configuração, consulte [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) e o [esquema de configuração do WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="54f7d-107">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="54f7d-108">O atributo `transactionFlow` especifica se o fluxo de transações está habilitado para pontos de extremidade de serviço que usam a associação.</span><span class="sxs-lookup"><span data-stu-id="54f7d-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="54f7d-109">Configurando o transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="54f7d-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="54f7d-110">O atributo `transactionProtocol` especifica o protocolo de transação a ser usado com pontos de extremidade de serviço que usam a associação.</span><span class="sxs-lookup"><span data-stu-id="54f7d-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="54f7d-111">Veja a seguir um exemplo de uma seção de configuração que configura a associação especificada para dar suporte ao fluxo de transações, bem como a usar o protocolo WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="54f7d-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="54f7d-112">Configurando o transactionTimeout</span><span class="sxs-lookup"><span data-stu-id="54f7d-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="54f7d-113">Você pode configurar o atributo `transactionTimeout` para o serviço WCF no elemento `behavior` do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="54f7d-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="54f7d-114">O código a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="54f7d-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="54f7d-115">O atributo `transactionTimeout` especifica o período de tempo no qual uma nova transação criada no serviço deve ser concluída.</span><span class="sxs-lookup"><span data-stu-id="54f7d-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="54f7d-116">Ele é usado como o tempo limite de <xref:System.Transactions.TransactionScope> para qualquer operação que estabelece uma nova transação e, se <xref:System.ServiceModel.OperationBehaviorAttribute> for aplicado, a propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> será definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="54f7d-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="54f7d-117">O tempo limite especifica a duração do tempo desde a criação da transação até a conclusão da fase 1 no protocolo de confirmação de duas fases.</span><span class="sxs-lookup"><span data-stu-id="54f7d-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="54f7d-118">Se esse atributo for definido em uma seção de configuração de `service`, você deverá aplicar pelo menos um método do serviço correspondente com <xref:System.ServiceModel.OperationBehaviorAttribute>, no qual a propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> está definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="54f7d-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="54f7d-119">Observe que o valor de tempo limite usado é o valor menor entre esse `transactionTimeout` definição de configuração e qualquer propriedade de <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="54f7d-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f7d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54f7d-120">See also</span></span>

- [<span data-ttu-id="54f7d-121">> de associação de \<</span><span class="sxs-lookup"><span data-stu-id="54f7d-121">\<binding></span></span>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="54f7d-122">Esquema de configuração do WCF</span><span class="sxs-lookup"><span data-stu-id="54f7d-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
