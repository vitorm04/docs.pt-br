---
title: '&lt;adicionar&gt; &lt;authorizationPolicies&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72af0529cea2e6810bdb7a518874a313e3ceab40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="5e643-102">&lt;adicionar&gt; &lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="5e643-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="5e643-103">Especifica uma política de autorização para transformação de declaração.</span><span class="sxs-lookup"><span data-stu-id="5e643-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="5e643-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5e643-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e643-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="5e643-105">\<behaviors></span></span>  
<span data-ttu-id="5e643-106">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="5e643-106">\<behavior></span></span>  
<span data-ttu-id="5e643-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="5e643-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="5e643-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="5e643-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="5e643-109">\<add></span><span class="sxs-lookup"><span data-stu-id="5e643-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e643-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e643-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="5e643-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="5e643-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e643-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5e643-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5e643-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5e643-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e643-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e643-114">Attributes</span></span>  
  
|<span data-ttu-id="5e643-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="5e643-115">Attribute</span></span>|<span data-ttu-id="5e643-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e643-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="5e643-117">Um atributo de cadeia de caracteres necessário.</span><span class="sxs-lookup"><span data-stu-id="5e643-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="5e643-118">O [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] modelo de controle de acesso oferece suporte a um conjunto de políticas de autorização como tipos de provisionamento.</span><span class="sxs-lookup"><span data-stu-id="5e643-118">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="5e643-119">Esse atributo especifica uma política de autorização, que permite que a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="5e643-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="5e643-120">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="5e643-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e643-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5e643-121">Child Elements</span></span>  
 <span data-ttu-id="5e643-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5e643-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e643-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e643-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5e643-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e643-124">Element</span></span>|<span data-ttu-id="5e643-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e643-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e643-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="5e643-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="5e643-127">Especifica uma coleção de tipos de política de autorização.</span><span class="sxs-lookup"><span data-stu-id="5e643-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e643-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e643-128">Remarks</span></span>  
 <span data-ttu-id="5e643-129">Cada política de autorização contém um único necessário `policyType` atributo que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5e643-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="5e643-130">O atributo especifica uma política de autorização, que permite que a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="5e643-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="5e643-131">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="5e643-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="5e643-132">Para obter mais informações sobre como funciona a uma política de autorização, consulte <xref:System.IdentityModel.Policy.IAuthorizationPolicy> e [política de autorização](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="5e643-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e643-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e643-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="5e643-134">Autorizando o acesso a operações de serviço</span><span class="sxs-lookup"><span data-stu-id="5e643-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="5e643-135">Como criar um gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="5e643-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="5e643-136">\<add></span><span class="sxs-lookup"><span data-stu-id="5e643-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="5e643-137">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="5e643-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
