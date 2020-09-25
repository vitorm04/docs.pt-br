---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 11378e6cc8cbe8e631fd77ab74c91a616099df52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190079"
---
# \<enableWebScript>

<span data-ttu-id="fdc05-101">Esse elemento habilita o comportamento do ponto de extremidade que torna possível consumir o serviço de páginas da Web do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="fdc05-101">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="fdc05-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdc05-102">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdc05-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fdc05-103">Attributes and Elements</span></span>  

 <span data-ttu-id="fdc05-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fdc05-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdc05-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="fdc05-105">Attributes</span></span>  

 <span data-ttu-id="fdc05-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fdc05-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fdc05-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fdc05-107">Child Elements</span></span>  

 <span data-ttu-id="fdc05-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fdc05-108">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fdc05-109">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fdc05-109">Parent Elements</span></span>  
  
|<span data-ttu-id="fdc05-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="fdc05-110">Element</span></span>|<span data-ttu-id="fdc05-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdc05-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="fdc05-112">Especifica o conjunto de comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fdc05-112">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdc05-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="fdc05-113">Remarks</span></span>  

 <span data-ttu-id="fdc05-114">Esse comportamento só deve ser usado em conjunto com a [\<webHttpBinding>](webhttpbinding.md) associação padrão ou com o [\<webMessageEncoding>](webmessageencoding.md) elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="fdc05-114">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="fdc05-115">Para obter mais informações sobre esse comportamento, consulte <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> .</span><span class="sxs-lookup"><span data-stu-id="fdc05-115">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc05-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="fdc05-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="fdc05-117">Integração de AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="fdc05-117">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
