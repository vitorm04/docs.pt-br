---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: a5ea10601732021af578c17d4f5c5ab69c98f17a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128421"
---
# <a name="discoveryclient"></a><span data-ttu-id="428a4-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="428a4-101">\<discoveryClient></span></span>
<span data-ttu-id="428a4-102">Um elemento de configuração para a criação de uma associação personalizada que permite que um aplicativo cliente pesquise automaticamente por um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="428a4-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="428a4-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="428a4-103">\<system.serviceModel></span></span>  
<span data-ttu-id="428a4-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="428a4-104">\<bindings></span></span>  
<span data-ttu-id="428a4-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="428a4-105">\<customBinding></span></span>  
<span data-ttu-id="428a4-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="428a4-106">\<binding></span></span>  
<span data-ttu-id="428a4-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="428a4-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="428a4-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="428a4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="428a4-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="428a4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="428a4-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="428a4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="428a4-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="428a4-111">Attributes</span></span>  
  
|<span data-ttu-id="428a4-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="428a4-112">Attribute</span></span>|<span data-ttu-id="428a4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="428a4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="428a4-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="428a4-114">discoveryEndpoint</span></span>|<span data-ttu-id="428a4-115">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente por um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="428a4-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="428a4-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="428a4-116">Child Elements</span></span>  
  
|<span data-ttu-id="428a4-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="428a4-117">Element</span></span>|<span data-ttu-id="428a4-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="428a4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="428a4-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="428a4-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="428a4-120">Um elemento de configuração que fornece um conjunto de critérios utilizados por um aplicativo cliente para pesquisar para um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="428a4-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="428a4-121">Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e encontre os critérios de término (quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="428a4-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="428a4-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="428a4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="428a4-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="428a4-123">Element</span></span>|<span data-ttu-id="428a4-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="428a4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="428a4-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="428a4-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="428a4-126">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="428a4-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="428a4-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="428a4-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
