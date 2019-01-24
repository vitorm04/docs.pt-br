---
title: '&lt;remover&gt; o elemento &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 33c6b935bb8d39f05e26646d4731ce1459beba81
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702139"
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="80ce1-102">&lt;remover&gt; o elemento &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="80ce1-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="80ce1-103">Especifica os tipos de declarações a serem removidas na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="80ce1-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="80ce1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="80ce1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80ce1-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="80ce1-105">\<bindings></span></span>  
<span data-ttu-id="80ce1-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="80ce1-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="80ce1-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="80ce1-107">\<binding></span></span>  
<span data-ttu-id="80ce1-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="80ce1-108">\<security></span></span>  
<span data-ttu-id="80ce1-109">\<message></span><span class="sxs-lookup"><span data-stu-id="80ce1-109">\<message></span></span>  
<span data-ttu-id="80ce1-110">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="80ce1-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ce1-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80ce1-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80ce1-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="80ce1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="80ce1-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="80ce1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80ce1-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="80ce1-114">Attributes</span></span>  
  
|<span data-ttu-id="80ce1-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="80ce1-115">Attribute</span></span>|<span data-ttu-id="80ce1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="80ce1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80ce1-117">claimType</span><span class="sxs-lookup"><span data-stu-id="80ce1-117">claimType</span></span>|<span data-ttu-id="80ce1-118">Um URI que define o tipo de declaração a ser removido.</span><span class="sxs-lookup"><span data-stu-id="80ce1-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80ce1-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="80ce1-119">Child Elements</span></span>  
 <span data-ttu-id="80ce1-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="80ce1-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80ce1-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="80ce1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="80ce1-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="80ce1-122">Element</span></span>|<span data-ttu-id="80ce1-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="80ce1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80ce1-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="80ce1-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="80ce1-125">Especifica uma coleção de tipos de declaração exigidos.</span><span class="sxs-lookup"><span data-stu-id="80ce1-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="80ce1-126">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="80ce1-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="80ce1-127">Em um cenário federado, os serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="80ce1-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="80ce1-128">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="80ce1-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="80ce1-129">Cada elemento nesta coleção Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="80ce1-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80ce1-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80ce1-130">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
