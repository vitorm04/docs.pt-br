---
title: '&lt;serviceTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: f7aa623ee387f67f3bbff32249d3695049359cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524462"
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="3584f-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="3584f-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="3584f-103">Especifica o tempo limite para um serviço.</span><span class="sxs-lookup"><span data-stu-id="3584f-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="3584f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3584f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3584f-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="3584f-105">\<behaviors></span></span>  
<span data-ttu-id="3584f-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3584f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="3584f-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="3584f-107">\<behavior></span></span>  
<span data-ttu-id="3584f-108">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="3584f-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3584f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3584f-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="3584f-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="3584f-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3584f-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3584f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3584f-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3584f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3584f-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="3584f-113">Attributes</span></span>  
  
|<span data-ttu-id="3584f-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="3584f-114">Attribute</span></span>|<span data-ttu-id="3584f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3584f-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="3584f-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo que uma transação deve fluir de cliente ao servidor.</span><span class="sxs-lookup"><span data-stu-id="3584f-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="3584f-117">O padrão é "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="3584f-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3584f-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3584f-118">Child Elements</span></span>  
 <span data-ttu-id="3584f-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3584f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3584f-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3584f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3584f-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3584f-121">Element</span></span>|<span data-ttu-id="3584f-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3584f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3584f-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="3584f-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="3584f-124">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="3584f-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3584f-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3584f-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
