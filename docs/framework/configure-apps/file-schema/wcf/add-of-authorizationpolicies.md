---
title: <add> de <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 65398c5afa9750f215c95899bb6004cae671123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920269"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="fe664-102">\<Adicionar > de \<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="fe664-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="fe664-103">Especifica uma política de autorização para transformação de declaração.</span><span class="sxs-lookup"><span data-stu-id="fe664-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="fe664-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fe664-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fe664-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="fe664-105">\<behaviors></span></span>  
<span data-ttu-id="fe664-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="fe664-106">\<behavior></span></span>  
<span data-ttu-id="fe664-107">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="fe664-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="fe664-108">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="fe664-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="fe664-109">\<add></span><span class="sxs-lookup"><span data-stu-id="fe664-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe664-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe664-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="fe664-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="fe664-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe664-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fe664-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fe664-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fe664-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe664-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="fe664-114">Attributes</span></span>  
  
|<span data-ttu-id="fe664-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="fe664-115">Attribute</span></span>|<span data-ttu-id="fe664-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe664-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="fe664-117">Um atributo de cadeia de caracteres necessário.</span><span class="sxs-lookup"><span data-stu-id="fe664-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="fe664-118">O modelo de controle de acesso do Windows Communication Foundation (WCF) dá suporte ao provisionamento de um conjunto de políticas de autorização como tipos.</span><span class="sxs-lookup"><span data-stu-id="fe664-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="fe664-119">Esse atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="fe664-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="fe664-120">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="fe664-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe664-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fe664-121">Child Elements</span></span>  
 <span data-ttu-id="fe664-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fe664-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe664-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fe664-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fe664-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="fe664-124">Element</span></span>|<span data-ttu-id="fe664-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe664-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe664-126">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="fe664-126">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="fe664-127">Especifica uma coleção de tipos de política de autorização.</span><span class="sxs-lookup"><span data-stu-id="fe664-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe664-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe664-128">Remarks</span></span>  
 <span data-ttu-id="fe664-129">Cada política de autorização contém um único `policyType` atributo necessário que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fe664-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="fe664-130">O atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="fe664-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="fe664-131">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="fe664-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="fe664-132">Para obter mais informações sobre como funciona uma diretiva de autorização <xref:System.IdentityModel.Policy.IAuthorizationPolicy> , consulte e [política de autorização](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="fe664-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe664-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe664-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="fe664-134">Autorizando o acesso a operações de serviço</span><span class="sxs-lookup"><span data-stu-id="fe664-134">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="fe664-135">Como: Criar um Gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="fe664-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="fe664-136">\<add></span><span class="sxs-lookup"><span data-stu-id="fe664-136">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="fe664-137">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="fe664-137">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
