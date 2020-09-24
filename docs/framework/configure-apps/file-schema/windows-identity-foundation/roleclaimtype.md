---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 36d727f97597df816779da1c1f7ed5da1a1697f2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164929"
---
# \<roleClaimType>

<span data-ttu-id="25259-101">Especifica o tipo de declaração que define as declarações de tipo de função na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornada pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="25259-101">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="25259-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="25259-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25259-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="25259-103">Attributes and Elements</span></span>  

 <span data-ttu-id="25259-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="25259-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25259-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="25259-105">Attributes</span></span>  
  
|<span data-ttu-id="25259-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="25259-106">Attribute</span></span>|<span data-ttu-id="25259-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="25259-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="25259-108">value</span><span class="sxs-lookup"><span data-stu-id="25259-108">value</span></span>|<span data-ttu-id="25259-109">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser usada para o tipo de declaração de função.</span><span class="sxs-lookup"><span data-stu-id="25259-109">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25259-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="25259-110">Child Elements</span></span>  

 <span data-ttu-id="25259-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="25259-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25259-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="25259-112">Parent Elements</span></span>  
  
|<span data-ttu-id="25259-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="25259-113">Element</span></span>|<span data-ttu-id="25259-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="25259-114">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="25259-115">Fornece a configuração para a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="25259-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25259-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="25259-116">Remarks</span></span>  

 <span data-ttu-id="25259-117">O `<roleClaimType>` elemento define a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objeto é inicializado a partir da configuração.</span><span class="sxs-lookup"><span data-stu-id="25259-117">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25259-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25259-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="25259-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="25259-119">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
