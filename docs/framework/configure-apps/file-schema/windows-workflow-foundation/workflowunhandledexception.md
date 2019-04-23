---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: cfe3350ac42d1e0e837b79f25753f62dc2051dd2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096238"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="9ac99-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="9ac99-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="9ac99-102">Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9ac99-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="9ac99-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9ac99-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9ac99-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="9ac99-104">\<behaviors></span></span>  
<span data-ttu-id="9ac99-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9ac99-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="9ac99-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="9ac99-106">\<behavior></span></span>  
<span data-ttu-id="9ac99-107">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="9ac99-107">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ac99-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ac99-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ac99-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9ac99-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9ac99-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9ac99-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ac99-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9ac99-111">Attributes</span></span>  
  
|<span data-ttu-id="9ac99-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="9ac99-112">Attribute</span></span>|<span data-ttu-id="9ac99-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ac99-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ac99-114">ação</span><span class="sxs-lookup"><span data-stu-id="9ac99-114">action</span></span>|<span data-ttu-id="9ac99-115">Uma cadeia de caracteres que especifica a ação a ser executada quando ocorre uma exceção não tratada.</span><span class="sxs-lookup"><span data-stu-id="9ac99-115">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="9ac99-116">Esse atributo é do tipo<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="9ac99-116">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ac99-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9ac99-117">Child Elements</span></span>  
 <span data-ttu-id="9ac99-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9ac99-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ac99-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9ac99-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9ac99-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="9ac99-120">Element</span></span>|<span data-ttu-id="9ac99-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ac99-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ac99-122">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9ac99-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="9ac99-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="9ac99-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ac99-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ac99-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
