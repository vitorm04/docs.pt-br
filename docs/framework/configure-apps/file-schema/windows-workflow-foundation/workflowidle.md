---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 16a485b6d0ba2584cccd08a36506582fd3930f71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947172"
---
# <a name="workflowidle"></a><span data-ttu-id="51468-101">\<> workflowIdle</span><span class="sxs-lookup"><span data-stu-id="51468-101">\<workflowIdle></span></span>
<span data-ttu-id="51468-102">Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.</span><span class="sxs-lookup"><span data-stu-id="51468-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="51468-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="51468-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="51468-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="51468-104">\<behaviors></span></span>  
<span data-ttu-id="51468-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="51468-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="51468-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="51468-106">\<behavior></span></span>  
<span data-ttu-id="51468-107">\<> workflowIdle</span><span class="sxs-lookup"><span data-stu-id="51468-107">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51468-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51468-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51468-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="51468-109">Attributes and Elements</span></span>  
 <span data-ttu-id="51468-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="51468-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51468-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="51468-111">Attributes</span></span>  
  
|<span data-ttu-id="51468-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="51468-112">Attribute</span></span>|<span data-ttu-id="51468-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="51468-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51468-114">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="51468-114">timeToPersist</span></span>|<span data-ttu-id="51468-115">Um valor TimeSpan que especifica a duração entre a hora em que o fluxo de trabalho se torna ocioso e é persistido.</span><span class="sxs-lookup"><span data-stu-id="51468-115">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="51468-116">O valor padrão é TimeSpan. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="51468-116">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="51468-117">A duração começa a decorrer quando a instância de fluxo de trabalho fica ociosa.</span><span class="sxs-lookup"><span data-stu-id="51468-117">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="51468-118">Esse atributo será útil se você quiser persistir uma instância de fluxo de trabalho de forma mais agressiva enquanto mantém a instância na memória o mais longo possível.</span><span class="sxs-lookup"><span data-stu-id="51468-118">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="51468-119">Esse atributo só será válido se seu valor for menor que o atributo **TimeToUnload** .</span><span class="sxs-lookup"><span data-stu-id="51468-119">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="51468-120">Se for maior, ela será ignorada.</span><span class="sxs-lookup"><span data-stu-id="51468-120">If it is greater, it is ignored.</span></span> <span data-ttu-id="51468-121">Se esse atributo decorrer antes do valor especificado pelo atributo **TimeToUnload** , a persistência deverá ser concluída antes que o fluxo de trabalho seja descarregado.</span><span class="sxs-lookup"><span data-stu-id="51468-121">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="51468-122">Isso significa que a operação pode ser atrasada até que o fluxo de trabalho é mantido.</span><span class="sxs-lookup"><span data-stu-id="51468-122">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="51468-123">A camada de persistência é responsável por gerenciar quaisquer tentativas de erros transitórios e apenas lança exceções em erros não recuperáveis.</span><span class="sxs-lookup"><span data-stu-id="51468-123">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="51468-124">Portanto, todas as exceções geradas durante a persistência são tratadas como fatal e a instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="51468-124">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="51468-125">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="51468-125">timeToUnload</span></span>|<span data-ttu-id="51468-126">Um valor de Timespan que especifica a duração entre o momento em que o fluxo de trabalho fica ocioso e é descarregado.</span><span class="sxs-lookup"><span data-stu-id="51468-126">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="51468-127">O valor padrão é 1 minuto.</span><span class="sxs-lookup"><span data-stu-id="51468-127">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="51468-128">Descarregar um fluxo de trabalho significa que ele também é mantido.</span><span class="sxs-lookup"><span data-stu-id="51468-128">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="51468-129">Se esse atributo for definido como zero, a instância do fluxo de trabalho será persistida e descarregada imediatamente depois que o fluxo de trabalho se tornar ocioso.</span><span class="sxs-lookup"><span data-stu-id="51468-129">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="51468-130">Definir esse atributo como TimeSpan. MaxValue desabilita efetivamente a operação de descarregamento.</span><span class="sxs-lookup"><span data-stu-id="51468-130">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="51468-131">Instâncias de fluxo de trabalho ocioso nunca são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="51468-131">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51468-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="51468-132">Child Elements</span></span>  
 <span data-ttu-id="51468-133">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="51468-133">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51468-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="51468-134">Parent Elements</span></span>  
  
|<span data-ttu-id="51468-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="51468-135">Element</span></span>|<span data-ttu-id="51468-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="51468-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51468-137">\<comportamento > de \<percomportamentos ></span><span class="sxs-lookup"><span data-stu-id="51468-137">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="51468-138">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="51468-138">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51468-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51468-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
