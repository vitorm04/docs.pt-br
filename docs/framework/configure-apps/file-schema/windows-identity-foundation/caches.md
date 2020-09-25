---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 791c5be8aa48db2b17a42a216ad2bf5e7b5a4bc1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189871"
---
# \<caches>

<span data-ttu-id="02402-101">Registra os caches usados para tokens de sessão e detecção de reprodução de token.</span><span class="sxs-lookup"><span data-stu-id="02402-101">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="02402-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02402-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02402-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="02402-103">Attributes and Elements</span></span>  

 <span data-ttu-id="02402-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="02402-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02402-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="02402-105">Attributes</span></span>  

 <span data-ttu-id="02402-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="02402-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02402-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="02402-107">Child Elements</span></span>  
  
|<span data-ttu-id="02402-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="02402-108">Element</span></span>|<span data-ttu-id="02402-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="02402-109">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="02402-110">Registra um cache para tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="02402-110">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="02402-111">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="02402-111">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02402-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="02402-112">Parent Elements</span></span>  
  
|<span data-ttu-id="02402-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="02402-113">Element</span></span>|<span data-ttu-id="02402-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="02402-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="02402-115">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="02402-115">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="02402-116">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="02402-116">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02402-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="02402-117">Remarks</span></span>  

 <span data-ttu-id="02402-118">Um `<caches>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou no nível de coleção do manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="02402-118">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="02402-119">As configurações em uma coleção de manipulador de tokens substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="02402-119">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="02402-120">O `<caches>` elemento é representado pela <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> classe.</span><span class="sxs-lookup"><span data-stu-id="02402-120">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="02402-121">Os caches configurados são representados pela <xref:System.IdentityModel.Configuration.IdentityModelCaches> classe.</span><span class="sxs-lookup"><span data-stu-id="02402-121">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02402-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02402-122">Example</span></span>  

 <span data-ttu-id="02402-123">O XML a seguir mostra a configuração de um cache personalizado para manter os tokens de segurança de sessão ( <xref:System.IdentityModel.Tokens.SessionSecurityToken> ).</span><span class="sxs-lookup"><span data-stu-id="02402-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="02402-124">A configuração é obtida do `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="02402-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
