---
title: '&lt;remover&gt; o elemento &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 5d1f9c963792336f0938113beefbdef770831e9d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753232"
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="cbcdc-102">&lt;remover&gt; o elemento &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="cbcdc-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="cbcdc-103">Especifica os tipos de declarações a serem removidas na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="cbcdc-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="cbcdc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cbcdc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cbcdc-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="cbcdc-105">\<bindings></span></span>  
<span data-ttu-id="cbcdc-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="cbcdc-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="cbcdc-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="cbcdc-107">\<binding></span></span>  
<span data-ttu-id="cbcdc-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="cbcdc-108">\<security></span></span>  
<span data-ttu-id="cbcdc-109">\<message></span><span class="sxs-lookup"><span data-stu-id="cbcdc-109">\<message></span></span>  
<span data-ttu-id="cbcdc-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="cbcdc-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbcdc-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbcdc-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <remove claimType="URI" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbcdc-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cbcdc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cbcdc-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cbcdc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbcdc-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="cbcdc-114">Attributes</span></span>  
  
|<span data-ttu-id="cbcdc-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="cbcdc-115">Attribute</span></span>|<span data-ttu-id="cbcdc-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbcdc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbcdc-117">claimType</span><span class="sxs-lookup"><span data-stu-id="cbcdc-117">claimType</span></span>|<span data-ttu-id="cbcdc-118">Um URI que define o tipo de declaração a ser removido.</span><span class="sxs-lookup"><span data-stu-id="cbcdc-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbcdc-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cbcdc-119">Child Elements</span></span>  
 <span data-ttu-id="cbcdc-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cbcdc-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbcdc-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cbcdc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="cbcdc-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="cbcdc-122">Element</span></span>|<span data-ttu-id="cbcdc-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbcdc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbcdc-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="cbcdc-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="cbcdc-125">Especifica uma coleção de tipos de declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="cbcdc-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="cbcdc-126">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="cbcdc-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="cbcdc-127">Em um cenário federado, serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="cbcdc-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="cbcdc-128">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="cbcdc-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="cbcdc-129">Cada elemento na coleção Especifica os tipos de declarações obrigatórias e opcionais que deve aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="cbcdc-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbcdc-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbcdc-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
