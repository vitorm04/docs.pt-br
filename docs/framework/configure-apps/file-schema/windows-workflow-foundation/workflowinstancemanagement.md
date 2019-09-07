---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397529"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="fbbdb-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="fbbdb-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="fbbdb-102">Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="fbbdb-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fbbdb-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fbbdb-104">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fbbdb-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="fbbdb-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fbbdb-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="fbbdb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fbbdb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="fbbdb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fbbdb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="fbbdb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> workflowInstanceManagement**</span><span class="sxs-lookup"><span data-stu-id="fbbdb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbbdb-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbbdb-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbbdb-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fbbdb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fbbdb-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbbdb-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="fbbdb-112">Attributes</span></span>  
  
|<span data-ttu-id="fbbdb-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="fbbdb-113">Attribute</span></span>|<span data-ttu-id="fbbdb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbbdb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fbbdb-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="fbbdb-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="fbbdb-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fbbdb-116">Child Elements</span></span>  
 <span data-ttu-id="fbbdb-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fbbdb-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fbbdb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fbbdb-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="fbbdb-119">Element</span></span>|<span data-ttu-id="fbbdb-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbbdb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbbdb-121">\<comportamento > de \<percomportamentos ></span><span class="sxs-lookup"><span data-stu-id="fbbdb-121">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="fbbdb-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbbdb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbbdb-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
