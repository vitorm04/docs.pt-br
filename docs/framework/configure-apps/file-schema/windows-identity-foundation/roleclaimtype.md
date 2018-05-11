---
title: '&lt;roleClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 909df1bd6054d9737f91c30c3c6b2d68b932281c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltroleclaimtypegt"></a><span data-ttu-id="f82b5-102">&lt;roleClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="f82b5-102">&lt;roleClaimType&gt;</span></span>
<span data-ttu-id="f82b5-103">Especifica o tipo de declaração que define as declarações de tipo de função na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornados pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="f82b5-103">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="f82b5-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f82b5-104">\<system.identityModel></span></span>  
<span data-ttu-id="f82b5-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f82b5-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f82b5-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f82b5-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f82b5-107">\<add></span><span class="sxs-lookup"><span data-stu-id="f82b5-107">\<add></span></span>  
<span data-ttu-id="f82b5-108">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="f82b5-108">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="f82b5-109">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="f82b5-109">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f82b5-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f82b5-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f82b5-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f82b5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f82b5-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f82b5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f82b5-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="f82b5-113">Attributes</span></span>  
  
|<span data-ttu-id="f82b5-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="f82b5-114">Attribute</span></span>|<span data-ttu-id="f82b5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f82b5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f82b5-116">Valor </span><span class="sxs-lookup"><span data-stu-id="f82b5-116">value</span></span>|<span data-ttu-id="f82b5-117">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser usado para o tipo de declaração de função.</span><span class="sxs-lookup"><span data-stu-id="f82b5-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f82b5-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f82b5-118">Child Elements</span></span>  
 <span data-ttu-id="f82b5-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f82b5-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f82b5-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f82b5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f82b5-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f82b5-121">Element</span></span>|<span data-ttu-id="f82b5-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f82b5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f82b5-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="f82b5-123">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="f82b5-124">Fornece configuração para o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="f82b5-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f82b5-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="f82b5-125">Remarks</span></span>  
 <span data-ttu-id="f82b5-126">O `<roleClaimType>` elemento define o <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> é inicializar o objeto de configuração.</span><span class="sxs-lookup"><span data-stu-id="f82b5-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f82b5-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f82b5-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f82b5-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f82b5-128">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
