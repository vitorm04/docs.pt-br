---
title: '&lt;adicionar&gt; &lt;escopos&gt;'
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: e2bf649259d6ccb0e55428ab3619fe561d051ff7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146220"
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="96cb8-102">&lt;adicionar&gt; &lt;escopos&gt;</span><span class="sxs-lookup"><span data-stu-id="96cb8-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="96cb8-103">Adiciona um Uri que pode ser usado para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="96cb8-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="96cb8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="96cb8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="96cb8-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="96cb8-105">\<behaviors></span></span>  
<span data-ttu-id="96cb8-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="96cb8-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="96cb8-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="96cb8-107">\<behavior></span></span>  
<span data-ttu-id="96cb8-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="96cb8-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="96cb8-109">\<escopos ></span><span class="sxs-lookup"><span data-stu-id="96cb8-109">\<scopes></span></span>  
<span data-ttu-id="96cb8-110">\<add></span><span class="sxs-lookup"><span data-stu-id="96cb8-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96cb8-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96cb8-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96cb8-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="96cb8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="96cb8-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="96cb8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96cb8-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="96cb8-114">Attributes</span></span>  
  
|<span data-ttu-id="96cb8-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="96cb8-115">Attribute</span></span>|<span data-ttu-id="96cb8-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="96cb8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96cb8-117">escopo</span><span class="sxs-lookup"><span data-stu-id="96cb8-117">scope</span></span>|<span data-ttu-id="96cb8-118">Um URI que contém informações de escopo para o ponto de extremidade que pode ser usado em correspondem aos critérios para a localização de serviços.</span><span class="sxs-lookup"><span data-stu-id="96cb8-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96cb8-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="96cb8-119">Child Elements</span></span>  
 <span data-ttu-id="96cb8-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="96cb8-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96cb8-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="96cb8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="96cb8-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="96cb8-122">Element</span></span>|<span data-ttu-id="96cb8-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="96cb8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96cb8-124">\<escopos ></span><span class="sxs-lookup"><span data-stu-id="96cb8-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="96cb8-125">Contém uma coleção de elementos de configuração que especificam Uris que podem ser usados para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="96cb8-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96cb8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96cb8-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
