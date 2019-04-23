---
title: <add> de <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: c29e47f688118e34fbdb4deb396c930d478f0582
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187078"
---
# <a name="add-of-scopes"></a><span data-ttu-id="7326e-102">\<Adicionar > de \<escopos ></span><span class="sxs-lookup"><span data-stu-id="7326e-102">\<add> of \<scopes></span></span>
<span data-ttu-id="7326e-103">Adiciona um Uri que pode ser usado para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="7326e-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="7326e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7326e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7326e-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="7326e-105">\<behaviors></span></span>  
<span data-ttu-id="7326e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="7326e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7326e-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7326e-107">\<behavior></span></span>  
<span data-ttu-id="7326e-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="7326e-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="7326e-109">\<scopes></span><span class="sxs-lookup"><span data-stu-id="7326e-109">\<scopes></span></span>  
<span data-ttu-id="7326e-110">\<add></span><span class="sxs-lookup"><span data-stu-id="7326e-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7326e-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7326e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7326e-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7326e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7326e-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7326e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7326e-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7326e-114">Attributes</span></span>  
  
|<span data-ttu-id="7326e-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="7326e-115">Attribute</span></span>|<span data-ttu-id="7326e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7326e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7326e-117">escopo</span><span class="sxs-lookup"><span data-stu-id="7326e-117">scope</span></span>|<span data-ttu-id="7326e-118">Um URI que contém informações de escopo para o ponto de extremidade que pode ser usado em correspondem aos critérios para a localização de serviços.</span><span class="sxs-lookup"><span data-stu-id="7326e-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7326e-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7326e-119">Child Elements</span></span>  
 <span data-ttu-id="7326e-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7326e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7326e-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7326e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7326e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="7326e-122">Element</span></span>|<span data-ttu-id="7326e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="7326e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7326e-124">\<scopes></span><span class="sxs-lookup"><span data-stu-id="7326e-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="7326e-125">Contém uma coleção de elementos de configuração que especificam Uris que podem ser usados para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="7326e-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7326e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7326e-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
