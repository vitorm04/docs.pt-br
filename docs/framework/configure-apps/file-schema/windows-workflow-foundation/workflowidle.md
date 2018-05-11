---
title: '&lt;workflowIdle&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 65bcc1ccd357fb7f331665aefbd975b11a2378cd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowidlegt"></a><span data-ttu-id="b98d1-102">&lt;workflowIdle&gt;</span><span class="sxs-lookup"><span data-stu-id="b98d1-102">&lt;workflowIdle&gt;</span></span>
<span data-ttu-id="b98d1-103">Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.</span><span class="sxs-lookup"><span data-stu-id="b98d1-103">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="b98d1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b98d1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b98d1-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="b98d1-105">\<behaviors></span></span>  
<span data-ttu-id="b98d1-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b98d1-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b98d1-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="b98d1-107">\<behavior></span></span>  
<span data-ttu-id="b98d1-108">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="b98d1-108">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b98d1-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b98d1-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b98d1-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b98d1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b98d1-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b98d1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b98d1-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b98d1-112">Attributes</span></span>  
  
|<span data-ttu-id="b98d1-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b98d1-113">Attribute</span></span>|<span data-ttu-id="b98d1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b98d1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b98d1-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="b98d1-115">timeToPersist</span></span>|<span data-ttu-id="b98d1-116">Um valor Timespan que especifica a duração entre a hora em que o fluxo de trabalho se torna ocioso e é mantido.</span><span class="sxs-lookup"><span data-stu-id="b98d1-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="b98d1-117">O valor padrão é TimeSpan. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="b98d1-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="b98d1-118">A duração começa a decorrer quando a instância de fluxo de trabalho fica ociosa.</span><span class="sxs-lookup"><span data-stu-id="b98d1-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="b98d1-119">Esse atributo é útil se você quiser manter uma instância de fluxo de trabalho mais agressiva enquanto mantém a instância na memória por tempo possível.</span><span class="sxs-lookup"><span data-stu-id="b98d1-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="b98d1-120">Esse atributo só é válido se o valor for menor do que o **timeToUnload** atributo.</span><span class="sxs-lookup"><span data-stu-id="b98d1-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="b98d1-121">Se for maior, ela será ignorada.</span><span class="sxs-lookup"><span data-stu-id="b98d1-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="b98d1-122">Se esse atributo decorrer antes do valor especificado pelo **timeToUnload** atributo, persistência deve concluir antes do fluxo de trabalho é descarregado.</span><span class="sxs-lookup"><span data-stu-id="b98d1-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="b98d1-123">Isso significa que a operação pode ser atrasada até que o fluxo de trabalho é mantido.</span><span class="sxs-lookup"><span data-stu-id="b98d1-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="b98d1-124">A camada de persistência é responsável por gerenciar quaisquer tentativas de erros transitórios e apenas lança exceções em erros não recuperáveis.</span><span class="sxs-lookup"><span data-stu-id="b98d1-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="b98d1-125">Portanto, todas as exceções geradas durante a persistência são tratadas como fatal e a instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="b98d1-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="b98d1-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="b98d1-126">timeToUnload</span></span>|<span data-ttu-id="b98d1-127">Um valor de Timespan que especifica a duração entre o momento em que o fluxo de trabalho fica ocioso e é descarregado.</span><span class="sxs-lookup"><span data-stu-id="b98d1-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="b98d1-128">O valor padrão é 1 minuto.</span><span class="sxs-lookup"><span data-stu-id="b98d1-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="b98d1-129">Descarregar um fluxo de trabalho significa que ele também é mantido.</span><span class="sxs-lookup"><span data-stu-id="b98d1-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="b98d1-130">Se esse atributo for definido como zero, a instância de fluxo de trabalho é mantida e carregada imediatamente após o fluxo de trabalho se torna ocioso.</span><span class="sxs-lookup"><span data-stu-id="b98d1-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="b98d1-131">Definir esse atributo como TimeSpan. MaxValue efetivamente desabilita a operação.</span><span class="sxs-lookup"><span data-stu-id="b98d1-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="b98d1-132">Instâncias de fluxo de trabalho ocioso nunca são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="b98d1-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b98d1-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b98d1-133">Child Elements</span></span>  
 <span data-ttu-id="b98d1-134">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b98d1-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b98d1-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b98d1-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b98d1-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="b98d1-136">Element</span></span>|<span data-ttu-id="b98d1-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="b98d1-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b98d1-138">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b98d1-138">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b98d1-139">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="b98d1-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b98d1-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b98d1-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
