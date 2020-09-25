---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 716d960e2d5f896976c22a60d419d9b165b36178
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202455"
---
# \<webHttp>

<span data-ttu-id="c3e53-101">Esse elemento Especifica o <xref:System.ServiceModel.Description.WebHttpBehavior> em um ponto de extremidade por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="c3e53-101">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="c3e53-102">Esse comportamento, quando usado em conjunto com a [\<webHttpBinding>](webhttpbinding.md) associação padrão, habilita o modelo de programação da Web para um serviço Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c3e53-102">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a><span data-ttu-id="c3e53-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3e53-103">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3e53-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c3e53-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c3e53-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c3e53-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3e53-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="c3e53-106">Attributes</span></span>  
  
|<span data-ttu-id="c3e53-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="c3e53-107">Attribute</span></span>|<span data-ttu-id="c3e53-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3e53-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3e53-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="c3e53-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="c3e53-110">Quando essa propriedade é definida como `true` , a infraestrutura do WCF determina o melhor formato a ser usado.</span><span class="sxs-lookup"><span data-stu-id="c3e53-110">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="c3e53-111">A seleção automática de formato é desabilitada por padrão para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="c3e53-111">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="c3e53-112">A seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="c3e53-112">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="c3e53-113">DefaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="c3e53-113">defaultBodyStyle</span></span>|<span data-ttu-id="c3e53-114">Especifica o estilo de corpo padrão de mensagens retornadas.</span><span class="sxs-lookup"><span data-stu-id="c3e53-114">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="c3e53-115">Para obter mais informações, consulte <xref:System.ServiceModel.Web.WebMessageBodyStyle> e [formatação de http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="c3e53-115">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="c3e53-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="c3e53-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="c3e53-117">Especifica o formato de resposta de saída padrão para mensagens.</span><span class="sxs-lookup"><span data-stu-id="c3e53-117">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="c3e53-118">Para obter mais informações, consulte [formatação de http do WCF Web](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="c3e53-118">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="c3e53-119">Não</span><span class="sxs-lookup"><span data-stu-id="c3e53-119">faultExceptionEnabled</span></span>|<span data-ttu-id="c3e53-120">Obtém ou define o sinalizador que especifica se uma FaultException é gerada quando ocorre um erro de servidor interno (código de status HTTP: 500).</span><span class="sxs-lookup"><span data-stu-id="c3e53-120">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="c3e53-121">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="c3e53-121">helpEnabled</span></span>|<span data-ttu-id="c3e53-122">Obtém ou define um valor que determina se a página de ajuda está habilitada.</span><span class="sxs-lookup"><span data-stu-id="c3e53-122">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3e53-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c3e53-123">Child Elements</span></span>  

 <span data-ttu-id="c3e53-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c3e53-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3e53-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c3e53-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c3e53-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="c3e53-126">Element</span></span>|<span data-ttu-id="c3e53-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3e53-127">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c3e53-128">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c3e53-128">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3e53-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="c3e53-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="c3e53-130">Integração de AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="c3e53-130">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
