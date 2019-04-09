---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 98bc1b24da6e65a11a39d133057c1bb55b003a58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191608"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="9eef9-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="9eef9-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="9eef9-102">Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.</span><span class="sxs-lookup"><span data-stu-id="9eef9-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="9eef9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9eef9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9eef9-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="9eef9-104">\<behaviors></span></span>  
<span data-ttu-id="9eef9-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9eef9-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="9eef9-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="9eef9-106">\<behavior></span></span>  
<span data-ttu-id="9eef9-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="9eef9-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eef9-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9eef9-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eef9-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9eef9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9eef9-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9eef9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eef9-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9eef9-111">Attributes</span></span>  
  
|<span data-ttu-id="9eef9-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="9eef9-112">Attribute</span></span>|<span data-ttu-id="9eef9-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9eef9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9eef9-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="9eef9-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="9eef9-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9eef9-115">Child Elements</span></span>  
 <span data-ttu-id="9eef9-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9eef9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9eef9-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9eef9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9eef9-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="9eef9-118">Element</span></span>|<span data-ttu-id="9eef9-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9eef9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9eef9-120">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9eef9-120">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="9eef9-121">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="9eef9-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9eef9-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9eef9-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
