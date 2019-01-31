---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: eee6382c578648866045fd9b283454d9e0e76fcb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275012"
---
# <a name="scopes"></a><span data-ttu-id="5dbdb-101">\<scopes></span><span class="sxs-lookup"><span data-stu-id="5dbdb-101">\<scopes></span></span>
<span data-ttu-id="5dbdb-102">Contém uma coleção de elementos de configuração que especificam Uris que podem ser usados para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="5dbdb-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="5dbdb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5dbdb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5dbdb-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="5dbdb-104">\<behaviors></span></span>  
<span data-ttu-id="5dbdb-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="5dbdb-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="5dbdb-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5dbdb-106">\<behavior></span></span>  
<span data-ttu-id="5dbdb-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="5dbdb-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="5dbdb-108">\<scopes></span><span class="sxs-lookup"><span data-stu-id="5dbdb-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dbdb-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5dbdb-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dbdb-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5dbdb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5dbdb-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5dbdb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dbdb-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5dbdb-112">Attributes</span></span>  
 <span data-ttu-id="5dbdb-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5dbdb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5dbdb-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5dbdb-114">Child Elements</span></span>  
  
|<span data-ttu-id="5dbdb-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="5dbdb-115">Attribute</span></span>|<span data-ttu-id="5dbdb-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="5dbdb-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="5dbdb-117">\<add></span><span class="sxs-lookup"><span data-stu-id="5dbdb-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="5dbdb-118">Adiciona as informações de escopo para o ponto de extremidade que pode ser usado em correspondem aos critérios para a localização de serviços.</span><span class="sxs-lookup"><span data-stu-id="5dbdb-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5dbdb-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5dbdb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5dbdb-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="5dbdb-120">Element</span></span>|<span data-ttu-id="5dbdb-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="5dbdb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5dbdb-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="5dbdb-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="5dbdb-123">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua capacidade de descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="5dbdb-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5dbdb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5dbdb-124">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
