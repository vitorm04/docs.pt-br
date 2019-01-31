---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 812d44ef947d27b0f73d9dc2172494e89ee56d72
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270853"
---
# <a name="roleclaimtype"></a><span data-ttu-id="42971-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="42971-101">\<roleClaimType></span></span>
<span data-ttu-id="42971-102">Especifica o tipo de declaração que define as declarações de tipo de função na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornados pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="42971-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="42971-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="42971-103">\<system.identityModel></span></span>  
<span data-ttu-id="42971-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="42971-104">\<identityConfiguration></span></span>  
<span data-ttu-id="42971-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="42971-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="42971-106">\<add></span><span class="sxs-lookup"><span data-stu-id="42971-106">\<add></span></span>  
<span data-ttu-id="42971-107">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="42971-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="42971-108">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="42971-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42971-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42971-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42971-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="42971-110">Attributes and Elements</span></span>  
 <span data-ttu-id="42971-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="42971-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42971-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="42971-112">Attributes</span></span>  
  
|<span data-ttu-id="42971-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="42971-113">Attribute</span></span>|<span data-ttu-id="42971-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="42971-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42971-115">Valor </span><span class="sxs-lookup"><span data-stu-id="42971-115">value</span></span>|<span data-ttu-id="42971-116">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser usado para o tipo de declaração de função.</span><span class="sxs-lookup"><span data-stu-id="42971-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42971-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="42971-117">Child Elements</span></span>  
 <span data-ttu-id="42971-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="42971-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42971-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="42971-119">Parent Elements</span></span>  
  
|<span data-ttu-id="42971-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="42971-120">Element</span></span>|<span data-ttu-id="42971-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="42971-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42971-122">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="42971-122">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="42971-123">Fornece configuração para o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="42971-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42971-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="42971-124">Remarks</span></span>  
 <span data-ttu-id="42971-125">O `<roleClaimType>` conjuntos de elemento de <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objeto é inicializado da configuração.</span><span class="sxs-lookup"><span data-stu-id="42971-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42971-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="42971-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42971-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42971-127">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
