---
title: '&lt;BaseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 0af5dee41c6adf560c90874e6e9a44b62c5decc6
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147338"
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="69ddd-102">&lt;BaseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="69ddd-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="69ddd-103">Representa uma coleção de `baseAddress` elementos, que são os endereços base para um host de serviço em um ambiente auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="69ddd-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="69ddd-104">Se um endereço base estiver presente, os pontos de extremidade podem ser configurados com endereços em relação ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="69ddd-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="69ddd-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="69ddd-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="69ddd-106">\<client></span><span class="sxs-lookup"><span data-stu-id="69ddd-106">\<client></span></span>  
<span data-ttu-id="69ddd-107">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="69ddd-107">\<endpoint></span></span>  
<span data-ttu-id="69ddd-108">\<host ></span><span class="sxs-lookup"><span data-stu-id="69ddd-108">\<host></span></span>  
<span data-ttu-id="69ddd-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="69ddd-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69ddd-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69ddd-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="69ddd-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="69ddd-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69ddd-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="69ddd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="69ddd-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="69ddd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69ddd-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="69ddd-114">Attributes</span></span>  
 <span data-ttu-id="69ddd-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="69ddd-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69ddd-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="69ddd-116">Child Elements</span></span>  
  
|<span data-ttu-id="69ddd-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="69ddd-117">Element</span></span>|<span data-ttu-id="69ddd-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="69ddd-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69ddd-119">\<add></span><span class="sxs-lookup"><span data-stu-id="69ddd-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="69ddd-120">Um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="69ddd-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69ddd-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="69ddd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="69ddd-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="69ddd-122">Element</span></span>|<span data-ttu-id="69ddd-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="69ddd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69ddd-124">\<host ></span><span class="sxs-lookup"><span data-stu-id="69ddd-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="69ddd-125">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="69ddd-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69ddd-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69ddd-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="69ddd-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="69ddd-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
