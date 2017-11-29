---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 4ffe9764eb730be4859fb66ae2f0cc845c9404e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a><span data-ttu-id="954ca-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="954ca-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="954ca-103">Fornece configuração para o <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="954ca-103">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="954ca-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="954ca-104">\<system.identityModel></span></span>  
<span data-ttu-id="954ca-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="954ca-105">\<identityConfiguration></span></span>  
<span data-ttu-id="954ca-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="954ca-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="954ca-107">\<add></span><span class="sxs-lookup"><span data-stu-id="954ca-107">\<add></span></span>  
<span data-ttu-id="954ca-108">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="954ca-108">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="954ca-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="954ca-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="954ca-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="954ca-110">Attributes and Elements</span></span>  
 <span data-ttu-id="954ca-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="954ca-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="954ca-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="954ca-112">Attributes</span></span>  
  
|<span data-ttu-id="954ca-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="954ca-113">Attribute</span></span>|<span data-ttu-id="954ca-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="954ca-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="954ca-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="954ca-115">membershipProviderName</span></span>|<span data-ttu-id="954ca-116">Especifica o <xref:System.Web.Security.MembershipProvider> que deve ser usado pelo manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="954ca-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="954ca-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="954ca-117">Child Elements</span></span>  
 <span data-ttu-id="954ca-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="954ca-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="954ca-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="954ca-119">Parent Elements</span></span>  
  
|<span data-ttu-id="954ca-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="954ca-120">Element</span></span>|<span data-ttu-id="954ca-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="954ca-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="954ca-122">\<add></span><span class="sxs-lookup"><span data-stu-id="954ca-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="954ca-123">Adiciona o manipulador de token de segurança especificados na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="954ca-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="954ca-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="954ca-124">Remarks</span></span>  
 <span data-ttu-id="954ca-125">O `<userNameSecurityTokenHandlerRequirement>` elemento define o <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> propriedade quando um <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> é inicializar o objeto de configuração.</span><span class="sxs-lookup"><span data-stu-id="954ca-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="954ca-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="954ca-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
