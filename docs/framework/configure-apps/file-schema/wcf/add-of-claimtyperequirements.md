---
title: <add> de <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 00699a6fa5d0de7ac554db6ef8d0bbe511a85c0a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149212"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="ec076-102">\<add> de \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="ec076-102">\<add> of \<claimTypeRequirements></span></span>

<span data-ttu-id="ec076-103">Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="ec076-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="ec076-104">Por exemplo, os serviços definem os requisitos de credenciais de entrada, que devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="ec076-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ec076-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ec076-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec076-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ec076-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ec076-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ec076-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec076-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="ec076-108">Attributes</span></span>  
  
|<span data-ttu-id="ec076-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="ec076-109">Attribute</span></span>|<span data-ttu-id="ec076-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec076-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec076-111">claimType</span><span class="sxs-lookup"><span data-stu-id="ec076-111">claimType</span></span>|<span data-ttu-id="ec076-112">Um URI que define o tipo de uma declaração.</span><span class="sxs-lookup"><span data-stu-id="ec076-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="ec076-113">Por exemplo, para comprar um produto de um site da Web, o usuário deve apresentar um cartão de crédito válido com limite de crédito suficiente.</span><span class="sxs-lookup"><span data-stu-id="ec076-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="ec076-114">O tipo de declaração seria o URI do cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="ec076-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="ec076-115">isOptional</span><span class="sxs-lookup"><span data-stu-id="ec076-115">isOptional</span></span>|<span data-ttu-id="ec076-116">Um valor booliano que especifica se isso é para uma declaração opcional.</span><span class="sxs-lookup"><span data-stu-id="ec076-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="ec076-117">Defina esse atributo como `false` se for uma declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="ec076-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="ec076-118">Você pode usar esse atributo quando o serviço solicitar algumas informações, mas não precisar dela.</span><span class="sxs-lookup"><span data-stu-id="ec076-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="ec076-119">Por exemplo, se você precisar que o usuário insira seu nome, sobrenome e endereço, mas decida que o número de telefone é opcional.</span><span class="sxs-lookup"><span data-stu-id="ec076-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec076-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ec076-120">Child Elements</span></span>  

 <span data-ttu-id="ec076-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ec076-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec076-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ec076-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ec076-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec076-123">Element</span></span>|<span data-ttu-id="ec076-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec076-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="ec076-125">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="ec076-125">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="ec076-126">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="ec076-126">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="ec076-127">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="ec076-127">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="ec076-128">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="ec076-128">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec076-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec076-129">Remarks</span></span>  

 <span data-ttu-id="ec076-130">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="ec076-130">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="ec076-131">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="ec076-131">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="ec076-132">Esse requisito é manifestado em uma política de segurança.</span><span class="sxs-lookup"><span data-stu-id="ec076-132">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="ec076-133">Quando um cliente solicita credenciais de um serviço federado (por exemplo, CardSpace), ele coloca os requisitos em uma solicitação de token (RequestSecurityToken) para que o serviço federado possa emitir as credenciais que atendem aos requisitos de acordo.</span><span class="sxs-lookup"><span data-stu-id="ec076-133">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec076-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec076-134">Example</span></span>  

 <span data-ttu-id="ec076-135">A configuração a seguir adiciona dois requisitos de tipo de declaração a uma associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="ec076-135">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="ec076-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec076-136">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<claimTypeRequirements>](claimtyperequirements-element.md)
- [<span data-ttu-id="ec076-137">Associações</span><span class="sxs-lookup"><span data-stu-id="ec076-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ec076-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="ec076-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ec076-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="ec076-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="ec076-140">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ec076-140">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="ec076-141">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="ec076-141">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
