---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 123f58ee3d77bf605db21fa0d9537b3196d56468
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919109"
---
# <a name="enablewebscript"></a><span data-ttu-id="c9c15-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="c9c15-101">\<enableWebScript></span></span>
<span data-ttu-id="c9c15-102">Esse elemento habilita o comportamento do ponto de extremidade que torna possível consumir o serviço de páginas da Web do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="c9c15-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="c9c15-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c9c15-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c9c15-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="c9c15-104">\<behaviors></span></span>  
<span data-ttu-id="c9c15-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c9c15-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="c9c15-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="c9c15-106">\<behavior></span></span>  
<span data-ttu-id="c9c15-107">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="c9c15-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9c15-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9c15-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9c15-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c9c15-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c9c15-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c9c15-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9c15-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c9c15-111">Attributes</span></span>  
 <span data-ttu-id="c9c15-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c9c15-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c9c15-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c9c15-113">Child Elements</span></span>  
 <span data-ttu-id="c9c15-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c9c15-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9c15-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c9c15-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c9c15-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9c15-116">Element</span></span>|<span data-ttu-id="c9c15-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9c15-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9c15-118">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="c9c15-118">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c9c15-119">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c9c15-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9c15-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9c15-120">Remarks</span></span>  
 <span data-ttu-id="c9c15-121">Esse comportamento só deve ser usado em conjunto com a associação [ \<](webhttpbinding.md) de WebHttpBinding > padrão ou com o elemento de associação de [ \<> webMessageEncoding](webmessageencoding.md) .</span><span class="sxs-lookup"><span data-stu-id="c9c15-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="c9c15-122">Para obter mais informações sobre esse comportamento, <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>consulte.</span><span class="sxs-lookup"><span data-stu-id="c9c15-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c15-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9c15-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="c9c15-124">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="c9c15-124">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="c9c15-125">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="c9c15-125">\<webHttp></span></span>](webhttp.md)
