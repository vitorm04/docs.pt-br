---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 47366c5bb2bd9228268fce3ae6e1fb5ad457dab1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942614"
---
# <a name="nameclaimtype"></a><span data-ttu-id="4d1b4-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="4d1b4-101">\<nameClaimType></span></span>
<span data-ttu-id="4d1b4-102">Define o tipo de declaração que especifica <xref:System.Security.Principal.IIdentity.Name%2A> a propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d1b4-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="4d1b4-103">O tipo de declaração é usado para pesquisar um <xref:System.Security.Claims.Claim> na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornados pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método desse manipulador de tokens.</span><span class="sxs-lookup"><span data-stu-id="4d1b4-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="4d1b4-104">O valor da declaração de correspondência é definido como o nome do gerado a <xref:System.Security.Principal.IIdentity> partir desse manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="4d1b4-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="4d1b4-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4d1b4-105">\<system.identityModel></span></span>  
<span data-ttu-id="4d1b4-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4d1b4-106">\<identityConfiguration></span></span>  
<span data-ttu-id="4d1b4-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4d1b4-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="4d1b4-108">\<add></span><span class="sxs-lookup"><span data-stu-id="4d1b4-108">\<add></span></span>  
<span data-ttu-id="4d1b4-109">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="4d1b4-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="4d1b4-110">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="4d1b4-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d1b4-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d1b4-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d1b4-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4d1b4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4d1b4-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4d1b4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d1b4-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="4d1b4-114">Attributes</span></span>  
  
|<span data-ttu-id="4d1b4-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="4d1b4-115">Attribute</span></span>|<span data-ttu-id="4d1b4-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d1b4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d1b4-117">value</span><span class="sxs-lookup"><span data-stu-id="4d1b4-117">value</span></span>|<span data-ttu-id="4d1b4-118">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser <xref:System.Security.Principal.IIdentity.Name%2A> usada para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d1b4-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="4d1b4-119">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4d1b4-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d1b4-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4d1b4-120">Child Elements</span></span>  
 <span data-ttu-id="4d1b4-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4d1b4-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d1b4-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4d1b4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4d1b4-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="4d1b4-123">Element</span></span>|<span data-ttu-id="4d1b4-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d1b4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d1b4-125">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="4d1b4-125">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="4d1b4-126">Fornece a configuração para <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> a classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="4d1b4-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d1b4-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d1b4-127">Remarks</span></span>  
 <span data-ttu-id="4d1b4-128">O `<nameClaimType>` elemento define a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> Propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objeto é inicializado a partir da configuração.</span><span class="sxs-lookup"><span data-stu-id="4d1b4-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d1b4-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d1b4-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d1b4-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d1b4-130">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
