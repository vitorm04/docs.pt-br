---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855348"
---
# \<dynamicEndpoint>
<span data-ttu-id="0226b-101">Este elemento de configuração define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0226b-101">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="0226b-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0226b-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0226b-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0226b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0226b-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0226b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0226b-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="0226b-105">Attributes</span></span>  
 <span data-ttu-id="0226b-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0226b-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0226b-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0226b-107">Child Elements</span></span>  
  
|<span data-ttu-id="0226b-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="0226b-108">Element</span></span>|<span data-ttu-id="0226b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0226b-109">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="0226b-110">Contém as configurações necessárias para um aplicativo participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="0226b-110">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0226b-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0226b-111">Parent Elements</span></span>  
  
|<span data-ttu-id="0226b-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="0226b-112">Element</span></span>|<span data-ttu-id="0226b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0226b-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="0226b-114">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="0226b-114">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0226b-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="0226b-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
