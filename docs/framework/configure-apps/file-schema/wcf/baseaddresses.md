---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: dc4b31e729f9037da101bdf3e6cde28e91b1a070
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277011"
---
# <a name="baseaddresses"></a><span data-ttu-id="e4b06-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="e4b06-101">\<baseAddresses></span></span>
<span data-ttu-id="e4b06-102">Representa uma coleção de `baseAddress` elementos, que são os endereços base para um host de serviço em um ambiente auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="e4b06-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="e4b06-103">Se um endereço base estiver presente, os pontos de extremidade podem ser configurados com endereços em relação ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="e4b06-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="e4b06-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e4b06-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4b06-105">\<client></span><span class="sxs-lookup"><span data-stu-id="e4b06-105">\<client></span></span>  
<span data-ttu-id="e4b06-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="e4b06-106">\<endpoint></span></span>  
<span data-ttu-id="e4b06-107">\<host></span><span class="sxs-lookup"><span data-stu-id="e4b06-107">\<host></span></span>  
<span data-ttu-id="e4b06-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="e4b06-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4b06-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4b06-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="e4b06-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="e4b06-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4b06-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e4b06-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e4b06-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e4b06-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4b06-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="e4b06-113">Attributes</span></span>  
 <span data-ttu-id="e4b06-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e4b06-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4b06-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e4b06-115">Child Elements</span></span>  
  
|<span data-ttu-id="e4b06-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="e4b06-116">Element</span></span>|<span data-ttu-id="e4b06-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4b06-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4b06-118">\<add></span><span class="sxs-lookup"><span data-stu-id="e4b06-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="e4b06-119">Um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="e4b06-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4b06-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e4b06-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e4b06-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e4b06-121">Element</span></span>|<span data-ttu-id="e4b06-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4b06-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4b06-123">\<host></span><span class="sxs-lookup"><span data-stu-id="e4b06-123">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="e4b06-124">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="e4b06-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4b06-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4b06-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="e4b06-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="e4b06-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
