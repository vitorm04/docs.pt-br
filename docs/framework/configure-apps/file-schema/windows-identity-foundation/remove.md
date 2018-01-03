---
title: '&lt;remove&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 15c2561487eecb44cf3542768de0a77d1dd6713d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt"></a><span data-ttu-id="3e6dd-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="3e6dd-102">&lt;remove&gt;</span></span>
<span data-ttu-id="3e6dd-103">Remove o manipulador de token de segurança especificado da coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="3e6dd-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="3e6dd-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="3e6dd-104">\<system.identityModel></span></span>  
<span data-ttu-id="3e6dd-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3e6dd-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3e6dd-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="3e6dd-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3e6dd-107">\<Remover ></span><span class="sxs-lookup"><span data-stu-id="3e6dd-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e6dd-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e6dd-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e6dd-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3e6dd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3e6dd-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3e6dd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e6dd-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e6dd-111">Attributes</span></span>  
  
|<span data-ttu-id="3e6dd-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="3e6dd-112">Attribute</span></span>|<span data-ttu-id="3e6dd-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e6dd-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e6dd-114">tipo</span><span class="sxs-lookup"><span data-stu-id="3e6dd-114">type</span></span>|<span data-ttu-id="3e6dd-115">O nome do tipo CLR do manipulador de token a ser removido.</span><span class="sxs-lookup"><span data-stu-id="3e6dd-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="3e6dd-116">Para obter mais informações sobre como especificar o `type` de atributo, consulte [referências de tipo personalizado](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="3e6dd-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="3e6dd-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3e6dd-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e6dd-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e6dd-118">Child Elements</span></span>  
 <span data-ttu-id="3e6dd-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3e6dd-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e6dd-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e6dd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3e6dd-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e6dd-121">Element</span></span>|<span data-ttu-id="3e6dd-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e6dd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e6dd-123">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="3e6dd-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="3e6dd-124">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3e6dd-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3e6dd-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e6dd-125">Example</span></span>  
 <span data-ttu-id="3e6dd-126">O XML a seguir mostra o uso do `<add>` e `<remove>` elementos para substituir o manipulador de token de sessão padrão com um manipulador de token de sessão personalizadas.</span><span class="sxs-lookup"><span data-stu-id="3e6dd-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="3e6dd-127">O XML é obtido o `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="3e6dd-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
