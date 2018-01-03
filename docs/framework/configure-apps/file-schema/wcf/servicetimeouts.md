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
ms.workload: dotnet
ms.openlocfilehash: 0d8bfde535eb417614eee4ec6a2db7985152be33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="c0be3-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="c0be3-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="c0be3-103">Especifica o tempo limite para um serviço.</span><span class="sxs-lookup"><span data-stu-id="c0be3-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="c0be3-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c0be3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c0be3-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="c0be3-105">\<behaviors></span></span>  
<span data-ttu-id="c0be3-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c0be3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c0be3-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="c0be3-107">\<behavior></span></span>  
<span data-ttu-id="c0be3-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="c0be3-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0be3-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0be3-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="c0be3-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="c0be3-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0be3-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c0be3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c0be3-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c0be3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0be3-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="c0be3-113">Attributes</span></span>  
  
|<span data-ttu-id="c0be3-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="c0be3-114">Attribute</span></span>|<span data-ttu-id="c0be3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0be3-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="c0be3-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo que uma transação deve fluir de cliente para servidor.</span><span class="sxs-lookup"><span data-stu-id="c0be3-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="c0be3-117">O padrão é "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="c0be3-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0be3-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c0be3-118">Child Elements</span></span>  
 <span data-ttu-id="c0be3-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c0be3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0be3-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c0be3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c0be3-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0be3-121">Element</span></span>|<span data-ttu-id="c0be3-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0be3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0be3-123">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="c0be3-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c0be3-124">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="c0be3-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0be3-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0be3-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
