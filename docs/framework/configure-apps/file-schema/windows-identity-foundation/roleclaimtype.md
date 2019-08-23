---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0ce2e06ee895d09de193bac1fe7038e71794dda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942536"
---
# <a name="roleclaimtype"></a><span data-ttu-id="ede03-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="ede03-101">\<roleClaimType></span></span>
<span data-ttu-id="ede03-102">Especifica o tipo de declaração que define as declarações de tipo de função na <xref:System.Security.Claims.ClaimsIdentity> coleção de objetos retornada <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> pelo método do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="ede03-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="ede03-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ede03-103">\<system.identityModel></span></span>  
<span data-ttu-id="ede03-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ede03-104">\<identityConfiguration></span></span>  
<span data-ttu-id="ede03-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ede03-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="ede03-106">\<add></span><span class="sxs-lookup"><span data-stu-id="ede03-106">\<add></span></span>  
<span data-ttu-id="ede03-107">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="ede03-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="ede03-108">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="ede03-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ede03-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ede03-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ede03-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ede03-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ede03-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ede03-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ede03-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ede03-112">Attributes</span></span>  
  
|<span data-ttu-id="ede03-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="ede03-113">Attribute</span></span>|<span data-ttu-id="ede03-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ede03-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ede03-115">value</span><span class="sxs-lookup"><span data-stu-id="ede03-115">value</span></span>|<span data-ttu-id="ede03-116">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser usada para o tipo de declaração de função.</span><span class="sxs-lookup"><span data-stu-id="ede03-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ede03-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ede03-117">Child Elements</span></span>  
 <span data-ttu-id="ede03-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ede03-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ede03-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ede03-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ede03-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="ede03-120">Element</span></span>|<span data-ttu-id="ede03-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ede03-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ede03-122">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="ede03-122">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="ede03-123">Fornece a configuração para <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> a classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="ede03-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ede03-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="ede03-124">Remarks</span></span>  
 <span data-ttu-id="ede03-125">O `<roleClaimType>` elemento define a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> Propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objeto é inicializado a partir da configuração.</span><span class="sxs-lookup"><span data-stu-id="ede03-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ede03-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ede03-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ede03-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ede03-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
