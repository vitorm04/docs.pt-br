---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: af9cf127652f1e12ae57948f9b4a6a26285af793
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192250"
---
# \<discoveryClient>

<span data-ttu-id="af77f-101">Um elemento de configuração para criar uma associação personalizada que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="af77f-101">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="af77f-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af77f-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af77f-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="af77f-103">Attributes and Elements</span></span>  

 <span data-ttu-id="af77f-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="af77f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af77f-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="af77f-105">Attributes</span></span>  
  
|<span data-ttu-id="af77f-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="af77f-106">Attribute</span></span>|<span data-ttu-id="af77f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="af77f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af77f-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="af77f-108">discoveryEndpoint</span></span>|<span data-ttu-id="af77f-109">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="af77f-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af77f-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="af77f-110">Child Elements</span></span>  
  
|<span data-ttu-id="af77f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="af77f-111">Element</span></span>|<span data-ttu-id="af77f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="af77f-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="af77f-113">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="af77f-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="af77f-114">Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="af77f-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af77f-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="af77f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="af77f-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="af77f-116">Element</span></span>|<span data-ttu-id="af77f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="af77f-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="af77f-118">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="af77f-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af77f-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="af77f-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
