---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854806"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="761b8-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="761b8-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="761b8-102">Este elemento de configuração define um ponto de extremidade padrão com uma associação [ \<WebHttpBinding fixa >](webhttpbinding.md) que adiciona automaticamente o comportamento de [ \<> enableWebScript](enablewebscript.md) .</span><span class="sxs-lookup"><span data-stu-id="761b8-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="761b8-103">Use esse ponto de extremidade quando estiver escrevendo um serviço que é chamado de um aplicativo ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="761b8-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="761b8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="761b8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="761b8-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="761b8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="761b8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="761b8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="761b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> webScriptEndpoint**</span><span class="sxs-lookup"><span data-stu-id="761b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="761b8-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="761b8-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="761b8-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="761b8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="761b8-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="761b8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="761b8-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="761b8-111">Attributes</span></span>  
  
|<span data-ttu-id="761b8-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="761b8-112">Attribute</span></span>|<span data-ttu-id="761b8-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="761b8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="761b8-114">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="761b8-114">webEndpointType</span></span>|<span data-ttu-id="761b8-115">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="761b8-115">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="761b8-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="761b8-116">Child Elements</span></span>  
 <span data-ttu-id="761b8-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="761b8-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="761b8-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="761b8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="761b8-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="761b8-119">Element</span></span>|<span data-ttu-id="761b8-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="761b8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="761b8-121">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="761b8-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="761b8-122">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="761b8-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="761b8-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="761b8-123">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
