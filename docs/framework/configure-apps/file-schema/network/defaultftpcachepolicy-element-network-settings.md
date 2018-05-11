---
title: '&lt;defaultFtpCachePolicy&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e4ea16c925114d4ad4054af5f340c764ed6fe4fd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="6cebf-102">&lt;defaultFtpCachePolicy&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="6cebf-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="6cebf-103">Descreve se o cache de FTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="6cebf-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="6cebf-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6cebf-104">\<configuration></span></span>  
<span data-ttu-id="6cebf-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6cebf-105">\<system.net></span></span>  
<span data-ttu-id="6cebf-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="6cebf-106">\<requestCaching></span></span>  
<span data-ttu-id="6cebf-107">\<defaultFtpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="6cebf-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cebf-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6cebf-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cebf-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6cebf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6cebf-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6cebf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cebf-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="6cebf-111">Attributes</span></span>  
  
|<span data-ttu-id="6cebf-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="6cebf-112">Attribute</span></span>|<span data-ttu-id="6cebf-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cebf-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="6cebf-114">Especifica o política de cache de FTP.</span><span class="sxs-lookup"><span data-stu-id="6cebf-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="6cebf-115">O valor padrão é `Default`.</span><span class="sxs-lookup"><span data-stu-id="6cebf-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="6cebf-116">policyLevel atributo</span><span class="sxs-lookup"><span data-stu-id="6cebf-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="6cebf-117">Valor</span><span class="sxs-lookup"><span data-stu-id="6cebf-117">Value</span></span>|<span data-ttu-id="6cebf-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cebf-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="6cebf-119">Retorna o recurso em cache se o recurso for atualizado, o comprimento do conteúdo é preciso e a expiração, modificação e atributos de comprimento de conteúdo estão presentes.</span><span class="sxs-lookup"><span data-stu-id="6cebf-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="6cebf-120">Retorna o recurso do servidor.</span><span class="sxs-lookup"><span data-stu-id="6cebf-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="6cebf-121">Retorna o recurso em cache se o comprimento do conteúdo está presente e corresponde ao tamanho de entrada.</span><span class="sxs-lookup"><span data-stu-id="6cebf-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="6cebf-122">Retorna o recurso em cache se o comprimento do conteúdo for fornecido e corresponda ao tamanho de entrada; Caso contrário, o recurso é baixado do servidor e é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="6cebf-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="6cebf-123">Retorna o recurso em cache se o carimbo de hora do recurso em cache é o mesmo que o carimbo de hora do recurso no servidor. Caso contrário, o recurso é baixado do servidor, armazenado no cache e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="6cebf-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="6cebf-124">Baixe o recurso do servidor, armazena em cache e retorna o recurso para o chamador.</span><span class="sxs-lookup"><span data-stu-id="6cebf-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="6cebf-125">Se existe um recurso de cache, ele será excluído.</span><span class="sxs-lookup"><span data-stu-id="6cebf-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="6cebf-126">O recurso é baixado do servidor e é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="6cebf-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="6cebf-127">Atende a uma solicitação usando a cópia do recurso armazenada em cache se o carimbo de data/hora for igual ao do recurso no servidor; caso contrário, o recurso será baixado do servidor, apresentado ao chamador e armazenado no cache.</span><span class="sxs-lookup"><span data-stu-id="6cebf-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6cebf-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6cebf-128">Child Elements</span></span>  
 <span data-ttu-id="6cebf-129">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6cebf-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6cebf-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6cebf-130">Parent Elements</span></span>  
  
|<span data-ttu-id="6cebf-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="6cebf-131">Element</span></span>|<span data-ttu-id="6cebf-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cebf-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cebf-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="6cebf-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="6cebf-134">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="6cebf-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cebf-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="6cebf-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cebf-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6cebf-136">Example</span></span>  
 <span data-ttu-id="6cebf-137">O exemplo a seguir mostra como especificar um FTP caching de política de `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="6cebf-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6cebf-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cebf-138">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="6cebf-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="6cebf-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
