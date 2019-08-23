---
title: <add> de <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: b190cb72e21d47bdc62aab2daba0f6eea1ee04ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926624"
---
# <a name="add-of-scopes"></a><span data-ttu-id="8760c-102">\<Adicionar > de \<escopos ></span><span class="sxs-lookup"><span data-stu-id="8760c-102">\<add> of \<scopes></span></span>
<span data-ttu-id="8760c-103">Adiciona um URI de escopo personalizado que pode ser usado para filtrar pontos de extremidade de serviço durante a consulta.</span><span class="sxs-lookup"><span data-stu-id="8760c-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="8760c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8760c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8760c-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="8760c-105">\<behaviors></span></span>  
<span data-ttu-id="8760c-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="8760c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="8760c-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="8760c-107">\<behavior></span></span>  
<span data-ttu-id="8760c-108">\<> endpointDiscovery</span><span class="sxs-lookup"><span data-stu-id="8760c-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="8760c-109">\<escopos ></span><span class="sxs-lookup"><span data-stu-id="8760c-109">\<scopes></span></span>  
<span data-ttu-id="8760c-110">\<add></span><span class="sxs-lookup"><span data-stu-id="8760c-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8760c-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8760c-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8760c-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8760c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8760c-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8760c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8760c-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="8760c-114">Attributes</span></span>  
  
|<span data-ttu-id="8760c-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="8760c-115">Attribute</span></span>|<span data-ttu-id="8760c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="8760c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8760c-117">escopo</span><span class="sxs-lookup"><span data-stu-id="8760c-117">scope</span></span>|<span data-ttu-id="8760c-118">Um URI que contém informações de escopo para o ponto de extremidade que pode ser usado em critérios de correspondência para localizar serviços.</span><span class="sxs-lookup"><span data-stu-id="8760c-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8760c-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8760c-119">Child Elements</span></span>  
 <span data-ttu-id="8760c-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8760c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8760c-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8760c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8760c-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="8760c-122">Element</span></span>|<span data-ttu-id="8760c-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="8760c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8760c-124">\<scopes></span><span class="sxs-lookup"><span data-stu-id="8760c-124">\<scopes></span></span>](scopes.md)|<span data-ttu-id="8760c-125">Contém uma coleção de elementos de configuração que especificam URIs de escopo personalizado que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta.</span><span class="sxs-lookup"><span data-stu-id="8760c-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8760c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8760c-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
