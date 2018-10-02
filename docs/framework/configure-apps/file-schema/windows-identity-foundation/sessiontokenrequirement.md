---
title: '&lt;sessionTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 4d5d2348f04ace7596a3a513c5106ea612dc17b7
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48037159"
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="793ea-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="793ea-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="793ea-103">Fornece configuração para o <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="793ea-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="793ea-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="793ea-104">\<system.identityModel></span></span>  
<span data-ttu-id="793ea-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="793ea-105">\<identityConfiguration></span></span>  
<span data-ttu-id="793ea-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="793ea-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="793ea-107">\<add></span><span class="sxs-lookup"><span data-stu-id="793ea-107">\<add></span></span>  
<span data-ttu-id="793ea-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="793ea-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="793ea-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="793ea-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="793ea-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="793ea-110">Attributes and Elements</span></span>  
 <span data-ttu-id="793ea-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="793ea-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="793ea-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="793ea-112">Attributes</span></span>  
  
|<span data-ttu-id="793ea-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="793ea-113">Attribute</span></span>|<span data-ttu-id="793ea-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="793ea-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="793ea-115">tempo de vida</span><span class="sxs-lookup"><span data-stu-id="793ea-115">lifetime</span></span>|<span data-ttu-id="793ea-116">Especifica o tempo de vida de tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="793ea-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="793ea-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="793ea-117">Child Elements</span></span>  
 <span data-ttu-id="793ea-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="793ea-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="793ea-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="793ea-119">Parent Elements</span></span>  
  
|<span data-ttu-id="793ea-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="793ea-120">Element</span></span>|<span data-ttu-id="793ea-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="793ea-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="793ea-122">\<add></span><span class="sxs-lookup"><span data-stu-id="793ea-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="793ea-123">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="793ea-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="793ea-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="793ea-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
