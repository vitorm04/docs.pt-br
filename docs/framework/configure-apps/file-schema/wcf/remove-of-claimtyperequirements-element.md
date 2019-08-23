---
title: <remove>do <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 7238c253bfbc3224c8bbd31265e197dd35e56514
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934233"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="d0cd3-102">\<Remover > do \<elemento de > ClaimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="d0cd3-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="d0cd3-103">Especifica os tipos de declarações a serem removidas na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="d0cd3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0cd3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0cd3-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d0cd3-105">\<bindings></span></span>  
<span data-ttu-id="d0cd3-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="d0cd3-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d0cd3-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="d0cd3-107">\<binding></span></span>  
<span data-ttu-id="d0cd3-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="d0cd3-108">\<security></span></span>  
<span data-ttu-id="d0cd3-109">\<message></span><span class="sxs-lookup"><span data-stu-id="d0cd3-109">\<message></span></span>  
<span data-ttu-id="d0cd3-110">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d0cd3-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0cd3-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0cd3-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0cd3-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d0cd3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d0cd3-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0cd3-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="d0cd3-114">Attributes</span></span>  
  
|<span data-ttu-id="d0cd3-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="d0cd3-115">Attribute</span></span>|<span data-ttu-id="d0cd3-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0cd3-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0cd3-117">claimType</span><span class="sxs-lookup"><span data-stu-id="d0cd3-117">claimType</span></span>|<span data-ttu-id="d0cd3-118">Um URI que define o tipo de uma declaração a ser removida.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0cd3-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d0cd3-119">Child Elements</span></span>  
 <span data-ttu-id="d0cd3-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0cd3-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d0cd3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d0cd3-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0cd3-122">Element</span></span>|<span data-ttu-id="d0cd3-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0cd3-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0cd3-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d0cd3-124">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="d0cd3-125">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="d0cd3-126">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="d0cd3-127">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d0cd3-128">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d0cd3-129">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0cd3-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0cd3-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
