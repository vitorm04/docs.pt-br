---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: af8a2568eb13bb3007065c4b4a3564aae27de7ac
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280924"
---
# <a name="workflowidle"></a><span data-ttu-id="f97d5-101">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="f97d5-101">\<workflowIdle></span></span>
<span data-ttu-id="f97d5-102">Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.</span><span class="sxs-lookup"><span data-stu-id="f97d5-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="f97d5-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f97d5-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f97d5-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="f97d5-104">\<behaviors></span></span>  
<span data-ttu-id="f97d5-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f97d5-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="f97d5-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f97d5-106">\<behavior></span></span>  
<span data-ttu-id="f97d5-107">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="f97d5-107">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f97d5-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f97d5-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f97d5-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f97d5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f97d5-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f97d5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f97d5-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f97d5-111">Attributes</span></span>  
  
|<span data-ttu-id="f97d5-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="f97d5-112">Attribute</span></span>|<span data-ttu-id="f97d5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f97d5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f97d5-114">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="f97d5-114">timeToPersist</span></span>|<span data-ttu-id="f97d5-115">Um valor de Timespan que especifica a duração entre a hora em que o fluxo de trabalho fica ocioso e é mantido.</span><span class="sxs-lookup"><span data-stu-id="f97d5-115">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="f97d5-116">O valor padrão é TimeSpan. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="f97d5-116">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="f97d5-117">A duração começa a decorrer quando a instância de fluxo de trabalho fica ociosa.</span><span class="sxs-lookup"><span data-stu-id="f97d5-117">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="f97d5-118">Esse atributo é útil se você quiser manter uma instância de fluxo de trabalho mais agressivamente enquanto mantém a instância na memória por mais tempo.</span><span class="sxs-lookup"><span data-stu-id="f97d5-118">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="f97d5-119">Esse atributo só será válido se seu valor é menor do que o **timeToUnload** atributo.</span><span class="sxs-lookup"><span data-stu-id="f97d5-119">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="f97d5-120">Se for maior, ela será ignorada.</span><span class="sxs-lookup"><span data-stu-id="f97d5-120">If it is greater, it is ignored.</span></span> <span data-ttu-id="f97d5-121">Se esse atributo decorrer antes do valor especificado pela **timeToUnload** atributo, persistência deve ser concluída antes que o fluxo de trabalho é descarregado.</span><span class="sxs-lookup"><span data-stu-id="f97d5-121">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="f97d5-122">Isso significa que a operação pode ser atrasada até que o fluxo de trabalho é mantido.</span><span class="sxs-lookup"><span data-stu-id="f97d5-122">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="f97d5-123">A camada de persistência é responsável por gerenciar quaisquer tentativas de erros transitórios e apenas lança exceções em erros não recuperáveis.</span><span class="sxs-lookup"><span data-stu-id="f97d5-123">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="f97d5-124">Portanto, todas as exceções geradas durante a persistência são tratadas como fatal e a instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="f97d5-124">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="f97d5-125">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="f97d5-125">timeToUnload</span></span>|<span data-ttu-id="f97d5-126">Um valor de Timespan que especifica a duração entre o momento em que o fluxo de trabalho fica ocioso e é descarregado.</span><span class="sxs-lookup"><span data-stu-id="f97d5-126">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="f97d5-127">O valor padrão é 1 minuto.</span><span class="sxs-lookup"><span data-stu-id="f97d5-127">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="f97d5-128">Descarregar um fluxo de trabalho significa que ele também é mantido.</span><span class="sxs-lookup"><span data-stu-id="f97d5-128">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="f97d5-129">Se esse atributo é definido como zero, a instância de fluxo de trabalho é mantida e descarregada imediatamente após o fluxo de trabalho fica ocioso.</span><span class="sxs-lookup"><span data-stu-id="f97d5-129">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="f97d5-130">Definir esse atributo como TimeSpan efetivamente desabilita a operação.</span><span class="sxs-lookup"><span data-stu-id="f97d5-130">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="f97d5-131">Instâncias de fluxo de trabalho ocioso nunca são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="f97d5-131">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f97d5-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f97d5-132">Child Elements</span></span>  
 <span data-ttu-id="f97d5-133">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f97d5-133">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f97d5-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f97d5-134">Parent Elements</span></span>  
  
|<span data-ttu-id="f97d5-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="f97d5-135">Element</span></span>|<span data-ttu-id="f97d5-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="f97d5-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f97d5-137">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f97d5-137">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f97d5-138">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="f97d5-138">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f97d5-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f97d5-139">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
