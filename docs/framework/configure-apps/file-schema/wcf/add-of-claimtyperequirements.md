---
title: '&lt;adicionar&gt; &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: b4f9275fdc36ea3c7ba79c6609f039c3b1f4c3ed
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750590"
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt"></a><span data-ttu-id="0b22c-102">&lt;adicionar&gt; &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="0b22c-102">&lt;add&gt; of &lt;claimTypeRequirements&gt;</span></span>
<span data-ttu-id="0b22c-103">Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="0b22c-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="0b22c-104">Por exemplo, serviços de estado os requisitos de credenciais de entrada, que devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="0b22c-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="0b22c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0b22c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="0b22c-106">\<associações ></span><span class="sxs-lookup"><span data-stu-id="0b22c-106">\<bindings></span></span>  
<span data-ttu-id="0b22c-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0b22c-107">\<customBinding></span></span>  
<span data-ttu-id="0b22c-108">\<associação ></span><span class="sxs-lookup"><span data-stu-id="0b22c-108">\<binding></span></span>  
<span data-ttu-id="0b22c-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="0b22c-109">\<security></span></span>  
<span data-ttu-id="0b22c-110">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="0b22c-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="0b22c-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="0b22c-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b22c-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b22c-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
           isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b22c-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0b22c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0b22c-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0b22c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b22c-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="0b22c-115">Attributes</span></span>  
  
|<span data-ttu-id="0b22c-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="0b22c-116">Attribute</span></span>|<span data-ttu-id="0b22c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b22c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b22c-118">claimType</span><span class="sxs-lookup"><span data-stu-id="0b22c-118">claimType</span></span>|<span data-ttu-id="0b22c-119">Um URI que define o tipo de declaração.</span><span class="sxs-lookup"><span data-stu-id="0b22c-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="0b22c-120">Por exemplo, para adquirir um produto de um site, o usuário deve apresentar um cartão de crédito válido com limite de crédito suficiente.</span><span class="sxs-lookup"><span data-stu-id="0b22c-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="0b22c-121">O tipo de declaração seria o URI do cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="0b22c-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="0b22c-122">é opcional</span><span class="sxs-lookup"><span data-stu-id="0b22c-122">isOptional</span></span>|<span data-ttu-id="0b22c-123">Um valor booleano que especifica se esta é uma declaração opcional.</span><span class="sxs-lookup"><span data-stu-id="0b22c-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="0b22c-124">Defina este atributo como `false` quando se trata de uma declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="0b22c-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="0b22c-125">Você pode usar esse atributo quando o serviço solicita informações, mas não a exige.</span><span class="sxs-lookup"><span data-stu-id="0b22c-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="0b22c-126">Por exemplo, se você precisar que o usuário insira seu nome, sobrenome e endereço, mas decidir que o número de telefone é opcional.</span><span class="sxs-lookup"><span data-stu-id="0b22c-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b22c-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0b22c-127">Child Elements</span></span>  
 <span data-ttu-id="0b22c-128">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0b22c-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b22c-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0b22c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="0b22c-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b22c-130">Element</span></span>|<span data-ttu-id="0b22c-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b22c-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b22c-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="0b22c-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="0b22c-133">Especifica uma coleção de tipos de declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="0b22c-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="0b22c-134">Em um cenário federado, serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="0b22c-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="0b22c-135">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="0b22c-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="0b22c-136">Cada elemento na coleção Especifica os tipos de declarações obrigatórias e opcionais que deve aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="0b22c-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b22c-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b22c-137">Remarks</span></span>  
 <span data-ttu-id="0b22c-138">Em um cenário federado, serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="0b22c-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="0b22c-139">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="0b22c-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="0b22c-140">Esse requisito é manifestado em uma política de segurança.</span><span class="sxs-lookup"><span data-stu-id="0b22c-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="0b22c-141">Quando um credenciais de solicitações de cliente de um serviço federado (por exemplo, o CardSpace), ele coloca os requisitos em uma solicitação de token (RequestSecurityToken) para que o serviço federado pode emitir as credenciais que satisfaça os requisitos de acordo.</span><span class="sxs-lookup"><span data-stu-id="0b22c-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b22c-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b22c-142">Example</span></span>  
 <span data-ttu-id="0b22c-143">A configuração a seguir adiciona dois requisitos de tipo de declaração para uma associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="0b22c-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b22c-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b22c-144">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="0b22c-145">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="0b22c-145">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)  
 [<span data-ttu-id="0b22c-146">Associações</span><span class="sxs-lookup"><span data-stu-id="0b22c-146">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0b22c-147">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="0b22c-147">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="0b22c-148">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="0b22c-148">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="0b22c-149">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0b22c-149">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="0b22c-150">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0b22c-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="0b22c-151">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="0b22c-151">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
