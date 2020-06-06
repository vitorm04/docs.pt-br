---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251933"
---
# \<nameClaimType>
<span data-ttu-id="d25b3-101">Define o tipo de declaração que especifica a <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d25b3-101">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d25b3-102">O tipo de declaração é usado para pesquisar um <xref:System.Security.Claims.Claim> na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornados pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método desse manipulador de tokens.</span><span class="sxs-lookup"><span data-stu-id="d25b3-102">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="d25b3-103">O valor da declaração de correspondência é definido como o nome do gerado a <xref:System.Security.Principal.IIdentity> partir desse manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="d25b3-103">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="d25b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d25b3-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d25b3-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d25b3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d25b3-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d25b3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d25b3-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d25b3-107">Attributes</span></span>  
  
|<span data-ttu-id="d25b3-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="d25b3-108">Attribute</span></span>|<span data-ttu-id="d25b3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d25b3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d25b3-110">value</span><span class="sxs-lookup"><span data-stu-id="d25b3-110">value</span></span>|<span data-ttu-id="d25b3-111">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser usada para a <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d25b3-111">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d25b3-112">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="d25b3-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d25b3-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d25b3-113">Child Elements</span></span>  
 <span data-ttu-id="d25b3-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d25b3-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d25b3-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d25b3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d25b3-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="d25b3-116">Element</span></span>|<span data-ttu-id="d25b3-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d25b3-117">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="d25b3-118">Fornece a configuração para a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="d25b3-118">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d25b3-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="d25b3-119">Remarks</span></span>  
 <span data-ttu-id="d25b3-120">O `<nameClaimType>` elemento define a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objeto é inicializado a partir da configuração.</span><span class="sxs-lookup"><span data-stu-id="d25b3-120">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d25b3-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d25b3-121">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d25b3-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="d25b3-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
