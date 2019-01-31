---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 0c575e02862884e8f7ecf062138c36fe731f8e19
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271896"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="a571d-101">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="a571d-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="a571d-102">Fornece configuração para o <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="a571d-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="a571d-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a571d-103">\<system.identityModel></span></span>  
<span data-ttu-id="a571d-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a571d-104">\<identityConfiguration></span></span>  
<span data-ttu-id="a571d-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="a571d-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="a571d-106">\<add></span><span class="sxs-lookup"><span data-stu-id="a571d-106">\<add></span></span>  
<span data-ttu-id="a571d-107">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="a571d-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a571d-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a571d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a571d-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a571d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a571d-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a571d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a571d-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a571d-111">Attributes</span></span>  
  
|<span data-ttu-id="a571d-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="a571d-112">Attribute</span></span>|<span data-ttu-id="a571d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a571d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a571d-114">tempo de vida</span><span class="sxs-lookup"><span data-stu-id="a571d-114">lifetime</span></span>|<span data-ttu-id="a571d-115">Especifica o tempo de vida de tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="a571d-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a571d-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a571d-116">Child Elements</span></span>  
 <span data-ttu-id="a571d-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a571d-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a571d-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a571d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a571d-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="a571d-119">Element</span></span>|<span data-ttu-id="a571d-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="a571d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a571d-121">\<add></span><span class="sxs-lookup"><span data-stu-id="a571d-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="a571d-122">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="a571d-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a571d-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a571d-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
