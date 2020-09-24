---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 790e852eb515e19afc324f6e1c25db81ed22999c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148666"
---
# \<workflowIdle>

<span data-ttu-id="d9993-101">Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.</span><span class="sxs-lookup"><span data-stu-id="d9993-101">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a><span data-ttu-id="d9993-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="d9993-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9993-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d9993-103">Attributes and Elements</span></span>  

 <span data-ttu-id="d9993-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d9993-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9993-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="d9993-105">Attributes</span></span>  
  
|<span data-ttu-id="d9993-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="d9993-106">Attribute</span></span>|<span data-ttu-id="d9993-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9993-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9993-108">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="d9993-108">timeToPersist</span></span>|<span data-ttu-id="d9993-109">Um valor de Timespan que especifica a duração entre o momento em que o fluxo de trabalho fica ocioso e é mantido.</span><span class="sxs-lookup"><span data-stu-id="d9993-109">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="d9993-110">O valor padrão é TimeSpan. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="d9993-110">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="d9993-111">A duração começa a decorrer quando a instância de fluxo de trabalho fica ociosa.</span><span class="sxs-lookup"><span data-stu-id="d9993-111">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="d9993-112">Esse atributo é útil se você quiser manter uma instância de fluxo de trabalho mais agressivamente enquanto mantém a instância na memória para o máximo possível.</span><span class="sxs-lookup"><span data-stu-id="d9993-112">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="d9993-113">Esse atributo só será válido se seu valor for menor que o atributo **TimeToUnload** .</span><span class="sxs-lookup"><span data-stu-id="d9993-113">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="d9993-114">Se for maior, ela será ignorada.</span><span class="sxs-lookup"><span data-stu-id="d9993-114">If it is greater, it is ignored.</span></span> <span data-ttu-id="d9993-115">Se esse atributo decorrer antes do valor especificado pelo atributo **TimeToUnload** , a persistência deverá ser concluída antes que o fluxo de trabalho seja descarregado.</span><span class="sxs-lookup"><span data-stu-id="d9993-115">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="d9993-116">Isso significa que a operação pode ser atrasada até que o fluxo de trabalho é mantido.</span><span class="sxs-lookup"><span data-stu-id="d9993-116">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="d9993-117">A camada de persistência é responsável por gerenciar quaisquer tentativas de erros transitórios e apenas lança exceções em erros não recuperáveis.</span><span class="sxs-lookup"><span data-stu-id="d9993-117">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="d9993-118">Portanto, todas as exceções geradas durante a persistência são tratadas como fatal e a instância de fluxo de trabalho será anulada.</span><span class="sxs-lookup"><span data-stu-id="d9993-118">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="d9993-119">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="d9993-119">timeToUnload</span></span>|<span data-ttu-id="d9993-120">Um valor de Timespan que especifica a duração entre o momento em que o fluxo de trabalho fica ocioso e é descarregado.</span><span class="sxs-lookup"><span data-stu-id="d9993-120">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="d9993-121">O valor padrão é 1 minuto.</span><span class="sxs-lookup"><span data-stu-id="d9993-121">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="d9993-122">Descarregar um fluxo de trabalho significa que ele também é mantido.</span><span class="sxs-lookup"><span data-stu-id="d9993-122">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="d9993-123">Se esse atributo for definido como zero, a instância de fluxo de trabalho é mantida e descarregada imediatamente após o fluxo de trabalho fica ocioso.</span><span class="sxs-lookup"><span data-stu-id="d9993-123">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="d9993-124">Definir esse atributo como TimeSpan efetivamente desabilita a operação.</span><span class="sxs-lookup"><span data-stu-id="d9993-124">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="d9993-125">Instâncias de fluxo de trabalho ocioso nunca são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="d9993-125">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9993-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d9993-126">Child Elements</span></span>  

 <span data-ttu-id="d9993-127">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d9993-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9993-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d9993-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d9993-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9993-129">Element</span></span>|<span data-ttu-id="d9993-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9993-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9993-131">\<behavior> desse \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d9993-131">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="d9993-132">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="d9993-132">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9993-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9993-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
