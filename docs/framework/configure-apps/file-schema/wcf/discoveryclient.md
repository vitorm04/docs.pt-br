---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 5e586437e3b269d361c254744e820ee8e8c0ca0a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400394"
---
# <a name="discoveryclient"></a><span data-ttu-id="89b6e-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="89b6e-101">\<discoveryClient></span></span>
<span data-ttu-id="89b6e-102">Um elemento de configuração para criar uma associação personalizada que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="89b6e-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="89b6e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="89b6e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="89b6e-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="89b6e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="89b6e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="89b6e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="89b6e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="89b6e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="89b6e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="89b6e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="89b6e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryClient >**</span><span class="sxs-lookup"><span data-stu-id="89b6e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89b6e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89b6e-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89b6e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="89b6e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="89b6e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="89b6e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89b6e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="89b6e-112">Attributes</span></span>  
  
|<span data-ttu-id="89b6e-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="89b6e-113">Attribute</span></span>|<span data-ttu-id="89b6e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="89b6e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89b6e-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="89b6e-115">discoveryEndpoint</span></span>|<span data-ttu-id="89b6e-116">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="89b6e-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89b6e-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="89b6e-117">Child Elements</span></span>  
  
|<span data-ttu-id="89b6e-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="89b6e-118">Element</span></span>|<span data-ttu-id="89b6e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="89b6e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89b6e-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="89b6e-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="89b6e-121">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="89b6e-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="89b6e-122">Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="89b6e-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89b6e-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="89b6e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="89b6e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="89b6e-124">Element</span></span>|<span data-ttu-id="89b6e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="89b6e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89b6e-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="89b6e-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="89b6e-127">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="89b6e-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89b6e-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89b6e-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
