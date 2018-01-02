---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 9f4b87d6c620a07ee831888086bdab75a689875e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="69d7f-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="69d7f-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="69d7f-103">Registra um cache de tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="69d7f-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="69d7f-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="69d7f-104">\<system.identityModel></span></span>  
<span data-ttu-id="69d7f-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="69d7f-105">\<identityConfiguration></span></span>  
<span data-ttu-id="69d7f-106">\<armazena em cache ></span><span class="sxs-lookup"><span data-stu-id="69d7f-106">\<caches></span></span>  
<span data-ttu-id="69d7f-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="69d7f-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69d7f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69d7f-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69d7f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="69d7f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="69d7f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="69d7f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69d7f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="69d7f-111">Attributes</span></span>  
  
|<span data-ttu-id="69d7f-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="69d7f-112">Attribute</span></span>|<span data-ttu-id="69d7f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="69d7f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69d7f-114">tipo</span><span class="sxs-lookup"><span data-stu-id="69d7f-114">type</span></span>|<span data-ttu-id="69d7f-115">Um tipo que deriva de <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe.</span><span class="sxs-lookup"><span data-stu-id="69d7f-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69d7f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="69d7f-116">Child Elements</span></span>  
 <span data-ttu-id="69d7f-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="69d7f-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69d7f-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="69d7f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="69d7f-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="69d7f-119">Element</span></span>|<span data-ttu-id="69d7f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="69d7f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69d7f-121">\<armazena em cache ></span><span class="sxs-lookup"><span data-stu-id="69d7f-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="69d7f-122">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="69d7f-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="69d7f-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69d7f-123">Example</span></span>  
 <span data-ttu-id="69d7f-124">O XML a seguir mostra a configuração de um cache personalizado para manter a sessão de tokens de segurança (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="69d7f-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="69d7f-125">A configuração é obtida o `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="69d7f-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="69d7f-126">Para obter mais informações sobre esse exemplo, consulte [índice de exemplo de código do WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="69d7f-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69d7f-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69d7f-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
