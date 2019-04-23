---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 0b014a9d797ded61949a374486824ee3ebc34661
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136247"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="7e7b0-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="7e7b0-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="7e7b0-102">Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="7e7b0-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="7e7b0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7e7b0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7e7b0-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="7e7b0-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e7b0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e7b0-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e7b0-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7e7b0-106">Attributes and Elements</span></span>  
 <span data-ttu-id="7e7b0-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7e7b0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e7b0-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="7e7b0-108">Attributes</span></span>  
  
|<span data-ttu-id="7e7b0-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="7e7b0-109">Attribute</span></span>|<span data-ttu-id="7e7b0-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e7b0-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e7b0-111">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="7e7b0-111">discoveryEndpoint</span></span>|<span data-ttu-id="7e7b0-112">Uma cadeia de caracteres que contém o nome do ponto de extremidade de descoberta que permite que um aplicativo cliente pesquise automaticamente por um serviço detectável e encontre seu endereço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7e7b0-112">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e7b0-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7e7b0-113">Child Elements</span></span>  
  
|<span data-ttu-id="7e7b0-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="7e7b0-114">Element</span></span>|<span data-ttu-id="7e7b0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e7b0-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e7b0-116">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="7e7b0-116">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="7e7b0-117">Um elemento de configuração que fornece um conjunto de critérios utilizados por um aplicativo cliente para pesquisar para um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="7e7b0-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="7e7b0-118">Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e encontre os critérios de término (quanto tempo a pesquisa deve durar).</span><span class="sxs-lookup"><span data-stu-id="7e7b0-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e7b0-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7e7b0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7e7b0-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="7e7b0-120">Element</span></span>|<span data-ttu-id="7e7b0-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e7b0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e7b0-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="7e7b0-122">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="7e7b0-123">Define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7e7b0-123">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e7b0-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e7b0-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
