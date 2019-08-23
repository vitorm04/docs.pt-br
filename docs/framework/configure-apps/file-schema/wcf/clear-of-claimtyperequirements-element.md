---
title: <clear>do <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: e7e3bebd85decbaa4d216743f9bea9e135b87995
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926128"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="f5493-102">\<limpar > do \<elemento de > ClaimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="f5493-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="f5493-103">Especifica que todos os tipos de declaração sejam removidos na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="f5493-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="f5493-104">Isso garante que a coleção comece vazia.</span><span class="sxs-lookup"><span data-stu-id="f5493-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="f5493-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f5493-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f5493-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f5493-106">\<bindings></span></span>  
<span data-ttu-id="f5493-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="f5493-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="f5493-108">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="f5493-108">\<binding></span></span>  
<span data-ttu-id="f5493-109">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="f5493-109">\<security></span></span>  
<span data-ttu-id="f5493-110">\<message></span><span class="sxs-lookup"><span data-stu-id="f5493-110">\<message></span></span>  
<span data-ttu-id="f5493-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="f5493-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5493-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5493-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5493-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f5493-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f5493-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f5493-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5493-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="f5493-115">Attributes</span></span>  
 <span data-ttu-id="f5493-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f5493-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f5493-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f5493-117">Child Elements</span></span>  
 <span data-ttu-id="f5493-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f5493-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5493-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f5493-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f5493-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="f5493-120">Element</span></span>|<span data-ttu-id="f5493-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5493-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5493-122">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="f5493-122">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="f5493-123">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="f5493-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="f5493-124">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="f5493-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="f5493-125">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="f5493-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="f5493-126">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="f5493-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="f5493-127">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="f5493-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5493-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5493-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
