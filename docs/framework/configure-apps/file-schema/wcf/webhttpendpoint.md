---
title: '&lt;webHttpEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 46691a36b62898583132b5668b06de5659926d66
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767083"
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="2fe24-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="2fe24-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="2fe24-103">Este elemento de configuração define um ponto de extremidade padrão fixa [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação que automaticamente adiciona o [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) comportamento.</span><span class="sxs-lookup"><span data-stu-id="2fe24-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="2fe24-104">Use esse ponto de extremidade ao escrever um serviço REST.</span><span class="sxs-lookup"><span data-stu-id="2fe24-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="2fe24-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2fe24-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2fe24-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2fe24-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fe24-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fe24-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String" 
                        defaultOutgoingResponseFormat="Xml/Json" 
                        helpEnabled="Boolean" 
                        webEndpointType="String"/>
    </webHttpEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fe24-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2fe24-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2fe24-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2fe24-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fe24-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2fe24-110">Attributes</span></span>  
  
|<span data-ttu-id="2fe24-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="2fe24-111">Attribute</span></span>|<span data-ttu-id="2fe24-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fe24-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2fe24-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="2fe24-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="2fe24-114">Um valor booliano que indica se a seleção automática de formato é habilitada.</span><span class="sxs-lookup"><span data-stu-id="2fe24-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="2fe24-115">Quando a seleção automática de formato estiver habilitada, a infraestrutura analisa o `Accept` cabeçalho da mensagem de solicitação e determina o formato de resposta mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="2fe24-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="2fe24-116">Se o `Accept` cabeçalho não especifica um formato de resposta adequado, usa a infraestrutura de `Content-Type` de mensagem de solicitação ou o formato de resposta padrão da operação.</span><span class="sxs-lookup"><span data-stu-id="2fe24-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="2fe24-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="2fe24-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="2fe24-118">Um atributo que especifica o formato de resposta de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="2fe24-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="2fe24-119">Esse atributo é do <xref:System.ServiceModel.Web.WebMessageFormat> tipo</span><span class="sxs-lookup"><span data-stu-id="2fe24-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="2fe24-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="2fe24-120">helpEnabled</span></span>|<span data-ttu-id="2fe24-121">Um valor booliano que indica se a página de ajuda HTTP está habilitada para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2fe24-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="2fe24-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="2fe24-122">webEndpointType</span></span>|<span data-ttu-id="2fe24-123">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2fe24-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fe24-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2fe24-124">Child Elements</span></span>  
 <span data-ttu-id="2fe24-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2fe24-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2fe24-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2fe24-126">Parent Elements</span></span>  
  
|<span data-ttu-id="2fe24-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="2fe24-127">Element</span></span>|<span data-ttu-id="2fe24-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fe24-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fe24-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2fe24-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="2fe24-130">Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="2fe24-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2fe24-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fe24-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
