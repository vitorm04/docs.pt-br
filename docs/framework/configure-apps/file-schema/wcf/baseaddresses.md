---
title: '&lt;baseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 34d400e74b24e9eb4140d1b43597b0217b23d80c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730120"
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="07b80-102">&lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="07b80-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="07b80-103">Representa uma coleção de `baseAddress` elementos, que são os endereços base para um host de serviço em um ambiente auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="07b80-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="07b80-104">Se um endereço base estiver presente, os pontos de extremidade podem ser configurados com endereços em relação ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="07b80-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="07b80-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="07b80-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="07b80-106">\<client></span><span class="sxs-lookup"><span data-stu-id="07b80-106">\<client></span></span>  
<span data-ttu-id="07b80-107">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="07b80-107">\<endpoint></span></span>  
<span data-ttu-id="07b80-108">\<host></span><span class="sxs-lookup"><span data-stu-id="07b80-108">\<host></span></span>  
<span data-ttu-id="07b80-109">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="07b80-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07b80-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07b80-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="07b80-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="07b80-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07b80-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="07b80-112">Attributes and Elements</span></span>  
 <span data-ttu-id="07b80-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="07b80-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07b80-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="07b80-114">Attributes</span></span>  
 <span data-ttu-id="07b80-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="07b80-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="07b80-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="07b80-116">Child Elements</span></span>  
  
|<span data-ttu-id="07b80-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="07b80-117">Element</span></span>|<span data-ttu-id="07b80-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="07b80-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07b80-119">\<add></span><span class="sxs-lookup"><span data-stu-id="07b80-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="07b80-120">Um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="07b80-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="07b80-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="07b80-121">Parent Elements</span></span>  
  
|<span data-ttu-id="07b80-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="07b80-122">Element</span></span>|<span data-ttu-id="07b80-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="07b80-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07b80-124">\<host></span><span class="sxs-lookup"><span data-stu-id="07b80-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="07b80-125">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="07b80-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07b80-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07b80-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="07b80-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="07b80-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
