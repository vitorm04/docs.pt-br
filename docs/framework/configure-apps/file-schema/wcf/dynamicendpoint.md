---
title: '&lt;DynamicEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 78ec2d4639161f8e10105f205576f052c8a5567c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146830"
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="cbe45-102">&lt;DynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="cbe45-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="cbe45-103">Este elemento de configuração define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cbe45-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="cbe45-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cbe45-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cbe45-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="cbe45-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbe45-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbe45-106">Syntax</span></span>  
  
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
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbe45-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cbe45-107">Attributes and Elements</span></span>  
 <span data-ttu-id="cbe45-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cbe45-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbe45-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="cbe45-109">Attributes</span></span>  
 <span data-ttu-id="cbe45-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cbe45-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cbe45-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cbe45-111">Child Elements</span></span>  
  
|<span data-ttu-id="cbe45-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="cbe45-112">Element</span></span>|<span data-ttu-id="cbe45-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbe45-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbe45-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="cbe45-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="cbe45-115">Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="cbe45-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cbe45-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cbe45-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cbe45-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="cbe45-117">Element</span></span>|<span data-ttu-id="cbe45-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbe45-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbe45-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="cbe45-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="cbe45-120">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="cbe45-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbe45-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbe45-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
