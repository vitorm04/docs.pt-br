---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251933"
---
# <a name="nameclaimtype"></a><span data-ttu-id="c860e-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="c860e-101">\<nameClaimType></span></span>
<span data-ttu-id="c860e-102">Define o tipo de declaração que especifica <xref:System.Security.Principal.IIdentity.Name%2A> a propriedade.</span><span class="sxs-lookup"><span data-stu-id="c860e-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="c860e-103">O tipo de declaração é usado para pesquisar um <xref:System.Security.Claims.Claim> na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornados pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método desse manipulador de tokens.</span><span class="sxs-lookup"><span data-stu-id="c860e-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="c860e-104">O valor da declaração de correspondência é definido como o nome do gerado a <xref:System.Security.Principal.IIdentity> partir desse manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="c860e-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
<span data-ttu-id="c860e-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c860e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c860e-106">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c860e-106">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c860e-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c860e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c860e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="c860e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="c860e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Adicionar >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="c860e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="c860e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> samlSecurityTokenRequirement**](samlsecuritytokenrequirement.md)</span><span class="sxs-lookup"><span data-stu-id="c860e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)</span></span>\
<span data-ttu-id="c860e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> nameClaimType**</span><span class="sxs-lookup"><span data-stu-id="c860e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c860e-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c860e-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c860e-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c860e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c860e-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c860e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c860e-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="c860e-115">Attributes</span></span>  
  
|<span data-ttu-id="c860e-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="c860e-116">Attribute</span></span>|<span data-ttu-id="c860e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c860e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c860e-118">value</span><span class="sxs-lookup"><span data-stu-id="c860e-118">value</span></span>|<span data-ttu-id="c860e-119">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser <xref:System.Security.Principal.IIdentity.Name%2A> usada para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="c860e-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="c860e-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c860e-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c860e-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c860e-121">Child Elements</span></span>  
 <span data-ttu-id="c860e-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c860e-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c860e-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c860e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c860e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="c860e-124">Element</span></span>|<span data-ttu-id="c860e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="c860e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c860e-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="c860e-126">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="c860e-127">Fornece a configuração para <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> a classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="c860e-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c860e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="c860e-128">Remarks</span></span>  
 <span data-ttu-id="c860e-129">O `<nameClaimType>` elemento define a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> Propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objeto é inicializado a partir da configuração.</span><span class="sxs-lookup"><span data-stu-id="c860e-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c860e-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c860e-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c860e-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c860e-131">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
