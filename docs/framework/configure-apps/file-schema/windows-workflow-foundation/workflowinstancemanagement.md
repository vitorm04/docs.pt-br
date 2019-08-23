---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: a22c72b7a683e3ecab4344c92e7d835a184a58d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947156"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="ad76f-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="ad76f-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="ad76f-102">Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.</span><span class="sxs-lookup"><span data-stu-id="ad76f-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="ad76f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ad76f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ad76f-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="ad76f-104">\<behaviors></span></span>  
<span data-ttu-id="ad76f-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="ad76f-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="ad76f-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="ad76f-106">\<behavior></span></span>  
<span data-ttu-id="ad76f-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="ad76f-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad76f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad76f-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad76f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ad76f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ad76f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ad76f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad76f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ad76f-111">Attributes</span></span>  
  
|<span data-ttu-id="ad76f-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="ad76f-112">Attribute</span></span>|<span data-ttu-id="ad76f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad76f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad76f-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="ad76f-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="ad76f-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ad76f-115">Child Elements</span></span>  
 <span data-ttu-id="ad76f-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ad76f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad76f-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ad76f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ad76f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="ad76f-118">Element</span></span>|<span data-ttu-id="ad76f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad76f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad76f-120">\<comportamento > de \<percomportamentos ></span><span class="sxs-lookup"><span data-stu-id="ad76f-120">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="ad76f-121">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="ad76f-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad76f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad76f-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
