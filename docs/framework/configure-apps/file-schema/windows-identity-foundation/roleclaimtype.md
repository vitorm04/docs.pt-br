---
title: '&lt;roleClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 6114a95f3942c367849785ce981858f276c0b8fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599940"
---
# <a name="ltroleclaimtypegt"></a><span data-ttu-id="54ae0-102">&lt;roleClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="54ae0-102">&lt;roleClaimType&gt;</span></span>
<span data-ttu-id="54ae0-103">Especifica o tipo de declaração que define as declarações de tipo de função na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornados pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="54ae0-103">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="54ae0-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="54ae0-104">\<system.identityModel></span></span>  
<span data-ttu-id="54ae0-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="54ae0-105">\<identityConfiguration></span></span>  
<span data-ttu-id="54ae0-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="54ae0-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="54ae0-107">\<add></span><span class="sxs-lookup"><span data-stu-id="54ae0-107">\<add></span></span>  
<span data-ttu-id="54ae0-108">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="54ae0-108">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="54ae0-109">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="54ae0-109">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54ae0-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54ae0-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54ae0-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="54ae0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="54ae0-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="54ae0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54ae0-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="54ae0-113">Attributes</span></span>  
  
|<span data-ttu-id="54ae0-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="54ae0-114">Attribute</span></span>|<span data-ttu-id="54ae0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="54ae0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54ae0-116">Valor </span><span class="sxs-lookup"><span data-stu-id="54ae0-116">value</span></span>|<span data-ttu-id="54ae0-117">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser usado para o tipo de declaração de função.</span><span class="sxs-lookup"><span data-stu-id="54ae0-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54ae0-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="54ae0-118">Child Elements</span></span>  
 <span data-ttu-id="54ae0-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="54ae0-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54ae0-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="54ae0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="54ae0-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="54ae0-121">Element</span></span>|<span data-ttu-id="54ae0-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="54ae0-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54ae0-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="54ae0-123">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="54ae0-124">Fornece configuração para o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="54ae0-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54ae0-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="54ae0-125">Remarks</span></span>  
 <span data-ttu-id="54ae0-126">O `<roleClaimType>` conjuntos de elemento de <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objeto é inicializado da configuração.</span><span class="sxs-lookup"><span data-stu-id="54ae0-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54ae0-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54ae0-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54ae0-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54ae0-128">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
