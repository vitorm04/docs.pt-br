---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 5ad75ae18772d6e7c724f2cbf40c1e3083d5c345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941972"
---
# <a name="caches"></a><span data-ttu-id="3c1aa-101">\<caches></span><span class="sxs-lookup"><span data-stu-id="3c1aa-101">\<caches></span></span>
<span data-ttu-id="3c1aa-102">Registra os caches usados para tokens de sessão e detecção de reprodução de token.</span><span class="sxs-lookup"><span data-stu-id="3c1aa-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="3c1aa-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3c1aa-103">\<system.identityModel></span></span>  
<span data-ttu-id="3c1aa-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3c1aa-104">\<identityConfiguration></span></span>  
<span data-ttu-id="3c1aa-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="3c1aa-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c1aa-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c1aa-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c1aa-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3c1aa-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3c1aa-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3c1aa-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c1aa-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="3c1aa-109">Attributes</span></span>  
 <span data-ttu-id="3c1aa-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3c1aa-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3c1aa-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3c1aa-111">Child Elements</span></span>  
  
|<span data-ttu-id="3c1aa-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3c1aa-112">Element</span></span>|<span data-ttu-id="3c1aa-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c1aa-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c1aa-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="3c1aa-114">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="3c1aa-115">Registra um cache para tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="3c1aa-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="3c1aa-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="3c1aa-116">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="3c1aa-117">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="3c1aa-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c1aa-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3c1aa-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3c1aa-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="3c1aa-119">Element</span></span>|<span data-ttu-id="3c1aa-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c1aa-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c1aa-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3c1aa-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="3c1aa-122">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="3c1aa-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="3c1aa-123">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="3c1aa-123">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="3c1aa-124">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="3c1aa-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c1aa-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c1aa-125">Remarks</span></span>  
 <span data-ttu-id="3c1aa-126">Um `<caches>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou no nível de coleção do manipulador de token de `<securityTokenHandlerConfiguration>` segurança sob o elemento.</span><span class="sxs-lookup"><span data-stu-id="3c1aa-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="3c1aa-127">As configurações em uma coleção de manipulador de tokens substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="3c1aa-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="3c1aa-128">O `<caches>` elemento é representado <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> pela classe.</span><span class="sxs-lookup"><span data-stu-id="3c1aa-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="3c1aa-129">Os caches configurados são representados pela <xref:System.IdentityModel.Configuration.IdentityModelCaches> classe.</span><span class="sxs-lookup"><span data-stu-id="3c1aa-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c1aa-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c1aa-130">Example</span></span>  
 <span data-ttu-id="3c1aa-131">O XML a seguir mostra a configuração de um cache personalizado para manter os tokens<xref:System.IdentityModel.Tokens.SessionSecurityToken>de segurança de sessão ().</span><span class="sxs-lookup"><span data-stu-id="3c1aa-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="3c1aa-132">A configuração é obtida do `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="3c1aa-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
