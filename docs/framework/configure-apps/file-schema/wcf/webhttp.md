---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 795e61b9054d2ea9276970988018c50099bcbe17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769792"
---
# <a name="webhttp"></a><span data-ttu-id="a1eaf-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="a1eaf-101">\<webHttp></span></span>
<span data-ttu-id="a1eaf-102">Esse elemento Especifica o <xref:System.ServiceModel.Description.WebHttpBehavior> em um ponto de extremidade por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="a1eaf-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="a1eaf-103">Esse comportamento, quando usado em conjunto com o [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) habilita a associação padrão, o modelo de programação da Web para um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a1eaf-103">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="a1eaf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a1eaf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a1eaf-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="a1eaf-105">\<behaviors></span></span>  
<span data-ttu-id="a1eaf-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a1eaf-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="a1eaf-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a1eaf-107">\<behavior></span></span>  
<span data-ttu-id="a1eaf-108">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="a1eaf-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1eaf-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1eaf-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1eaf-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a1eaf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a1eaf-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a1eaf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1eaf-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a1eaf-112">Attributes</span></span>  
  
|<span data-ttu-id="a1eaf-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a1eaf-113">Attribute</span></span>|<span data-ttu-id="a1eaf-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1eaf-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a1eaf-115">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="a1eaf-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="a1eaf-116">Quando essa propriedade é definida como `true`, a infraestrutura WCF determina o melhor formato para usar.</span><span class="sxs-lookup"><span data-stu-id="a1eaf-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="a1eaf-117">Seleção automática de formato com versões anteriores é desabilitada por padrão para compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="a1eaf-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="a1eaf-118">Seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="a1eaf-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="a1eaf-119">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="a1eaf-119">defaultBodyStyle</span></span>|<span data-ttu-id="a1eaf-120">Especifica o estilo de corpo padrão das mensagens retornadas.</span><span class="sxs-lookup"><span data-stu-id="a1eaf-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="a1eaf-121">Para obter mais informações, consulte <xref:System.ServiceModel.Web.WebMessageBodyStyle> e [formatação do WCF Web HTTP](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="a1eaf-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="a1eaf-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="a1eaf-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="a1eaf-123">Especifica o formato de resposta da saída padrão para mensagens.</span><span class="sxs-lookup"><span data-stu-id="a1eaf-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="a1eaf-124">Para obter mais informações, consulte [formatação do WCF Web HTTP](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="a1eaf-124">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="a1eaf-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="a1eaf-125">faultExceptionEnabled</span></span>|<span data-ttu-id="a1eaf-126">Obtém ou define o sinalizador que especifica se uma FaultException é gerada quando ocorre um erro de servidor interno (código de status HTTP: 500).</span><span class="sxs-lookup"><span data-stu-id="a1eaf-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="a1eaf-127">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="a1eaf-127">helpEnabled</span></span>|<span data-ttu-id="a1eaf-128">Obtém ou define um valor que determina se a página de Ajuda está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a1eaf-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1eaf-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a1eaf-129">Child Elements</span></span>  
 <span data-ttu-id="a1eaf-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a1eaf-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1eaf-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a1eaf-131">Parent Elements</span></span>  
  
|<span data-ttu-id="a1eaf-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1eaf-132">Element</span></span>|<span data-ttu-id="a1eaf-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1eaf-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1eaf-134">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a1eaf-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a1eaf-135">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a1eaf-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1eaf-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1eaf-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="a1eaf-137">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="a1eaf-137">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="a1eaf-138">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a1eaf-138">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
