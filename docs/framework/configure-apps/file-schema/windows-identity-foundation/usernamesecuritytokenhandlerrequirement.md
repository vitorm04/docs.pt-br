---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: a49b41c04c8f184188b62e04c3b232bd33752fca
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185516"
---
# \<userNameSecurityTokenHandlerRequirement>

<span data-ttu-id="94a56-101">Fornece a configuração para a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="94a56-101">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="94a56-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94a56-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94a56-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="94a56-103">Attributes and Elements</span></span>  

 <span data-ttu-id="94a56-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="94a56-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94a56-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="94a56-105">Attributes</span></span>  
  
|<span data-ttu-id="94a56-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="94a56-106">Attribute</span></span>|<span data-ttu-id="94a56-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="94a56-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94a56-108">membershipProvidername</span><span class="sxs-lookup"><span data-stu-id="94a56-108">membershipProviderName</span></span>|<span data-ttu-id="94a56-109">Especifica o <xref:System.Web.Security.MembershipProvider> que deve ser usado pelo manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="94a56-109">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94a56-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="94a56-110">Child Elements</span></span>  

 <span data-ttu-id="94a56-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="94a56-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94a56-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="94a56-112">Parent Elements</span></span>  
  
|<span data-ttu-id="94a56-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="94a56-113">Element</span></span>|<span data-ttu-id="94a56-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="94a56-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="94a56-115">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="94a56-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94a56-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="94a56-116">Remarks</span></span>  

 <span data-ttu-id="94a56-117">O `<userNameSecurityTokenHandlerRequirement>` elemento define a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> propriedade quando um <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> objeto é inicializado a partir da configuração.</span><span class="sxs-lookup"><span data-stu-id="94a56-117">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94a56-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94a56-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
