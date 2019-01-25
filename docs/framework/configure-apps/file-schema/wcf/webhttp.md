---
title: '&lt;webHttp&gt;'
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: b52259af5e05de5bf5dd42a2cd0bf4b01f3e46f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597548"
---
# <a name="ltwebhttpgt"></a><span data-ttu-id="70e1e-102">&lt;webHttp&gt;</span><span class="sxs-lookup"><span data-stu-id="70e1e-102">&lt;webHttp&gt;</span></span>
<span data-ttu-id="70e1e-103">Esse elemento Especifica o <xref:System.ServiceModel.Description.WebHttpBehavior> em um ponto de extremidade por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="70e1e-103">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="70e1e-104">Esse comportamento, quando usado em conjunto com o [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) habilita a associação padrão, o modelo de programação da Web para um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="70e1e-104">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="70e1e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="70e1e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="70e1e-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="70e1e-106">\<behaviors></span></span>  
<span data-ttu-id="70e1e-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="70e1e-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="70e1e-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="70e1e-108">\<behavior></span></span>  
<span data-ttu-id="70e1e-109">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="70e1e-109">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70e1e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70e1e-110">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70e1e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="70e1e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="70e1e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="70e1e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70e1e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="70e1e-113">Attributes</span></span>  
  
|<span data-ttu-id="70e1e-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="70e1e-114">Attribute</span></span>|<span data-ttu-id="70e1e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="70e1e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70e1e-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="70e1e-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="70e1e-117">Quando essa propriedade é definida como `true`, a infraestrutura WCF determina o melhor formato para usar.</span><span class="sxs-lookup"><span data-stu-id="70e1e-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="70e1e-118">Seleção automática de formato com versões anteriores é desabilitada por padrão para compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="70e1e-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="70e1e-119">Seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="70e1e-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="70e1e-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="70e1e-120">defaultBodyStyle</span></span>|<span data-ttu-id="70e1e-121">Especifica o estilo de corpo padrão das mensagens retornadas.</span><span class="sxs-lookup"><span data-stu-id="70e1e-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="70e1e-122">Para obter mais informações, consulte <xref:System.ServiceModel.Web.WebMessageBodyStyle> e [formatação do WCF Web HTTP](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="70e1e-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="70e1e-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="70e1e-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="70e1e-124">Especifica o formato de resposta da saída padrão para mensagens.</span><span class="sxs-lookup"><span data-stu-id="70e1e-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="70e1e-125">Para obter mais informações, consulte [formatação do WCF Web HTTP](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="70e1e-125">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="70e1e-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="70e1e-126">faultExceptionEnabled</span></span>|<span data-ttu-id="70e1e-127">Obtém ou define o sinalizador que especifica se uma FaultException é gerada quando ocorre um erro de servidor interno (código de status HTTP: 500).</span><span class="sxs-lookup"><span data-stu-id="70e1e-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="70e1e-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="70e1e-128">helpEnabled</span></span>|<span data-ttu-id="70e1e-129">Obtém ou define um valor que determina se a página de Ajuda está habilitada.</span><span class="sxs-lookup"><span data-stu-id="70e1e-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70e1e-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="70e1e-130">Child Elements</span></span>  
 <span data-ttu-id="70e1e-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="70e1e-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70e1e-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="70e1e-132">Parent Elements</span></span>  
  
|<span data-ttu-id="70e1e-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="70e1e-133">Element</span></span>|<span data-ttu-id="70e1e-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="70e1e-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70e1e-135">\<behavior></span><span class="sxs-lookup"><span data-stu-id="70e1e-135">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="70e1e-136">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="70e1e-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70e1e-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70e1e-137">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="70e1e-138">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="70e1e-138">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="70e1e-139">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="70e1e-139">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
