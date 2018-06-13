---
title: '&lt;Escopos&gt;'
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 7e2dda0d0def4d1f90bf1b4dbf54f18983355222
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749615"
---
# <a name="ltscopesgt"></a><span data-ttu-id="1e3e9-102">&lt;Escopos&gt;</span><span class="sxs-lookup"><span data-stu-id="1e3e9-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="1e3e9-103">Contém uma coleção de elementos de configuração que especificam Uris que podem ser usados para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="1e3e9-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="1e3e9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1e3e9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1e3e9-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="1e3e9-105">\<behaviors></span></span>  
<span data-ttu-id="1e3e9-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="1e3e9-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1e3e9-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="1e3e9-107">\<behavior></span></span>  
<span data-ttu-id="1e3e9-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="1e3e9-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="1e3e9-109">\<escopos ></span><span class="sxs-lookup"><span data-stu-id="1e3e9-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e3e9-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e3e9-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e3e9-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1e3e9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1e3e9-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1e3e9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e3e9-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="1e3e9-113">Attributes</span></span>  
 <span data-ttu-id="1e3e9-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1e3e9-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e3e9-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1e3e9-115">Child Elements</span></span>  
  
|<span data-ttu-id="1e3e9-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="1e3e9-116">Attribute</span></span>|<span data-ttu-id="1e3e9-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e3e9-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="1e3e9-118">\<add></span><span class="sxs-lookup"><span data-stu-id="1e3e9-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="1e3e9-119">Adiciona as informações de escopo para o ponto de extremidade que pode ser usada em critérios de correspondência para localizar serviços.</span><span class="sxs-lookup"><span data-stu-id="1e3e9-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e3e9-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1e3e9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1e3e9-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e3e9-121">Element</span></span>|<span data-ttu-id="1e3e9-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e3e9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e3e9-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="1e3e9-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="1e3e9-124">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua capacidade de descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="1e3e9-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e3e9-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e3e9-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
