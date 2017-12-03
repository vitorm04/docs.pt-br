---
title: '&lt;adicionar&gt; &lt;escopos&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4771c519edda36541034d9256beb858ef17763c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="ad4f2-102">&lt;adicionar&gt; &lt;escopos&gt;</span><span class="sxs-lookup"><span data-stu-id="ad4f2-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="ad4f2-103">Adiciona um Uri que pode ser usado para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="ad4f2-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="ad4f2-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ad4f2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ad4f2-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="ad4f2-105">\<behaviors></span></span>  
<span data-ttu-id="ad4f2-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ad4f2-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ad4f2-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="ad4f2-107">\<behavior></span></span>  
<span data-ttu-id="ad4f2-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="ad4f2-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="ad4f2-109">\<escopos ></span><span class="sxs-lookup"><span data-stu-id="ad4f2-109">\<scopes></span></span>  
<span data-ttu-id="ad4f2-110">\<add></span><span class="sxs-lookup"><span data-stu-id="ad4f2-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad4f2-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad4f2-111">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad4f2-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ad4f2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ad4f2-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ad4f2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad4f2-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="ad4f2-114">Attributes</span></span>  
  
|<span data-ttu-id="ad4f2-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="ad4f2-115">Attribute</span></span>|<span data-ttu-id="ad4f2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad4f2-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad4f2-117">escopo</span><span class="sxs-lookup"><span data-stu-id="ad4f2-117">scope</span></span>|<span data-ttu-id="ad4f2-118">Um URI que contém informações de escopo para o ponto de extremidade que pode ser usada em critérios de correspondência para localizar serviços.</span><span class="sxs-lookup"><span data-stu-id="ad4f2-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad4f2-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ad4f2-119">Child Elements</span></span>  
 <span data-ttu-id="ad4f2-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ad4f2-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad4f2-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ad4f2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ad4f2-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="ad4f2-122">Element</span></span>|<span data-ttu-id="ad4f2-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad4f2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad4f2-124">\<escopos ></span><span class="sxs-lookup"><span data-stu-id="ad4f2-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="ad4f2-125">Contém uma coleção de elementos de configuração que especificam Uris que podem ser usados para filtrar pontos de extremidade de serviço durante consulta de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="ad4f2-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad4f2-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad4f2-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
