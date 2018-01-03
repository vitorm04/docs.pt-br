---
title: '&lt;dynamicEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46fb4f1f4688aede484b177e30b8bc8dfff1ece2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="d7395-102">&lt;dynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="d7395-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="d7395-103">Este elemento de configuração define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço de ponto de extremidade dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d7395-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="d7395-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d7395-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d7395-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="d7395-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7395-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7395-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7395-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d7395-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d7395-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d7395-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7395-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d7395-109">Attributes</span></span>  
 <span data-ttu-id="d7395-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d7395-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d7395-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d7395-111">Child Elements</span></span>  
  
|<span data-ttu-id="d7395-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7395-112">Element</span></span>|<span data-ttu-id="d7395-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7395-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7395-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="d7395-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="d7395-115">Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="d7395-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7395-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d7395-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d7395-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7395-117">Element</span></span>|<span data-ttu-id="d7395-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7395-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7395-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="d7395-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="d7395-120">Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="d7395-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7395-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7395-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
