---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 6f9cb127deb5651ed27a0ef5802512fb5b6c7b54
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190092"
---
# \<dynamicEndpoint>

<span data-ttu-id="69405-101">Este elemento de configuração define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="69405-101">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="69405-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69405-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69405-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="69405-103">Attributes and Elements</span></span>  

 <span data-ttu-id="69405-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="69405-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69405-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="69405-105">Attributes</span></span>  

 <span data-ttu-id="69405-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="69405-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69405-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="69405-107">Child Elements</span></span>  
  
|<span data-ttu-id="69405-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="69405-108">Element</span></span>|<span data-ttu-id="69405-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="69405-109">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="69405-110">Contém as configurações necessárias para um aplicativo participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="69405-110">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69405-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="69405-111">Parent Elements</span></span>  
  
|<span data-ttu-id="69405-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="69405-112">Element</span></span>|<span data-ttu-id="69405-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="69405-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="69405-114">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="69405-114">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69405-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="69405-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
