---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: e1a53869faa1997d2e79c3d2869a15001ee29626
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673154"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="23159-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="23159-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="23159-102">Este elemento de configuração define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="23159-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="23159-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="23159-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="23159-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="23159-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23159-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23159-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23159-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="23159-106">Attributes and Elements</span></span>  
 <span data-ttu-id="23159-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="23159-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23159-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="23159-108">Attributes</span></span>  
 <span data-ttu-id="23159-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="23159-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23159-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="23159-110">Child Elements</span></span>  
  
|<span data-ttu-id="23159-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="23159-111">Element</span></span>|<span data-ttu-id="23159-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="23159-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23159-113">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="23159-113">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="23159-114">Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="23159-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23159-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="23159-115">Parent Elements</span></span>  
  
|<span data-ttu-id="23159-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="23159-116">Element</span></span>|<span data-ttu-id="23159-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="23159-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23159-118">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="23159-118">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="23159-119">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="23159-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23159-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23159-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
