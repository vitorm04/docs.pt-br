---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399162"
---
# <a name="webhttp"></a><span data-ttu-id="a6938-101">\<> Webhttp</span><span class="sxs-lookup"><span data-stu-id="a6938-101">\<webHttp></span></span>
<span data-ttu-id="a6938-102">Esse elemento Especifica o <xref:System.ServiceModel.Description.WebHttpBehavior> em um ponto de extremidade por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="a6938-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="a6938-103">Esse comportamento, quando usado em conjunto com o [ \<WebHttpBinding >](webhttpbinding.md) associação padrão, habilita o modelo de programação da Web para um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a6938-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
<span data-ttu-id="a6938-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6938-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a6938-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a6938-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a6938-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a6938-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a6938-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a6938-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="a6938-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a6938-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="a6938-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Webhttp**</span><span class="sxs-lookup"><span data-stu-id="a6938-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6938-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6938-110">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6938-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a6938-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a6938-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a6938-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6938-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a6938-113">Attributes</span></span>  
  
|<span data-ttu-id="a6938-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="a6938-114">Attribute</span></span>|<span data-ttu-id="a6938-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6938-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6938-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="a6938-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="a6938-117">Quando essa propriedade é definida como `true`, a infraestrutura do WCF determina o melhor formato a ser usado.</span><span class="sxs-lookup"><span data-stu-id="a6938-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="a6938-118">A seleção automática de formato é desabilitada por padrão para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="a6938-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="a6938-119">A seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="a6938-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="a6938-120">DefaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="a6938-120">defaultBodyStyle</span></span>|<span data-ttu-id="a6938-121">Especifica o estilo de corpo padrão de mensagens retornadas.</span><span class="sxs-lookup"><span data-stu-id="a6938-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="a6938-122">Para obter mais informações, <xref:System.ServiceModel.Web.WebMessageBodyStyle> consulte e [formatação de http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="a6938-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="a6938-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="a6938-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="a6938-124">Especifica o formato de resposta de saída padrão para mensagens.</span><span class="sxs-lookup"><span data-stu-id="a6938-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="a6938-125">Para obter mais informações, consulte [formatação de http do WCF Web](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="a6938-125">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="a6938-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="a6938-126">faultExceptionEnabled</span></span>|<span data-ttu-id="a6938-127">Obtém ou define o sinalizador que especifica se uma FaultException é gerada quando ocorre um erro de servidor interno (código de status HTTP: 500).</span><span class="sxs-lookup"><span data-stu-id="a6938-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="a6938-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="a6938-128">helpEnabled</span></span>|<span data-ttu-id="a6938-129">Obtém ou define um valor que determina se a página de ajuda está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a6938-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6938-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a6938-130">Child Elements</span></span>  
 <span data-ttu-id="a6938-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a6938-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6938-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a6938-132">Parent Elements</span></span>  
  
|<span data-ttu-id="a6938-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6938-133">Element</span></span>|<span data-ttu-id="a6938-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6938-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6938-135">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="a6938-135">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a6938-136">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a6938-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6938-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6938-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="a6938-138">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="a6938-138">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="a6938-139">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a6938-139">\<webHttpBinding></span></span>](webhttpbinding.md)
