---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: fed8964e03b80e365fdc5eafd45b4fc372a6e352
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944261"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="d7015-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="d7015-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="d7015-102">Fornece a configuração para <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> a classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="d7015-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="d7015-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d7015-103">\<system.identityModel></span></span>  
<span data-ttu-id="d7015-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d7015-104">\<identityConfiguration></span></span>  
<span data-ttu-id="d7015-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d7015-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d7015-106">\<add></span><span class="sxs-lookup"><span data-stu-id="d7015-106">\<add></span></span>  
<span data-ttu-id="d7015-107">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="d7015-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7015-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7015-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7015-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d7015-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d7015-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d7015-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7015-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="d7015-111">Attributes</span></span>  
  
|<span data-ttu-id="d7015-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="d7015-112">Attribute</span></span>|<span data-ttu-id="d7015-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7015-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7015-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="d7015-114">membershipProviderName</span></span>|<span data-ttu-id="d7015-115">Especifica o <xref:System.Web.Security.MembershipProvider> que deve ser usado pelo manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="d7015-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7015-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d7015-116">Child Elements</span></span>  
 <span data-ttu-id="d7015-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d7015-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7015-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d7015-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d7015-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7015-119">Element</span></span>|<span data-ttu-id="d7015-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7015-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7015-121">\<add></span><span class="sxs-lookup"><span data-stu-id="d7015-121">\<add></span></span>](add.md)|<span data-ttu-id="d7015-122">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="d7015-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7015-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7015-123">Remarks</span></span>  
 <span data-ttu-id="d7015-124">O `<userNameSecurityTokenHandlerRequirement>` elemento define a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> Propriedade quando um <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> objeto é inicializado a partir da configuração.</span><span class="sxs-lookup"><span data-stu-id="d7015-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7015-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d7015-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
