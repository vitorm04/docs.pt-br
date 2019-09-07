---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399407"
---
# <a name="transactedbatching"></a><span data-ttu-id="b341b-101">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="b341b-101">\<transactedBatching></span></span>

<span data-ttu-id="b341b-102">Especifica se o envio em lote de transações tem suporte para operações de recebimento.</span><span class="sxs-lookup"><span data-stu-id="b341b-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="b341b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b341b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b341b-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b341b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b341b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b341b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="b341b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b341b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="b341b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b341b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="b341b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> transactedBatching**</span><span class="sxs-lookup"><span data-stu-id="b341b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="b341b-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b341b-109">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b341b-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b341b-110">Attributes and Elements</span></span>

<span data-ttu-id="b341b-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b341b-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b341b-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b341b-112">Attributes</span></span>

|<span data-ttu-id="b341b-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b341b-113">Attribute</span></span>|<span data-ttu-id="b341b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b341b-114">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="b341b-115">Um inteiro que especifica o número máximo de operações de recebimento que podem ser agrupadas em uma transação.</span><span class="sxs-lookup"><span data-stu-id="b341b-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="b341b-116">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="b341b-116">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b341b-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b341b-117">Child Elements</span></span>

<span data-ttu-id="b341b-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b341b-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b341b-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b341b-119">Parent Elements</span></span>

|<span data-ttu-id="b341b-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="b341b-120">Element</span></span>|<span data-ttu-id="b341b-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="b341b-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b341b-122">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="b341b-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b341b-123">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b341b-123">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b341b-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="b341b-124">Remarks</span></span>

<span data-ttu-id="b341b-125">Um transporte configurado com o envio em lote de transações tenta o lote de várias operações de recebimento em uma transação.</span><span class="sxs-lookup"><span data-stu-id="b341b-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="b341b-126">Ao fazer isso, o custo relativamente alto para criar uma transação e confirmá-la em todas as operações de recebimento é evitado.</span><span class="sxs-lookup"><span data-stu-id="b341b-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="b341b-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b341b-127">Example</span></span>

<span data-ttu-id="b341b-128">O exemplo a seguir mostra como adicionar o comportamento de envio em lote transacionado a um serviço em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b341b-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b341b-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b341b-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
