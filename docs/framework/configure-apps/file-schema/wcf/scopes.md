---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 8bc720238ca3039106345783381cd26134fc46b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213071"
---
# <a name="scopes"></a><span data-ttu-id="4c8f5-101">\<scopes></span><span class="sxs-lookup"><span data-stu-id="4c8f5-101">\<scopes></span></span>
<span data-ttu-id="4c8f5-102">Contém uma coleção de elementos de configuração que especificam Uris que podem ser usados para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4c8f5-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="4c8f5-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4c8f5-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4c8f5-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="4c8f5-104">\<behaviors></span></span>  
<span data-ttu-id="4c8f5-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="4c8f5-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="4c8f5-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4c8f5-106">\<behavior></span></span>  
<span data-ttu-id="4c8f5-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="4c8f5-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="4c8f5-108">\<scopes></span><span class="sxs-lookup"><span data-stu-id="4c8f5-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c8f5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c8f5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c8f5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4c8f5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4c8f5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4c8f5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c8f5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="4c8f5-112">Attributes</span></span>  
 <span data-ttu-id="4c8f5-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4c8f5-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4c8f5-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4c8f5-114">Child Elements</span></span>  
  
|<span data-ttu-id="4c8f5-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="4c8f5-115">Attribute</span></span>|<span data-ttu-id="4c8f5-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c8f5-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="4c8f5-117">\<add></span><span class="sxs-lookup"><span data-stu-id="4c8f5-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="4c8f5-118">Adiciona as informações de escopo para o ponto de extremidade que pode ser usado em correspondem aos critérios para a localização de serviços.</span><span class="sxs-lookup"><span data-stu-id="4c8f5-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4c8f5-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4c8f5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4c8f5-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="4c8f5-120">Element</span></span>|<span data-ttu-id="4c8f5-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c8f5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c8f5-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="4c8f5-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="4c8f5-123">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua capacidade de descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="4c8f5-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c8f5-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c8f5-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
