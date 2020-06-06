---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400382"
---
# \<enableWebScript>
<span data-ttu-id="12966-101">Esse elemento habilita o comportamento do ponto de extremidade que torna possível consumir o serviço de páginas da Web do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="12966-101">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="12966-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12966-102">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12966-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="12966-103">Attributes and Elements</span></span>  
 <span data-ttu-id="12966-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="12966-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12966-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="12966-105">Attributes</span></span>  
 <span data-ttu-id="12966-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="12966-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="12966-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="12966-107">Child Elements</span></span>  
 <span data-ttu-id="12966-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="12966-108">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12966-109">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="12966-109">Parent Elements</span></span>  
  
|<span data-ttu-id="12966-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="12966-110">Element</span></span>|<span data-ttu-id="12966-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="12966-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="12966-112">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="12966-112">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12966-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="12966-113">Remarks</span></span>  
 <span data-ttu-id="12966-114">Esse comportamento só deve ser usado em conjunto com a [\<webHttpBinding>](webhttpbinding.md) associação padrão ou com o [\<webMessageEncoding>](webmessageencoding.md) elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="12966-114">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="12966-115">Para obter mais informações sobre esse comportamento, consulte <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> .</span><span class="sxs-lookup"><span data-stu-id="12966-115">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12966-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="12966-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="12966-117">Integração AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="12966-117">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
