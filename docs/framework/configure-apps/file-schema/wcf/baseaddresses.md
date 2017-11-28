---
title: '&lt;baseAddresses&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4bf698b64b528b0ea109223a2d94e6725c8ce6b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="b75c7-102">&lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="b75c7-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="b75c7-103">Representa uma coleção de `baseAddress` elementos, que são endereços de base para um host de serviço em um ambiente de hospedagem interna.</span><span class="sxs-lookup"><span data-stu-id="b75c7-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="b75c7-104">Se um endereço base estiver presente, os pontos de extremidade podem ser configurados com endereços em relação ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="b75c7-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="b75c7-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b75c7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b75c7-106">\<cliente ></span><span class="sxs-lookup"><span data-stu-id="b75c7-106">\<client></span></span>  
<span data-ttu-id="b75c7-107">\<ponto de extremidade ></span><span class="sxs-lookup"><span data-stu-id="b75c7-107">\<endpoint></span></span>  
<span data-ttu-id="b75c7-108">\<host ></span><span class="sxs-lookup"><span data-stu-id="b75c7-108">\<host></span></span>  
<span data-ttu-id="b75c7-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="b75c7-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b75c7-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b75c7-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="b75c7-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="b75c7-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b75c7-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b75c7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b75c7-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b75c7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b75c7-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="b75c7-114">Attributes</span></span>  
 <span data-ttu-id="b75c7-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b75c7-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b75c7-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b75c7-116">Child Elements</span></span>  
  
|<span data-ttu-id="b75c7-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="b75c7-117">Element</span></span>|<span data-ttu-id="b75c7-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="b75c7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b75c7-119">\<add></span><span class="sxs-lookup"><span data-stu-id="b75c7-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="b75c7-120">Um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="b75c7-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b75c7-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b75c7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b75c7-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b75c7-122">Element</span></span>|<span data-ttu-id="b75c7-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b75c7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b75c7-124">\<host ></span><span class="sxs-lookup"><span data-stu-id="b75c7-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="b75c7-125">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="b75c7-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b75c7-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b75c7-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="b75c7-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="b75c7-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
