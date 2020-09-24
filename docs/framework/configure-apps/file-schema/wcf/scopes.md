---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 63f46753da13469147b378f373de9888a007bf52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162212"
---
# \<scopes>

<span data-ttu-id="355f3-101">Contém uma coleção de elementos de configuração que especificam URIs de escopo personalizado que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta.</span><span class="sxs-lookup"><span data-stu-id="355f3-101">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**  
  
## <a name="syntax"></a><span data-ttu-id="355f3-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="355f3-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="355f3-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="355f3-103">Attributes and Elements</span></span>  

 <span data-ttu-id="355f3-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="355f3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="355f3-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="355f3-105">Attributes</span></span>  

 <span data-ttu-id="355f3-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="355f3-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="355f3-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="355f3-107">Child Elements</span></span>  
  
|<span data-ttu-id="355f3-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="355f3-108">Attribute</span></span>|<span data-ttu-id="355f3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="355f3-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|<span data-ttu-id="355f3-110">Adiciona as informações de escopo para o ponto de extremidade que pode ser usado em critérios de correspondência para localizar serviços.</span><span class="sxs-lookup"><span data-stu-id="355f3-110">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="355f3-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="355f3-111">Parent Elements</span></span>  
  
|<span data-ttu-id="355f3-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="355f3-112">Element</span></span>|<span data-ttu-id="355f3-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="355f3-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="355f3-114">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="355f3-114">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="355f3-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="355f3-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
