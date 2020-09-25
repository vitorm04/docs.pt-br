---
title: <add> de <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 39cb89340907743c727a425bb2f140ac34842e3b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181668"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="d43c6-102">\<add> de \<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="d43c6-102">\<add> of \<authorizationPolicies></span></span>

<span data-ttu-id="d43c6-103">Especifica uma política de autorização para transformação de declaração.</span><span class="sxs-lookup"><span data-stu-id="d43c6-103">Specifies an authorization policy for claim transformation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="d43c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d43c6-104">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="d43c6-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="d43c6-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d43c6-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d43c6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d43c6-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d43c6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d43c6-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="d43c6-108">Attributes</span></span>  
  
|<span data-ttu-id="d43c6-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="d43c6-109">Attribute</span></span>|<span data-ttu-id="d43c6-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d43c6-110">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="d43c6-111">Um atributo de cadeia de caracteres necessário.</span><span class="sxs-lookup"><span data-stu-id="d43c6-111">A required String attribute.</span></span><br /><br /> <span data-ttu-id="d43c6-112">O modelo de controle de acesso do Windows Communication Foundation (WCF) dá suporte ao provisionamento de um conjunto de políticas de autorização como tipos.</span><span class="sxs-lookup"><span data-stu-id="d43c6-112">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="d43c6-113">Esse atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="d43c6-113">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="d43c6-114">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="d43c6-114">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d43c6-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d43c6-115">Child Elements</span></span>  

 <span data-ttu-id="d43c6-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d43c6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d43c6-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d43c6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d43c6-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="d43c6-118">Element</span></span>|<span data-ttu-id="d43c6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d43c6-119">Description</span></span>|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|<span data-ttu-id="d43c6-120">Especifica uma coleção de tipos de política de autorização.</span><span class="sxs-lookup"><span data-stu-id="d43c6-120">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d43c6-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="d43c6-121">Remarks</span></span>  

 <span data-ttu-id="d43c6-122">Cada política de autorização contém um único `policyType` atributo necessário que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d43c6-122">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="d43c6-123">O atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="d43c6-123">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="d43c6-124">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="d43c6-124">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="d43c6-125">Para obter mais informações sobre como funciona uma diretiva de autorização, consulte <xref:System.IdentityModel.Policy.IAuthorizationPolicy> e [política de autorização](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="d43c6-125">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d43c6-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="d43c6-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="d43c6-127">Autorizando o acesso às operações de serviço</span><span class="sxs-lookup"><span data-stu-id="d43c6-127">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="d43c6-128">Como: criar gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="d43c6-128">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="d43c6-129">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="d43c6-129">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
