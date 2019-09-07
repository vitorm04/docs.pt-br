---
title: <add> de <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 53da9dacbd3277bd8b608296a1515e3da7296f1c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398365"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="77aa1-102">\<Adicionar > de \<ClaimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="77aa1-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="77aa1-103">Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="77aa1-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="77aa1-104">Por exemplo, os serviços definem os requisitos de credenciais de entrada, que devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="77aa1-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="77aa1-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="77aa1-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="77aa1-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="77aa1-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="77aa1-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="77aa1-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="77aa1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="77aa1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="77aa1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="77aa1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="77aa1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="77aa1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="77aa1-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> issuedTokenParameters**](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="77aa1-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="77aa1-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> claimTypeRequirements**](claimtyperequirements-element.md)</span><span class="sxs-lookup"><span data-stu-id="77aa1-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span></span>\
<span data-ttu-id="77aa1-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="77aa1-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77aa1-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77aa1-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77aa1-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="77aa1-115">Attributes and Elements</span></span>  
 <span data-ttu-id="77aa1-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="77aa1-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77aa1-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="77aa1-117">Attributes</span></span>  
  
|<span data-ttu-id="77aa1-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="77aa1-118">Attribute</span></span>|<span data-ttu-id="77aa1-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="77aa1-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77aa1-120">claimType</span><span class="sxs-lookup"><span data-stu-id="77aa1-120">claimType</span></span>|<span data-ttu-id="77aa1-121">Um URI que define o tipo de uma declaração.</span><span class="sxs-lookup"><span data-stu-id="77aa1-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="77aa1-122">Por exemplo, para comprar um produto de um site da Web, o usuário deve apresentar um cartão de crédito válido com limite de crédito suficiente.</span><span class="sxs-lookup"><span data-stu-id="77aa1-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="77aa1-123">O tipo de declaração seria o URI do cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="77aa1-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="77aa1-124">isOptional</span><span class="sxs-lookup"><span data-stu-id="77aa1-124">isOptional</span></span>|<span data-ttu-id="77aa1-125">Um valor booliano que especifica se isso é para uma declaração opcional.</span><span class="sxs-lookup"><span data-stu-id="77aa1-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="77aa1-126">Defina esse atributo como `false` se for uma declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="77aa1-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="77aa1-127">Você pode usar esse atributo quando o serviço solicitar algumas informações, mas não precisar dela.</span><span class="sxs-lookup"><span data-stu-id="77aa1-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="77aa1-128">Por exemplo, se você precisar que o usuário insira seu nome, sobrenome e endereço, mas decida que o número de telefone é opcional.</span><span class="sxs-lookup"><span data-stu-id="77aa1-128">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77aa1-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="77aa1-129">Child Elements</span></span>  
 <span data-ttu-id="77aa1-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="77aa1-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="77aa1-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="77aa1-131">Parent Elements</span></span>  
  
|<span data-ttu-id="77aa1-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="77aa1-132">Element</span></span>|<span data-ttu-id="77aa1-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="77aa1-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77aa1-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="77aa1-134">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="77aa1-135">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="77aa1-135">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="77aa1-136">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="77aa1-136">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="77aa1-137">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="77aa1-137">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="77aa1-138">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="77aa1-138">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77aa1-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="77aa1-139">Remarks</span></span>  
 <span data-ttu-id="77aa1-140">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="77aa1-140">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="77aa1-141">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="77aa1-141">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="77aa1-142">Esse requisito é manifestado em uma política de segurança.</span><span class="sxs-lookup"><span data-stu-id="77aa1-142">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="77aa1-143">Quando um cliente solicita credenciais de um serviço federado (por exemplo, CardSpace), ele coloca os requisitos em uma solicitação de token (RequestSecurityToken) para que o serviço federado possa emitir as credenciais que atendem aos requisitos de acordo.</span><span class="sxs-lookup"><span data-stu-id="77aa1-143">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77aa1-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77aa1-144">Example</span></span>  
 <span data-ttu-id="77aa1-145">A configuração a seguir adiciona dois requisitos de tipo de declaração a uma associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="77aa1-145">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="77aa1-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77aa1-146">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="77aa1-147">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="77aa1-147">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="77aa1-148">Associações</span><span class="sxs-lookup"><span data-stu-id="77aa1-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="77aa1-149">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="77aa1-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="77aa1-150">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="77aa1-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="77aa1-151">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="77aa1-151">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="77aa1-152">Como: Criar uma associação personalizada usando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="77aa1-152">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="77aa1-153">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="77aa1-153">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
