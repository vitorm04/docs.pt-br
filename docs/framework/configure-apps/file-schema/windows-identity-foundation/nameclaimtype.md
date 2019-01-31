---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: aab76949d9c31ac003b8afd519c2ad66529cbf26
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254849"
---
# <a name="nameclaimtype"></a><span data-ttu-id="42f31-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="42f31-101">\<nameClaimType></span></span>
<span data-ttu-id="42f31-102">Define o tipo de declaração que especifica o <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="42f31-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="42f31-103">O tipo de declaração é usado para pesquisar um <xref:System.Security.Claims.Claim> na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornados pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método desse manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="42f31-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="42f31-104">O valor da declaração correspondente, em seguida, é definido como o nome da <xref:System.Security.Principal.IIdentity> gerado deste manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="42f31-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="42f31-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="42f31-105">\<system.identityModel></span></span>  
<span data-ttu-id="42f31-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="42f31-106">\<identityConfiguration></span></span>  
<span data-ttu-id="42f31-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="42f31-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="42f31-108">\<add></span><span class="sxs-lookup"><span data-stu-id="42f31-108">\<add></span></span>  
<span data-ttu-id="42f31-109">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="42f31-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="42f31-110">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="42f31-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42f31-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42f31-111">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42f31-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="42f31-112">Attributes and Elements</span></span>  
 <span data-ttu-id="42f31-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="42f31-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42f31-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="42f31-114">Attributes</span></span>  
  
|<span data-ttu-id="42f31-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="42f31-115">Attribute</span></span>|<span data-ttu-id="42f31-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="42f31-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42f31-117">Valor </span><span class="sxs-lookup"><span data-stu-id="42f31-117">value</span></span>|<span data-ttu-id="42f31-118">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser usado para o <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="42f31-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="42f31-119">Necessário.</span><span class="sxs-lookup"><span data-stu-id="42f31-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42f31-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="42f31-120">Child Elements</span></span>  
 <span data-ttu-id="42f31-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="42f31-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42f31-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="42f31-122">Parent Elements</span></span>  
  
|<span data-ttu-id="42f31-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="42f31-123">Element</span></span>|<span data-ttu-id="42f31-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="42f31-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42f31-125">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="42f31-125">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="42f31-126">Fornece configuração para o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="42f31-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42f31-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="42f31-127">Remarks</span></span>  
 <span data-ttu-id="42f31-128">O `<nameClaimType>` conjuntos de elemento de <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objeto é inicializado da configuração.</span><span class="sxs-lookup"><span data-stu-id="42f31-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42f31-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="42f31-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42f31-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42f31-130">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
