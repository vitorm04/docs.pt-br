---
title: <add> De <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: c29e47f688118e34fbdb4deb396c930d478f0582
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187078"
---
# <a name="add-of-scopes"></a><span data-ttu-id="42dd2-102">\<Adicionar > de \<escopos ></span><span class="sxs-lookup"><span data-stu-id="42dd2-102">\<add> of \<scopes></span></span>
<span data-ttu-id="42dd2-103">Adiciona um Uri que pode ser usado para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="42dd2-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="42dd2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="42dd2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="42dd2-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="42dd2-105">\<behaviors></span></span>  
<span data-ttu-id="42dd2-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="42dd2-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="42dd2-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="42dd2-107">\<behavior></span></span>  
<span data-ttu-id="42dd2-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="42dd2-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="42dd2-109">\<scopes></span><span class="sxs-lookup"><span data-stu-id="42dd2-109">\<scopes></span></span>  
<span data-ttu-id="42dd2-110">\<add></span><span class="sxs-lookup"><span data-stu-id="42dd2-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42dd2-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42dd2-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42dd2-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="42dd2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="42dd2-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="42dd2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42dd2-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="42dd2-114">Attributes</span></span>  
  
|<span data-ttu-id="42dd2-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="42dd2-115">Attribute</span></span>|<span data-ttu-id="42dd2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="42dd2-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42dd2-117">escopo</span><span class="sxs-lookup"><span data-stu-id="42dd2-117">scope</span></span>|<span data-ttu-id="42dd2-118">Um URI que contém informações de escopo para o ponto de extremidade que pode ser usado em correspondem aos critérios para a localização de serviços.</span><span class="sxs-lookup"><span data-stu-id="42dd2-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42dd2-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="42dd2-119">Child Elements</span></span>  
 <span data-ttu-id="42dd2-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="42dd2-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42dd2-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="42dd2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="42dd2-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="42dd2-122">Element</span></span>|<span data-ttu-id="42dd2-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="42dd2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42dd2-124">\<scopes></span><span class="sxs-lookup"><span data-stu-id="42dd2-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="42dd2-125">Contém uma coleção de elementos de configuração que especificam Uris que podem ser usados para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="42dd2-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42dd2-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42dd2-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
