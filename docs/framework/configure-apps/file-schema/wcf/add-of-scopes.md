---
title: '&lt;adicionar&gt; &lt;escopos&gt;'
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: 961fb3e388e3ae756bd7511ea6c65df6dd2a1486
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705567"
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="d9b59-102">&lt;adicionar&gt; &lt;escopos&gt;</span><span class="sxs-lookup"><span data-stu-id="d9b59-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="d9b59-103">Adiciona um Uri que pode ser usado para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="d9b59-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="d9b59-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d9b59-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d9b59-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="d9b59-105">\<behaviors></span></span>  
<span data-ttu-id="d9b59-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d9b59-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d9b59-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d9b59-107">\<behavior></span></span>  
<span data-ttu-id="d9b59-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="d9b59-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="d9b59-109">\<scopes></span><span class="sxs-lookup"><span data-stu-id="d9b59-109">\<scopes></span></span>  
<span data-ttu-id="d9b59-110">\<add></span><span class="sxs-lookup"><span data-stu-id="d9b59-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b59-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9b59-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9b59-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d9b59-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d9b59-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d9b59-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9b59-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="d9b59-114">Attributes</span></span>  
  
|<span data-ttu-id="d9b59-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="d9b59-115">Attribute</span></span>|<span data-ttu-id="d9b59-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9b59-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9b59-117">escopo</span><span class="sxs-lookup"><span data-stu-id="d9b59-117">scope</span></span>|<span data-ttu-id="d9b59-118">Um URI que contém informações de escopo para o ponto de extremidade que pode ser usado em correspondem aos critérios para a localização de serviços.</span><span class="sxs-lookup"><span data-stu-id="d9b59-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9b59-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d9b59-119">Child Elements</span></span>  
 <span data-ttu-id="d9b59-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d9b59-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9b59-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d9b59-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d9b59-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9b59-122">Element</span></span>|<span data-ttu-id="d9b59-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9b59-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9b59-124">\<scopes></span><span class="sxs-lookup"><span data-stu-id="d9b59-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="d9b59-125">Contém uma coleção de elementos de configuração que especificam Uris que podem ser usados para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="d9b59-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9b59-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9b59-126">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
