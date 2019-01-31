---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 9c9bbb9ccc7879510ae3e2bee2fabd604fd52f65
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266644"
---
# <a name="enablewebscript"></a><span data-ttu-id="6f28a-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="6f28a-101">\<enableWebScript></span></span>
<span data-ttu-id="6f28a-102">Esse elemento permite que o comportamento de ponto de extremidade que torna possível consumir o serviço de páginas da web de ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="6f28a-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="6f28a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6f28a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6f28a-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="6f28a-104">\<behaviors></span></span>  
<span data-ttu-id="6f28a-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="6f28a-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="6f28a-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="6f28a-106">\<behavior></span></span>  
<span data-ttu-id="6f28a-107">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="6f28a-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f28a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f28a-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f28a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6f28a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6f28a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6f28a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f28a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="6f28a-111">Attributes</span></span>  
 <span data-ttu-id="6f28a-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6f28a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f28a-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6f28a-113">Child Elements</span></span>  
 <span data-ttu-id="6f28a-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6f28a-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f28a-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6f28a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6f28a-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="6f28a-116">Element</span></span>|<span data-ttu-id="6f28a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f28a-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f28a-118">\<behavior></span><span class="sxs-lookup"><span data-stu-id="6f28a-118">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="6f28a-119">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6f28a-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f28a-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f28a-120">Remarks</span></span>  
 <span data-ttu-id="6f28a-121">Esse comportamento só deve ser usado em conjunto com qualquer um de [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação padrão, ou o [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="6f28a-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="6f28a-122">Para obter mais informações sobre esse comportamento, consulte <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="6f28a-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f28a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f28a-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="6f28a-124">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="6f28a-124">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="6f28a-125">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="6f28a-125">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
