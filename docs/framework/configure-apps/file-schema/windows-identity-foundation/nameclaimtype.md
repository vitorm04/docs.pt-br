---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 5202e162a7eb5fc4e36d6a6c0a2c18af48872a69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791593"
---
# <a name="nameclaimtype"></a><span data-ttu-id="08878-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="08878-101">\<nameClaimType></span></span>
<span data-ttu-id="08878-102">Define o tipo de declaração que especifica o <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="08878-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="08878-103">O tipo de declaração é usado para pesquisar um <xref:System.Security.Claims.Claim> na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornados pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método desse manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="08878-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="08878-104">O valor da declaração correspondente, em seguida, é definido como o nome da <xref:System.Security.Principal.IIdentity> gerado deste manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="08878-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="08878-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="08878-105">\<system.identityModel></span></span>  
<span data-ttu-id="08878-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="08878-106">\<identityConfiguration></span></span>  
<span data-ttu-id="08878-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="08878-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="08878-108">\<add></span><span class="sxs-lookup"><span data-stu-id="08878-108">\<add></span></span>  
<span data-ttu-id="08878-109">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="08878-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="08878-110">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="08878-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08878-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08878-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08878-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="08878-112">Attributes and Elements</span></span>  
 <span data-ttu-id="08878-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="08878-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08878-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="08878-114">Attributes</span></span>  
  
|<span data-ttu-id="08878-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="08878-115">Attribute</span></span>|<span data-ttu-id="08878-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="08878-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08878-117">Valor </span><span class="sxs-lookup"><span data-stu-id="08878-117">value</span></span>|<span data-ttu-id="08878-118">Uma cadeia de caracteres que especifica o URI que representa o tipo de declaração da declaração a ser usado para o <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="08878-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="08878-119">Necessário.</span><span class="sxs-lookup"><span data-stu-id="08878-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08878-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="08878-120">Child Elements</span></span>  
 <span data-ttu-id="08878-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="08878-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08878-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="08878-122">Parent Elements</span></span>  
  
|<span data-ttu-id="08878-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="08878-123">Element</span></span>|<span data-ttu-id="08878-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="08878-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08878-125">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="08878-125">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="08878-126">Fornece configuração para o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="08878-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08878-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="08878-127">Remarks</span></span>  
 <span data-ttu-id="08878-128">O `<nameClaimType>` conjuntos de elemento de <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> propriedade quando um <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objeto é inicializado da configuração.</span><span class="sxs-lookup"><span data-stu-id="08878-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08878-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08878-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08878-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08878-130">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
