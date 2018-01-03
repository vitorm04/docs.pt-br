---
title: '&lt;webHttp&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b488d4e4884f92b107b2b6be71827a2f8b4cdbf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebhttpgt"></a><span data-ttu-id="5e3bd-102">&lt;webHttp&gt;</span><span class="sxs-lookup"><span data-stu-id="5e3bd-102">&lt;webHttp&gt;</span></span>
<span data-ttu-id="5e3bd-103">Este elemento Especifica o <xref:System.ServiceModel.Description.WebHttpBehavior> em um ponto de extremidade por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="5e3bd-103">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="5e3bd-104">Esse comportamento, quando usado em conjunto com o [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação padrão, permite que o modelo de programação da Web para um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="5e3bd-104">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>  
  
 <span data-ttu-id="5e3bd-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5e3bd-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e3bd-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="5e3bd-106">\<behaviors></span></span>  
<span data-ttu-id="5e3bd-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5e3bd-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="5e3bd-108">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="5e3bd-108">\<behavior></span></span>  
<span data-ttu-id="5e3bd-109">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="5e3bd-109">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e3bd-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e3bd-110">Syntax</span></span>  
  
```xml  
<webHttp />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e3bd-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5e3bd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5e3bd-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5e3bd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e3bd-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e3bd-113">Attributes</span></span>  
  
|<span data-ttu-id="5e3bd-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="5e3bd-114">Attribute</span></span>|<span data-ttu-id="5e3bd-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e3bd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e3bd-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="5e3bd-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="5e3bd-117">Quando essa propriedade é definida como `true`, a infraestrutura WCF determina o melhor formato a ser usado.</span><span class="sxs-lookup"><span data-stu-id="5e3bd-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="5e3bd-118">Seleção automática de formato com versões anteriores é desabilitada por padrão para compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="5e3bd-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="5e3bd-119">Seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="5e3bd-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="5e3bd-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="5e3bd-120">defaultBodyStyle</span></span>|<span data-ttu-id="5e3bd-121">Especifica o estilo de corpo padrão das mensagens retornadas.</span><span class="sxs-lookup"><span data-stu-id="5e3bd-121">Specifies the default body style of returned messages.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="5e3bd-122"><xref:System.ServiceModel.Web.WebMessageBodyStyle> e [formatação HTTP Web do WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="5e3bd-122"> <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="5e3bd-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="5e3bd-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="5e3bd-124">Especifica o formato de resposta de saída do padrão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="5e3bd-124">Specifies the default outgoing response format for messages.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="5e3bd-125">[Formatação HTTP Web do WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="5e3bd-125"> [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="5e3bd-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="5e3bd-126">faultExceptionEnabled</span></span>|<span data-ttu-id="5e3bd-127">Obtém ou define o sinalizador que especifica se uma FaultException é gerada quando ocorre um erro de servidor interno (código de status HTTP: 500).</span><span class="sxs-lookup"><span data-stu-id="5e3bd-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="5e3bd-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="5e3bd-128">helpEnabled</span></span>|<span data-ttu-id="5e3bd-129">Obtém ou define um valor que determina se a página de Ajuda está habilitada.</span><span class="sxs-lookup"><span data-stu-id="5e3bd-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e3bd-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5e3bd-130">Child Elements</span></span>  
 <span data-ttu-id="5e3bd-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5e3bd-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e3bd-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e3bd-132">Parent Elements</span></span>  
  
|<span data-ttu-id="5e3bd-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e3bd-133">Element</span></span>|<span data-ttu-id="5e3bd-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e3bd-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e3bd-135">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="5e3bd-135">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5e3bd-136">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5e3bd-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e3bd-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e3bd-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="5e3bd-138">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="5e3bd-138">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="5e3bd-139">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="5e3bd-139">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
