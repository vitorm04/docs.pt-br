---
title: Elemento <synchronousReceive>
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399504"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="62f4c-102">\<elemento de > synchronousReceive</span><span class="sxs-lookup"><span data-stu-id="62f4c-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="62f4c-103">Este elemento de configuração é usado para especificar o comportamento de tempo de execução para receber mensagens em um serviço ou aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="62f4c-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="62f4c-104">Ele não tem nenhum atributo ou elemento filho.</span><span class="sxs-lookup"><span data-stu-id="62f4c-104">It does not have any attributes or child elements.</span></span>  
  
<span data-ttu-id="62f4c-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62f4c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62f4c-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="62f4c-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="62f4c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62f4c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="62f4c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62f4c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="62f4c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62f4c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="62f4c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> synchronousReceive**</span><span class="sxs-lookup"><span data-stu-id="62f4c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f4c-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62f4c-111">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62f4c-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="62f4c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="62f4c-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="62f4c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62f4c-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="62f4c-114">Attributes</span></span>  
 <span data-ttu-id="62f4c-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="62f4c-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="62f4c-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="62f4c-116">Child Elements</span></span>  
 <span data-ttu-id="62f4c-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="62f4c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62f4c-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="62f4c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="62f4c-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="62f4c-119">Element</span></span>|<span data-ttu-id="62f4c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="62f4c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62f4c-121">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="62f4c-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="62f4c-122">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="62f4c-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62f4c-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="62f4c-123">Remarks</span></span>  
 <span data-ttu-id="62f4c-124">Use esse comportamento para instruir o ouvinte de canal a usar um recebimento síncrono, em vez do padrão, assíncrono.</span><span class="sxs-lookup"><span data-stu-id="62f4c-124">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="62f4c-125">Windows Communication Foundation (WCF) emite um novo thread para bombeamento para cada canal aceito.</span><span class="sxs-lookup"><span data-stu-id="62f4c-125">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="62f4c-126">Se houver muitos canais, haverá a possibilidade de ficar sem threads.</span><span class="sxs-lookup"><span data-stu-id="62f4c-126">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f4c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62f4c-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
