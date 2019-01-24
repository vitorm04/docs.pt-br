---
title: '&lt;webScriptEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: acafb5b6a5c4911dcf21a55cfb9e93883067e5ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566379"
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="ac481-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="ac481-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="ac481-103">Este elemento de configuração define um ponto de extremidade padrão com um fixo [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação que automaticamente adiciona o [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento.</span><span class="sxs-lookup"><span data-stu-id="ac481-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="ac481-104">Use esse ponto de extremidade quando você estiver escrevendo um serviço que é chamado de um aplicativo ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="ac481-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="ac481-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ac481-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ac481-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ac481-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac481-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac481-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac481-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ac481-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ac481-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ac481-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac481-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ac481-110">Attributes</span></span>  
  
|<span data-ttu-id="ac481-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ac481-111">Attribute</span></span>|<span data-ttu-id="ac481-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac481-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac481-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="ac481-113">webEndpointType</span></span>|<span data-ttu-id="ac481-114">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ac481-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac481-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ac481-115">Child Elements</span></span>  
 <span data-ttu-id="ac481-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ac481-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac481-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ac481-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ac481-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="ac481-118">Element</span></span>|<span data-ttu-id="ac481-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac481-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac481-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ac481-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="ac481-121">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="ac481-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac481-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac481-122">See also</span></span>
- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
