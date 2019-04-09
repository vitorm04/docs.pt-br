---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b8864760c1700cd785922b922346204d194f56cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176807"
---
# <a name="clientvia"></a><span data-ttu-id="181aa-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="181aa-101">\<clientVia></span></span>
<span data-ttu-id="181aa-102">Especifica o URI para o qual o canal de transporte deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="181aa-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="181aa-103">Para obter mais informações, consulte <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="181aa-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="181aa-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="181aa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="181aa-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="181aa-105">\<behaviors></span></span>  
<span data-ttu-id="181aa-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="181aa-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="181aa-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="181aa-107">\<behavior></span></span>  
<span data-ttu-id="181aa-108">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="181aa-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="181aa-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="181aa-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="181aa-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="181aa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="181aa-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="181aa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="181aa-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="181aa-112">Attributes</span></span>  
  
|<span data-ttu-id="181aa-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="181aa-113">Attribute</span></span>|<span data-ttu-id="181aa-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="181aa-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="181aa-115">Uma cadeia de caracteres que especifica um URI que indica a rota que uma mensagem deve seguir.</span><span class="sxs-lookup"><span data-stu-id="181aa-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="181aa-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="181aa-116">Child Elements</span></span>  
 <span data-ttu-id="181aa-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="181aa-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="181aa-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="181aa-118">Parent Elements</span></span>  
  
|<span data-ttu-id="181aa-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="181aa-119">Element</span></span>|<span data-ttu-id="181aa-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="181aa-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="181aa-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="181aa-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="181aa-122">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="181aa-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="181aa-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="181aa-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
