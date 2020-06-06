---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 929c5d170bfc27160e3e15b8bd2f9f26e0ed8975
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855406"
---
# \<discoveryClientSettings>
<span data-ttu-id="b60fd-101">Contém as configurações necessárias para um aplicativo participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="b60fd-101">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="b60fd-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b60fd-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b60fd-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b60fd-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b60fd-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b60fd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b60fd-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="b60fd-105">Attributes</span></span>  
  
|<span data-ttu-id="b60fd-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="b60fd-106">Attribute</span></span>|<span data-ttu-id="b60fd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b60fd-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b60fd-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="b60fd-108">discoveryEndpoint</span></span>|<span data-ttu-id="b60fd-109">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b60fd-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b60fd-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b60fd-110">Child Elements</span></span>  
  
|<span data-ttu-id="b60fd-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="b60fd-111">Element</span></span>|<span data-ttu-id="b60fd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b60fd-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="b60fd-113">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="b60fd-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="b60fd-114">Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="b60fd-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b60fd-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b60fd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b60fd-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="b60fd-116">Element</span></span>|<span data-ttu-id="b60fd-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b60fd-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="b60fd-118">Define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b60fd-118">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b60fd-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="b60fd-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
