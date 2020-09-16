---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 4169fe307e9ef7c391500a2292fcc247f435caa9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555881"
---
# \<sessionSecurityTokenCache>
<span data-ttu-id="0b4ca-101">Registra um cache para tokens de sessão com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="0b4ca-101">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**  
  
## <a name="syntax"></a><span data-ttu-id="0b4ca-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b4ca-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b4ca-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0b4ca-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0b4ca-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0b4ca-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b4ca-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="0b4ca-105">Attributes</span></span>  
  
|<span data-ttu-id="0b4ca-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="0b4ca-106">Attribute</span></span>|<span data-ttu-id="0b4ca-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b4ca-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b4ca-108">type</span><span class="sxs-lookup"><span data-stu-id="0b4ca-108">type</span></span>|<span data-ttu-id="0b4ca-109">Um tipo que deriva da <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe.</span><span class="sxs-lookup"><span data-stu-id="0b4ca-109">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b4ca-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0b4ca-110">Child Elements</span></span>  
 <span data-ttu-id="0b4ca-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0b4ca-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b4ca-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0b4ca-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0b4ca-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b4ca-113">Element</span></span>|<span data-ttu-id="0b4ca-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b4ca-114">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="0b4ca-115">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="0b4ca-115">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0b4ca-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b4ca-116">Example</span></span>  
 <span data-ttu-id="0b4ca-117">O XML a seguir mostra a configuração de um cache personalizado para manter os tokens de segurança de sessão ( <xref:System.IdentityModel.Tokens.SessionSecurityToken> ).</span><span class="sxs-lookup"><span data-stu-id="0b4ca-117">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="0b4ca-118">A configuração é obtida do `ClaimsAwareWebFarm` exemplo.</span><span class="sxs-lookup"><span data-stu-id="0b4ca-118">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="0b4ca-119">Para obter mais informações sobre este exemplo, consulte o [índice de exemplo de código do WIF](/previous-versions/dotnet/framework/security/wif-code-sample-index).</span><span class="sxs-lookup"><span data-stu-id="0b4ca-119">For more information about this sample, see [WIF Code Sample Index](/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b4ca-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="0b4ca-120">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
