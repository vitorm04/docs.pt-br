---
title: '&lt;workflowIdle&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 9d9eb45090367fb2cc18fc357c219e74d63fb667
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628091"
---
# <a name="ltworkflowidlegt"></a><span data-ttu-id="a0454-102">&lt;workflowIdle&gt;</span><span class="sxs-lookup"><span data-stu-id="a0454-102">&lt;workflowIdle&gt;</span></span>
<span data-ttu-id="a0454-103">Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.</span><span class="sxs-lookup"><span data-stu-id="a0454-103">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="a0454-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a0454-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a0454-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="a0454-105">\<behaviors></span></span>  
<span data-ttu-id="a0454-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a0454-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a0454-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a0454-107">\<behavior></span></span>  
<span data-ttu-id="a0454-108">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="a0454-108">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0454-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0454-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0454-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a0454-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a0454-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a0454-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0454-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a0454-112">Attributes</span></span>  
  
|<span data-ttu-id="a0454-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a0454-113">Attribute</span></span>|<span data-ttu-id="a0454-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0454-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a0454-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="a0454-115">timeToPersist</span></span>|<span data-ttu-id="a0454-116">Um valor de Timespan que especifica a duração entre a hora em que o fluxo de trabalho fica ocioso e é mantido.</span><span class="sxs-lookup"><span data-stu-id="a0454-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="a0454-117">O valor padrão é TimeSpan. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="a0454-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="a0454-118">A duração começa a decorrer quando a instância de fluxo de trabalho fica ociosa.</span><span class="sxs-lookup"><span data-stu-id="a0454-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="a0454-119">Esse atributo é útil se você quiser manter uma instância de fluxo de trabalho mais agressivamente enquanto mantém a instância na memória por mais tempo.</span><span class="sxs-lookup"><span data-stu-id="a0454-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="a0454-120">Esse atributo só será válido se seu valor é menor do que o **timeToUnload** atributo.</span><span class="sxs-lookup"><span data-stu-id="a0454-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="a0454-121">Se for maior, ela será ignorada.</span><span class="sxs-lookup"><span data-stu-id="a0454-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="a0454-122">Se esse atributo decorrer antes do valor especificado pela **timeToUnload** atributo, persistência deve ser concluída antes que o fluxo de trabalho é descarregado.</span><span class="sxs-lookup"><span data-stu-id="a0454-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="a0454-123">Isso significa que a operação pode ser atrasada até que o fluxo de trabalho é mantido.</span><span class="sxs-lookup"><span data-stu-id="a0454-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="a0454-124">A camada de persistência é responsável por gerenciar quaisquer tentativas de erros transitórios e apenas lança exceções em erros não recuperáveis.</span><span class="sxs-lookup"><span data-stu-id="a0454-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="a0454-125">Portanto, todas as exceções geradas durante a persistência são tratadas como fatal e a instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="a0454-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="a0454-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="a0454-126">timeToUnload</span></span>|<span data-ttu-id="a0454-127">Um valor de Timespan que especifica a duração entre o momento em que o fluxo de trabalho fica ocioso e é descarregado.</span><span class="sxs-lookup"><span data-stu-id="a0454-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="a0454-128">O valor padrão é 1 minuto.</span><span class="sxs-lookup"><span data-stu-id="a0454-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="a0454-129">Descarregar um fluxo de trabalho significa que ele também é mantido.</span><span class="sxs-lookup"><span data-stu-id="a0454-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="a0454-130">Se esse atributo é definido como zero, a instância de fluxo de trabalho é mantida e descarregada imediatamente após o fluxo de trabalho fica ocioso.</span><span class="sxs-lookup"><span data-stu-id="a0454-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="a0454-131">Definir esse atributo como TimeSpan efetivamente desabilita a operação.</span><span class="sxs-lookup"><span data-stu-id="a0454-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="a0454-132">Instâncias de fluxo de trabalho ocioso nunca são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="a0454-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0454-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a0454-133">Child Elements</span></span>  
 <span data-ttu-id="a0454-134">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a0454-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0454-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a0454-135">Parent Elements</span></span>  
  
|<span data-ttu-id="a0454-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="a0454-136">Element</span></span>|<span data-ttu-id="a0454-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0454-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0454-138">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a0454-138">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="a0454-139">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="a0454-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0454-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0454-140">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
