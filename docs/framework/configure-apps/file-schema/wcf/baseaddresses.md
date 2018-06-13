---
title: '&lt;BaseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 8de962cc70e1399dd1e9459473055651f9aca5fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747480"
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="24aed-102">&lt;BaseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="24aed-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="24aed-103">Representa uma coleção de `baseAddress` elementos, que são endereços de base para um host de serviço em um ambiente de hospedagem interna.</span><span class="sxs-lookup"><span data-stu-id="24aed-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="24aed-104">Se um endereço base estiver presente, os pontos de extremidade podem ser configurados com endereços em relação ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="24aed-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="24aed-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="24aed-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="24aed-106">\<client></span><span class="sxs-lookup"><span data-stu-id="24aed-106">\<client></span></span>  
<span data-ttu-id="24aed-107">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="24aed-107">\<endpoint></span></span>  
<span data-ttu-id="24aed-108">\<host ></span><span class="sxs-lookup"><span data-stu-id="24aed-108">\<host></span></span>  
<span data-ttu-id="24aed-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="24aed-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24aed-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24aed-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="24aed-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="24aed-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24aed-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="24aed-112">Attributes and Elements</span></span>  
 <span data-ttu-id="24aed-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="24aed-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24aed-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="24aed-114">Attributes</span></span>  
 <span data-ttu-id="24aed-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="24aed-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24aed-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="24aed-116">Child Elements</span></span>  
  
|<span data-ttu-id="24aed-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="24aed-117">Element</span></span>|<span data-ttu-id="24aed-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="24aed-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24aed-119">\<add></span><span class="sxs-lookup"><span data-stu-id="24aed-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="24aed-120">Um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="24aed-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24aed-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="24aed-121">Parent Elements</span></span>  
  
|<span data-ttu-id="24aed-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="24aed-122">Element</span></span>|<span data-ttu-id="24aed-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="24aed-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24aed-124">\<host ></span><span class="sxs-lookup"><span data-stu-id="24aed-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="24aed-125">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="24aed-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24aed-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24aed-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="24aed-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="24aed-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
