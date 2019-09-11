---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855348"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="4f657-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="4f657-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="4f657-102">Este elemento de configuração define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4f657-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="4f657-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4f657-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4f657-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4f657-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4f657-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="4f657-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="4f657-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> dynamicEndpoint**</span><span class="sxs-lookup"><span data-stu-id="4f657-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f657-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f657-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f657-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4f657-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4f657-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4f657-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f657-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f657-110">Attributes</span></span>  
 <span data-ttu-id="4f657-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4f657-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f657-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4f657-112">Child Elements</span></span>  
  
|<span data-ttu-id="4f657-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f657-113">Element</span></span>|<span data-ttu-id="4f657-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f657-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f657-115">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="4f657-115">\<discoveryClientSettings></span></span>](discoveryclientsettings.md)|<span data-ttu-id="4f657-116">Contém as configurações necessárias para um aplicativo participar do processo de descoberta de serviço como um cliente.</span><span class="sxs-lookup"><span data-stu-id="4f657-116">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f657-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4f657-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4f657-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f657-118">Element</span></span>|<span data-ttu-id="4f657-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f657-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f657-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="4f657-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="4f657-121">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="4f657-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f657-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f657-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
