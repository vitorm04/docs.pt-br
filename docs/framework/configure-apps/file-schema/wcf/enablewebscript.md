---
title: '&lt;enableWebScript&gt;'
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 1115b598776ca7d28698815974e06f3de57be598
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600096"
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="963bb-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="963bb-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="963bb-103">Esse elemento permite que o comportamento de ponto de extremidade que torna possível consumir o serviço de páginas da web de ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="963bb-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="963bb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="963bb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="963bb-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="963bb-105">\<behaviors></span></span>  
<span data-ttu-id="963bb-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="963bb-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="963bb-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="963bb-107">\<behavior></span></span>  
<span data-ttu-id="963bb-108">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="963bb-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="963bb-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="963bb-109">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="963bb-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="963bb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="963bb-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="963bb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="963bb-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="963bb-112">Attributes</span></span>  
 <span data-ttu-id="963bb-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="963bb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="963bb-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="963bb-114">Child Elements</span></span>  
 <span data-ttu-id="963bb-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="963bb-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="963bb-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="963bb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="963bb-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="963bb-117">Element</span></span>|<span data-ttu-id="963bb-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="963bb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="963bb-119">\<behavior></span><span class="sxs-lookup"><span data-stu-id="963bb-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="963bb-120">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="963bb-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="963bb-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="963bb-121">Remarks</span></span>  
 <span data-ttu-id="963bb-122">Esse comportamento só deve ser usado em conjunto com qualquer um de [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação padrão, ou o [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="963bb-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="963bb-123">Para obter mais informações sobre esse comportamento, consulte <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="963bb-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963bb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="963bb-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="963bb-125">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="963bb-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="963bb-126">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="963bb-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
