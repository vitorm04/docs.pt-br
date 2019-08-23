---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 9be3bf980c3756678d26d8652271113d4daaba43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943705"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="83c9a-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="83c9a-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="83c9a-102">Registra um cache para tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="83c9a-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="83c9a-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="83c9a-103">\<system.identityModel></span></span>  
<span data-ttu-id="83c9a-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="83c9a-104">\<identityConfiguration></span></span>  
<span data-ttu-id="83c9a-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="83c9a-105">\<caches></span></span>  
<span data-ttu-id="83c9a-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="83c9a-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83c9a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83c9a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83c9a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="83c9a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="83c9a-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="83c9a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83c9a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="83c9a-110">Attributes</span></span>  
  
|<span data-ttu-id="83c9a-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="83c9a-111">Attribute</span></span>|<span data-ttu-id="83c9a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="83c9a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83c9a-113">tipo</span><span class="sxs-lookup"><span data-stu-id="83c9a-113">type</span></span>|<span data-ttu-id="83c9a-114">Um tipo que deriva da <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe.</span><span class="sxs-lookup"><span data-stu-id="83c9a-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83c9a-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="83c9a-115">Child Elements</span></span>  
 <span data-ttu-id="83c9a-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="83c9a-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83c9a-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="83c9a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="83c9a-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="83c9a-118">Element</span></span>|<span data-ttu-id="83c9a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="83c9a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83c9a-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="83c9a-120">\<caches></span></span>](caches.md)|<span data-ttu-id="83c9a-121">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="83c9a-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="83c9a-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83c9a-122">Example</span></span>  
 <span data-ttu-id="83c9a-123">O XML a seguir mostra a configuração de um cache personalizado para manter os tokens<xref:System.IdentityModel.Tokens.SessionSecurityToken>de segurança de sessão ().</span><span class="sxs-lookup"><span data-stu-id="83c9a-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="83c9a-124">A configuração é obtida do `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="83c9a-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="83c9a-125">Para obter mais informações sobre este exemplo, consulte o [índice de exemplo de código do WIF](../../../security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="83c9a-125">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="83c9a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83c9a-126">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
