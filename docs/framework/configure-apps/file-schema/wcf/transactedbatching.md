---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 12369f1053638583a3864fab396869d0e7045732
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918671"
---
# <a name="transactedbatching"></a><span data-ttu-id="1f3fd-101">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="1f3fd-101">\<transactedBatching></span></span>

<span data-ttu-id="1f3fd-102">Especifica se o envio em lote de transações tem suporte para operações de recebimento.</span><span class="sxs-lookup"><span data-stu-id="1f3fd-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="1f3fd-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1f3fd-103">\<system.ServiceModel></span></span>\
<span data-ttu-id="1f3fd-104">\<comportamentos > </span><span class="sxs-lookup"><span data-stu-id="1f3fd-104">\<behaviors></span></span>\
<span data-ttu-id="1f3fd-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="1f3fd-105">\<endpointBehaviors></span></span>\
<span data-ttu-id="1f3fd-106">\<comportamento > </span><span class="sxs-lookup"><span data-stu-id="1f3fd-106">\<behavior></span></span>\
<span data-ttu-id="1f3fd-107">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="1f3fd-107">\<transactedBatching></span></span>

## <a name="syntax"></a><span data-ttu-id="1f3fd-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f3fd-108">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f3fd-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1f3fd-109">Attributes and Elements</span></span>

<span data-ttu-id="1f3fd-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1f3fd-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f3fd-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="1f3fd-111">Attributes</span></span>

|<span data-ttu-id="1f3fd-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="1f3fd-112">Attribute</span></span>|<span data-ttu-id="1f3fd-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1f3fd-113">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="1f3fd-114">Um inteiro que especifica o número máximo de operações de recebimento que podem ser agrupadas em uma transação.</span><span class="sxs-lookup"><span data-stu-id="1f3fd-114">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="1f3fd-115">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="1f3fd-115">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1f3fd-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1f3fd-116">Child Elements</span></span>

<span data-ttu-id="1f3fd-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1f3fd-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f3fd-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1f3fd-118">Parent Elements</span></span>

|<span data-ttu-id="1f3fd-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="1f3fd-119">Element</span></span>|<span data-ttu-id="1f3fd-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="1f3fd-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f3fd-121">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="1f3fd-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1f3fd-122">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="1f3fd-122">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f3fd-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="1f3fd-123">Remarks</span></span>

<span data-ttu-id="1f3fd-124">Um transporte configurado com o envio em lote de transações tenta o lote de várias operações de recebimento em uma transação.</span><span class="sxs-lookup"><span data-stu-id="1f3fd-124">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="1f3fd-125">Ao fazer isso, o custo relativamente alto para criar uma transação e confirmá-la em todas as operações de recebimento é evitado.</span><span class="sxs-lookup"><span data-stu-id="1f3fd-125">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="1f3fd-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1f3fd-126">Example</span></span>

<span data-ttu-id="1f3fd-127">O exemplo a seguir mostra como adicionar o comportamento de envio em lote transacionado a um serviço em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1f3fd-127">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
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

## <a name="see-also"></a><span data-ttu-id="1f3fd-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f3fd-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
