---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: 3d95624c82388ed6219fc567dd2d3c17bedad7a1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255283"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="85b9b-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="85b9b-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="85b9b-102">Este elemento de configuração define um ponto de extremidade padrão com um fixo [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação que automaticamente adiciona o [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento.</span><span class="sxs-lookup"><span data-stu-id="85b9b-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="85b9b-103">Use esse ponto de extremidade quando você estiver escrevendo um serviço que é chamado de um aplicativo ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="85b9b-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="85b9b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="85b9b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="85b9b-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="85b9b-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85b9b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85b9b-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85b9b-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="85b9b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="85b9b-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="85b9b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85b9b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="85b9b-109">Attributes</span></span>  
  
|<span data-ttu-id="85b9b-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="85b9b-110">Attribute</span></span>|<span data-ttu-id="85b9b-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="85b9b-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85b9b-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="85b9b-112">webEndpointType</span></span>|<span data-ttu-id="85b9b-113">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="85b9b-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85b9b-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="85b9b-114">Child Elements</span></span>  
 <span data-ttu-id="85b9b-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="85b9b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85b9b-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="85b9b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="85b9b-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="85b9b-117">Element</span></span>|<span data-ttu-id="85b9b-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="85b9b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85b9b-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="85b9b-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="85b9b-120">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="85b9b-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85b9b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85b9b-121">See also</span></span>
- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
