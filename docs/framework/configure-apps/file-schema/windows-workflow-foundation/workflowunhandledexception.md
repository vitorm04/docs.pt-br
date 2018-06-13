---
title: '&lt;workflowUnhandledException&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: d9db6ecc2e95e0d1ec5738f1d2f4a09a89c57f21
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755130"
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="14fda-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="14fda-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="14fda-103">Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="14fda-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="14fda-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="14fda-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="14fda-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="14fda-105">\<behaviors></span></span>  
<span data-ttu-id="14fda-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="14fda-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="14fda-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="14fda-107">\<behavior></span></span>  
<span data-ttu-id="14fda-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="14fda-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14fda-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14fda-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14fda-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="14fda-110">Attributes and Elements</span></span>  
 <span data-ttu-id="14fda-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="14fda-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14fda-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="14fda-112">Attributes</span></span>  
  
|<span data-ttu-id="14fda-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="14fda-113">Attribute</span></span>|<span data-ttu-id="14fda-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="14fda-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14fda-115">ação</span><span class="sxs-lookup"><span data-stu-id="14fda-115">action</span></span>|<span data-ttu-id="14fda-116">Uma cadeia de caracteres que especifica a ação a ser executada quando ocorre uma exceção não tratada.</span><span class="sxs-lookup"><span data-stu-id="14fda-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="14fda-117">Esse atributo é do tipo<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="14fda-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14fda-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="14fda-118">Child Elements</span></span>  
 <span data-ttu-id="14fda-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="14fda-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14fda-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="14fda-120">Parent Elements</span></span>  
  
|<span data-ttu-id="14fda-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="14fda-121">Element</span></span>|<span data-ttu-id="14fda-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="14fda-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14fda-123">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="14fda-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="14fda-124">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="14fda-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14fda-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14fda-125">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
