---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 71305720cad0206ec3dabb1863e2f1cd72eb85f0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739039"
---
# <a name="discoveryclient"></a><span data-ttu-id="6af1f-101">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="6af1f-101">\<discoveryClient></span></span>
<span data-ttu-id="6af1f-102">Um elemento de configuração para criar uma associação personalizada que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6af1f-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="6af1f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6af1f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6af1f-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6af1f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6af1f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="6af1f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6af1f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="6af1f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="6af1f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="6af1f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6af1f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryClient >**</span><span class="sxs-lookup"><span data-stu-id="6af1f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af1f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6af1f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6af1f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6af1f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6af1f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6af1f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6af1f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="6af1f-112">Attributes</span></span>  
  
|<span data-ttu-id="6af1f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="6af1f-113">Attribute</span></span>|<span data-ttu-id="6af1f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6af1f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6af1f-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="6af1f-115">discoveryEndpoint</span></span>|<span data-ttu-id="6af1f-116">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6af1f-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6af1f-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6af1f-117">Child Elements</span></span>  
  
|<span data-ttu-id="6af1f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="6af1f-118">Element</span></span>|<span data-ttu-id="6af1f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="6af1f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6af1f-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="6af1f-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="6af1f-121">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="6af1f-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="6af1f-122">Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="6af1f-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6af1f-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6af1f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6af1f-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="6af1f-124">Element</span></span>|<span data-ttu-id="6af1f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="6af1f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6af1f-126">\<binding ></span><span class="sxs-lookup"><span data-stu-id="6af1f-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="6af1f-127">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="6af1f-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6af1f-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6af1f-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
