---
title: <add> de <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: e2597bc51e788c919bfe3ce3422ae2911cc6b33b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400694"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="6f788-102">\<Adicionar > de \<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="6f788-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="6f788-103">Especifica uma política de autorização para transformação de declaração.</span><span class="sxs-lookup"><span data-stu-id="6f788-103">Specifies an authorization policy for claim transformation.</span></span>  
  
<span data-ttu-id="6f788-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6f788-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6f788-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6f788-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6f788-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6f788-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="6f788-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6f788-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="6f788-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6f788-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="6f788-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de autorização**](serviceauthorization-element.md)</span><span class="sxs-lookup"><span data-stu-id="6f788-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)</span></span>\
<span data-ttu-id="6f788-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> authorizationPolicies**](authorizationpolicies.md)</span><span class="sxs-lookup"><span data-stu-id="6f788-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)</span></span>\
<span data-ttu-id="6f788-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="6f788-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f788-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f788-112">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="6f788-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="6f788-113">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f788-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6f788-114">Attributes and Elements</span></span>  
 <span data-ttu-id="6f788-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6f788-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f788-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="6f788-116">Attributes</span></span>  
  
|<span data-ttu-id="6f788-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="6f788-117">Attribute</span></span>|<span data-ttu-id="6f788-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f788-118">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="6f788-119">Um atributo de cadeia de caracteres necessário.</span><span class="sxs-lookup"><span data-stu-id="6f788-119">A required String attribute.</span></span><br /><br /> <span data-ttu-id="6f788-120">O modelo de controle de acesso do Windows Communication Foundation (WCF) dá suporte ao provisionamento de um conjunto de políticas de autorização como tipos.</span><span class="sxs-lookup"><span data-stu-id="6f788-120">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="6f788-121">Esse atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="6f788-121">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="6f788-122">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="6f788-122">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f788-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6f788-123">Child Elements</span></span>  
 <span data-ttu-id="6f788-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6f788-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f788-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6f788-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6f788-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="6f788-126">Element</span></span>|<span data-ttu-id="6f788-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f788-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f788-128">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="6f788-128">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="6f788-129">Especifica uma coleção de tipos de política de autorização.</span><span class="sxs-lookup"><span data-stu-id="6f788-129">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f788-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f788-130">Remarks</span></span>  
 <span data-ttu-id="6f788-131">Cada política de autorização contém um único `policyType` atributo necessário que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6f788-131">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="6f788-132">O atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="6f788-132">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="6f788-133">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="6f788-133">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="6f788-134">Para obter mais informações sobre como funciona uma diretiva de autorização <xref:System.IdentityModel.Policy.IAuthorizationPolicy> , consulte e [política de autorização](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="6f788-134">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f788-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f788-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="6f788-136">Autorizando o acesso a operações de serviço</span><span class="sxs-lookup"><span data-stu-id="6f788-136">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="6f788-137">Como: Criar um Gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="6f788-137">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="6f788-138">\<add></span><span class="sxs-lookup"><span data-stu-id="6f788-138">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="6f788-139">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="6f788-139">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
