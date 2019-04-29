---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: b1d04280ef993297102d446ba5a7db54e8404dd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750781"
---
# <a name="caches"></a><span data-ttu-id="13dc5-101">\<caches></span><span class="sxs-lookup"><span data-stu-id="13dc5-101">\<caches></span></span>
<span data-ttu-id="13dc5-102">Registra os caches usados para detecção de reprodução de token e tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="13dc5-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="13dc5-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="13dc5-103">\<system.identityModel></span></span>  
<span data-ttu-id="13dc5-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="13dc5-104">\<identityConfiguration></span></span>  
<span data-ttu-id="13dc5-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="13dc5-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13dc5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13dc5-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13dc5-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13dc5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="13dc5-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="13dc5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13dc5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="13dc5-109">Attributes</span></span>  
 <span data-ttu-id="13dc5-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="13dc5-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="13dc5-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="13dc5-111">Child Elements</span></span>  
  
|<span data-ttu-id="13dc5-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="13dc5-112">Element</span></span>|<span data-ttu-id="13dc5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="13dc5-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13dc5-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="13dc5-114">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="13dc5-115">Registra um cache de tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="13dc5-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="13dc5-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="13dc5-116">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="13dc5-117">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="13dc5-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13dc5-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="13dc5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="13dc5-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="13dc5-119">Element</span></span>|<span data-ttu-id="13dc5-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="13dc5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13dc5-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="13dc5-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="13dc5-122">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="13dc5-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="13dc5-123">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="13dc5-123">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="13dc5-124">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="13dc5-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13dc5-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="13dc5-125">Remarks</span></span>  
 <span data-ttu-id="13dc5-126">Um `<caches>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou em nível de conjunto de manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="13dc5-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="13dc5-127">As configurações em uma coleção de manipulador de token substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="13dc5-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="13dc5-128">O `<caches>` elemento é representado pelo <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> classe.</span><span class="sxs-lookup"><span data-stu-id="13dc5-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="13dc5-129">Os caches configurados são representados pelo <xref:System.IdentityModel.Configuration.IdentityModelCaches> classe.</span><span class="sxs-lookup"><span data-stu-id="13dc5-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13dc5-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13dc5-130">Example</span></span>  
 <span data-ttu-id="13dc5-131">O XML a seguir mostra a configuração de um cache personalizado para manter os tokens de segurança de sessão (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="13dc5-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="13dc5-132">A configuração é obtida a `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="13dc5-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
