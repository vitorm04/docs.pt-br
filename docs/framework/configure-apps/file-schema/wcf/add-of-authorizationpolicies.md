---
title: '&lt;adicionar&gt; &lt;authorizationPolicies&gt;'
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: c283f99bedc16352ffca4c41c3d4628271200695
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577497"
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="863ae-102">&lt;adicionar&gt; &lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="863ae-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="863ae-103">Especifica uma política de autorização para transformação de declaração.</span><span class="sxs-lookup"><span data-stu-id="863ae-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="863ae-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="863ae-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="863ae-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="863ae-105">\<behaviors></span></span>  
<span data-ttu-id="863ae-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="863ae-106">\<behavior></span></span>  
<span data-ttu-id="863ae-107">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="863ae-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="863ae-108">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="863ae-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="863ae-109">\<add></span><span class="sxs-lookup"><span data-stu-id="863ae-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="863ae-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="863ae-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="863ae-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="863ae-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="863ae-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="863ae-112">Attributes and Elements</span></span>  
 <span data-ttu-id="863ae-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="863ae-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="863ae-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="863ae-114">Attributes</span></span>  
  
|<span data-ttu-id="863ae-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="863ae-115">Attribute</span></span>|<span data-ttu-id="863ae-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="863ae-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="863ae-117">Um atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="863ae-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="863ae-118">O modelo de controle de acesso do Windows Communication Foundation (WCF) oferece suporte a um conjunto de políticas de autorização como tipos de provisionamento.</span><span class="sxs-lookup"><span data-stu-id="863ae-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="863ae-119">Esse atributo especifica uma política de autorização, que possibilita a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="863ae-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="863ae-120">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="863ae-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="863ae-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="863ae-121">Child Elements</span></span>  
 <span data-ttu-id="863ae-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="863ae-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="863ae-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="863ae-123">Parent Elements</span></span>  
  
|<span data-ttu-id="863ae-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="863ae-124">Element</span></span>|<span data-ttu-id="863ae-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="863ae-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="863ae-126">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="863ae-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="863ae-127">Especifica uma coleção de tipos de política de autorização.</span><span class="sxs-lookup"><span data-stu-id="863ae-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="863ae-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="863ae-128">Remarks</span></span>  
 <span data-ttu-id="863ae-129">Cada política de autorização contém um único necessário `policyType` atributo que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="863ae-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="863ae-130">O atributo especifica uma política de autorização, que possibilita a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="863ae-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="863ae-131">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="863ae-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="863ae-132">Para obter mais informações sobre como funciona uma política de autorização, consulte <xref:System.IdentityModel.Policy.IAuthorizationPolicy> e [política de autorização](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="863ae-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="863ae-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="863ae-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="863ae-134">Autorizando o acesso a operações de serviço</span><span class="sxs-lookup"><span data-stu-id="863ae-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="863ae-135">Como: Criar um Gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="863ae-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="863ae-136">\<add></span><span class="sxs-lookup"><span data-stu-id="863ae-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [<span data-ttu-id="863ae-137">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="863ae-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
