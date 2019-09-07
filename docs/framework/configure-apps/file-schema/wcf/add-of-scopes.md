---
title: <add> de <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398301"
---
# <a name="add-of-scopes"></a><span data-ttu-id="a7dca-102">\<Adicionar > de \<escopos ></span><span class="sxs-lookup"><span data-stu-id="a7dca-102">\<add> of \<scopes></span></span>
<span data-ttu-id="a7dca-103">Adiciona um URI de escopo personalizado que pode ser usado para filtrar pontos de extremidade de serviço durante a consulta.</span><span class="sxs-lookup"><span data-stu-id="a7dca-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="a7dca-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a7dca-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a7dca-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a7dca-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a7dca-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a7dca-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a7dca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a7dca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="a7dca-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a7dca-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="a7dca-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointDiscovery**](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="a7dca-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="a7dca-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<escopos >** ](scopes.md)</span><span class="sxs-lookup"><span data-stu-id="a7dca-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)</span></span>\
<span data-ttu-id="a7dca-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="a7dca-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7dca-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7dca-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7dca-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a7dca-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a7dca-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a7dca-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7dca-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="a7dca-115">Attributes</span></span>  
  
|<span data-ttu-id="a7dca-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="a7dca-116">Attribute</span></span>|<span data-ttu-id="a7dca-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7dca-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7dca-118">escopo</span><span class="sxs-lookup"><span data-stu-id="a7dca-118">scope</span></span>|<span data-ttu-id="a7dca-119">Um URI que contém informações de escopo para o ponto de extremidade que pode ser usado em critérios de correspondência para localizar serviços.</span><span class="sxs-lookup"><span data-stu-id="a7dca-119">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7dca-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a7dca-120">Child Elements</span></span>  
 <span data-ttu-id="a7dca-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a7dca-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7dca-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a7dca-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a7dca-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="a7dca-123">Element</span></span>|<span data-ttu-id="a7dca-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7dca-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7dca-125">\<scopes></span><span class="sxs-lookup"><span data-stu-id="a7dca-125">\<scopes></span></span>](scopes.md)|<span data-ttu-id="a7dca-126">Contém uma coleção de elementos de configuração que especificam URIs de escopo personalizado que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta.</span><span class="sxs-lookup"><span data-stu-id="a7dca-126">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7dca-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7dca-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
