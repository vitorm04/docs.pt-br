---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400382"
---
# <a name="enablewebscript"></a><span data-ttu-id="5f0a7-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="5f0a7-101">\<enableWebScript></span></span>
<span data-ttu-id="5f0a7-102">Esse elemento habilita o comportamento do ponto de extremidade que torna possível consumir o serviço de páginas da Web do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="5f0a7-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
<span data-ttu-id="5f0a7-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5f0a7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5f0a7-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5f0a7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5f0a7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5f0a7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5f0a7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5f0a7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="5f0a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5f0a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="5f0a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> enableWebScript**</span><span class="sxs-lookup"><span data-stu-id="5f0a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f0a7-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f0a7-109">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f0a7-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5f0a7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5f0a7-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5f0a7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f0a7-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5f0a7-112">Attributes</span></span>  
 <span data-ttu-id="5f0a7-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5f0a7-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f0a7-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5f0a7-114">Child Elements</span></span>  
 <span data-ttu-id="5f0a7-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5f0a7-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f0a7-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5f0a7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5f0a7-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="5f0a7-117">Element</span></span>|<span data-ttu-id="5f0a7-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f0a7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f0a7-119">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="5f0a7-119">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="5f0a7-120">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5f0a7-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f0a7-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f0a7-121">Remarks</span></span>  
 <span data-ttu-id="5f0a7-122">Esse comportamento só deve ser usado em conjunto com a associação de [ \<WebHttpBinding >](webhttpbinding.md) padrão ou com o elemento de associação de [ \<> webMessageEncoding](webmessageencoding.md) .</span><span class="sxs-lookup"><span data-stu-id="5f0a7-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="5f0a7-123">Para obter mais informações sobre esse comportamento, <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>consulte.</span><span class="sxs-lookup"><span data-stu-id="5f0a7-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f0a7-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f0a7-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="5f0a7-125">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="5f0a7-125">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="5f0a7-126">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="5f0a7-126">\<webHttp></span></span>](webhttp.md)
