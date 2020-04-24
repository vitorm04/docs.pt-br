---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: a0db10ceb75a470dbf799d717b2059355dd104bb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646073"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="2917a-101">\<sessãoSegurançacache></span><span class="sxs-lookup"><span data-stu-id="2917a-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="2917a-102">Registra um cache para tokens de sessão com um serviço ou uma coleção de manipuladores de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="2917a-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="2917a-103">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2917a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2917a-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="2917a-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="2917a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="2917a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="2917a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span><span class="sxs-lookup"><span data-stu-id="2917a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="2917a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessãoSecurityTokenCache>**</span><span class="sxs-lookup"><span data-stu-id="2917a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2917a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2917a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2917a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2917a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2917a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2917a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2917a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="2917a-111">Attributes</span></span>  
  
|<span data-ttu-id="2917a-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="2917a-112">Attribute</span></span>|<span data-ttu-id="2917a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2917a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2917a-114">type</span><span class="sxs-lookup"><span data-stu-id="2917a-114">type</span></span>|<span data-ttu-id="2917a-115">Um tipo que deriva <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> da classe.</span><span class="sxs-lookup"><span data-stu-id="2917a-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2917a-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2917a-116">Child Elements</span></span>  
 <span data-ttu-id="2917a-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2917a-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2917a-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2917a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2917a-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="2917a-119">Element</span></span>|<span data-ttu-id="2917a-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="2917a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2917a-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="2917a-121">\<caches></span></span>](caches.md)|<span data-ttu-id="2917a-122">Registra os caches usados por um serviço ou uma coleção de manipuladores de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="2917a-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2917a-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2917a-123">Example</span></span>  
 <span data-ttu-id="2917a-124">O XML a seguir mostra a configuração de um<xref:System.IdentityModel.Tokens.SessionSecurityToken>cache personalizado para a manutenção de tokens de segurança de sessão ().</span><span class="sxs-lookup"><span data-stu-id="2917a-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="2917a-125">A configuração é `ClaimsAwareWebFarm` retirada da amostra.</span><span class="sxs-lookup"><span data-stu-id="2917a-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="2917a-126">Para obter mais informações sobre esta amostra, consulte [WIF Code Sample Index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span><span class="sxs-lookup"><span data-stu-id="2917a-126">For more information about this sample, see [WIF Code Sample Index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2917a-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="2917a-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
