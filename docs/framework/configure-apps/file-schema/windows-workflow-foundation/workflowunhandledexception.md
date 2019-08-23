---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: c46d1fb9eb853e57c7ad1b97eb9a22556cdfb7d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913105"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="1d5b9-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="1d5b9-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="1d5b9-102">Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1d5b9-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="1d5b9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1d5b9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1d5b9-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="1d5b9-104">\<behaviors></span></span>  
<span data-ttu-id="1d5b9-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="1d5b9-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="1d5b9-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="1d5b9-106">\<behavior></span></span>  
<span data-ttu-id="1d5b9-107">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="1d5b9-107">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d5b9-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d5b9-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d5b9-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1d5b9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1d5b9-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1d5b9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d5b9-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="1d5b9-111">Attributes</span></span>  
  
|<span data-ttu-id="1d5b9-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="1d5b9-112">Attribute</span></span>|<span data-ttu-id="1d5b9-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d5b9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d5b9-114">ação</span><span class="sxs-lookup"><span data-stu-id="1d5b9-114">action</span></span>|<span data-ttu-id="1d5b9-115">Uma cadeia de caracteres que especifica a ação a ser executada quando ocorre uma exceção não tratada.</span><span class="sxs-lookup"><span data-stu-id="1d5b9-115">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="1d5b9-116">Esse atributo é do tipo<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="1d5b9-116">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d5b9-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1d5b9-117">Child Elements</span></span>  
 <span data-ttu-id="1d5b9-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1d5b9-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d5b9-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1d5b9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1d5b9-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d5b9-120">Element</span></span>|<span data-ttu-id="1d5b9-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d5b9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d5b9-122">\<comportamento > de \<percomportamentos ></span><span class="sxs-lookup"><span data-stu-id="1d5b9-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="1d5b9-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="1d5b9-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d5b9-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d5b9-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
