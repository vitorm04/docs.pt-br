---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 87952a92bab1ef7147100332bcef87b6f0534817
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270359"
---
# <a name="servicethrottling"></a><span data-ttu-id="544b6-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="544b6-101">\<serviceThrottling></span></span>
<span data-ttu-id="544b6-102">Especifica o mecanismo de limitação de um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="544b6-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="544b6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="544b6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="544b6-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="544b6-104">\<behaviors></span></span>  
<span data-ttu-id="544b6-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="544b6-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="544b6-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="544b6-106">\<behavior></span></span>  
<span data-ttu-id="544b6-107">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="544b6-107">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="544b6-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="544b6-108">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="544b6-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="544b6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="544b6-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="544b6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="544b6-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="544b6-111">Attributes</span></span>  
  
|<span data-ttu-id="544b6-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="544b6-112">Attribute</span></span>|<span data-ttu-id="544b6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="544b6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="544b6-114">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="544b6-114">maxConcurrentCalls</span></span>|<span data-ttu-id="544b6-115">Um número inteiro positivo que limita o número de mensagens que são processadas atualmente por meio de um <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="544b6-115">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="544b6-116">As chamadas além do limite são enfileiradas.</span><span class="sxs-lookup"><span data-stu-id="544b6-116">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="544b6-117">Definir esse valor como 0 é equivalente a defini-lo como Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="544b6-117">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="544b6-118">O padrão é 16 \* contagem de processadores.</span><span class="sxs-lookup"><span data-stu-id="544b6-118">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="544b6-119">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="544b6-119">maxConcurrentInstances</span></span>|<span data-ttu-id="544b6-120">Um número inteiro positivo que limita o número de objetos <xref:System.ServiceModel.InstanceContext> executados ao mesmo tempo em um <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="544b6-120">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="544b6-121">As solicitações para criar instâncias adicionais serão enfileiradas e concluídas quando um slot abaixo do limite ficar disponível.</span><span class="sxs-lookup"><span data-stu-id="544b6-121">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="544b6-122">A opção é a soma de maxConcurrentSessions e MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="544b6-122">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="544b6-123">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="544b6-123">maxConcurrentSessions</span></span>|<span data-ttu-id="544b6-124">Um número inteiro positivo que limita o número de sessões que um objeto <xref:System.ServiceModel.ServiceHost> pode aceitar.</span><span class="sxs-lookup"><span data-stu-id="544b6-124">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="544b6-125">O serviço aceitará conexões além do limite, mas somente os canais abaixo do limite estarão ativos (as mensagens são lidas do canal).</span><span class="sxs-lookup"><span data-stu-id="544b6-125">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="544b6-126">Definir esse valor como 0 é equivalente a defini-lo como Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="544b6-126">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="544b6-127">O padrão é 100 \* contagem de processadores.</span><span class="sxs-lookup"><span data-stu-id="544b6-127">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="544b6-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="544b6-128">Child Elements</span></span>  
 <span data-ttu-id="544b6-129">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="544b6-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="544b6-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="544b6-130">Parent Elements</span></span>  
  
|<span data-ttu-id="544b6-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="544b6-131">Element</span></span>|<span data-ttu-id="544b6-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="544b6-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="544b6-133">\<behavior></span><span class="sxs-lookup"><span data-stu-id="544b6-133">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="544b6-134">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="544b6-134">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="544b6-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="544b6-135">Remarks</span></span>  
 <span data-ttu-id="544b6-136">Os controles de limitação colocam limites no número de chamadas simultâneas, instâncias ou sessões para evitar a sobrecarga de consumo de recursos.</span><span class="sxs-lookup"><span data-stu-id="544b6-136">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="544b6-137">Um rastreamento é gravado cada vez que o valor dos atributos é atingido.</span><span class="sxs-lookup"><span data-stu-id="544b6-137">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="544b6-138">O primeiro rastreamento é gravado como um aviso.</span><span class="sxs-lookup"><span data-stu-id="544b6-138">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="544b6-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="544b6-139">Example</span></span>  
 <span data-ttu-id="544b6-140">O seguinte exemplo de configuração especifica que o serviço limita o máximo de chamadas simultâneas para 2, e o número máximo de instâncias simultâneas para 10.</span><span class="sxs-lookup"><span data-stu-id="544b6-140">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="544b6-141">Para obter um exemplo detalhado da execução deste exemplo, consulte [limitação](../../../../../docs/framework/wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="544b6-141">For a detailed example of running this example, see [Throttling](../../../../../docs/framework/wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="544b6-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="544b6-142">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="544b6-143">Usando o ServiceThrottlingBehavior para desempenho do serviço WCF de controle</span><span class="sxs-lookup"><span data-stu-id="544b6-143">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
