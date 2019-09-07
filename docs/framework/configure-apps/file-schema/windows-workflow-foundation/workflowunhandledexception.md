---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 29b6d8982e712a0fa595b3103803f1795adea892
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398561"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="0a137-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="0a137-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="0a137-102">Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0a137-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="0a137-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0a137-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0a137-104">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0a137-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="0a137-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0a137-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="0a137-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0a137-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="0a137-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0a137-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="0a137-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> workflowUnhandledException**</span><span class="sxs-lookup"><span data-stu-id="0a137-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a137-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a137-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a137-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0a137-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0a137-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0a137-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a137-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="0a137-112">Attributes</span></span>  
  
|<span data-ttu-id="0a137-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="0a137-113">Attribute</span></span>|<span data-ttu-id="0a137-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a137-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a137-115">ação</span><span class="sxs-lookup"><span data-stu-id="0a137-115">action</span></span>|<span data-ttu-id="0a137-116">Uma cadeia de caracteres que especifica a ação a ser executada quando ocorre uma exceção não tratada.</span><span class="sxs-lookup"><span data-stu-id="0a137-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="0a137-117">Esse atributo é do tipo<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="0a137-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a137-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0a137-118">Child Elements</span></span>  
 <span data-ttu-id="0a137-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0a137-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a137-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0a137-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0a137-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a137-121">Element</span></span>|<span data-ttu-id="0a137-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a137-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a137-123">\<comportamento > de \<percomportamentos ></span><span class="sxs-lookup"><span data-stu-id="0a137-123">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="0a137-124">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="0a137-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a137-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a137-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
