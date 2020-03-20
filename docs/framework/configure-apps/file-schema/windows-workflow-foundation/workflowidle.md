---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151839"
---
# <a name="workflowidle"></a><span data-ttu-id="9615a-101">\<fluxo de trabalho> de locomoção</span><span class="sxs-lookup"><span data-stu-id="9615a-101">\<workflowIdle></span></span>
<span data-ttu-id="9615a-102">Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.</span><span class="sxs-lookup"><span data-stu-id="9615a-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="9615a-103">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9615a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9615a-104">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9615a-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="9615a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportamentos>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9615a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="9615a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviçocomportamentos>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9615a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="9615a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportamento>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9615a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="9615a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<fluxo de trabalho>de risada**</span><span class="sxs-lookup"><span data-stu-id="9615a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9615a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9615a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9615a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9615a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9615a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9615a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9615a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9615a-112">Attributes</span></span>  
  
|<span data-ttu-id="9615a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="9615a-113">Attribute</span></span>|<span data-ttu-id="9615a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9615a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9615a-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="9615a-115">timeToPersist</span></span>|<span data-ttu-id="9615a-116">Um valor de Timespan que especifica a duração entre o momento em que o fluxo de trabalho fica ocioso e é mantido.</span><span class="sxs-lookup"><span data-stu-id="9615a-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="9615a-117">O valor padrão é TimeSpan. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="9615a-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="9615a-118">A duração começa a decorrer quando a instância de fluxo de trabalho fica ociosa.</span><span class="sxs-lookup"><span data-stu-id="9615a-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="9615a-119">Esse atributo é útil se você quiser manter uma instância de fluxo de trabalho mais agressivamente enquanto mantém a instância na memória para o máximo possível.</span><span class="sxs-lookup"><span data-stu-id="9615a-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="9615a-120">Este atributo só é válido se seu valor for menor do que o atributo **timeToUnload.**</span><span class="sxs-lookup"><span data-stu-id="9615a-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="9615a-121">Se for maior, ela será ignorada.</span><span class="sxs-lookup"><span data-stu-id="9615a-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="9615a-122">Se esse atributo se escorrer antes do valor especificado pelo atributo **timeToUnload,** a persistência deve ser concluída antes que o fluxo de trabalho seja descarregado.</span><span class="sxs-lookup"><span data-stu-id="9615a-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="9615a-123">Isso significa que a operação pode ser atrasada até que o fluxo de trabalho é mantido.</span><span class="sxs-lookup"><span data-stu-id="9615a-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="9615a-124">A camada de persistência é responsável por gerenciar quaisquer tentativas de erros transitórios e apenas lança exceções em erros não recuperáveis.</span><span class="sxs-lookup"><span data-stu-id="9615a-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="9615a-125">Portanto, todas as exceções geradas durante a persistência são tratadas como fatal e a instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="9615a-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="9615a-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="9615a-126">timeToUnload</span></span>|<span data-ttu-id="9615a-127">Um valor de Timespan que especifica a duração entre o momento em que o fluxo de trabalho fica ocioso e é descarregado.</span><span class="sxs-lookup"><span data-stu-id="9615a-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="9615a-128">O valor padrão é 1 minuto.</span><span class="sxs-lookup"><span data-stu-id="9615a-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="9615a-129">Descarregar um fluxo de trabalho significa que ele também é mantido.</span><span class="sxs-lookup"><span data-stu-id="9615a-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="9615a-130">Se esse atributo for definido como zero, a instância de fluxo de trabalho é mantida e descarregada imediatamente após o fluxo de trabalho fica ocioso.</span><span class="sxs-lookup"><span data-stu-id="9615a-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="9615a-131">Definir esse atributo como TimeSpan efetivamente desabilita a operação.</span><span class="sxs-lookup"><span data-stu-id="9615a-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="9615a-132">Instâncias de fluxo de trabalho ocioso nunca são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="9615a-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9615a-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9615a-133">Child Elements</span></span>  
 <span data-ttu-id="9615a-134">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9615a-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9615a-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9615a-135">Parent Elements</span></span>  
  
|<span data-ttu-id="9615a-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="9615a-136">Element</span></span>|<span data-ttu-id="9615a-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="9615a-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9615a-138">\<> de \<comportamento de>de serviços</span><span class="sxs-lookup"><span data-stu-id="9615a-138">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="9615a-139">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="9615a-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9615a-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="9615a-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
