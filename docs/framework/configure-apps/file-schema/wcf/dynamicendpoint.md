---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 786a70e8c686497e91492938a4d0796db4f6dd91
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269790"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="d8b66-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="d8b66-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="d8b66-102">Este elemento de configuração define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d8b66-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="d8b66-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d8b66-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d8b66-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="d8b66-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8b66-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8b66-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8b66-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d8b66-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d8b66-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d8b66-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8b66-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="d8b66-108">Attributes</span></span>  
 <span data-ttu-id="d8b66-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d8b66-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8b66-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d8b66-110">Child Elements</span></span>  
  
|<span data-ttu-id="d8b66-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="d8b66-111">Element</span></span>|<span data-ttu-id="d8b66-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8b66-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8b66-113">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="d8b66-113">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="d8b66-114">Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="d8b66-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8b66-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d8b66-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d8b66-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="d8b66-116">Element</span></span>|<span data-ttu-id="d8b66-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8b66-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8b66-118">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="d8b66-118">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="d8b66-119">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="d8b66-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8b66-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8b66-120">See also</span></span>
- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
