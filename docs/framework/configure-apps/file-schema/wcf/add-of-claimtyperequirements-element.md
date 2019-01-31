---
title: <add> de <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 6971837ef2e68de54179daaf225394b9de769987
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275581"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="a59f0-102">\<Adicionar > de \<claimTypeRequirements > elemento</span><span class="sxs-lookup"><span data-stu-id="a59f0-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="a59f0-103">Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="a59f0-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="a59f0-104">Por exemplo, serviços de estado os requisitos de credenciais de entrada, que devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="a59f0-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="a59f0-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a59f0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a59f0-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a59f0-106">\<bindings></span></span>  
<span data-ttu-id="a59f0-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="a59f0-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a59f0-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="a59f0-108">\<binding></span></span>  
<span data-ttu-id="a59f0-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="a59f0-109">\<security></span></span>  
<span data-ttu-id="a59f0-110">\<message></span><span class="sxs-lookup"><span data-stu-id="a59f0-110">\<message></span></span>  
<span data-ttu-id="a59f0-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="a59f0-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a59f0-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a59f0-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a59f0-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a59f0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a59f0-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a59f0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a59f0-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="a59f0-115">Attributes</span></span>  
  
|<span data-ttu-id="a59f0-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="a59f0-116">Attribute</span></span>|<span data-ttu-id="a59f0-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a59f0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a59f0-118">claimType</span><span class="sxs-lookup"><span data-stu-id="a59f0-118">claimType</span></span>|<span data-ttu-id="a59f0-119">Um URI que define o tipo de declaração.</span><span class="sxs-lookup"><span data-stu-id="a59f0-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="a59f0-120">Por exemplo, para adquirir um produto de um site, o usuário deve apresentar um cartão de crédito válido com limite de crédito suficiente.</span><span class="sxs-lookup"><span data-stu-id="a59f0-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="a59f0-121">O tipo de declaração seria o URI do cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="a59f0-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="a59f0-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="a59f0-122">isOptional</span></span>|<span data-ttu-id="a59f0-123">Um valor booliano que especifica se esta é uma declaração opcional.</span><span class="sxs-lookup"><span data-stu-id="a59f0-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="a59f0-124">Defina esse atributo como `false` quando se trata de uma declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="a59f0-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="a59f0-125">Você pode usar esse atributo quando o serviço solicita algumas informações, mas não a exige.</span><span class="sxs-lookup"><span data-stu-id="a59f0-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="a59f0-126">Por exemplo, se você precisar que o usuário insira seu nome, sobrenome e endereço, mas decidir que o número de telefone é opcional.</span><span class="sxs-lookup"><span data-stu-id="a59f0-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a59f0-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a59f0-127">Child Elements</span></span>  
 <span data-ttu-id="a59f0-128">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a59f0-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a59f0-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a59f0-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a59f0-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="a59f0-130">Element</span></span>|<span data-ttu-id="a59f0-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="a59f0-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a59f0-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="a59f0-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="a59f0-133">Especifica uma coleção de tipos de declaração exigidos.</span><span class="sxs-lookup"><span data-stu-id="a59f0-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="a59f0-134">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="a59f0-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="a59f0-135">Em um cenário federado, os serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="a59f0-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a59f0-136">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="a59f0-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a59f0-137">Cada elemento nesta coleção Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="a59f0-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a59f0-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="a59f0-138">Remarks</span></span>  
 <span data-ttu-id="a59f0-139">Em um cenário federado, os serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="a59f0-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a59f0-140">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="a59f0-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a59f0-141">Esse requisito é manifestado em uma política de segurança.</span><span class="sxs-lookup"><span data-stu-id="a59f0-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="a59f0-142">Quando um credenciais de solicitações de cliente de um serviço federado (por exemplo, o CardSpace), ele coloca os requisitos em uma solicitação de token (RequestSecurityToken) para que o serviço federado pode emitir as credenciais que satisfazem os requisitos de forma adequada.</span><span class="sxs-lookup"><span data-stu-id="a59f0-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a59f0-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a59f0-143">Example</span></span>  
 <span data-ttu-id="a59f0-144">A configuração a seguir adiciona dois requisitos de tipo de declaração para uma associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="a59f0-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a59f0-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a59f0-145">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
