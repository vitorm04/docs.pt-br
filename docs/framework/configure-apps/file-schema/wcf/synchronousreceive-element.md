---
title: '<synchronousReceive> Elemento '
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: 20390f747c8beaccba1cfea7a9ea0ed366037ecb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166537"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="631e1-102">\<synchronousReceive > elemento</span><span class="sxs-lookup"><span data-stu-id="631e1-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="631e1-103">Este elemento de configuração é usado para especificar o comportamento de tempo de execução para receber mensagens em um cliente ou serviço de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="631e1-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="631e1-104">Ele não tem nenhum atributo ou elemento filho.</span><span class="sxs-lookup"><span data-stu-id="631e1-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="631e1-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="631e1-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="631e1-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="631e1-106">\<behaviors></span></span>  
<span data-ttu-id="631e1-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="631e1-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="631e1-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="631e1-108">\<behavior></span></span>  
<span data-ttu-id="631e1-109">\<synchronousReceive></span><span class="sxs-lookup"><span data-stu-id="631e1-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="631e1-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="631e1-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="631e1-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="631e1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="631e1-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="631e1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="631e1-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="631e1-113">Attributes</span></span>  
 <span data-ttu-id="631e1-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="631e1-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="631e1-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="631e1-115">Child Elements</span></span>  
 <span data-ttu-id="631e1-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="631e1-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="631e1-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="631e1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="631e1-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="631e1-118">Element</span></span>|<span data-ttu-id="631e1-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="631e1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="631e1-120">\<behavior></span><span class="sxs-lookup"><span data-stu-id="631e1-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="631e1-121">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="631e1-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="631e1-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="631e1-122">Remarks</span></span>  
 <span data-ttu-id="631e1-123">Use esse comportamento para instruir o ouvinte de canais para receber um síncrono de uso, em vez do padrão, assíncrono.</span><span class="sxs-lookup"><span data-stu-id="631e1-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="631e1-124">Windows Communication Foundation (WCF) emite um novo thread para a bomba para cada canal aceito.</span><span class="sxs-lookup"><span data-stu-id="631e1-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="631e1-125">Se houver muitos canais, há a possibilidade de falta de threads.</span><span class="sxs-lookup"><span data-stu-id="631e1-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="631e1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="631e1-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
