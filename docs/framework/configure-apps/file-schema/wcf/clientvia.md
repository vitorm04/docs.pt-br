---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b12a882d942555a24c145b243d2cea764ba106b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919501"
---
# <a name="clientvia"></a><span data-ttu-id="dd966-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="dd966-101">\<clientVia></span></span>
<span data-ttu-id="dd966-102">Especifica o URI para o qual o canal de transporte deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="dd966-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="dd966-103">Para obter mais informações, consulte <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="dd966-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="dd966-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dd966-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dd966-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="dd966-105">\<behaviors></span></span>  
<span data-ttu-id="dd966-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="dd966-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="dd966-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="dd966-107">\<behavior></span></span>  
<span data-ttu-id="dd966-108">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="dd966-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd966-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd966-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd966-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dd966-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dd966-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dd966-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd966-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="dd966-112">Attributes</span></span>  
  
|<span data-ttu-id="dd966-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="dd966-113">Attribute</span></span>|<span data-ttu-id="dd966-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd966-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="dd966-115">Uma cadeia de caracteres que especifica um URI que indica a rota que deve ser tomada por uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="dd966-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd966-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dd966-116">Child Elements</span></span>  
 <span data-ttu-id="dd966-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="dd966-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd966-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dd966-118">Parent Elements</span></span>  
  
|<span data-ttu-id="dd966-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd966-119">Element</span></span>|<span data-ttu-id="dd966-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd966-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd966-121">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="dd966-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="dd966-122">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="dd966-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd966-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd966-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
