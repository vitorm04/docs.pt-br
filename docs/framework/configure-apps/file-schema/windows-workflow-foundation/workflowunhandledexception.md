---
title: '&lt;workflowUnhandledException&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4266eb6480c98c7ea1b96f2325a018b0fdcba041
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="f72df-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="f72df-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="f72df-103">Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f72df-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="f72df-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f72df-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f72df-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="f72df-105">\<behaviors></span></span>  
<span data-ttu-id="f72df-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f72df-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f72df-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="f72df-107">\<behavior></span></span>  
<span data-ttu-id="f72df-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="f72df-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f72df-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f72df-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f72df-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f72df-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f72df-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f72df-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f72df-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f72df-112">Attributes</span></span>  
  
|<span data-ttu-id="f72df-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="f72df-113">Attribute</span></span>|<span data-ttu-id="f72df-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f72df-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f72df-115">ação</span><span class="sxs-lookup"><span data-stu-id="f72df-115">action</span></span>|<span data-ttu-id="f72df-116">Uma cadeia de caracteres que especifica a ação a ser executada quando ocorre uma exceção não tratada.</span><span class="sxs-lookup"><span data-stu-id="f72df-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="f72df-117">Esse atributo é do tipo<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="f72df-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f72df-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f72df-118">Child Elements</span></span>  
 <span data-ttu-id="f72df-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f72df-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f72df-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f72df-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f72df-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f72df-121">Element</span></span>|<span data-ttu-id="f72df-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f72df-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f72df-123">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f72df-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f72df-124">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="f72df-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f72df-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f72df-125">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
