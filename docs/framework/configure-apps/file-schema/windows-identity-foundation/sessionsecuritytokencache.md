---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 697c20d1f526cb376c2430f0006349f7d8f9b2f1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257928"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="ba73e-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="ba73e-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="ba73e-102">Registra um cache de tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ba73e-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="ba73e-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ba73e-103">\<system.identityModel></span></span>  
<span data-ttu-id="ba73e-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ba73e-104">\<identityConfiguration></span></span>  
<span data-ttu-id="ba73e-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="ba73e-105">\<caches></span></span>  
<span data-ttu-id="ba73e-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="ba73e-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba73e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba73e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba73e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ba73e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ba73e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ba73e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba73e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ba73e-110">Attributes</span></span>  
  
|<span data-ttu-id="ba73e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ba73e-111">Attribute</span></span>|<span data-ttu-id="ba73e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba73e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba73e-113">tipo</span><span class="sxs-lookup"><span data-stu-id="ba73e-113">type</span></span>|<span data-ttu-id="ba73e-114">Um tipo que deriva de <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe.</span><span class="sxs-lookup"><span data-stu-id="ba73e-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba73e-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ba73e-115">Child Elements</span></span>  
 <span data-ttu-id="ba73e-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ba73e-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba73e-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ba73e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ba73e-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="ba73e-118">Element</span></span>|<span data-ttu-id="ba73e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba73e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba73e-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="ba73e-120">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="ba73e-121">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ba73e-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ba73e-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba73e-122">Example</span></span>  
 <span data-ttu-id="ba73e-123">O XML a seguir mostra a configuração de um cache personalizado para manter os tokens de segurança de sessão (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="ba73e-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="ba73e-124">A configuração é obtida a `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="ba73e-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="ba73e-125">Para obter mais informações sobre este exemplo, consulte [índice de exemplo de código do WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="ba73e-125">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba73e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba73e-126">See also</span></span>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
