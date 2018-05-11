---
title: '&lt;webScriptEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b53b7cc3ce812b72830c0ad83c5cc2b42bfc25a7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="26b52-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="26b52-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="26b52-103">Este elemento de configuração define um ponto de extremidade padrão fixa [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação que automaticamente adiciona o [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento.</span><span class="sxs-lookup"><span data-stu-id="26b52-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="26b52-104">Use esse ponto de extremidade quando você estiver escrevendo um serviço que é chamado de um aplicativo ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="26b52-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="26b52-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="26b52-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="26b52-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="26b52-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26b52-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26b52-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26b52-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="26b52-108">Attributes and Elements</span></span>  
 <span data-ttu-id="26b52-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="26b52-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26b52-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="26b52-110">Attributes</span></span>  
  
|<span data-ttu-id="26b52-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="26b52-111">Attribute</span></span>|<span data-ttu-id="26b52-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="26b52-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26b52-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="26b52-113">webEndpointType</span></span>|<span data-ttu-id="26b52-114">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="26b52-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26b52-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="26b52-115">Child Elements</span></span>  
 <span data-ttu-id="26b52-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="26b52-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26b52-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="26b52-117">Parent Elements</span></span>  
  
|<span data-ttu-id="26b52-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="26b52-118">Element</span></span>|<span data-ttu-id="26b52-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="26b52-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26b52-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="26b52-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="26b52-121">Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="26b52-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26b52-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26b52-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
