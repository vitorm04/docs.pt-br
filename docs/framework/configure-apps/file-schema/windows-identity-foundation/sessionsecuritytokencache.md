---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 024375cb114bb080c576ea033e5588526350ecdf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510085"
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="43b55-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="43b55-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="43b55-103">Registra um cache de tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="43b55-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="43b55-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="43b55-104">\<system.identityModel></span></span>  
<span data-ttu-id="43b55-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="43b55-105">\<identityConfiguration></span></span>  
<span data-ttu-id="43b55-106">\<caches></span><span class="sxs-lookup"><span data-stu-id="43b55-106">\<caches></span></span>  
<span data-ttu-id="43b55-107">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="43b55-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43b55-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43b55-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43b55-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="43b55-109">Attributes and Elements</span></span>  
 <span data-ttu-id="43b55-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="43b55-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43b55-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="43b55-111">Attributes</span></span>  
  
|<span data-ttu-id="43b55-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="43b55-112">Attribute</span></span>|<span data-ttu-id="43b55-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="43b55-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43b55-114">tipo</span><span class="sxs-lookup"><span data-stu-id="43b55-114">type</span></span>|<span data-ttu-id="43b55-115">Um tipo que deriva de <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe.</span><span class="sxs-lookup"><span data-stu-id="43b55-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43b55-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="43b55-116">Child Elements</span></span>  
 <span data-ttu-id="43b55-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="43b55-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43b55-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="43b55-118">Parent Elements</span></span>  
  
|<span data-ttu-id="43b55-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="43b55-119">Element</span></span>|<span data-ttu-id="43b55-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="43b55-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43b55-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="43b55-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="43b55-122">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="43b55-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43b55-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43b55-123">Example</span></span>  
 <span data-ttu-id="43b55-124">O XML a seguir mostra a configuração de um cache personalizado para manter os tokens de segurança de sessão (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="43b55-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="43b55-125">A configuração é obtida a `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="43b55-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="43b55-126">Para obter mais informações sobre este exemplo, consulte [índice de exemplo de código do WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="43b55-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43b55-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43b55-127">See also</span></span>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
