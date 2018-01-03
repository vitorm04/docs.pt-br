---
title: elemento &lt;synchronousReceive&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63923121ae96b85bd192899a8d8ad285a3ad5b2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="38b9a-102">elemento &lt;synchronousReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="38b9a-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="38b9a-103">Este elemento de configuração é usado para especificar o comportamento de tempo de execução para receber mensagens em um cliente ou serviço de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="38b9a-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="38b9a-104">Ele não tem atributos ou elementos filho.</span><span class="sxs-lookup"><span data-stu-id="38b9a-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="38b9a-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="38b9a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="38b9a-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="38b9a-106">\<behaviors></span></span>  
<span data-ttu-id="38b9a-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="38b9a-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="38b9a-108">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="38b9a-108">\<behavior></span></span>  
<span data-ttu-id="38b9a-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="38b9a-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b9a-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38b9a-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38b9a-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="38b9a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="38b9a-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="38b9a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38b9a-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="38b9a-113">Attributes</span></span>  
 <span data-ttu-id="38b9a-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="38b9a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="38b9a-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="38b9a-115">Child Elements</span></span>  
 <span data-ttu-id="38b9a-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="38b9a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38b9a-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="38b9a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="38b9a-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="38b9a-118">Element</span></span>|<span data-ttu-id="38b9a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="38b9a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38b9a-120">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="38b9a-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="38b9a-121">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="38b9a-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38b9a-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="38b9a-122">Remarks</span></span>  
 <span data-ttu-id="38b9a-123">Use esse comportamento para instruir o ouvinte de canal para usar um síncrono receber, em vez do padrão assíncrono.</span><span class="sxs-lookup"><span data-stu-id="38b9a-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="38b9a-124">emite um novo thread para a bomba de cada canal aceito.</span><span class="sxs-lookup"><span data-stu-id="38b9a-124"> issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="38b9a-125">Se houver muita canais, há a possibilidade de falta de threads.</span><span class="sxs-lookup"><span data-stu-id="38b9a-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38b9a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38b9a-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
