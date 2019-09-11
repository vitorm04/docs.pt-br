---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 929c5d170bfc27160e3e15b8bd2f9f26e0ed8975
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855406"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="e268a-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="e268a-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="e268a-102">Contém as configurações necessárias para um aplicativo participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="e268a-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="e268a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e268a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e268a-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e268a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e268a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="e268a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="e268a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dynamicEndpoint**](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="e268a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="e268a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> standardEndpoint**</span><span class="sxs-lookup"><span data-stu-id="e268a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="e268a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> discoveryClientSettings**</span><span class="sxs-lookup"><span data-stu-id="e268a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e268a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e268a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e268a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e268a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e268a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e268a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e268a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e268a-112">Attributes</span></span>  
  
|<span data-ttu-id="e268a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e268a-113">Attribute</span></span>|<span data-ttu-id="e268a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e268a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e268a-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="e268a-115">discoveryEndpoint</span></span>|<span data-ttu-id="e268a-116">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e268a-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e268a-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e268a-117">Child Elements</span></span>  
  
|<span data-ttu-id="e268a-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="e268a-118">Element</span></span>|<span data-ttu-id="e268a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e268a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e268a-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e268a-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="e268a-121">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="e268a-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="e268a-122">Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="e268a-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e268a-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e268a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e268a-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="e268a-124">Element</span></span>|<span data-ttu-id="e268a-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="e268a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e268a-126">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e268a-126">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="e268a-127">Define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e268a-127">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e268a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e268a-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
