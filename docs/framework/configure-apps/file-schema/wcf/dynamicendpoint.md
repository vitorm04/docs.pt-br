---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 3dc7fb19c5c7729620a5d9f3df1111b2dbdacf78
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925829"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="ec747-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="ec747-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="ec747-102">Este elemento de configuração define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ec747-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="ec747-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ec747-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ec747-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ec747-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec747-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec747-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec747-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ec747-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ec747-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ec747-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec747-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="ec747-108">Attributes</span></span>  
 <span data-ttu-id="ec747-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ec747-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec747-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ec747-110">Child Elements</span></span>  
  
|<span data-ttu-id="ec747-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec747-111">Element</span></span>|<span data-ttu-id="ec747-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec747-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec747-113">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="ec747-113">\<discoveryClientSettings></span></span>](discoveryclientsettings.md)|<span data-ttu-id="ec747-114">Contém as configurações necessárias para um aplicativo participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="ec747-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec747-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ec747-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ec747-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec747-116">Element</span></span>|<span data-ttu-id="ec747-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec747-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec747-118">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ec747-118">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="ec747-119">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="ec747-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec747-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec747-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
