---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252155"
---
# \<caches>
<span data-ttu-id="b49d3-101">Registra os caches usados para tokens de sessão e detecção de reprodução de token.</span><span class="sxs-lookup"><span data-stu-id="b49d3-101">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="b49d3-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b49d3-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b49d3-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b49d3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b49d3-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b49d3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b49d3-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="b49d3-105">Attributes</span></span>  
 <span data-ttu-id="b49d3-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b49d3-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b49d3-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b49d3-107">Child Elements</span></span>  
  
|<span data-ttu-id="b49d3-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="b49d3-108">Element</span></span>|<span data-ttu-id="b49d3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b49d3-109">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="b49d3-110">Registra um cache para tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b49d3-110">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="b49d3-111">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b49d3-111">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b49d3-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b49d3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="b49d3-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b49d3-113">Element</span></span>|<span data-ttu-id="b49d3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b49d3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="b49d3-115">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="b49d3-115">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="b49d3-116">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b49d3-116">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b49d3-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="b49d3-117">Remarks</span></span>  
 <span data-ttu-id="b49d3-118">Um `<caches>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou no nível de coleção do manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="b49d3-118">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="b49d3-119">As configurações em uma coleção de manipulador de tokens substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="b49d3-119">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="b49d3-120">O `<caches>` elemento é representado pela <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> classe.</span><span class="sxs-lookup"><span data-stu-id="b49d3-120">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="b49d3-121">Os caches configurados são representados pela <xref:System.IdentityModel.Configuration.IdentityModelCaches> classe.</span><span class="sxs-lookup"><span data-stu-id="b49d3-121">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b49d3-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b49d3-122">Example</span></span>  
 <span data-ttu-id="b49d3-123">O XML a seguir mostra a configuração de um cache personalizado para manter os tokens de segurança de sessão ( <xref:System.IdentityModel.Tokens.SessionSecurityToken> ).</span><span class="sxs-lookup"><span data-stu-id="b49d3-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="b49d3-124">A configuração é obtida do `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="b49d3-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
