---
title: <add> do <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 920d2b3fa4b51ee56e30863d521214ff66e7fcf2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149238"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="7f4bd-102">\<add> do \<claimTypeRequirements> elemento</span><span class="sxs-lookup"><span data-stu-id="7f4bd-102">\<add> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="7f4bd-103">Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="7f4bd-104">Por exemplo, os serviços definem os requisitos de credenciais de entrada, que devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**
  
## <a name="syntax"></a><span data-ttu-id="7f4bd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f4bd-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f4bd-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7f4bd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7f4bd-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f4bd-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="7f4bd-108">Attributes</span></span>  
  
|<span data-ttu-id="7f4bd-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="7f4bd-109">Attribute</span></span>|<span data-ttu-id="7f4bd-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f4bd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f4bd-111">claimType</span><span class="sxs-lookup"><span data-stu-id="7f4bd-111">claimType</span></span>|<span data-ttu-id="7f4bd-112">Um URI que define o tipo de uma declaração.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="7f4bd-113">Por exemplo, para comprar um produto de um site da Web, o usuário deve apresentar um cartão de crédito válido com limite de crédito suficiente.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="7f4bd-114">O tipo de declaração seria o URI do cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="7f4bd-115">isOptional</span><span class="sxs-lookup"><span data-stu-id="7f4bd-115">isOptional</span></span>|<span data-ttu-id="7f4bd-116">Um valor booliano que especifica se isso é para uma declaração opcional.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="7f4bd-117">Defina esse atributo como `false` se for uma declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="7f4bd-118">Você pode usar esse atributo quando o serviço solicitar algumas informações, mas não precisar dela.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="7f4bd-119">Por exemplo, se você precisar que o usuário insira seu nome, sobrenome e endereço, mas decida que o número de telefone é opcional.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f4bd-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7f4bd-120">Child Elements</span></span>  

 <span data-ttu-id="7f4bd-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f4bd-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7f4bd-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7f4bd-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="7f4bd-123">Element</span></span>|<span data-ttu-id="7f4bd-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f4bd-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="7f4bd-125">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="7f4bd-126">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="7f4bd-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="7f4bd-127">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="7f4bd-128">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="7f4bd-129">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f4bd-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f4bd-130">Remarks</span></span>  

 <span data-ttu-id="7f4bd-131">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-131">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="7f4bd-132">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-132">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="7f4bd-133">Esse requisito é manifestado em uma política de segurança.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-133">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="7f4bd-134">Quando um cliente solicita credenciais de um serviço federado (por exemplo, CardSpace), ele coloca os requisitos em uma solicitação de token (RequestSecurityToken) para que o serviço federado possa emitir as credenciais que atendem aos requisitos de acordo.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-134">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f4bd-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f4bd-135">Example</span></span>  

 <span data-ttu-id="7f4bd-136">A configuração a seguir adiciona dois requisitos de tipo de declaração a uma associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="7f4bd-136">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f4bd-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="7f4bd-137">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
