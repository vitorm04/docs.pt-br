---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252155"
---
# <a name="caches"></a><span data-ttu-id="c455d-101">\<caches></span><span class="sxs-lookup"><span data-stu-id="c455d-101">\<caches></span></span>
<span data-ttu-id="c455d-102">Registra os caches usados para tokens de sessão e detecção de reprodução de token.</span><span class="sxs-lookup"><span data-stu-id="c455d-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
<span data-ttu-id="c455d-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c455d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c455d-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c455d-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c455d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c455d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c455d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<caches >**</span><span class="sxs-lookup"><span data-stu-id="c455d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c455d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c455d-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c455d-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c455d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c455d-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c455d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c455d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c455d-110">Attributes</span></span>  
 <span data-ttu-id="c455d-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c455d-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c455d-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c455d-112">Child Elements</span></span>  
  
|<span data-ttu-id="c455d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c455d-113">Element</span></span>|<span data-ttu-id="c455d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c455d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c455d-115">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="c455d-115">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="c455d-116">Registra um cache para tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="c455d-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="c455d-117">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="c455d-117">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="c455d-118">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="c455d-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c455d-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c455d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c455d-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="c455d-120">Element</span></span>|<span data-ttu-id="c455d-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="c455d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c455d-122">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c455d-122">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="c455d-123">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="c455d-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="c455d-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="c455d-124">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="c455d-125">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="c455d-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c455d-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="c455d-126">Remarks</span></span>  
 <span data-ttu-id="c455d-127">Um `<caches>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou no nível de coleção do manipulador de token de `<securityTokenHandlerConfiguration>` segurança sob o elemento.</span><span class="sxs-lookup"><span data-stu-id="c455d-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="c455d-128">As configurações em uma coleção de manipulador de tokens substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="c455d-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="c455d-129">O `<caches>` elemento é representado <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> pela classe.</span><span class="sxs-lookup"><span data-stu-id="c455d-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="c455d-130">Os caches configurados são representados pela <xref:System.IdentityModel.Configuration.IdentityModelCaches> classe.</span><span class="sxs-lookup"><span data-stu-id="c455d-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c455d-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c455d-131">Example</span></span>  
 <span data-ttu-id="c455d-132">O XML a seguir mostra a configuração de um cache personalizado para manter os tokens<xref:System.IdentityModel.Tokens.SessionSecurityToken>de segurança de sessão ().</span><span class="sxs-lookup"><span data-stu-id="c455d-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="c455d-133">A configuração é obtida do `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="c455d-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
