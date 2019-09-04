---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: e949b16f76f20191b84bbbbb6e8b019d913316f0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251840"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="ff3de-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="ff3de-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="ff3de-102">Registra um cache para tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ff3de-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="ff3de-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff3de-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ff3de-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ff3de-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ff3de-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ff3de-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ff3de-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<caches >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="ff3de-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="ff3de-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> sessionSecurityTokenCache**</span><span class="sxs-lookup"><span data-stu-id="ff3de-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff3de-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff3de-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff3de-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ff3de-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ff3de-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ff3de-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff3de-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ff3de-111">Attributes</span></span>  
  
|<span data-ttu-id="ff3de-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="ff3de-112">Attribute</span></span>|<span data-ttu-id="ff3de-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff3de-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff3de-114">tipo</span><span class="sxs-lookup"><span data-stu-id="ff3de-114">type</span></span>|<span data-ttu-id="ff3de-115">Um tipo que deriva da <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe.</span><span class="sxs-lookup"><span data-stu-id="ff3de-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff3de-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ff3de-116">Child Elements</span></span>  
 <span data-ttu-id="ff3de-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ff3de-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff3de-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ff3de-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ff3de-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff3de-119">Element</span></span>|<span data-ttu-id="ff3de-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff3de-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff3de-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="ff3de-121">\<caches></span></span>](caches.md)|<span data-ttu-id="ff3de-122">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ff3de-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ff3de-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff3de-123">Example</span></span>  
 <span data-ttu-id="ff3de-124">O XML a seguir mostra a configuração de um cache personalizado para manter os tokens<xref:System.IdentityModel.Tokens.SessionSecurityToken>de segurança de sessão ().</span><span class="sxs-lookup"><span data-stu-id="ff3de-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="ff3de-125">A configuração é obtida do `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="ff3de-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="ff3de-126">Para obter mais informações sobre este exemplo, consulte o [índice de exemplo de código do WIF](../../../security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="ff3de-126">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff3de-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff3de-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
