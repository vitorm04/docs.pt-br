---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 18769794da8528f085c567264827db5aa6b214f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790449"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="43496-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="43496-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="43496-102">Fornece configuração para o <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="43496-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="43496-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="43496-103">\<system.identityModel></span></span>  
<span data-ttu-id="43496-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="43496-104">\<identityConfiguration></span></span>  
<span data-ttu-id="43496-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="43496-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="43496-106">\<add></span><span class="sxs-lookup"><span data-stu-id="43496-106">\<add></span></span>  
<span data-ttu-id="43496-107">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="43496-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43496-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43496-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43496-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="43496-109">Attributes and Elements</span></span>  
 <span data-ttu-id="43496-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="43496-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43496-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="43496-111">Attributes</span></span>  
  
|<span data-ttu-id="43496-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="43496-112">Attribute</span></span>|<span data-ttu-id="43496-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="43496-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43496-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="43496-114">membershipProviderName</span></span>|<span data-ttu-id="43496-115">Especifica o <xref:System.Web.Security.MembershipProvider> que deve ser usado pelo manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="43496-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43496-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="43496-116">Child Elements</span></span>  
 <span data-ttu-id="43496-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="43496-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43496-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="43496-118">Parent Elements</span></span>  
  
|<span data-ttu-id="43496-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="43496-119">Element</span></span>|<span data-ttu-id="43496-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="43496-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43496-121">\<add></span><span class="sxs-lookup"><span data-stu-id="43496-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="43496-122">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="43496-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43496-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="43496-123">Remarks</span></span>  
 <span data-ttu-id="43496-124">O `<userNameSecurityTokenHandlerRequirement>` conjuntos de elemento de <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> propriedade quando um <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> objeto é inicializado da configuração.</span><span class="sxs-lookup"><span data-stu-id="43496-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43496-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43496-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
