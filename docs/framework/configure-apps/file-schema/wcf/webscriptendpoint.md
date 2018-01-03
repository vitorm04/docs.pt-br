---
title: '&lt;webScriptEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 855a0fc0727bf0559b922317d439f7550f18d9ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="7fdac-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="7fdac-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="7fdac-103">Este elemento de configuração define um ponto de extremidade padrão fixa [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação que automaticamente adiciona o [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento.</span><span class="sxs-lookup"><span data-stu-id="7fdac-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="7fdac-104">Use esse ponto de extremidade quando você estiver escrevendo um serviço que é chamado de um aplicativo ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="7fdac-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="7fdac-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7fdac-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="7fdac-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="7fdac-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fdac-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fdac-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fdac-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7fdac-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7fdac-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7fdac-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fdac-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="7fdac-110">Attributes</span></span>  
  
|<span data-ttu-id="7fdac-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="7fdac-111">Attribute</span></span>|<span data-ttu-id="7fdac-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fdac-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7fdac-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="7fdac-113">webEndpointType</span></span>|<span data-ttu-id="7fdac-114">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7fdac-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fdac-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7fdac-115">Child Elements</span></span>  
 <span data-ttu-id="7fdac-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7fdac-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7fdac-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7fdac-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7fdac-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="7fdac-118">Element</span></span>|<span data-ttu-id="7fdac-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fdac-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fdac-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="7fdac-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="7fdac-121">Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="7fdac-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fdac-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fdac-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
