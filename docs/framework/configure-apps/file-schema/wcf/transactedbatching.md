---
title: '&lt;transactedBatching&gt;'
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 2f89a1a6c2cc110a4695b792c5aa801b516393be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565989"
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="e57b2-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="e57b2-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="e57b2-103">Especifica se o envio em lote de transações tem suporte para operações de recebimento.</span><span class="sxs-lookup"><span data-stu-id="e57b2-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="e57b2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e57b2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e57b2-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="e57b2-105">\<behaviors></span></span>  
<span data-ttu-id="e57b2-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e57b2-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e57b2-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e57b2-107">\<behavior></span></span>  
<span data-ttu-id="e57b2-108">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="e57b2-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e57b2-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e57b2-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e57b2-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e57b2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e57b2-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e57b2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e57b2-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e57b2-112">Attributes</span></span>  
  
|<span data-ttu-id="e57b2-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e57b2-113">Attribute</span></span>|<span data-ttu-id="e57b2-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e57b2-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="e57b2-115">Um inteiro que especifica o número máximo de operações de recebimento que podem ser enviadas em lote juntas em uma transação.</span><span class="sxs-lookup"><span data-stu-id="e57b2-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="e57b2-116">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="e57b2-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e57b2-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e57b2-117">Child Elements</span></span>  
 <span data-ttu-id="e57b2-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e57b2-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e57b2-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e57b2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e57b2-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="e57b2-120">Element</span></span>|<span data-ttu-id="e57b2-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="e57b2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e57b2-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e57b2-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e57b2-123">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e57b2-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e57b2-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="e57b2-124">Remarks</span></span>  
 <span data-ttu-id="e57b2-125">Um transporte configurado com transações em lotes de tentativas de enviar em lote várias operações em uma transação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="e57b2-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="e57b2-126">Ao fazer isso, o custo relativamente alto de criação de uma transação e confirmá-lo em cada receber operação é evitada.</span><span class="sxs-lookup"><span data-stu-id="e57b2-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e57b2-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e57b2-127">Example</span></span>  
 <span data-ttu-id="e57b2-128">O exemplo a seguir mostra como adicionar o comportamento de envio em lote transacionado para um serviço em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e57b2-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />
      <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <behaviors>
    <endpointBehaviors>
      <behavior name="endpointBehavior">
        <transactedBatching maxBatchSize="10" />
      </behavior>
    </endpointBehaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="true" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="e57b2-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e57b2-129">See also</span></span>
- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
