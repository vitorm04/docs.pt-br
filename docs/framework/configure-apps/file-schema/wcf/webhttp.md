---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: ca6d401109d14ce11dcd40c393cd079170e4d20d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259859"
---
# <a name="webhttp"></a><span data-ttu-id="8e5b9-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="8e5b9-101">\<webHttp></span></span>
<span data-ttu-id="8e5b9-102">Esse elemento Especifica o <xref:System.ServiceModel.Description.WebHttpBehavior> em um ponto de extremidade por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="8e5b9-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="8e5b9-103">Esse comportamento, quando usado em conjunto com o [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) habilita a associação padrão, o modelo de programação da Web para um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8e5b9-103">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="8e5b9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8e5b9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8e5b9-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="8e5b9-105">\<behaviors></span></span>  
<span data-ttu-id="8e5b9-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="8e5b9-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="8e5b9-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="8e5b9-107">\<behavior></span></span>  
<span data-ttu-id="8e5b9-108">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="8e5b9-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e5b9-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e5b9-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e5b9-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8e5b9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8e5b9-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8e5b9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e5b9-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e5b9-112">Attributes</span></span>  
  
|<span data-ttu-id="8e5b9-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8e5b9-113">Attribute</span></span>|<span data-ttu-id="8e5b9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e5b9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e5b9-115">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="8e5b9-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="8e5b9-116">Quando essa propriedade é definida como `true`, a infraestrutura WCF determina o melhor formato para usar.</span><span class="sxs-lookup"><span data-stu-id="8e5b9-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="8e5b9-117">Seleção automática de formato com versões anteriores é desabilitada por padrão para compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="8e5b9-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="8e5b9-118">Seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="8e5b9-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="8e5b9-119">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="8e5b9-119">defaultBodyStyle</span></span>|<span data-ttu-id="8e5b9-120">Especifica o estilo de corpo padrão das mensagens retornadas.</span><span class="sxs-lookup"><span data-stu-id="8e5b9-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="8e5b9-121">Para obter mais informações, consulte <xref:System.ServiceModel.Web.WebMessageBodyStyle> e [formatação do WCF Web HTTP](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="8e5b9-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="8e5b9-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="8e5b9-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="8e5b9-123">Especifica o formato de resposta da saída padrão para mensagens.</span><span class="sxs-lookup"><span data-stu-id="8e5b9-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="8e5b9-124">Para obter mais informações, consulte [formatação do WCF Web HTTP](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="8e5b9-124">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="8e5b9-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="8e5b9-125">faultExceptionEnabled</span></span>|<span data-ttu-id="8e5b9-126">Obtém ou define o sinalizador que especifica se uma FaultException é gerada quando ocorre um erro de servidor interno (código de status HTTP: 500).</span><span class="sxs-lookup"><span data-stu-id="8e5b9-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="8e5b9-127">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="8e5b9-127">helpEnabled</span></span>|<span data-ttu-id="8e5b9-128">Obtém ou define um valor que determina se a página de Ajuda está habilitada.</span><span class="sxs-lookup"><span data-stu-id="8e5b9-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e5b9-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8e5b9-129">Child Elements</span></span>  
 <span data-ttu-id="8e5b9-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8e5b9-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e5b9-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8e5b9-131">Parent Elements</span></span>  
  
|<span data-ttu-id="8e5b9-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e5b9-132">Element</span></span>|<span data-ttu-id="8e5b9-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e5b9-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e5b9-134">\<behavior></span><span class="sxs-lookup"><span data-stu-id="8e5b9-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8e5b9-135">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8e5b9-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e5b9-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e5b9-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="8e5b9-137">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="8e5b9-137">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="8e5b9-138">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8e5b9-138">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
