---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 2783796166d56be3d4983ab09a60d62491699fe3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925859"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="83870-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="83870-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="83870-102">Contém as configurações necessárias para um aplicativo participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="83870-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="83870-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="83870-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="83870-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="83870-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83870-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83870-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83870-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="83870-106">Attributes and Elements</span></span>  
 <span data-ttu-id="83870-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="83870-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83870-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="83870-108">Attributes</span></span>  
  
|<span data-ttu-id="83870-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="83870-109">Attribute</span></span>|<span data-ttu-id="83870-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="83870-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83870-111">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="83870-111">discoveryEndpoint</span></span>|<span data-ttu-id="83870-112">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="83870-112">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83870-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="83870-113">Child Elements</span></span>  
  
|<span data-ttu-id="83870-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="83870-114">Element</span></span>|<span data-ttu-id="83870-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="83870-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83870-116">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="83870-116">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="83870-117">Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="83870-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="83870-118">Os critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (por quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="83870-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83870-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="83870-119">Parent Elements</span></span>  
  
|<span data-ttu-id="83870-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="83870-120">Element</span></span>|<span data-ttu-id="83870-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="83870-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83870-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="83870-122">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="83870-123">Define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="83870-123">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83870-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83870-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
