---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5d725cc0d16457f2bdfb404baf4758e3431ce6b7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a><span data-ttu-id="09309-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="09309-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="09309-103">Fornece configuração para o <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="09309-103">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="09309-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="09309-104">\<system.identityModel></span></span>  
<span data-ttu-id="09309-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="09309-105">\<identityConfiguration></span></span>  
<span data-ttu-id="09309-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="09309-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="09309-107">\<add></span><span class="sxs-lookup"><span data-stu-id="09309-107">\<add></span></span>  
<span data-ttu-id="09309-108">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="09309-108">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09309-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09309-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09309-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="09309-110">Attributes and Elements</span></span>  
 <span data-ttu-id="09309-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="09309-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09309-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="09309-112">Attributes</span></span>  
  
|<span data-ttu-id="09309-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="09309-113">Attribute</span></span>|<span data-ttu-id="09309-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="09309-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09309-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="09309-115">membershipProviderName</span></span>|<span data-ttu-id="09309-116">Especifica o <xref:System.Web.Security.MembershipProvider> que deve ser usado pelo manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="09309-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09309-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="09309-117">Child Elements</span></span>  
 <span data-ttu-id="09309-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="09309-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09309-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="09309-119">Parent Elements</span></span>  
  
|<span data-ttu-id="09309-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="09309-120">Element</span></span>|<span data-ttu-id="09309-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="09309-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09309-122">\<add></span><span class="sxs-lookup"><span data-stu-id="09309-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="09309-123">Adiciona o manipulador de token de segurança especificados na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="09309-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09309-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="09309-124">Remarks</span></span>  
 <span data-ttu-id="09309-125">O `<userNameSecurityTokenHandlerRequirement>` elemento define o <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> propriedade quando um <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> é inicializar o objeto de configuração.</span><span class="sxs-lookup"><span data-stu-id="09309-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09309-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09309-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
