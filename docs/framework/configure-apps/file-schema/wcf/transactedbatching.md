---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399407"
---
# \<transactedBatching>

<span data-ttu-id="cd61f-101">Especifica se o envio em lote de transações tem suporte para operações de recebimento.</span><span class="sxs-lookup"><span data-stu-id="cd61f-101">Specifies whether transaction batching is supported for receive operations.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**  

## <a name="syntax"></a><span data-ttu-id="cd61f-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd61f-102">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cd61f-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cd61f-103">Attributes and Elements</span></span>

<span data-ttu-id="cd61f-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cd61f-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cd61f-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="cd61f-105">Attributes</span></span>

|<span data-ttu-id="cd61f-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="cd61f-106">Attribute</span></span>|<span data-ttu-id="cd61f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd61f-107">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="cd61f-108">Um inteiro que especifica o número máximo de operações de recebimento que podem ser agrupadas em uma transação.</span><span class="sxs-lookup"><span data-stu-id="cd61f-108">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="cd61f-109">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="cd61f-109">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="cd61f-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cd61f-110">Child Elements</span></span>

<span data-ttu-id="cd61f-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cd61f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cd61f-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cd61f-112">Parent Elements</span></span>

|<span data-ttu-id="cd61f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="cd61f-113">Element</span></span>|<span data-ttu-id="cd61f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd61f-114">Description</span></span>|
|-------------|-----------------|
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="cd61f-115">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="cd61f-115">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cd61f-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd61f-116">Remarks</span></span>

<span data-ttu-id="cd61f-117">Um transporte configurado com o envio em lote de transações tenta o lote de várias operações de recebimento em uma transação.</span><span class="sxs-lookup"><span data-stu-id="cd61f-117">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="cd61f-118">Ao fazer isso, o custo relativamente alto para criar uma transação e confirmá-la em todas as operações de recebimento é evitado.</span><span class="sxs-lookup"><span data-stu-id="cd61f-118">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="cd61f-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd61f-119">Example</span></span>

<span data-ttu-id="cd61f-120">O exemplo a seguir mostra como adicionar o comportamento de envio em lote transacionado a um serviço em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cd61f-120">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cd61f-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="cd61f-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
