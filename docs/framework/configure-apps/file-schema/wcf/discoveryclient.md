---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 71305720cad0206ec3dabb1863e2f1cd72eb85f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739039"
---
# \<discoveryClient>
<span data-ttu-id="7f582-101">Um elemento de configuração para criar uma associação personalizada que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7f582-101">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="7f582-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f582-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f582-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7f582-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7f582-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7f582-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f582-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="7f582-105">Attributes</span></span>  
  
|<span data-ttu-id="7f582-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="7f582-106">Attribute</span></span>|<span data-ttu-id="7f582-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f582-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f582-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="7f582-108">discoveryEndpoint</span></span>|<span data-ttu-id="7f582-109">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7f582-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f582-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7f582-110">Child Elements</span></span>  
  
|<span data-ttu-id="7f582-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="7f582-111">Element</span></span>|<span data-ttu-id="7f582-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f582-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="7f582-113">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="7f582-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="7f582-114">Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="7f582-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f582-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7f582-115">Parent Elements</span></span>  
  
|<span data-ttu-id="7f582-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="7f582-116">Element</span></span>|<span data-ttu-id="7f582-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f582-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="7f582-118">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="7f582-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f582-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="7f582-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
