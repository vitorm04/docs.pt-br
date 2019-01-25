---
title: '&lt;discoveryClient&gt;'
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 5046d3342372960211942128372e9f62d98a2952
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573079"
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="ae1c6-102">&lt;discoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="ae1c6-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="ae1c6-103">Um elemento de configuração para a criação de uma associação personalizada que permite que um aplicativo cliente pesquise automaticamente por um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae1c6-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="ae1c6-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ae1c6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ae1c6-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ae1c6-105">\<bindings></span></span>  
<span data-ttu-id="ae1c6-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ae1c6-106">\<customBinding></span></span>  
<span data-ttu-id="ae1c6-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="ae1c6-107">\<binding></span></span>  
<span data-ttu-id="ae1c6-108">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="ae1c6-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae1c6-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae1c6-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae1c6-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ae1c6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ae1c6-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ae1c6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae1c6-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ae1c6-112">Attributes</span></span>  
  
|<span data-ttu-id="ae1c6-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="ae1c6-113">Attribute</span></span>|<span data-ttu-id="ae1c6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae1c6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae1c6-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="ae1c6-115">discoveryEndpoint</span></span>|<span data-ttu-id="ae1c6-116">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente por um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae1c6-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae1c6-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ae1c6-117">Child Elements</span></span>  
  
|<span data-ttu-id="ae1c6-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae1c6-118">Element</span></span>|<span data-ttu-id="ae1c6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae1c6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae1c6-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ae1c6-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="ae1c6-121">Um elemento de configuração que fornece um conjunto de critérios utilizados por um aplicativo cliente para pesquisar para um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="ae1c6-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="ae1c6-122">Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e encontre os critérios de término (quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="ae1c6-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae1c6-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ae1c6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ae1c6-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae1c6-124">Element</span></span>|<span data-ttu-id="ae1c6-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae1c6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae1c6-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="ae1c6-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ae1c6-127">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="ae1c6-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae1c6-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae1c6-128">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
