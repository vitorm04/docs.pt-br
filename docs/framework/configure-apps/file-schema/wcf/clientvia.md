---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: a1c2ee68fb039e24e1462148cb52daf1bb57f8ed
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398105"
---
# <a name="clientvia"></a><span data-ttu-id="b7f61-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="b7f61-101">\<clientVia></span></span>
<span data-ttu-id="b7f61-102">Especifica o URI para o qual o canal de transporte deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="b7f61-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="b7f61-103">Para obter mais informações, consulte <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="b7f61-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
<span data-ttu-id="b7f61-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b7f61-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b7f61-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b7f61-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b7f61-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b7f61-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="b7f61-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b7f61-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="b7f61-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b7f61-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="b7f61-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> clientVia**</span><span class="sxs-lookup"><span data-stu-id="b7f61-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7f61-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7f61-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7f61-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7f61-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b7f61-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7f61-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7f61-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7f61-113">Attributes</span></span>  
  
|<span data-ttu-id="b7f61-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="b7f61-114">Attribute</span></span>|<span data-ttu-id="b7f61-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7f61-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="b7f61-116">Uma cadeia de caracteres que especifica um URI que indica a rota que deve ser tomada por uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="b7f61-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7f61-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7f61-117">Child Elements</span></span>  
 <span data-ttu-id="b7f61-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b7f61-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7f61-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7f61-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b7f61-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7f61-120">Element</span></span>|<span data-ttu-id="b7f61-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7f61-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7f61-122">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="b7f61-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b7f61-123">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7f61-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7f61-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7f61-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
