---
title: '&lt;enableWebScript&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cfb6981947b457d5fdad59e96bdcd6937b9abd02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="4f353-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="4f353-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="4f353-103">Este elemento habilita o comportamento de ponto de extremidade que torna possível consumir o serviço de páginas da web de ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="4f353-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="4f353-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4f353-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4f353-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="4f353-105">\<behaviors></span></span>  
<span data-ttu-id="4f353-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4f353-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4f353-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="4f353-107">\<behavior></span></span>  
<span data-ttu-id="4f353-108">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="4f353-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f353-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f353-109">Syntax</span></span>  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f353-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4f353-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4f353-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4f353-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f353-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f353-112">Attributes</span></span>  
 <span data-ttu-id="4f353-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4f353-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f353-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4f353-114">Child Elements</span></span>  
 <span data-ttu-id="4f353-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4f353-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f353-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4f353-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4f353-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f353-117">Element</span></span>|<span data-ttu-id="4f353-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f353-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f353-119">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="4f353-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4f353-120">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="4f353-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f353-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f353-121">Remarks</span></span>  
 <span data-ttu-id="4f353-122">Esse comportamento só deve ser usado em conjunto com o o [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação padrão, ou o [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="4f353-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="4f353-123">Para obter mais informações sobre esse comportamento, consulte <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="4f353-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f353-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f353-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [<span data-ttu-id="4f353-125">Integração de AJAX e suporte a JSON</span><span class="sxs-lookup"><span data-stu-id="4f353-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="4f353-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="4f353-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
