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
ms.openlocfilehash: fd1649edbf7a2c8546992019df667f27df68e02c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698326"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="7bd04-102">\<defaultFtpCachePolicy > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="7bd04-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="7bd04-103">Descreve se o cache FTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="7bd04-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
[<span data-ttu-id="7bd04-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="7bd04-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="7bd04-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7bd04-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="7bd04-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<requestCaching >** ](requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7bd04-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>  
<span data-ttu-id="7bd04-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<defaultFtpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="7bd04-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bd04-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bd04-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bd04-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7bd04-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7bd04-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7bd04-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bd04-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="7bd04-111">Attributes</span></span>  
  
|<span data-ttu-id="7bd04-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="7bd04-112">Attribute</span></span>|<span data-ttu-id="7bd04-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bd04-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="7bd04-114">Especifica a política de cache de FTP.</span><span class="sxs-lookup"><span data-stu-id="7bd04-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="7bd04-115">O valor padrão é `Default`.</span><span class="sxs-lookup"><span data-stu-id="7bd04-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="7bd04-116">Atributo policyLevel</span><span class="sxs-lookup"><span data-stu-id="7bd04-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="7bd04-117">Valor</span><span class="sxs-lookup"><span data-stu-id="7bd04-117">Value</span></span>|<span data-ttu-id="7bd04-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bd04-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="7bd04-119">Retorna o recurso armazenado em cache se o recurso for atualizado, se o tamanho do conteúdo for preciso e os atributos de expiração, modificação e comprimento do conteúdo estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="7bd04-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="7bd04-120">Retorna o recurso do servidor.</span><span class="sxs-lookup"><span data-stu-id="7bd04-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="7bd04-121">Retorna o recurso armazenado em cache se o tamanho do conteúdo estiver presente e corresponder ao tamanho da entrada.</span><span class="sxs-lookup"><span data-stu-id="7bd04-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="7bd04-122">Retornará o recurso armazenado em cache se o comprimento do conteúdo for fornecido e corresponder ao tamanho da entrada; caso contrário, o recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="7bd04-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="7bd04-123">Retorna o recurso armazenado em cache se o carimbo de data/hora do recurso armazenado em cache for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, armazenado no cache e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="7bd04-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="7bd04-124">Baixa o recurso do servidor, armazena-o no cache e retorna o recurso para o chamador.</span><span class="sxs-lookup"><span data-stu-id="7bd04-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="7bd04-125">Se um recurso armazenado em cache existir, ele será excluído.</span><span class="sxs-lookup"><span data-stu-id="7bd04-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="7bd04-126">O recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="7bd04-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="7bd04-127">Atende a uma solicitação usando a cópia do recurso armazenada em cache se o carimbo de data/hora for igual ao do recurso no servidor; caso contrário, o recurso será baixado do servidor, apresentado ao chamador e armazenado no cache.</span><span class="sxs-lookup"><span data-stu-id="7bd04-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bd04-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7bd04-128">Child Elements</span></span>  
 <span data-ttu-id="7bd04-129">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7bd04-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bd04-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7bd04-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7bd04-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="7bd04-131">Element</span></span>|<span data-ttu-id="7bd04-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bd04-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bd04-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="7bd04-133">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="7bd04-134">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="7bd04-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bd04-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="7bd04-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bd04-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7bd04-136">Example</span></span>  
 <span data-ttu-id="7bd04-137">O exemplo a seguir mostra como especificar uma política de cache de FTP de `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="7bd04-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7bd04-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bd04-138">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="7bd04-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="7bd04-139">Network Settings Schema</span></span>](index.md)
