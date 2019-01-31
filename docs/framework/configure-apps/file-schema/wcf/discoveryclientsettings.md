---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 5b60c7281b92a487ba3ee275f7405cb82bd6cd87
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282237"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="8e3db-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="8e3db-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="8e3db-102">Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="8e3db-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="8e3db-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8e3db-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8e3db-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="8e3db-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e3db-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e3db-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e3db-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8e3db-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8e3db-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8e3db-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e3db-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e3db-108">Attributes</span></span>  
  
|<span data-ttu-id="8e3db-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="8e3db-109">Attribute</span></span>|<span data-ttu-id="8e3db-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e3db-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e3db-111">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="8e3db-111">discoveryEndpoint</span></span>|<span data-ttu-id="8e3db-112">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente por um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8e3db-112">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e3db-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8e3db-113">Child Elements</span></span>  
  
|<span data-ttu-id="8e3db-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e3db-114">Element</span></span>|<span data-ttu-id="8e3db-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e3db-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e3db-116">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="8e3db-116">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="8e3db-117">Um elemento de configuração que fornece um conjunto de critérios utilizados por um aplicativo cliente para pesquisar para um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="8e3db-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="8e3db-118">Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e encontre os critérios de término (quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="8e3db-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e3db-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8e3db-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8e3db-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e3db-120">Element</span></span>|<span data-ttu-id="8e3db-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e3db-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e3db-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="8e3db-122">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="8e3db-123">Define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8e3db-123">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e3db-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e3db-124">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
