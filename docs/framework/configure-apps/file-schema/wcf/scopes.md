---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399925"
---
# <a name="scopes"></a><span data-ttu-id="3baad-101">\<escopos ></span><span class="sxs-lookup"><span data-stu-id="3baad-101">\<scopes></span></span>
<span data-ttu-id="3baad-102">Contém uma coleção de elementos de configuração que especificam URIs de escopo personalizado que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta.</span><span class="sxs-lookup"><span data-stu-id="3baad-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="3baad-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3baad-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3baad-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3baad-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3baad-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3baad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="3baad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3baad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="3baad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3baad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="3baad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointDiscovery**](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="3baad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="3baad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<escopos >**</span><span class="sxs-lookup"><span data-stu-id="3baad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3baad-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3baad-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3baad-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3baad-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3baad-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3baad-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3baad-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="3baad-113">Attributes</span></span>  
 <span data-ttu-id="3baad-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3baad-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3baad-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3baad-115">Child Elements</span></span>  
  
|<span data-ttu-id="3baad-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="3baad-116">Attribute</span></span>|<span data-ttu-id="3baad-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3baad-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="3baad-118">\<add></span><span class="sxs-lookup"><span data-stu-id="3baad-118">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="3baad-119">Adiciona as informações de escopo para o ponto de extremidade que pode ser usado em critérios de correspondência para localizar serviços.</span><span class="sxs-lookup"><span data-stu-id="3baad-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3baad-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3baad-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3baad-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3baad-121">Element</span></span>|<span data-ttu-id="3baad-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3baad-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3baad-123">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="3baad-123">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="3baad-124">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="3baad-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3baad-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3baad-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
