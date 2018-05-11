---
title: '&lt;DynamicEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 215bc9d8540b2d782a0c63f2f5be96f6fcde6812
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="c8fdc-102">&lt;DynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="c8fdc-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="c8fdc-103">Este elemento de configuração define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço de ponto de extremidade dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c8fdc-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="c8fdc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c8fdc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c8fdc-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c8fdc-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8fdc-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8fdc-106">Syntax</span></span>  
  
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
            <add name="String" namespace="String" />
          <contractTypeNames>
          <extensions />
          <scopes>
            <add scope="URI" />
          </scopes>
        </findCriteria>
      </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8fdc-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c8fdc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c8fdc-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c8fdc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8fdc-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="c8fdc-109">Attributes</span></span>  
 <span data-ttu-id="c8fdc-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c8fdc-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c8fdc-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c8fdc-111">Child Elements</span></span>  
  
|<span data-ttu-id="c8fdc-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c8fdc-112">Element</span></span>|<span data-ttu-id="c8fdc-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8fdc-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8fdc-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="c8fdc-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="c8fdc-115">Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="c8fdc-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c8fdc-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c8fdc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c8fdc-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="c8fdc-117">Element</span></span>|<span data-ttu-id="c8fdc-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8fdc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8fdc-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c8fdc-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="c8fdc-120">Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="c8fdc-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8fdc-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8fdc-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
