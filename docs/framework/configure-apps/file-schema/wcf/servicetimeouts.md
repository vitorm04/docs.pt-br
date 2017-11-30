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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecefda0a3447aa029079fbb3633b05054f42195a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="439e8-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="439e8-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="439e8-103">Especifica o tempo limite para um serviço.</span><span class="sxs-lookup"><span data-stu-id="439e8-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="439e8-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="439e8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="439e8-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="439e8-105">\<behaviors></span></span>  
<span data-ttu-id="439e8-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="439e8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="439e8-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="439e8-107">\<behavior></span></span>  
<span data-ttu-id="439e8-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="439e8-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="439e8-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="439e8-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="439e8-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="439e8-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="439e8-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="439e8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="439e8-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="439e8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="439e8-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="439e8-113">Attributes</span></span>  
  
|<span data-ttu-id="439e8-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="439e8-114">Attribute</span></span>|<span data-ttu-id="439e8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="439e8-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="439e8-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo que uma transação deve fluir de cliente para servidor.</span><span class="sxs-lookup"><span data-stu-id="439e8-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="439e8-117">O padrão é "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="439e8-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="439e8-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="439e8-118">Child Elements</span></span>  
 <span data-ttu-id="439e8-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="439e8-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="439e8-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="439e8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="439e8-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="439e8-121">Element</span></span>|<span data-ttu-id="439e8-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="439e8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="439e8-123">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="439e8-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="439e8-124">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="439e8-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="439e8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="439e8-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
