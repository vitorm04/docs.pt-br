---
title: <add> de <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 97d3ecca369aeffb7b2e8464f385eeae13bd470f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168838"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="9e30b-102">\<Adicionar > de \<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="9e30b-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="9e30b-103">Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="9e30b-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="9e30b-104">Por exemplo, serviços de estado os requisitos de credenciais de entrada, que devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="9e30b-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="9e30b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9e30b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9e30b-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9e30b-106">\<bindings></span></span>  
<span data-ttu-id="9e30b-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9e30b-107">\<customBinding></span></span>  
<span data-ttu-id="9e30b-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="9e30b-108">\<binding></span></span>  
<span data-ttu-id="9e30b-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="9e30b-109">\<security></span></span>  
<span data-ttu-id="9e30b-110">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="9e30b-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="9e30b-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="9e30b-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e30b-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e30b-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e30b-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9e30b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9e30b-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9e30b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e30b-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="9e30b-115">Attributes</span></span>  
  
|<span data-ttu-id="9e30b-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="9e30b-116">Attribute</span></span>|<span data-ttu-id="9e30b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e30b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e30b-118">claimType</span><span class="sxs-lookup"><span data-stu-id="9e30b-118">claimType</span></span>|<span data-ttu-id="9e30b-119">Um URI que define o tipo de declaração.</span><span class="sxs-lookup"><span data-stu-id="9e30b-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="9e30b-120">Por exemplo, para adquirir um produto de um site, o usuário deve apresentar um cartão de crédito válido com limite de crédito suficiente.</span><span class="sxs-lookup"><span data-stu-id="9e30b-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="9e30b-121">O tipo de declaração seria o URI do cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="9e30b-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="9e30b-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="9e30b-122">isOptional</span></span>|<span data-ttu-id="9e30b-123">Um valor booliano que especifica se esta é uma declaração opcional.</span><span class="sxs-lookup"><span data-stu-id="9e30b-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="9e30b-124">Defina esse atributo como `false` quando se trata de uma declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="9e30b-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="9e30b-125">Você pode usar esse atributo quando o serviço solicita algumas informações, mas não a exige.</span><span class="sxs-lookup"><span data-stu-id="9e30b-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="9e30b-126">Por exemplo, se você precisar que o usuário insira seu nome, sobrenome e endereço, mas decidir que o número de telefone é opcional.</span><span class="sxs-lookup"><span data-stu-id="9e30b-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e30b-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9e30b-127">Child Elements</span></span>  
 <span data-ttu-id="9e30b-128">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9e30b-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e30b-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9e30b-129">Parent Elements</span></span>  
  
|<span data-ttu-id="9e30b-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="9e30b-130">Element</span></span>|<span data-ttu-id="9e30b-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e30b-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e30b-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="9e30b-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="9e30b-133">Especifica uma coleção de tipos de declaração exigidos.</span><span class="sxs-lookup"><span data-stu-id="9e30b-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="9e30b-134">Em um cenário federado, os serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="9e30b-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="9e30b-135">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="9e30b-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="9e30b-136">Cada elemento nesta coleção Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="9e30b-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e30b-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e30b-137">Remarks</span></span>  
 <span data-ttu-id="9e30b-138">Em um cenário federado, os serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="9e30b-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="9e30b-139">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="9e30b-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="9e30b-140">Esse requisito é manifestado em uma política de segurança.</span><span class="sxs-lookup"><span data-stu-id="9e30b-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="9e30b-141">Quando um credenciais de solicitações de cliente de um serviço federado (por exemplo, o CardSpace), ele coloca os requisitos em uma solicitação de token (RequestSecurityToken) para que o serviço federado pode emitir as credenciais que satisfazem os requisitos de forma adequada.</span><span class="sxs-lookup"><span data-stu-id="9e30b-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e30b-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e30b-142">Example</span></span>  
 <span data-ttu-id="9e30b-143">A configuração a seguir adiciona dois requisitos de tipo de declaração para uma associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="9e30b-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9e30b-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e30b-144">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9e30b-145">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="9e30b-145">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)
- [<span data-ttu-id="9e30b-146">Associações</span><span class="sxs-lookup"><span data-stu-id="9e30b-146">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="9e30b-147">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="9e30b-147">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9e30b-148">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="9e30b-148">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="9e30b-149">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9e30b-149">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="9e30b-150">Como: Criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9e30b-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="9e30b-151">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="9e30b-151">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
