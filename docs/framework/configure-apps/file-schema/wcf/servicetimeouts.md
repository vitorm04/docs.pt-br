---
title: '&lt;serviceTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 4cb4b4ae6fe01430989d9ee5f3d94b16778595aa
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148468"
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="2a99e-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="2a99e-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="2a99e-103">Especifica o tempo limite para um serviço.</span><span class="sxs-lookup"><span data-stu-id="2a99e-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="2a99e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a99e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a99e-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="2a99e-105">\<behaviors></span></span>  
<span data-ttu-id="2a99e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2a99e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="2a99e-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="2a99e-107">\<behavior></span></span>  
<span data-ttu-id="2a99e-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="2a99e-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a99e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a99e-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="2a99e-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="2a99e-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a99e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2a99e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2a99e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2a99e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a99e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a99e-113">Attributes</span></span>  
  
|<span data-ttu-id="2a99e-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="2a99e-114">Attribute</span></span>|<span data-ttu-id="2a99e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a99e-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="2a99e-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo que uma transação deve fluir de cliente ao servidor.</span><span class="sxs-lookup"><span data-stu-id="2a99e-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="2a99e-117">O padrão é "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="2a99e-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a99e-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2a99e-118">Child Elements</span></span>  
 <span data-ttu-id="2a99e-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2a99e-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a99e-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a99e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2a99e-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a99e-121">Element</span></span>|<span data-ttu-id="2a99e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a99e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a99e-123">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="2a99e-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2a99e-124">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="2a99e-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a99e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a99e-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
