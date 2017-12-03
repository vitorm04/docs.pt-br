---
title: '&lt;workflowInstanceManagement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28e0f2b0ed88ee73edb52a8c18346746beb34771
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="5c7fe-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="5c7fe-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="5c7fe-103">Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.</span><span class="sxs-lookup"><span data-stu-id="5c7fe-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="5c7fe-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5c7fe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5c7fe-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="5c7fe-105">\<behaviors></span></span>  
<span data-ttu-id="5c7fe-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5c7fe-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5c7fe-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="5c7fe-107">\<behavior></span></span>  
<span data-ttu-id="5c7fe-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="5c7fe-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c7fe-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c7fe-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c7fe-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5c7fe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5c7fe-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5c7fe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c7fe-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5c7fe-112">Attributes</span></span>  
  
|<span data-ttu-id="5c7fe-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5c7fe-113">Attribute</span></span>|<span data-ttu-id="5c7fe-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c7fe-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c7fe-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="5c7fe-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="5c7fe-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5c7fe-116">Child Elements</span></span>  
 <span data-ttu-id="5c7fe-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5c7fe-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c7fe-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5c7fe-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5c7fe-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c7fe-119">Element</span></span>|<span data-ttu-id="5c7fe-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c7fe-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c7fe-121">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5c7fe-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="5c7fe-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="5c7fe-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c7fe-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c7fe-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
