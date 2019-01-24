---
title: '&lt;scopes&gt;'
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 1235b483f63ab71405803c16f2d3c9926b15cfad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642981"
---
# <a name="ltscopesgt"></a><span data-ttu-id="bdc7e-102">&lt;scopes&gt;</span><span class="sxs-lookup"><span data-stu-id="bdc7e-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="bdc7e-103">Contém uma coleção de elementos de configuração que especificam Uris que podem ser usados para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="bdc7e-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="bdc7e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bdc7e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bdc7e-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="bdc7e-105">\<behaviors></span></span>  
<span data-ttu-id="bdc7e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="bdc7e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="bdc7e-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="bdc7e-107">\<behavior></span></span>  
<span data-ttu-id="bdc7e-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="bdc7e-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="bdc7e-109">\<scopes></span><span class="sxs-lookup"><span data-stu-id="bdc7e-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc7e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdc7e-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdc7e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bdc7e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bdc7e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bdc7e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdc7e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="bdc7e-113">Attributes</span></span>  
 <span data-ttu-id="bdc7e-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bdc7e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bdc7e-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bdc7e-115">Child Elements</span></span>  
  
|<span data-ttu-id="bdc7e-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="bdc7e-116">Attribute</span></span>|<span data-ttu-id="bdc7e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdc7e-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="bdc7e-118">\<add></span><span class="sxs-lookup"><span data-stu-id="bdc7e-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="bdc7e-119">Adiciona as informações de escopo para o ponto de extremidade que pode ser usado em correspondem aos critérios para a localização de serviços.</span><span class="sxs-lookup"><span data-stu-id="bdc7e-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bdc7e-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bdc7e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bdc7e-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="bdc7e-121">Element</span></span>|<span data-ttu-id="bdc7e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdc7e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bdc7e-123">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="bdc7e-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="bdc7e-124">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua capacidade de descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="bdc7e-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bdc7e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdc7e-125">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
