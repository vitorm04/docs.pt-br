---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398561"
---
# \<workflowUnhandledException>
<span data-ttu-id="00ad9-101">Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="00ad9-101">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="00ad9-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00ad9-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00ad9-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="00ad9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="00ad9-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="00ad9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00ad9-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="00ad9-105">Attributes</span></span>  
  
|<span data-ttu-id="00ad9-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="00ad9-106">Attribute</span></span>|<span data-ttu-id="00ad9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="00ad9-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00ad9-108">ação</span><span class="sxs-lookup"><span data-stu-id="00ad9-108">action</span></span>|<span data-ttu-id="00ad9-109">Uma cadeia de caracteres que especifica a ação a ser executada quando ocorre uma exceção não tratada.</span><span class="sxs-lookup"><span data-stu-id="00ad9-109">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="00ad9-110">Esse atributo é do tipo<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="00ad9-110">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00ad9-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="00ad9-111">Child Elements</span></span>  
 <span data-ttu-id="00ad9-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="00ad9-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00ad9-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="00ad9-113">Parent Elements</span></span>  
  
|<span data-ttu-id="00ad9-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="00ad9-114">Element</span></span>|<span data-ttu-id="00ad9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="00ad9-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00ad9-116">\<behavior>desse\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="00ad9-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="00ad9-117">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="00ad9-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00ad9-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="00ad9-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
