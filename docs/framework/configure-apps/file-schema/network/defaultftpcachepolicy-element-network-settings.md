---
title: <defaultFtpCachePolicy> (Configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 36d174beea58ff96674bd873bfbcb8be89591669
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132529"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="e5250-102">\<defaultFtpCachePolicy > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="e5250-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="e5250-103">Descreve se o cache de FTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="e5250-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="e5250-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e5250-104">\<configuration></span></span>  
<span data-ttu-id="e5250-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e5250-105">\<system.net></span></span>  
<span data-ttu-id="e5250-106">\<requestCaching></span><span class="sxs-lookup"><span data-stu-id="e5250-106">\<requestCaching></span></span>  
<span data-ttu-id="e5250-107">\<defaultFtpCachePolicy></span><span class="sxs-lookup"><span data-stu-id="e5250-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5250-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5250-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5250-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e5250-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e5250-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e5250-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5250-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e5250-111">Attributes</span></span>  
  
|<span data-ttu-id="e5250-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="e5250-112">Attribute</span></span>|<span data-ttu-id="e5250-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5250-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="e5250-114">Especifica o política de cache de FTP.</span><span class="sxs-lookup"><span data-stu-id="e5250-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="e5250-115">O valor padrão é `Default`.</span><span class="sxs-lookup"><span data-stu-id="e5250-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="e5250-116">policyLevel atributo</span><span class="sxs-lookup"><span data-stu-id="e5250-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="e5250-117">Valor</span><span class="sxs-lookup"><span data-stu-id="e5250-117">Value</span></span>|<span data-ttu-id="e5250-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5250-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="e5250-119">Retorna o recurso armazenado em cache se o recurso estiver atualizado, o comprimento do conteúdo é preciso e a expiração, modificação e atributos de comprimento de conteúdo estão presentes.</span><span class="sxs-lookup"><span data-stu-id="e5250-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="e5250-120">Retorna o recursos do servidor.</span><span class="sxs-lookup"><span data-stu-id="e5250-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="e5250-121">Retorna o recurso armazenado em cache se o comprimento do conteúdo está presente e corresponde ao tamanho de entrada.</span><span class="sxs-lookup"><span data-stu-id="e5250-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="e5250-122">Retorna o recurso armazenado em cache se o comprimento do conteúdo é fornecido e corresponde o tamanho da entrada. Caso contrário, o recurso é baixado do servidor e é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="e5250-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="e5250-123">Retorna o recurso armazenado em cache se o carimbo de hora do recurso em cache é o mesmo que o carimbo de hora do recurso no servidor. Caso contrário, o recurso é baixado do servidor, armazenado no cache e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="e5250-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="e5250-124">Baixa o recurso do servidor, armazena em cache e retorna o recurso para o chamador.</span><span class="sxs-lookup"><span data-stu-id="e5250-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="e5250-125">Se existir um recurso armazenado em cache, ele será excluído.</span><span class="sxs-lookup"><span data-stu-id="e5250-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="e5250-126">O recurso é baixado do servidor e é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="e5250-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="e5250-127">Atende a uma solicitação usando a cópia do recurso armazenada em cache se o carimbo de data/hora for igual ao do recurso no servidor; caso contrário, o recurso será baixado do servidor, apresentado ao chamador e armazenado no cache.</span><span class="sxs-lookup"><span data-stu-id="e5250-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5250-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e5250-128">Child Elements</span></span>  
 <span data-ttu-id="e5250-129">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e5250-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5250-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e5250-130">Parent Elements</span></span>  
  
|<span data-ttu-id="e5250-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="e5250-131">Element</span></span>|<span data-ttu-id="e5250-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5250-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5250-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="e5250-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="e5250-134">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="e5250-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5250-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5250-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5250-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5250-136">Example</span></span>  
 <span data-ttu-id="e5250-137">O exemplo a seguir mostra como especificar um política de cache de FTP `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="e5250-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5250-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5250-138">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="e5250-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="e5250-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
