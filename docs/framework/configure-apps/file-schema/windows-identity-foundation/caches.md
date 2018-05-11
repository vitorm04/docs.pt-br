---
title: '&lt;Caches&gt;'
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a9766b826eb7a708b4b4e99b6bd984f9fc76812
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcachesgt"></a><span data-ttu-id="cdce9-102">&lt;Caches&gt;</span><span class="sxs-lookup"><span data-stu-id="cdce9-102">&lt;caches&gt;</span></span>
<span data-ttu-id="cdce9-103">Registra os caches usados para detecção de reprodução de token e tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="cdce9-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="cdce9-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="cdce9-104">\<system.identityModel></span></span>  
<span data-ttu-id="cdce9-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="cdce9-105">\<identityConfiguration></span></span>  
<span data-ttu-id="cdce9-106">\<armazena em cache ></span><span class="sxs-lookup"><span data-stu-id="cdce9-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdce9-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdce9-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdce9-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cdce9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cdce9-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cdce9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdce9-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="cdce9-110">Attributes</span></span>  
 <span data-ttu-id="cdce9-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="cdce9-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cdce9-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cdce9-112">Child Elements</span></span>  
  
|<span data-ttu-id="cdce9-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="cdce9-113">Element</span></span>|<span data-ttu-id="cdce9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdce9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdce9-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="cdce9-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="cdce9-116">Registra um cache de tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="cdce9-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="cdce9-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="cdce9-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="cdce9-118">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="cdce9-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdce9-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cdce9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cdce9-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="cdce9-120">Element</span></span>|<span data-ttu-id="cdce9-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdce9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdce9-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="cdce9-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="cdce9-123">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="cdce9-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="cdce9-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="cdce9-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="cdce9-125">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="cdce9-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdce9-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="cdce9-126">Remarks</span></span>  
 <span data-ttu-id="cdce9-127">Um `<caches>` elemento pode ser especificado no nível de serviço sob a `<identityConfiguration>` elemento ou em nível de coleção de manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="cdce9-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="cdce9-128">As configurações em uma coleção de manipulador de token substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="cdce9-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="cdce9-129">O `<caches>` elemento é representado pela <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> classe.</span><span class="sxs-lookup"><span data-stu-id="cdce9-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="cdce9-130">Os caches configurados são representados pelo <xref:System.IdentityModel.Configuration.IdentityModelCaches> classe.</span><span class="sxs-lookup"><span data-stu-id="cdce9-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdce9-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cdce9-131">Example</span></span>  
 <span data-ttu-id="cdce9-132">O XML a seguir mostra a configuração de um cache personalizado para manter a sessão de tokens de segurança (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="cdce9-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="cdce9-133">A configuração é obtida o `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="cdce9-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
