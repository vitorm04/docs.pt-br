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
ms.openlocfilehash: 9261a430642cb4d5ac4507835bd0fd3561bd8c02
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088436"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="51c6f-102">Elemento \<defaultFtpCachePolicy> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="51c6f-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="51c6f-103">Descreve se o cache FTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="51c6f-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="51c6f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51c6f-104">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51c6f-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="51c6f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="51c6f-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="51c6f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51c6f-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="51c6f-107">Attributes</span></span>  
  
|<span data-ttu-id="51c6f-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="51c6f-108">Attribute</span></span>|<span data-ttu-id="51c6f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="51c6f-109">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="51c6f-110">Especifica a política de cache de FTP.</span><span class="sxs-lookup"><span data-stu-id="51c6f-110">Specifies the FTP caching policy.</span></span> <span data-ttu-id="51c6f-111">O valor padrão é `Default`.</span><span class="sxs-lookup"><span data-stu-id="51c6f-111">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="51c6f-112">Atributo policyLevel</span><span class="sxs-lookup"><span data-stu-id="51c6f-112">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="51c6f-113">Valor</span><span class="sxs-lookup"><span data-stu-id="51c6f-113">Value</span></span>|<span data-ttu-id="51c6f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="51c6f-114">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="51c6f-115">Retorna o recurso armazenado em cache se o recurso for atualizado, se o tamanho do conteúdo for preciso e os atributos de expiração, modificação e comprimento do conteúdo estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="51c6f-115">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="51c6f-116">Retorna o recurso do servidor.</span><span class="sxs-lookup"><span data-stu-id="51c6f-116">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="51c6f-117">Retorna o recurso armazenado em cache se o tamanho do conteúdo estiver presente e corresponder ao tamanho da entrada.</span><span class="sxs-lookup"><span data-stu-id="51c6f-117">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="51c6f-118">Retornará o recurso armazenado em cache se o comprimento do conteúdo for fornecido e corresponder ao tamanho da entrada; caso contrário, o recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="51c6f-118">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="51c6f-119">Retorna o recurso armazenado em cache se o carimbo de data/hora do recurso armazenado em cache for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, armazenado no cache e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="51c6f-119">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="51c6f-120">Baixa o recurso do servidor, armazena-o no cache e retorna o recurso para o chamador.</span><span class="sxs-lookup"><span data-stu-id="51c6f-120">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="51c6f-121">Se um recurso armazenado em cache existir, ele será excluído.</span><span class="sxs-lookup"><span data-stu-id="51c6f-121">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="51c6f-122">O recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="51c6f-122">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="51c6f-123">Atende a uma solicitação usando a cópia do recurso armazenada em cache se o carimbo de data/hora for igual ao do recurso no servidor; caso contrário, o recurso será baixado do servidor, apresentado ao chamador e armazenado no cache.</span><span class="sxs-lookup"><span data-stu-id="51c6f-123">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51c6f-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="51c6f-124">Child Elements</span></span>  
 <span data-ttu-id="51c6f-125">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="51c6f-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51c6f-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="51c6f-126">Parent Elements</span></span>  
  
|<span data-ttu-id="51c6f-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="51c6f-127">Element</span></span>|<span data-ttu-id="51c6f-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="51c6f-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51c6f-129">requestCaching</span><span class="sxs-lookup"><span data-stu-id="51c6f-129">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="51c6f-130">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="51c6f-130">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51c6f-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="51c6f-131">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="51c6f-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51c6f-132">Example</span></span>  
 <span data-ttu-id="51c6f-133">O exemplo a seguir mostra como especificar uma política de cache de FTP do `NoCacheNoStore` .</span><span class="sxs-lookup"><span data-stu-id="51c6f-133">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51c6f-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="51c6f-134">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="51c6f-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="51c6f-135">Network Settings Schema</span></span>](index.md)
