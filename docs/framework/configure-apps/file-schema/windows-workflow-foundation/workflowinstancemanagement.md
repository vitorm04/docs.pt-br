---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397529"
---
# \<workflowInstanceManagement>
<span data-ttu-id="e8698-101">Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.</span><span class="sxs-lookup"><span data-stu-id="e8698-101">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="e8698-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8698-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8698-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e8698-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e8698-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e8698-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8698-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="e8698-105">Attributes</span></span>  
  
|<span data-ttu-id="e8698-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="e8698-106">Attribute</span></span>|<span data-ttu-id="e8698-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8698-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8698-108">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="e8698-108">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="e8698-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e8698-109">Child Elements</span></span>  
 <span data-ttu-id="e8698-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e8698-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8698-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e8698-111">Parent Elements</span></span>  
  
|<span data-ttu-id="e8698-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e8698-112">Element</span></span>|<span data-ttu-id="e8698-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8698-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8698-114">\<behavior>desse\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e8698-114">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="e8698-115">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="e8698-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8698-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="e8698-116">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
