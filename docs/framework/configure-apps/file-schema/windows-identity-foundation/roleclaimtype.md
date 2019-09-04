---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0f651377346b1f14a4226128cd5cf7059543adca
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251906"
---
# <a name="roleclaimtype"></a><span data-ttu-id="5fe27-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="5fe27-101">\<roleClaimType></span></span>
<span data-ttu-id="5fe27-102">Especifica o tipo de declaração que define as declarações de tipo de função na <xref:System.Security.Claims.ClaimsIdentity> coleção de objetos retornada <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> pelo método do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="5fe27-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
<span data-ttu-id="5fe27-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5fe27-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5fe27-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="5fe27-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="5fe27-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="5fe27-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="5fe27-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="5fe27-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="5fe27-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Adicionar >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="5fe27-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="5fe27-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> samlSecurityTokenRequirement**](samlsecuritytokenrequirement.md)</span><span class="sxs-lookup"><span data-stu-id="5fe27-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)</span></span>\
<span data-ttu-id="5fe27-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> roleClaimType**</span><span class="sxs-lookup"><span data-stu-id="5fe27-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe27-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5fe27-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fe27-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5fe27-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5fe27-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5fe27-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fe27-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="5fe27-113">Attributes</span></span>  
  
|<span data-ttu-id="5fe27-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="5fe27-114">Attribute</span></span>|<span data-ttu-id="5fe27-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5fe27-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5fe27-116">value</span><span class="sxs-lookup"><span data-stu-id="5fe27-116">value</span></span>|<span data-ttu-id="5fe27-117">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser usada para o tipo de declaração de função.</span><span class="sxs-lookup"><span data-stu-id="5fe27-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fe27-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5fe27-118">Child Elements</span></span>  
 <span data-ttu-id="5fe27-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5fe27-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fe27-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5fe27-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5fe27-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="5fe27-121">Element</span></span>|<span data-ttu-id="5fe27-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="5fe27-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fe27-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="5fe27-123">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="5fe27-124">Fornece a configuração para <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> a classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="5fe27-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fe27-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="5fe27-125">Remarks</span></span>  
 <span data-ttu-id="5fe27-126">O `<roleClaimType>` elemento define a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> Propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objeto é inicializado a partir da configuração.</span><span class="sxs-lookup"><span data-stu-id="5fe27-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fe27-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fe27-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fe27-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fe27-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
