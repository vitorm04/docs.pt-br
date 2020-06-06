---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399162"
---
# \<webHttp>
<span data-ttu-id="13449-101">Esse elemento Especifica o <xref:System.ServiceModel.Description.WebHttpBehavior> em um ponto de extremidade por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="13449-101">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="13449-102">Esse comportamento, quando usado em conjunto com a [\<webHttpBinding>](webhttpbinding.md) associação padrão, habilita o modelo de programação da Web para um serviço Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="13449-102">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a><span data-ttu-id="13449-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13449-103">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13449-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13449-104">Attributes and Elements</span></span>  
 <span data-ttu-id="13449-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="13449-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13449-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="13449-106">Attributes</span></span>  
  
|<span data-ttu-id="13449-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="13449-107">Attribute</span></span>|<span data-ttu-id="13449-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="13449-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13449-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="13449-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="13449-110">Quando essa propriedade é definida como `true` , a infraestrutura do WCF determina o melhor formato a ser usado.</span><span class="sxs-lookup"><span data-stu-id="13449-110">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="13449-111">A seleção automática de formato é desabilitada por padrão para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="13449-111">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="13449-112">A seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="13449-112">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="13449-113">DefaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="13449-113">defaultBodyStyle</span></span>|<span data-ttu-id="13449-114">Especifica o estilo de corpo padrão de mensagens retornadas.</span><span class="sxs-lookup"><span data-stu-id="13449-114">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="13449-115">Para obter mais informações, consulte <xref:System.ServiceModel.Web.WebMessageBodyStyle> e [formatação de http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="13449-115">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="13449-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="13449-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="13449-117">Especifica o formato de resposta de saída padrão para mensagens.</span><span class="sxs-lookup"><span data-stu-id="13449-117">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="13449-118">Para obter mais informações, consulte [formatação de http do WCF Web](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="13449-118">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="13449-119">Não</span><span class="sxs-lookup"><span data-stu-id="13449-119">faultExceptionEnabled</span></span>|<span data-ttu-id="13449-120">Obtém ou define o sinalizador que especifica se uma FaultException é gerada quando ocorre um erro de servidor interno (código de status HTTP: 500).</span><span class="sxs-lookup"><span data-stu-id="13449-120">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="13449-121">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="13449-121">helpEnabled</span></span>|<span data-ttu-id="13449-122">Obtém ou define um valor que determina se a página de ajuda está habilitada.</span><span class="sxs-lookup"><span data-stu-id="13449-122">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13449-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="13449-123">Child Elements</span></span>  
 <span data-ttu-id="13449-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="13449-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13449-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="13449-125">Parent Elements</span></span>  
  
|<span data-ttu-id="13449-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="13449-126">Element</span></span>|<span data-ttu-id="13449-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="13449-127">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="13449-128">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="13449-128">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13449-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="13449-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="13449-130">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="13449-130">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
