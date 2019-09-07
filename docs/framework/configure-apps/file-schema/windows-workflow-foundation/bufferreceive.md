---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398842"
---
# <a name="bufferreceive"></a><span data-ttu-id="efad5-101">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="efad5-101">\<bufferReceive></span></span>
<span data-ttu-id="efad5-102">Um comportamento de serviço que permite que um serviço a ser usado em buffer recebe o processamento, que permite que um serviço de fluxo de trabalho processar mensagens de fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="efad5-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="efad5-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="efad5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="efad5-104">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="efad5-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="efad5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="efad5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="efad5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="efad5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="efad5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="efad5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="efad5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> bufferReceive**</span><span class="sxs-lookup"><span data-stu-id="efad5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efad5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="efad5-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efad5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="efad5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="efad5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="efad5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efad5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="efad5-112">Attributes</span></span>  
  
|<span data-ttu-id="efad5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="efad5-113">Attribute</span></span>|<span data-ttu-id="efad5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="efad5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efad5-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="efad5-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="efad5-116">Um inteiro que especifica o número máximo de mensagens permitido para cada canal pendentes.</span><span class="sxs-lookup"><span data-stu-id="efad5-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="efad5-117">O valor padrão é 512.</span><span class="sxs-lookup"><span data-stu-id="efad5-117">The default value is 512.</span></span> <span data-ttu-id="efad5-118">Essa propriedade limita o número de mensagens de fora de ordem que pode ser recebido por um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="efad5-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efad5-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="efad5-119">Child Elements</span></span>  
 <span data-ttu-id="efad5-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="efad5-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="efad5-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="efad5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="efad5-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="efad5-122">Element</span></span>|<span data-ttu-id="efad5-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="efad5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efad5-124">\<comportamento > de \<percomportamentos ></span><span class="sxs-lookup"><span data-stu-id="efad5-124">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="efad5-125">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="efad5-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efad5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="efad5-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
