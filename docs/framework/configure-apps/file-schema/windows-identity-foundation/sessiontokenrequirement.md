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
ms.workload: dotnet
ms.openlocfilehash: 5a141dd83cb7ef1271906871097eb68da174d22f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="6f214-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="6f214-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="6f214-103">Fornece configuração para o <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="6f214-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="6f214-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="6f214-104">\<system.identityModel></span></span>  
<span data-ttu-id="6f214-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6f214-105">\<identityConfiguration></span></span>  
<span data-ttu-id="6f214-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="6f214-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="6f214-107">\<add></span><span class="sxs-lookup"><span data-stu-id="6f214-107">\<add></span></span>  
<span data-ttu-id="6f214-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="6f214-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f214-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f214-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f214-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6f214-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6f214-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6f214-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f214-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="6f214-112">Attributes</span></span>  
  
|<span data-ttu-id="6f214-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="6f214-113">Attribute</span></span>|<span data-ttu-id="6f214-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f214-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f214-115">tempo de vida</span><span class="sxs-lookup"><span data-stu-id="6f214-115">lifetime</span></span>|<span data-ttu-id="6f214-116">Especifica o tempo de vida de tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="6f214-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f214-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6f214-117">Child Elements</span></span>  
 <span data-ttu-id="6f214-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6f214-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f214-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6f214-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6f214-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="6f214-120">Element</span></span>|<span data-ttu-id="6f214-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f214-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f214-122">\<add></span><span class="sxs-lookup"><span data-stu-id="6f214-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="6f214-123">Adiciona o manipulador de token de segurança especificados na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="6f214-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6f214-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f214-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
