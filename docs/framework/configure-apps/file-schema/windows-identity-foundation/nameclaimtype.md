---
title: '&lt;nameClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: bd4033b2edea7450b66c25f446669b3ded65e9af
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112212"
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="519f5-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="519f5-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="519f5-103">Define o tipo de declaração que especifica o <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="519f5-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="519f5-104">O tipo de declaração é usado para pesquisar um <xref:System.Security.Claims.Claim> na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornados pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método desse manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="519f5-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="519f5-105">O valor da declaração correspondente, em seguida, é definido como o nome da <xref:System.Security.Principal.IIdentity> gerado deste manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="519f5-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="519f5-106">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="519f5-106">\<system.identityModel></span></span>  
<span data-ttu-id="519f5-107">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="519f5-107">\<identityConfiguration></span></span>  
<span data-ttu-id="519f5-108">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="519f5-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="519f5-109">\<add></span><span class="sxs-lookup"><span data-stu-id="519f5-109">\<add></span></span>  
<span data-ttu-id="519f5-110">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="519f5-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="519f5-111">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="519f5-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="519f5-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="519f5-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="519f5-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="519f5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="519f5-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="519f5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="519f5-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="519f5-115">Attributes</span></span>  
  
|<span data-ttu-id="519f5-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="519f5-116">Attribute</span></span>|<span data-ttu-id="519f5-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="519f5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="519f5-118">Valor </span><span class="sxs-lookup"><span data-stu-id="519f5-118">value</span></span>|<span data-ttu-id="519f5-119">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser usado para o <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="519f5-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="519f5-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="519f5-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="519f5-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="519f5-121">Child Elements</span></span>  
 <span data-ttu-id="519f5-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="519f5-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="519f5-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="519f5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="519f5-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="519f5-124">Element</span></span>|<span data-ttu-id="519f5-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="519f5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="519f5-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="519f5-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="519f5-127">Fornece configuração para o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="519f5-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="519f5-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="519f5-128">Remarks</span></span>  
 <span data-ttu-id="519f5-129">O `<nameClaimType>` conjuntos de elemento de <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objeto é inicializado da configuração.</span><span class="sxs-lookup"><span data-stu-id="519f5-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="519f5-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="519f5-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="519f5-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="519f5-131">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
