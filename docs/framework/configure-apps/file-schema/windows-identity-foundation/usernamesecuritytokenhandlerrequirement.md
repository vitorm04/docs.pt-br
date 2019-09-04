---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 5863c01e97e7f5fb6fe07c43174c0d6cb7a0a25d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251743"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="45dee-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="45dee-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="45dee-102">Fornece a configuração para <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> a classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="45dee-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="45dee-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="45dee-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="45dee-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="45dee-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="45dee-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="45dee-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="45dee-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="45dee-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="45dee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Adicionar >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="45dee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="45dee-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> userNameSecurityTokenHandlerRequirement**</span><span class="sxs-lookup"><span data-stu-id="45dee-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45dee-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45dee-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45dee-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="45dee-110">Attributes and Elements</span></span>  
 <span data-ttu-id="45dee-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="45dee-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45dee-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="45dee-112">Attributes</span></span>  
  
|<span data-ttu-id="45dee-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="45dee-113">Attribute</span></span>|<span data-ttu-id="45dee-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="45dee-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45dee-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="45dee-115">membershipProviderName</span></span>|<span data-ttu-id="45dee-116">Especifica o <xref:System.Web.Security.MembershipProvider> que deve ser usado pelo manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="45dee-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45dee-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="45dee-117">Child Elements</span></span>  
 <span data-ttu-id="45dee-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="45dee-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45dee-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="45dee-119">Parent Elements</span></span>  
  
|<span data-ttu-id="45dee-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="45dee-120">Element</span></span>|<span data-ttu-id="45dee-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="45dee-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45dee-122">\<add></span><span class="sxs-lookup"><span data-stu-id="45dee-122">\<add></span></span>](add.md)|<span data-ttu-id="45dee-123">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="45dee-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45dee-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="45dee-124">Remarks</span></span>  
 <span data-ttu-id="45dee-125">O `<userNameSecurityTokenHandlerRequirement>` elemento define a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> Propriedade quando um <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> objeto é inicializado a partir da configuração.</span><span class="sxs-lookup"><span data-stu-id="45dee-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45dee-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45dee-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
