---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: dd6513930798e9e1ab263f75c9350511c2dcdcd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935180"
---
# <a name="scopes"></a><span data-ttu-id="62c99-101">\<escopos ></span><span class="sxs-lookup"><span data-stu-id="62c99-101">\<scopes></span></span>
<span data-ttu-id="62c99-102">Contém uma coleção de elementos de configuração que especificam URIs de escopo personalizado que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta.</span><span class="sxs-lookup"><span data-stu-id="62c99-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="62c99-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="62c99-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="62c99-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="62c99-104">\<behaviors></span></span>  
<span data-ttu-id="62c99-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="62c99-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="62c99-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="62c99-106">\<behavior></span></span>  
<span data-ttu-id="62c99-107">\<> endpointDiscovery</span><span class="sxs-lookup"><span data-stu-id="62c99-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="62c99-108">\<escopos ></span><span class="sxs-lookup"><span data-stu-id="62c99-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62c99-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62c99-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62c99-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="62c99-110">Attributes and Elements</span></span>  
 <span data-ttu-id="62c99-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="62c99-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62c99-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="62c99-112">Attributes</span></span>  
 <span data-ttu-id="62c99-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="62c99-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="62c99-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="62c99-114">Child Elements</span></span>  
  
|<span data-ttu-id="62c99-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="62c99-115">Attribute</span></span>|<span data-ttu-id="62c99-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="62c99-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="62c99-117">\<add></span><span class="sxs-lookup"><span data-stu-id="62c99-117">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="62c99-118">Adiciona as informações de escopo para o ponto de extremidade que pode ser usado em critérios de correspondência para localizar serviços.</span><span class="sxs-lookup"><span data-stu-id="62c99-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62c99-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="62c99-119">Parent Elements</span></span>  
  
|<span data-ttu-id="62c99-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="62c99-120">Element</span></span>|<span data-ttu-id="62c99-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="62c99-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62c99-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="62c99-122">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="62c99-123">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="62c99-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62c99-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62c99-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
