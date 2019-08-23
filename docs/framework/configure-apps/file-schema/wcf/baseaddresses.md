---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 059ea4e637ab906d1fde9807a73ac8341f81c574
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926418"
---
# <a name="baseaddresses"></a><span data-ttu-id="fa824-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="fa824-101">\<baseAddresses></span></span>
<span data-ttu-id="fa824-102">Representa uma coleção de `baseAddress` elementos, que são endereços base para um host de serviço em um ambiente de hospedagem interna.</span><span class="sxs-lookup"><span data-stu-id="fa824-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="fa824-103">Se um endereço base estiver presente, os pontos de extremidade poderão ser configurados com endereços relativos ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="fa824-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="fa824-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fa824-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa824-105">\<client></span><span class="sxs-lookup"><span data-stu-id="fa824-105">\<client></span></span>  
<span data-ttu-id="fa824-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="fa824-106">\<endpoint></span></span>  
<span data-ttu-id="fa824-107">\<host></span><span class="sxs-lookup"><span data-stu-id="fa824-107">\<host></span></span>  
<span data-ttu-id="fa824-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="fa824-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa824-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa824-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="fa824-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="fa824-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa824-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fa824-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fa824-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fa824-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa824-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="fa824-113">Attributes</span></span>  
 <span data-ttu-id="fa824-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fa824-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fa824-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fa824-115">Child Elements</span></span>  
  
|<span data-ttu-id="fa824-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="fa824-116">Element</span></span>|<span data-ttu-id="fa824-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa824-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa824-118">\<add></span><span class="sxs-lookup"><span data-stu-id="fa824-118">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="fa824-119">Um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="fa824-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa824-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fa824-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fa824-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="fa824-121">Element</span></span>|<span data-ttu-id="fa824-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa824-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa824-123">\<host></span><span class="sxs-lookup"><span data-stu-id="fa824-123">\<host></span></span>](host.md)|<span data-ttu-id="fa824-124">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="fa824-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa824-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa824-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="fa824-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="fa824-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
