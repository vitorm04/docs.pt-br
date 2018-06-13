---
title: '&lt;serviceThrottling&gt;'
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: b0f5197bf4e9017007f29f86048756b43e3b15fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750161"
---
# <a name="ltservicethrottlinggt"></a><span data-ttu-id="7b478-102">&lt;serviceThrottling&gt;</span><span class="sxs-lookup"><span data-stu-id="7b478-102">&lt;serviceThrottling&gt;</span></span>
<span data-ttu-id="7b478-103">Especifica o mecanismo de limitação de um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7b478-103">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="7b478-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7b478-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b478-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="7b478-105">\<behaviors></span></span>  
<span data-ttu-id="7b478-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7b478-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7b478-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="7b478-107">\<behavior></span></span>  
<span data-ttu-id="7b478-108">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="7b478-108">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b478-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b478-109">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"  
    maxConcurrentInstances="Integer"  
    maxConcurrentSessions="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b478-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7b478-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7b478-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7b478-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b478-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7b478-112">Attributes</span></span>  
  
|<span data-ttu-id="7b478-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="7b478-113">Attribute</span></span>|<span data-ttu-id="7b478-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b478-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b478-115">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="7b478-115">maxConcurrentCalls</span></span>|<span data-ttu-id="7b478-116">Um número inteiro positivo que limita o número de mensagens que são processadas atualmente por meio de um <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7b478-116">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="7b478-117">As chamadas além do limite são enfileiradas.</span><span class="sxs-lookup"><span data-stu-id="7b478-117">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="7b478-118">Definir esse valor como 0 é equivalente a defini-lo como Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="7b478-118">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="7b478-119">O padrão é 16 \* número de processadores.</span><span class="sxs-lookup"><span data-stu-id="7b478-119">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="7b478-120">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="7b478-120">maxConcurrentInstances</span></span>|<span data-ttu-id="7b478-121">Um número inteiro positivo que limita o número de objetos <xref:System.ServiceModel.InstanceContext> executados ao mesmo tempo em um <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7b478-121">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="7b478-122">As solicitações para criar instâncias adicionais serão enfileiradas e concluídas quando um slot abaixo do limite ficar disponível.</span><span class="sxs-lookup"><span data-stu-id="7b478-122">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="7b478-123">A opção é a soma de maxConcurrentSessions e MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="7b478-123">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="7b478-124">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="7b478-124">maxConcurrentSessions</span></span>|<span data-ttu-id="7b478-125">Um número inteiro positivo que limita o número de sessões que um objeto <xref:System.ServiceModel.ServiceHost> pode aceitar.</span><span class="sxs-lookup"><span data-stu-id="7b478-125">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="7b478-126">O serviço aceitará conexões além do limite, mas somente os canais abaixo do limite estarão ativos (as mensagens são lidas do canal).</span><span class="sxs-lookup"><span data-stu-id="7b478-126">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="7b478-127">Definir esse valor como 0 é equivalente a defini-lo como Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="7b478-127">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="7b478-128">O padrão é 100 \* contagem de processadores.</span><span class="sxs-lookup"><span data-stu-id="7b478-128">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b478-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7b478-129">Child Elements</span></span>  
 <span data-ttu-id="7b478-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7b478-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b478-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7b478-131">Parent Elements</span></span>  
  
|<span data-ttu-id="7b478-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b478-132">Element</span></span>|<span data-ttu-id="7b478-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b478-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b478-134">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="7b478-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7b478-135">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="7b478-135">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b478-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b478-136">Remarks</span></span>  
 <span data-ttu-id="7b478-137">Os controles de limitação colocam limites no número de chamadas simultâneas, instâncias ou sessões para evitar a sobrecarga de consumo de recursos.</span><span class="sxs-lookup"><span data-stu-id="7b478-137">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="7b478-138">Um rastreamento é gravado cada vez que o valor dos atributos é atingido.</span><span class="sxs-lookup"><span data-stu-id="7b478-138">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="7b478-139">O primeiro rastreamento é gravado como um aviso.</span><span class="sxs-lookup"><span data-stu-id="7b478-139">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b478-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b478-140">Example</span></span>  
 <span data-ttu-id="7b478-141">O seguinte exemplo de configuração especifica que o serviço limita o máximo de chamadas simultâneas para 2, e o número máximo de instâncias simultâneas para 10.</span><span class="sxs-lookup"><span data-stu-id="7b478-141">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="7b478-142">Para obter um exemplo detalhado de executar este exemplo, consulte [limitação](../../../../../docs/framework/wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="7b478-142">For a detailed example of running this example, see [Throttling](../../../../../docs/framework/wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>   
  <serviceBehaviors>   
    <behavior name="CalculatorServiceBehavior">   
      <serviceDebug includeExceptionDetailInFaults="False" />   
      <serviceMetadata httpGetEnabled="True"/>   
      <!-- Specify throttling behavior -->  
      <serviceThrottling maxConcurrentCalls="2"   
           maxConcurrentInstances="10"/>   
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b478-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b478-143">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>  
 [<span data-ttu-id="7b478-144">Usando o ServiceThrottlingBehavior para desempenho do serviço WCF de controle</span><span class="sxs-lookup"><span data-stu-id="7b478-144">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
