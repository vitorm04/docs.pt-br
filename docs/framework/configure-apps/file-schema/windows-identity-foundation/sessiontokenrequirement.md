---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 254d34149892abeaf31b9227f7567eb0a66ec0b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943671"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="bfd90-101">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="bfd90-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="bfd90-102">Fornece a configuração para <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> a classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="bfd90-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="bfd90-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="bfd90-103">\<system.identityModel></span></span>  
<span data-ttu-id="bfd90-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="bfd90-104">\<identityConfiguration></span></span>  
<span data-ttu-id="bfd90-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="bfd90-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="bfd90-106">\<add></span><span class="sxs-lookup"><span data-stu-id="bfd90-106">\<add></span></span>  
<span data-ttu-id="bfd90-107">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="bfd90-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfd90-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfd90-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfd90-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bfd90-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bfd90-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bfd90-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfd90-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="bfd90-111">Attributes</span></span>  
  
|<span data-ttu-id="bfd90-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="bfd90-112">Attribute</span></span>|<span data-ttu-id="bfd90-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfd90-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bfd90-114">tempo de vida</span><span class="sxs-lookup"><span data-stu-id="bfd90-114">lifetime</span></span>|<span data-ttu-id="bfd90-115">Especifica o tempo de vida dos tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="bfd90-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfd90-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bfd90-116">Child Elements</span></span>  
 <span data-ttu-id="bfd90-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="bfd90-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfd90-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bfd90-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bfd90-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="bfd90-119">Element</span></span>|<span data-ttu-id="bfd90-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfd90-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bfd90-121">\<add></span><span class="sxs-lookup"><span data-stu-id="bfd90-121">\<add></span></span>](add.md)|<span data-ttu-id="bfd90-122">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="bfd90-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bfd90-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bfd90-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
