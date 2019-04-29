---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 43415d9eac5e61f42006aecb3248dec9811eb3e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758126"
---
# <a name="transactedbatching"></a><span data-ttu-id="8eeb7-101">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="8eeb7-101">\<transactedBatching></span></span>

<span data-ttu-id="8eeb7-102">Especifica se o envio em lote de transações tem suporte para operações de recebimento.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="8eeb7-103">\<system.ServiceModel>\\</span><span class="sxs-lookup"><span data-stu-id="8eeb7-103">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="8eeb7-104">\<comportamentos > \\</span><span class="sxs-lookup"><span data-stu-id="8eeb7-104">\<behaviors>\\</span></span>
<span data-ttu-id="8eeb7-105">\<endpointBehaviors>\\</span><span class="sxs-lookup"><span data-stu-id="8eeb7-105">\<endpointBehaviors>\\</span></span>
<span data-ttu-id="8eeb7-106">\<behavior>\\</span><span class="sxs-lookup"><span data-stu-id="8eeb7-106">\<behavior>\\</span></span>
<span data-ttu-id="8eeb7-107">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="8eeb7-107">\<transactedBatching></span></span>

## <a name="syntax"></a><span data-ttu-id="8eeb7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8eeb7-108">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8eeb7-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8eeb7-109">Attributes and Elements</span></span>

<span data-ttu-id="8eeb7-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8eeb7-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="8eeb7-111">Attributes</span></span>

|<span data-ttu-id="8eeb7-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="8eeb7-112">Attribute</span></span>|<span data-ttu-id="8eeb7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8eeb7-113">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="8eeb7-114">Um inteiro que especifica o número máximo de operações de recebimento que podem ser enviadas em lote juntas em uma transação.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-114">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="8eeb7-115">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-115">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8eeb7-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8eeb7-116">Child Elements</span></span>

<span data-ttu-id="8eeb7-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8eeb7-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8eeb7-118">Parent Elements</span></span>

|<span data-ttu-id="8eeb7-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="8eeb7-119">Element</span></span>|<span data-ttu-id="8eeb7-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="8eeb7-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8eeb7-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="8eeb7-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8eeb7-122">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-122">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8eeb7-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="8eeb7-123">Remarks</span></span>

<span data-ttu-id="8eeb7-124">Um transporte configurado com transações em lotes de tentativas de enviar em lote várias operações em uma transação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-124">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="8eeb7-125">Ao fazer isso, o custo relativamente alto de criação de uma transação e confirmá-lo em cada receber operação é evitada.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-125">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="8eeb7-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8eeb7-126">Example</span></span>

<span data-ttu-id="8eeb7-127">O exemplo a seguir mostra como adicionar o comportamento de envio em lote transacionado para um serviço em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="8eeb7-127">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8eeb7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8eeb7-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
