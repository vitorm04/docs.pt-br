---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 5e62201a38dc4dc251996531a4af5f294dd2395f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151097"
---
# \<clientVia>

<span data-ttu-id="67657-101">Especifica o URI para o qual o canal de transporte deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="67657-101">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="67657-102">Para obter mais informações, consulte <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="67657-102">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="67657-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="67657-103">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67657-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="67657-104">Attributes and Elements</span></span>  

 <span data-ttu-id="67657-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="67657-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67657-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="67657-106">Attributes</span></span>  
  
|<span data-ttu-id="67657-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="67657-107">Attribute</span></span>|<span data-ttu-id="67657-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="67657-108">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="67657-109">Uma cadeia de caracteres que especifica um URI que indica a rota que deve ser tomada por uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="67657-109">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67657-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="67657-110">Child Elements</span></span>  

 <span data-ttu-id="67657-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="67657-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67657-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="67657-112">Parent Elements</span></span>  
  
|<span data-ttu-id="67657-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="67657-113">Element</span></span>|<span data-ttu-id="67657-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="67657-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="67657-115">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="67657-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67657-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="67657-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
