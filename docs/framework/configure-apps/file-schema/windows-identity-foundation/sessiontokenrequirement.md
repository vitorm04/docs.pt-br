---
title: '&lt;sessionTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 8b729f588d2195992b231661f7bb718240141fdd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="e70ea-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="e70ea-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="e70ea-103">Fornece configuração para o <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="e70ea-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="e70ea-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="e70ea-104">\<system.identityModel></span></span>  
<span data-ttu-id="e70ea-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e70ea-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e70ea-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="e70ea-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e70ea-107">\<add></span><span class="sxs-lookup"><span data-stu-id="e70ea-107">\<add></span></span>  
<span data-ttu-id="e70ea-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="e70ea-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e70ea-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e70ea-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e70ea-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e70ea-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e70ea-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e70ea-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e70ea-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e70ea-112">Attributes</span></span>  
  
|<span data-ttu-id="e70ea-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e70ea-113">Attribute</span></span>|<span data-ttu-id="e70ea-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e70ea-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e70ea-115">tempo de vida</span><span class="sxs-lookup"><span data-stu-id="e70ea-115">lifetime</span></span>|<span data-ttu-id="e70ea-116">Especifica o tempo de vida de tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="e70ea-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e70ea-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e70ea-117">Child Elements</span></span>  
 <span data-ttu-id="e70ea-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e70ea-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e70ea-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e70ea-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e70ea-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="e70ea-120">Element</span></span>|<span data-ttu-id="e70ea-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="e70ea-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e70ea-122">\<add></span><span class="sxs-lookup"><span data-stu-id="e70ea-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="e70ea-123">Adiciona o manipulador de token de segurança especificados na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="e70ea-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e70ea-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e70ea-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
