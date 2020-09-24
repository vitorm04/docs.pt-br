---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 6e3993e43aac746f380a30341fe4ebffcd257c5f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148510"
---
# \<workflowUnhandledException>

<span data-ttu-id="99b63-101">Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="99b63-101">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="99b63-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="99b63-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99b63-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="99b63-103">Attributes and Elements</span></span>  

 <span data-ttu-id="99b63-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="99b63-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99b63-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="99b63-105">Attributes</span></span>  
  
|<span data-ttu-id="99b63-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="99b63-106">Attribute</span></span>|<span data-ttu-id="99b63-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="99b63-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99b63-108">ação</span><span class="sxs-lookup"><span data-stu-id="99b63-108">action</span></span>|<span data-ttu-id="99b63-109">Uma cadeia de caracteres que especifica a ação a ser executada quando ocorre uma exceção não tratada.</span><span class="sxs-lookup"><span data-stu-id="99b63-109">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="99b63-110">Esse atributo é do tipo<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="99b63-110">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99b63-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="99b63-111">Child Elements</span></span>  

 <span data-ttu-id="99b63-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="99b63-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99b63-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="99b63-113">Parent Elements</span></span>  
  
|<span data-ttu-id="99b63-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="99b63-114">Element</span></span>|<span data-ttu-id="99b63-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="99b63-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99b63-116">\<behavior> desse \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="99b63-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="99b63-117">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="99b63-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99b63-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="99b63-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
