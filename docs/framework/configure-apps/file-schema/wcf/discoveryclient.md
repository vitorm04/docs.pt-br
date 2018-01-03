---
title: '&lt;discoveryClient&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c9cbdb61152a5315aaf919e3a3c58d9329449e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="b32a6-102">&lt;discoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="b32a6-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="b32a6-103">Um elemento de configuração para criar uma associação personalizada que permite que um aplicativo cliente para procurar por um serviço detectável e encontre seu endereço em tempo de execução automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b32a6-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="b32a6-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b32a6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b32a6-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="b32a6-105">\<bindings></span></span>  
<span data-ttu-id="b32a6-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b32a6-106">\<customBinding></span></span>  
<span data-ttu-id="b32a6-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="b32a6-107">\<binding></span></span>  
<span data-ttu-id="b32a6-108">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="b32a6-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b32a6-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b32a6-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String" >
  <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String" namespace="String" />
    <contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b32a6-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b32a6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b32a6-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b32a6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b32a6-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b32a6-112">Attributes</span></span>  
  
|<span data-ttu-id="b32a6-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b32a6-113">Attribute</span></span>|<span data-ttu-id="b32a6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b32a6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b32a6-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="b32a6-115">discoveryEndpoint</span></span>|<span data-ttu-id="b32a6-116">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente para procurar por um serviço detectável e encontre seu endereço em tempo de execução automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b32a6-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b32a6-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b32a6-117">Child Elements</span></span>  
  
|<span data-ttu-id="b32a6-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="b32a6-118">Element</span></span>|<span data-ttu-id="b32a6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b32a6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b32a6-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b32a6-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="b32a6-121">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar para um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="b32a6-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="b32a6-122">Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="b32a6-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b32a6-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b32a6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b32a6-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="b32a6-124">Element</span></span>|<span data-ttu-id="b32a6-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="b32a6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b32a6-126">\<associação ></span><span class="sxs-lookup"><span data-stu-id="b32a6-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b32a6-127">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="b32a6-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b32a6-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b32a6-128">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
