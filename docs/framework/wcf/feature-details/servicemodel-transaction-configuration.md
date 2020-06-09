---
title: Configuração de transação de ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 1d04a7bb756cccb33b436c1f57decc0249764828
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600329"
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="5e7c1-102">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5e7c1-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="5e7c1-103">Windows Communication Foundation (WCF) fornece três atributos para configurar transações para um serviço: `transactionFlow` , `transactionProtocol` e `transactionTimeout` .</span><span class="sxs-lookup"><span data-stu-id="5e7c1-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="5e7c1-104">Configurando o transactionFlow</span><span class="sxs-lookup"><span data-stu-id="5e7c1-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="5e7c1-105">A maioria das associações predefinidas que o WCF fornece contém os `transactionFlow` `transactionProtocol` atributos e, para que você possa configurar a associação para aceitar as transações de entrada de um ponto de extremidade específico usando um protocolo de fluxo de transação específico.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="5e7c1-106">Além disso, você pode usar o `transactionFlow` elemento e seu `transactionProtocol` atributo para criar sua própria associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="5e7c1-107">Para obter mais informações sobre como definir os elementos de configuração, consulte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) e [esquema de configuração do WCF](../../configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="5e7c1-107">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="5e7c1-108">O `transactionFlow` atributo especifica se o fluxo de transações está habilitado para pontos de extremidade de serviço que usam a associação.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="5e7c1-109">Configurando o transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="5e7c1-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="5e7c1-110">O `transactionProtocol` atributo especifica o protocolo de transação a ser usado com pontos de extremidade de serviço que usam a associação.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="5e7c1-111">Veja a seguir um exemplo de uma seção de configuração que configura a associação especificada para dar suporte ao fluxo de transações, bem como a usar o protocolo WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="5e7c1-112">Configurando o transactionTimeout</span><span class="sxs-lookup"><span data-stu-id="5e7c1-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="5e7c1-113">Você pode configurar o `transactionTimeout` atributo para seu serviço WCF no `behavior` elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="5e7c1-114">O código a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="5e7c1-115">O `transactionTimeout` atributo especifica o período de tempo no qual uma nova transação criada no serviço deve ser concluída.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="5e7c1-116">Ele é usado como o <xref:System.Transactions.TransactionScope> tempo limite para qualquer operação que estabeleça uma nova transação e, se <xref:System.ServiceModel.OperationBehaviorAttribute> for aplicado, a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedade será definida como `true` .</span><span class="sxs-lookup"><span data-stu-id="5e7c1-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="5e7c1-117">O tempo limite especifica a duração do tempo desde a criação da transação até a conclusão da fase 1 no protocolo de confirmação de duas fases.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="5e7c1-118">Se esse atributo for definido dentro de uma `service` seção de configuração, você deverá aplicar pelo menos um método do serviço correspondente com <xref:System.ServiceModel.OperationBehaviorAttribute> o, no qual a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedade é definida como `true` .</span><span class="sxs-lookup"><span data-stu-id="5e7c1-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="5e7c1-119">Observe que o valor de tempo limite usado é o valor menor entre esse `transactionTimeout` parâmetro de configuração e qualquer <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5e7c1-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e7c1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e7c1-120">See also</span></span>

- [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="5e7c1-121">Esquema de configuração do WCF</span><span class="sxs-lookup"><span data-stu-id="5e7c1-121">WCF Configuration Schema</span></span>](../../configure-apps/file-schema/wcf/index.md)
