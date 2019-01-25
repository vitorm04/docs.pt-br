---
title: '&lt;workflowInstanceManagement&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: ba3d9415efc21012b470fd2e9a7f426ca8f3aad1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662056"
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="fa548-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="fa548-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="fa548-103">Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.</span><span class="sxs-lookup"><span data-stu-id="fa548-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="fa548-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fa548-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa548-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="fa548-105">\<behaviors></span></span>  
<span data-ttu-id="fa548-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fa548-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fa548-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="fa548-107">\<behavior></span></span>  
<span data-ttu-id="fa548-108">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="fa548-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa548-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa548-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa548-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fa548-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fa548-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fa548-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa548-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="fa548-112">Attributes</span></span>  
  
|<span data-ttu-id="fa548-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="fa548-113">Attribute</span></span>|<span data-ttu-id="fa548-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa548-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa548-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="fa548-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="fa548-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fa548-116">Child Elements</span></span>  
 <span data-ttu-id="fa548-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fa548-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fa548-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fa548-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fa548-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="fa548-119">Element</span></span>|<span data-ttu-id="fa548-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa548-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa548-121">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fa548-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="fa548-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="fa548-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa548-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa548-123">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
