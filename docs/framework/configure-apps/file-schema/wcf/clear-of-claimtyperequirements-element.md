---
title: <clear> de <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 35d0391951204bd352918d3004f0cc4f9480b0e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704265"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="674f4-102">\<Limpar > de \<claimTypeRequirements > elemento</span><span class="sxs-lookup"><span data-stu-id="674f4-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="674f4-103">Especifica que todos os tipos de declaração a serem removidos na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="674f4-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="674f4-104">Isso garante que a coleção começa vazia.</span><span class="sxs-lookup"><span data-stu-id="674f4-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="674f4-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="674f4-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="674f4-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="674f4-106">\<bindings></span></span>  
<span data-ttu-id="674f4-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="674f4-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="674f4-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="674f4-108">\<binding></span></span>  
<span data-ttu-id="674f4-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="674f4-109">\<security></span></span>  
<span data-ttu-id="674f4-110">\<message></span><span class="sxs-lookup"><span data-stu-id="674f4-110">\<message></span></span>  
<span data-ttu-id="674f4-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="674f4-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="674f4-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="674f4-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="674f4-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="674f4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="674f4-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="674f4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="674f4-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="674f4-115">Attributes</span></span>  
 <span data-ttu-id="674f4-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="674f4-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="674f4-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="674f4-117">Child Elements</span></span>  
 <span data-ttu-id="674f4-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="674f4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="674f4-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="674f4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="674f4-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="674f4-120">Element</span></span>|<span data-ttu-id="674f4-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="674f4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="674f4-122">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="674f4-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="674f4-123">Especifica uma coleção de tipos de declaração exigidos.</span><span class="sxs-lookup"><span data-stu-id="674f4-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="674f4-124">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="674f4-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="674f4-125">Em um cenário federado, os serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="674f4-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="674f4-126">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="674f4-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="674f4-127">Cada elemento nesta coleção Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="674f4-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="674f4-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="674f4-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
