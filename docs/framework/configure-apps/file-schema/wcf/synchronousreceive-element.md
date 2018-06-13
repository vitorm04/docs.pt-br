---
title: elemento &lt;synchronousReceive&gt;
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: af1ca2ee1fe3c03c33f05e0c30c7b843b3720a36
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753255"
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="40f7a-102">elemento &lt;synchronousReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="40f7a-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="40f7a-103">Este elemento de configuração é usado para especificar o comportamento de tempo de execução para receber mensagens em um cliente ou serviço de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40f7a-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="40f7a-104">Ele não tem atributos ou elementos filho.</span><span class="sxs-lookup"><span data-stu-id="40f7a-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="40f7a-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="40f7a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="40f7a-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="40f7a-106">\<behaviors></span></span>  
<span data-ttu-id="40f7a-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="40f7a-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="40f7a-108">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="40f7a-108">\<behavior></span></span>  
<span data-ttu-id="40f7a-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="40f7a-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f7a-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40f7a-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40f7a-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="40f7a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="40f7a-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="40f7a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40f7a-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="40f7a-113">Attributes</span></span>  
 <span data-ttu-id="40f7a-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="40f7a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40f7a-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="40f7a-115">Child Elements</span></span>  
 <span data-ttu-id="40f7a-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="40f7a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40f7a-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="40f7a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="40f7a-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="40f7a-118">Element</span></span>|<span data-ttu-id="40f7a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="40f7a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40f7a-120">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="40f7a-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="40f7a-121">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="40f7a-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40f7a-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="40f7a-122">Remarks</span></span>  
 <span data-ttu-id="40f7a-123">Use esse comportamento para instruir o ouvinte de canal para usar um síncrono receber, em vez do padrão assíncrono.</span><span class="sxs-lookup"><span data-stu-id="40f7a-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="40f7a-124">Windows Communication Foundation (WCF) emite um novo thread para a bomba de cada canal aceito.</span><span class="sxs-lookup"><span data-stu-id="40f7a-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="40f7a-125">Se houver muita canais, há a possibilidade de falta de threads.</span><span class="sxs-lookup"><span data-stu-id="40f7a-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f7a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40f7a-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
