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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d835d96c89e8b292fc2c038794aa4056fda3a095
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="30544-102">&lt;adicionar&gt; &lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="30544-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="30544-103">Especifica uma política de autorização para transformação de declaração.</span><span class="sxs-lookup"><span data-stu-id="30544-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="30544-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="30544-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="30544-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="30544-105">\<behaviors></span></span>  
<span data-ttu-id="30544-106">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="30544-106">\<behavior></span></span>  
<span data-ttu-id="30544-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="30544-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="30544-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="30544-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="30544-109">\<add></span><span class="sxs-lookup"><span data-stu-id="30544-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30544-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30544-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="30544-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="30544-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30544-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="30544-112">Attributes and Elements</span></span>  
 <span data-ttu-id="30544-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="30544-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30544-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="30544-114">Attributes</span></span>  
  
|<span data-ttu-id="30544-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="30544-115">Attribute</span></span>|<span data-ttu-id="30544-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="30544-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="30544-117">Um atributo de cadeia de caracteres necessário.</span><span class="sxs-lookup"><span data-stu-id="30544-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="30544-118">O [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] modelo de controle de acesso oferece suporte a um conjunto de políticas de autorização como tipos de provisionamento.</span><span class="sxs-lookup"><span data-stu-id="30544-118">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="30544-119">Esse atributo especifica uma política de autorização, que permite que a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="30544-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="30544-120">Controle de acesso pode ser concedido ou negado com base no que.</span><span class="sxs-lookup"><span data-stu-id="30544-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30544-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="30544-121">Child Elements</span></span>  
 <span data-ttu-id="30544-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="30544-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30544-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="30544-123">Parent Elements</span></span>  
  
|<span data-ttu-id="30544-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="30544-124">Element</span></span>|<span data-ttu-id="30544-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="30544-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30544-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="30544-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="30544-127">Especifica uma coleção de tipos de política de autorização.</span><span class="sxs-lookup"><span data-stu-id="30544-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30544-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="30544-128">Remarks</span></span>  
 <span data-ttu-id="30544-129">Cada política de autorização contém um único necessário `policyType` atributo que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="30544-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="30544-130">O atributo especifica uma política de autorização, que permite que a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="30544-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="30544-131">Controle de acesso pode ser concedido ou negado com base no que.</span><span class="sxs-lookup"><span data-stu-id="30544-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="30544-132">Para obter mais informações sobre como funciona a uma política de autorização, consulte <xref:System.IdentityModel.Policy.IAuthorizationPolicy> e [política de autorização](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="30544-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30544-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30544-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="30544-134">Autorizando o acesso a operações de serviço</span><span class="sxs-lookup"><span data-stu-id="30544-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="30544-135">Como: criar um Gerenciador de autorização personalizada para um serviço</span><span class="sxs-lookup"><span data-stu-id="30544-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="30544-136">\<add></span><span class="sxs-lookup"><span data-stu-id="30544-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="30544-137">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="30544-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
