---
title: '&lt;serviceTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6d2940a4c4615a922efcc74802a82adbe10267c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="8e981-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="8e981-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="8e981-103">Especifica o tempo limite para um serviço.</span><span class="sxs-lookup"><span data-stu-id="8e981-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="8e981-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8e981-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8e981-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="8e981-105">\<behaviors></span></span>  
<span data-ttu-id="8e981-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8e981-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8e981-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="8e981-107">\<behavior></span></span>  
<span data-ttu-id="8e981-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="8e981-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e981-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e981-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="8e981-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="8e981-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e981-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8e981-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8e981-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8e981-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e981-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e981-113">Attributes</span></span>  
  
|<span data-ttu-id="8e981-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="8e981-114">Attribute</span></span>|<span data-ttu-id="8e981-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e981-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="8e981-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo que uma transação deve fluir de cliente para servidor.</span><span class="sxs-lookup"><span data-stu-id="8e981-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="8e981-117">O padrão é "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="8e981-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e981-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8e981-118">Child Elements</span></span>  
 <span data-ttu-id="8e981-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8e981-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e981-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8e981-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8e981-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e981-121">Element</span></span>|<span data-ttu-id="8e981-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e981-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e981-123">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="8e981-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8e981-124">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="8e981-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e981-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e981-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
