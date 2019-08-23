---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 366def5d0f4cc82b0ff0a5127701b0b5a6adb6a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940497"
---
# <a name="webhttp"></a><span data-ttu-id="dd9f9-101">\<> Webhttp</span><span class="sxs-lookup"><span data-stu-id="dd9f9-101">\<webHttp></span></span>
<span data-ttu-id="dd9f9-102">Esse elemento Especifica o <xref:System.ServiceModel.Description.WebHttpBehavior> em um ponto de extremidade por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="dd9f9-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="dd9f9-103">Esse comportamento, quando usado em conjunto com o [ \<WebHttpBinding >](webhttpbinding.md) associação padrão, habilita o modelo de programação da Web para um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dd9f9-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="dd9f9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dd9f9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dd9f9-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="dd9f9-105">\<behaviors></span></span>  
<span data-ttu-id="dd9f9-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="dd9f9-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="dd9f9-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="dd9f9-107">\<behavior></span></span>  
<span data-ttu-id="dd9f9-108">\<> Webhttp</span><span class="sxs-lookup"><span data-stu-id="dd9f9-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd9f9-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd9f9-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd9f9-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dd9f9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dd9f9-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dd9f9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd9f9-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="dd9f9-112">Attributes</span></span>  
  
|<span data-ttu-id="dd9f9-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="dd9f9-113">Attribute</span></span>|<span data-ttu-id="dd9f9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd9f9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd9f9-115">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="dd9f9-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="dd9f9-116">Quando essa propriedade é definida como `true`, a infraestrutura do WCF determina o melhor formato a ser usado.</span><span class="sxs-lookup"><span data-stu-id="dd9f9-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="dd9f9-117">A seleção automática de formato é desabilitada por padrão para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="dd9f9-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="dd9f9-118">A seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="dd9f9-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="dd9f9-119">DefaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="dd9f9-119">defaultBodyStyle</span></span>|<span data-ttu-id="dd9f9-120">Especifica o estilo de corpo padrão de mensagens retornadas.</span><span class="sxs-lookup"><span data-stu-id="dd9f9-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="dd9f9-121">Para obter mais informações, <xref:System.ServiceModel.Web.WebMessageBodyStyle> consulte e [formatação de http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="dd9f9-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="dd9f9-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="dd9f9-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="dd9f9-123">Especifica o formato de resposta de saída padrão para mensagens.</span><span class="sxs-lookup"><span data-stu-id="dd9f9-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="dd9f9-124">Para obter mais informações, consulte [formatação de http do WCF Web](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="dd9f9-124">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="dd9f9-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="dd9f9-125">faultExceptionEnabled</span></span>|<span data-ttu-id="dd9f9-126">Obtém ou define o sinalizador que especifica se uma FaultException é gerada quando ocorre um erro de servidor interno (código de status HTTP: 500).</span><span class="sxs-lookup"><span data-stu-id="dd9f9-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="dd9f9-127">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="dd9f9-127">helpEnabled</span></span>|<span data-ttu-id="dd9f9-128">Obtém ou define um valor que determina se a página de ajuda está habilitada.</span><span class="sxs-lookup"><span data-stu-id="dd9f9-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd9f9-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dd9f9-129">Child Elements</span></span>  
 <span data-ttu-id="dd9f9-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="dd9f9-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd9f9-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dd9f9-131">Parent Elements</span></span>  
  
|<span data-ttu-id="dd9f9-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd9f9-132">Element</span></span>|<span data-ttu-id="dd9f9-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd9f9-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd9f9-134">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="dd9f9-134">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="dd9f9-135">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="dd9f9-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd9f9-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd9f9-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="dd9f9-137">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="dd9f9-137">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="dd9f9-138">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="dd9f9-138">\<webHttpBinding></span></span>](webhttpbinding.md)
