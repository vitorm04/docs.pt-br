---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 5c2f0ef7ad509eb5d6c686802c3fe5a75ea1a258
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075509"
---
# <a name="servicetimeouts"></a><span data-ttu-id="14c54-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="14c54-101">\<serviceTimeouts></span></span>
<span data-ttu-id="14c54-102">Especifica o tempo limite para um serviço.</span><span class="sxs-lookup"><span data-stu-id="14c54-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="14c54-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="14c54-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="14c54-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="14c54-104">\<behaviors></span></span>  
<span data-ttu-id="14c54-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="14c54-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="14c54-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="14c54-106">\<behavior></span></span>  
<span data-ttu-id="14c54-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="14c54-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14c54-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14c54-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="14c54-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="14c54-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14c54-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="14c54-110">Attributes and Elements</span></span>  
 <span data-ttu-id="14c54-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="14c54-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14c54-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="14c54-112">Attributes</span></span>  
  
|<span data-ttu-id="14c54-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="14c54-113">Attribute</span></span>|<span data-ttu-id="14c54-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="14c54-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="14c54-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo que uma transação deve fluir de cliente ao servidor.</span><span class="sxs-lookup"><span data-stu-id="14c54-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="14c54-116">O padrão é "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="14c54-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14c54-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="14c54-117">Child Elements</span></span>  
 <span data-ttu-id="14c54-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="14c54-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14c54-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="14c54-119">Parent Elements</span></span>  
  
|<span data-ttu-id="14c54-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="14c54-120">Element</span></span>|<span data-ttu-id="14c54-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="14c54-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14c54-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="14c54-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="14c54-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="14c54-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14c54-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14c54-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
