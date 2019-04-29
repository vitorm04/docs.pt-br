---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 0c575e02862884e8f7ecf062138c36fe731f8e19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793764"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="e42c9-101">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="e42c9-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="e42c9-102">Fornece configuração para o <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="e42c9-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="e42c9-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e42c9-103">\<system.identityModel></span></span>  
<span data-ttu-id="e42c9-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e42c9-104">\<identityConfiguration></span></span>  
<span data-ttu-id="e42c9-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e42c9-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e42c9-106">\<add></span><span class="sxs-lookup"><span data-stu-id="e42c9-106">\<add></span></span>  
<span data-ttu-id="e42c9-107">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="e42c9-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e42c9-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e42c9-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e42c9-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e42c9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e42c9-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e42c9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e42c9-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e42c9-111">Attributes</span></span>  
  
|<span data-ttu-id="e42c9-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="e42c9-112">Attribute</span></span>|<span data-ttu-id="e42c9-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e42c9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e42c9-114">tempo de vida</span><span class="sxs-lookup"><span data-stu-id="e42c9-114">lifetime</span></span>|<span data-ttu-id="e42c9-115">Especifica o tempo de vida de tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="e42c9-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e42c9-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e42c9-116">Child Elements</span></span>  
 <span data-ttu-id="e42c9-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e42c9-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e42c9-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e42c9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e42c9-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="e42c9-119">Element</span></span>|<span data-ttu-id="e42c9-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e42c9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e42c9-121">\<add></span><span class="sxs-lookup"><span data-stu-id="e42c9-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="e42c9-122">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="e42c9-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e42c9-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e42c9-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
