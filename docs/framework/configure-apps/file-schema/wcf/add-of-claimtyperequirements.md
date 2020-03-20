---
title: <add> de <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153081"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="96143-102">\<adicionar> \<de claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="96143-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="96143-103">Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="96143-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="96143-104">Por exemplo, os serviços estabelecem os requisitos nas credenciais recebidas, que devem possuir um determinado conjunto de tipos de sinistros.</span><span class="sxs-lookup"><span data-stu-id="96143-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="96143-105">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="96143-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="96143-106">&nbsp;&nbsp;[**\<system.serviceModelo>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="96143-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="96143-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<vinculações>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="96143-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="96143-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de vinculação personalizada**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="96143-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="96143-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<vinculação>**</span><span class="sxs-lookup"><span data-stu-id="96143-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="96143-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurança**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="96143-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="96143-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>deparâmetros de token emitidos**](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="96143-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="96143-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span><span class="sxs-lookup"><span data-stu-id="96143-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span></span>\
<span data-ttu-id="96143-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**</span><span class="sxs-lookup"><span data-stu-id="96143-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96143-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96143-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96143-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="96143-115">Attributes and Elements</span></span>  
 <span data-ttu-id="96143-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="96143-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96143-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="96143-117">Attributes</span></span>  
  
|<span data-ttu-id="96143-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="96143-118">Attribute</span></span>|<span data-ttu-id="96143-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="96143-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96143-120">Claimtype</span><span class="sxs-lookup"><span data-stu-id="96143-120">claimType</span></span>|<span data-ttu-id="96143-121">Um URI que define o tipo de uma reclamação.</span><span class="sxs-lookup"><span data-stu-id="96143-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="96143-122">Por exemplo, para comprar um produto de um site, o usuário deve apresentar um cartão de crédito válido com limite de crédito suficiente.</span><span class="sxs-lookup"><span data-stu-id="96143-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="96143-123">O tipo de reclamação seria o uri do cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="96143-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="96143-124">isOptional</span><span class="sxs-lookup"><span data-stu-id="96143-124">isOptional</span></span>|<span data-ttu-id="96143-125">Um valor booleano que especifica se isso é para uma reclamação opcional.</span><span class="sxs-lookup"><span data-stu-id="96143-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="96143-126">Defina este `false` atributo para se esta é uma reivindicação necessária.</span><span class="sxs-lookup"><span data-stu-id="96143-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="96143-127">Você pode usar este atributo quando o serviço pede algumas informações, mas não exige isso.</span><span class="sxs-lookup"><span data-stu-id="96143-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="96143-128">Por exemplo, se você exigir que o usuário digite seu primeiro nome, sobrenome e endereço, mas decida que esse número de telefone é opcional.</span><span class="sxs-lookup"><span data-stu-id="96143-128">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96143-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="96143-129">Child Elements</span></span>  
 <span data-ttu-id="96143-130">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="96143-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96143-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="96143-131">Parent Elements</span></span>  
  
|<span data-ttu-id="96143-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="96143-132">Element</span></span>|<span data-ttu-id="96143-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="96143-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96143-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="96143-134">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="96143-135">Especifica uma coleção de tipos de sinistros necessários.</span><span class="sxs-lookup"><span data-stu-id="96143-135">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="96143-136">Em um cenário federado, os serviços estabelecem os requisitos das credenciais recebidas.</span><span class="sxs-lookup"><span data-stu-id="96143-136">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="96143-137">Por exemplo, as credenciais recebidas devem possuir um certo conjunto de tipos de reclamações.</span><span class="sxs-lookup"><span data-stu-id="96143-137">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="96143-138">Cada elemento desta coleção especifica os tipos de reivindicações necessárias e opcionais que se espera que apareçam em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="96143-138">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96143-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="96143-139">Remarks</span></span>  
 <span data-ttu-id="96143-140">Em um cenário federado, os serviços estabelecem os requisitos das credenciais recebidas.</span><span class="sxs-lookup"><span data-stu-id="96143-140">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="96143-141">Por exemplo, as credenciais recebidas devem possuir um certo conjunto de tipos de reclamações.</span><span class="sxs-lookup"><span data-stu-id="96143-141">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="96143-142">Essa exigência se manifesta em uma política de segurança.</span><span class="sxs-lookup"><span data-stu-id="96143-142">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="96143-143">Quando um cliente solicita credenciais de um serviço federado (por exemplo, CardSpace), ele coloca os requisitos em uma solicitação de token (RequestSecurityToken) para que o serviço federado possa emitir as credenciais que satisfaçam os requisitos em conformidade.</span><span class="sxs-lookup"><span data-stu-id="96143-143">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96143-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96143-144">Example</span></span>  
 <span data-ttu-id="96143-145">A configuração a seguir adiciona dois requisitos de tipo de solicitação a uma vinculação de segurança.</span><span class="sxs-lookup"><span data-stu-id="96143-145">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96143-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="96143-146">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="96143-147">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="96143-147">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="96143-148">Ligações</span><span class="sxs-lookup"><span data-stu-id="96143-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="96143-149">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="96143-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="96143-150">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="96143-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="96143-151">\<>de vinculação personalizada</span><span class="sxs-lookup"><span data-stu-id="96143-151">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="96143-152">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="96143-152">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="96143-153">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="96143-153">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
