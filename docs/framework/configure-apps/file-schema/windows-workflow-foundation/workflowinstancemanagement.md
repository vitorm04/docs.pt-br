---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 532d4c31a582b2b0cd90f6f42b20e00790f9ab02
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148653"
---
# \<workflowInstanceManagement>

<span data-ttu-id="ef408-101">Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.</span><span class="sxs-lookup"><span data-stu-id="ef408-101">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="ef408-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef408-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef408-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ef408-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ef408-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ef408-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef408-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="ef408-105">Attributes</span></span>  
  
|<span data-ttu-id="ef408-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="ef408-106">Attribute</span></span>|<span data-ttu-id="ef408-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef408-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef408-108">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="ef408-108">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="ef408-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ef408-109">Child Elements</span></span>  

 <span data-ttu-id="ef408-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ef408-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef408-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ef408-111">Parent Elements</span></span>  
  
|<span data-ttu-id="ef408-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ef408-112">Element</span></span>|<span data-ttu-id="ef408-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef408-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef408-114">\<behavior> desse \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ef408-114">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="ef408-115">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="ef408-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef408-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="ef408-116">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
