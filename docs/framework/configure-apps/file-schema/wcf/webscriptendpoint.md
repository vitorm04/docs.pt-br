---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854806"
---
# \<webScriptEndpoint>
<span data-ttu-id="fdd9f-101">Este elemento de configuração define um ponto de extremidade padrão com uma [\<webHttpBinding>](webhttpbinding.md) Associação fixa que adiciona automaticamente o [\<enableWebScript>](enablewebscript.md) comportamento.</span><span class="sxs-lookup"><span data-stu-id="fdd9f-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="fdd9f-102">Use esse ponto de extremidade quando estiver escrevendo um serviço que é chamado de um aplicativo ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="fdd9f-102">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="fdd9f-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdd9f-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdd9f-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fdd9f-104">Attributes and Elements</span></span>  
 <span data-ttu-id="fdd9f-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fdd9f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdd9f-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="fdd9f-106">Attributes</span></span>  
  
|<span data-ttu-id="fdd9f-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="fdd9f-107">Attribute</span></span>|<span data-ttu-id="fdd9f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdd9f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fdd9f-109">WebEndpointType</span><span class="sxs-lookup"><span data-stu-id="fdd9f-109">webEndpointType</span></span>|<span data-ttu-id="fdd9f-110">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fdd9f-110">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdd9f-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fdd9f-111">Child Elements</span></span>  
 <span data-ttu-id="fdd9f-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fdd9f-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fdd9f-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fdd9f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="fdd9f-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="fdd9f-114">Element</span></span>|<span data-ttu-id="fdd9f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdd9f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="fdd9f-116">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="fdd9f-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdd9f-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="fdd9f-117">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
