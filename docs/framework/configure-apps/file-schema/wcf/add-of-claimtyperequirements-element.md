---
title: <add>do <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 249227c20dd1610cba088017ae39e84d6cb683d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920202"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="2bf9f-102">\<Adicionar > do \<elemento ClaimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="2bf9f-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="2bf9f-103">Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="2bf9f-104">Por exemplo, os serviços definem os requisitos de credenciais de entrada, que devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="2bf9f-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2bf9f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2bf9f-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="2bf9f-106">\<bindings></span></span>  
<span data-ttu-id="2bf9f-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="2bf9f-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="2bf9f-108">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="2bf9f-108">\<binding></span></span>  
<span data-ttu-id="2bf9f-109">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="2bf9f-109">\<security></span></span>  
<span data-ttu-id="2bf9f-110">\<message></span><span class="sxs-lookup"><span data-stu-id="2bf9f-110">\<message></span></span>  
<span data-ttu-id="2bf9f-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="2bf9f-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bf9f-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bf9f-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bf9f-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2bf9f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2bf9f-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bf9f-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="2bf9f-115">Attributes</span></span>  
  
|<span data-ttu-id="2bf9f-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="2bf9f-116">Attribute</span></span>|<span data-ttu-id="2bf9f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bf9f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2bf9f-118">claimType</span><span class="sxs-lookup"><span data-stu-id="2bf9f-118">claimType</span></span>|<span data-ttu-id="2bf9f-119">Um URI que define o tipo de uma declaração.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="2bf9f-120">Por exemplo, para comprar um produto de um site da Web, o usuário deve apresentar um cartão de crédito válido com limite de crédito suficiente.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="2bf9f-121">O tipo de declaração seria o URI do cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="2bf9f-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="2bf9f-122">isOptional</span></span>|<span data-ttu-id="2bf9f-123">Um valor booliano que especifica se isso é para uma declaração opcional.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="2bf9f-124">Defina esse atributo como `false` se for uma declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="2bf9f-125">Você pode usar esse atributo quando o serviço solicitar algumas informações, mas não precisar dela.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="2bf9f-126">Por exemplo, se você precisar que o usuário insira seu nome, sobrenome e endereço, mas decida que o número de telefone é opcional.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bf9f-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2bf9f-127">Child Elements</span></span>  
 <span data-ttu-id="2bf9f-128">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2bf9f-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2bf9f-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2bf9f-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="2bf9f-130">Element</span></span>|<span data-ttu-id="2bf9f-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bf9f-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bf9f-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="2bf9f-132">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="2bf9f-133">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="2bf9f-134">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="2bf9f-135">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="2bf9f-136">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="2bf9f-137">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bf9f-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="2bf9f-138">Remarks</span></span>  
 <span data-ttu-id="2bf9f-139">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="2bf9f-140">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="2bf9f-141">Esse requisito é manifestado em uma política de segurança.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="2bf9f-142">Quando um cliente solicita credenciais de um serviço federado (por exemplo, CardSpace), ele coloca os requisitos em uma solicitação de token (RequestSecurityToken) para que o serviço federado possa emitir as credenciais que atendem aos requisitos de acordo.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bf9f-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2bf9f-143">Example</span></span>  
 <span data-ttu-id="2bf9f-144">A configuração a seguir adiciona dois requisitos de tipo de declaração a uma associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="2bf9f-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2bf9f-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bf9f-145">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
