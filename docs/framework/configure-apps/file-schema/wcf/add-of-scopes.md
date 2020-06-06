---
title: <add> de <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398301"
---
# <a name="add-of-scopes"></a><span data-ttu-id="69522-102">\<add> de \<scopes></span><span class="sxs-lookup"><span data-stu-id="69522-102">\<add> of \<scopes></span></span>
<span data-ttu-id="69522-103">Adiciona um URI de escopo personalizado que pode ser usado para filtrar pontos de extremidade de serviço durante a consulta.</span><span class="sxs-lookup"><span data-stu-id="69522-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="69522-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69522-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69522-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="69522-105">Attributes and Elements</span></span>  
 <span data-ttu-id="69522-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="69522-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69522-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="69522-107">Attributes</span></span>  
  
|<span data-ttu-id="69522-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="69522-108">Attribute</span></span>|<span data-ttu-id="69522-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="69522-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69522-110">scope</span><span class="sxs-lookup"><span data-stu-id="69522-110">scope</span></span>|<span data-ttu-id="69522-111">Um URI que contém informações de escopo para o ponto de extremidade que pode ser usado em critérios de correspondência para localizar serviços.</span><span class="sxs-lookup"><span data-stu-id="69522-111">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69522-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="69522-112">Child Elements</span></span>  
 <span data-ttu-id="69522-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="69522-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69522-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="69522-114">Parent Elements</span></span>  
  
|<span data-ttu-id="69522-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="69522-115">Element</span></span>|<span data-ttu-id="69522-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="69522-116">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="69522-117">Contém uma coleção de elementos de configuração que especificam URIs de escopo personalizado que podem ser usados para filtrar pontos de extremidade de serviço durante a consulta.</span><span class="sxs-lookup"><span data-stu-id="69522-117">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69522-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="69522-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
