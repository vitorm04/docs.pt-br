---
title: Elemento <defaultFtpCachePolicy> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: e081882aa8df89c0a1bf5d4c60f1395a3319c417
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190365"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="5ea27-102">Elemento \<defaultFtpCachePolicy> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="5ea27-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>

<span data-ttu-id="5ea27-103">Descreve se o cache FTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="5ea27-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="5ea27-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ea27-104">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ea27-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5ea27-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5ea27-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5ea27-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ea27-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ea27-107">Attributes</span></span>  
  
|<span data-ttu-id="5ea27-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="5ea27-108">Attribute</span></span>|<span data-ttu-id="5ea27-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ea27-109">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="5ea27-110">Especifica a política de cache de FTP.</span><span class="sxs-lookup"><span data-stu-id="5ea27-110">Specifies the FTP caching policy.</span></span> <span data-ttu-id="5ea27-111">O valor padrão é `Default`.</span><span class="sxs-lookup"><span data-stu-id="5ea27-111">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="5ea27-112">Atributo policyLevel</span><span class="sxs-lookup"><span data-stu-id="5ea27-112">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="5ea27-113">Valor</span><span class="sxs-lookup"><span data-stu-id="5ea27-113">Value</span></span>|<span data-ttu-id="5ea27-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ea27-114">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="5ea27-115">Retorna o recurso armazenado em cache se o recurso for atualizado, se o tamanho do conteúdo for preciso e os atributos de expiração, modificação e comprimento do conteúdo estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="5ea27-115">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="5ea27-116">Retorna o recurso do servidor.</span><span class="sxs-lookup"><span data-stu-id="5ea27-116">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="5ea27-117">Retorna o recurso armazenado em cache se o tamanho do conteúdo estiver presente e corresponder ao tamanho da entrada.</span><span class="sxs-lookup"><span data-stu-id="5ea27-117">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="5ea27-118">Retornará o recurso armazenado em cache se o comprimento do conteúdo for fornecido e corresponder ao tamanho da entrada; caso contrário, o recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="5ea27-118">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="5ea27-119">Retorna o recurso armazenado em cache se o carimbo de data/hora do recurso armazenado em cache for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, armazenado no cache e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="5ea27-119">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="5ea27-120">Baixa o recurso do servidor, armazena-o no cache e retorna o recurso para o chamador.</span><span class="sxs-lookup"><span data-stu-id="5ea27-120">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="5ea27-121">Se um recurso armazenado em cache existir, ele será excluído.</span><span class="sxs-lookup"><span data-stu-id="5ea27-121">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="5ea27-122">O recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="5ea27-122">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="5ea27-123">Atende a uma solicitação usando a cópia do recurso armazenada em cache se o carimbo de data/hora for igual ao do recurso no servidor; caso contrário, o recurso será baixado do servidor, apresentado ao chamador e armazenado no cache.</span><span class="sxs-lookup"><span data-stu-id="5ea27-123">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ea27-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5ea27-124">Child Elements</span></span>  

 <span data-ttu-id="5ea27-125">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5ea27-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ea27-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5ea27-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5ea27-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ea27-127">Element</span></span>|<span data-ttu-id="5ea27-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ea27-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ea27-129">requestCaching</span><span class="sxs-lookup"><span data-stu-id="5ea27-129">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="5ea27-130">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="5ea27-130">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ea27-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ea27-131">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ea27-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ea27-132">Example</span></span>  

 <span data-ttu-id="5ea27-133">O exemplo a seguir mostra como especificar uma política de cache de FTP do `NoCacheNoStore` .</span><span class="sxs-lookup"><span data-stu-id="5ea27-133">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ea27-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="5ea27-134">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="5ea27-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="5ea27-135">Network Settings Schema</span></span>](index.md)
