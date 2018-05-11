---
title: '&lt;nameClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e403667f16e316004f766b8476e20eca9bd1c988
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="0ffc8-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="0ffc8-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="0ffc8-103">Define o tipo de declaração que especifica o <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="0ffc8-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="0ffc8-104">O tipo de declaração é usado para pesquisar um <xref:System.Security.Claims.Claim> na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornados pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método deste manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="0ffc8-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="0ffc8-105">O valor da declaração correspondente, em seguida, é definido como o nome do <xref:System.Security.Principal.IIdentity> gerado deste manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="0ffc8-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="0ffc8-106">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0ffc8-106">\<system.identityModel></span></span>  
<span data-ttu-id="0ffc8-107">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="0ffc8-107">\<identityConfiguration></span></span>  
<span data-ttu-id="0ffc8-108">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="0ffc8-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="0ffc8-109">\<add></span><span class="sxs-lookup"><span data-stu-id="0ffc8-109">\<add></span></span>  
<span data-ttu-id="0ffc8-110">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="0ffc8-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="0ffc8-111">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="0ffc8-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ffc8-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ffc8-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ffc8-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0ffc8-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0ffc8-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0ffc8-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ffc8-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="0ffc8-115">Attributes</span></span>  
  
|<span data-ttu-id="0ffc8-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="0ffc8-116">Attribute</span></span>|<span data-ttu-id="0ffc8-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ffc8-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0ffc8-118">Valor </span><span class="sxs-lookup"><span data-stu-id="0ffc8-118">value</span></span>|<span data-ttu-id="0ffc8-119">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser usado para o <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="0ffc8-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="0ffc8-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0ffc8-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ffc8-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0ffc8-121">Child Elements</span></span>  
 <span data-ttu-id="0ffc8-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0ffc8-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ffc8-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0ffc8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0ffc8-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="0ffc8-124">Element</span></span>|<span data-ttu-id="0ffc8-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ffc8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ffc8-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="0ffc8-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="0ffc8-127">Fornece configuração para o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="0ffc8-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ffc8-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ffc8-128">Remarks</span></span>  
 <span data-ttu-id="0ffc8-129">O `<nameClaimType>` elemento define o <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> é inicializar o objeto de configuração.</span><span class="sxs-lookup"><span data-stu-id="0ffc8-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ffc8-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ffc8-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ffc8-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ffc8-131">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
