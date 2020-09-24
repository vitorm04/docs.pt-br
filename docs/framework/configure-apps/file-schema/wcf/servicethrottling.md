---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 0c6d844ac287037b7a546d3a48e7cd924e8a63d1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153606"
---
# \<serviceThrottling>

<span data-ttu-id="59dd9-101">Especifica o mecanismo de limitação de um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="59dd9-101">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**  
  
## <a name="syntax"></a><span data-ttu-id="59dd9-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="59dd9-102">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59dd9-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="59dd9-103">Attributes and Elements</span></span>  

 <span data-ttu-id="59dd9-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="59dd9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59dd9-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="59dd9-105">Attributes</span></span>  
  
|<span data-ttu-id="59dd9-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="59dd9-106">Attribute</span></span>|<span data-ttu-id="59dd9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="59dd9-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59dd9-108">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="59dd9-108">maxConcurrentCalls</span></span>|<span data-ttu-id="59dd9-109">Um número inteiro positivo que limita o número de mensagens que são processadas atualmente por meio de um <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="59dd9-109">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="59dd9-110">As chamadas além do limite são enfileiradas.</span><span class="sxs-lookup"><span data-stu-id="59dd9-110">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="59dd9-111">Definir esse valor como 0 é equivalente a defini-lo como Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="59dd9-111">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="59dd9-112">O padrão é 16 \* contagem de processador.</span><span class="sxs-lookup"><span data-stu-id="59dd9-112">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="59dd9-113">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="59dd9-113">maxConcurrentInstances</span></span>|<span data-ttu-id="59dd9-114">Um número inteiro positivo que limita o número de objetos <xref:System.ServiceModel.InstanceContext> executados ao mesmo tempo em um <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="59dd9-114">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="59dd9-115">As solicitações para criar instâncias adicionais serão enfileiradas e concluídas quando um slot abaixo do limite ficar disponível.</span><span class="sxs-lookup"><span data-stu-id="59dd9-115">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="59dd9-116">A opção é a soma de maxConcurrentSessions e MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="59dd9-116">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="59dd9-117">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="59dd9-117">maxConcurrentSessions</span></span>|<span data-ttu-id="59dd9-118">Um número inteiro positivo que limita o número de sessões que um objeto <xref:System.ServiceModel.ServiceHost> pode aceitar.</span><span class="sxs-lookup"><span data-stu-id="59dd9-118">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="59dd9-119">O serviço aceitará conexões além do limite, mas somente os canais abaixo do limite estarão ativos (as mensagens são lidas do canal).</span><span class="sxs-lookup"><span data-stu-id="59dd9-119">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="59dd9-120">Definir esse valor como 0 é equivalente a defini-lo como Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="59dd9-120">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="59dd9-121">O padrão é 100 \* contagem de processadores.</span><span class="sxs-lookup"><span data-stu-id="59dd9-121">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59dd9-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="59dd9-122">Child Elements</span></span>  

 <span data-ttu-id="59dd9-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="59dd9-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59dd9-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="59dd9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="59dd9-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="59dd9-125">Element</span></span>|<span data-ttu-id="59dd9-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="59dd9-126">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="59dd9-127">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="59dd9-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59dd9-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="59dd9-128">Remarks</span></span>  

 <span data-ttu-id="59dd9-129">Os controles de limitação colocam limites no número de chamadas simultâneas, instâncias ou sessões para evitar a sobrecarga de consumo de recursos.</span><span class="sxs-lookup"><span data-stu-id="59dd9-129">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="59dd9-130">Um rastreamento é gravado cada vez que o valor dos atributos é atingido.</span><span class="sxs-lookup"><span data-stu-id="59dd9-130">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="59dd9-131">O primeiro rastreamento é gravado como um aviso.</span><span class="sxs-lookup"><span data-stu-id="59dd9-131">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59dd9-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59dd9-132">Example</span></span>  

 <span data-ttu-id="59dd9-133">O seguinte exemplo de configuração especifica que o serviço limita o máximo de chamadas simultâneas para 2, e o número máximo de instâncias simultâneas para 10.</span><span class="sxs-lookup"><span data-stu-id="59dd9-133">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="59dd9-134">Para obter um exemplo detalhado de como executar este exemplo, consulte [limitação](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="59dd9-134">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="59dd9-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="59dd9-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="59dd9-136">Utilizando o ServiceThrottlingBehavior para controlar o desempenho de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="59dd9-136">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
