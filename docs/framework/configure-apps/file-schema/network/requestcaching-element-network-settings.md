---
title: Elemento <requestCaching> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: 2a3d0b182acad2351ed095934ca97c6194d344fc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659130"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="4539e-102">\<Elemento requestCaching> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="4539e-102">\<requestCaching> Element (Network Settings)</span></span>
<span data-ttu-id="4539e-103">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="4539e-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="4539e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4539e-104">\<configuration></span></span>  
<span data-ttu-id="4539e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4539e-105">\<system.net></span></span>  
<span data-ttu-id="4539e-106">\<requestCaching></span><span class="sxs-lookup"><span data-stu-id="4539e-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4539e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4539e-107">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4539e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4539e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4539e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4539e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4539e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="4539e-110">Attributes</span></span>  
  
|<span data-ttu-id="4539e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="4539e-111">Attribute</span></span>|<span data-ttu-id="4539e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4539e-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="4539e-113">Especifica se o cache fornece isolamento entre as informações de diferentes usuários.</span><span class="sxs-lookup"><span data-stu-id="4539e-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="4539e-114">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="4539e-114">The default value is `true`.</span></span> <span data-ttu-id="4539e-115">Esse valor deve ser `false` para aplicativos de camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="4539e-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="4539e-116">Especifica que o Caching está desabilitado para todas as respostas da Web e não pode ser substituído programaticamente.</span><span class="sxs-lookup"><span data-stu-id="4539e-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="4539e-117">Um dos valores na enumeração <xref:System.Net.Cache.RequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="4539e-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="4539e-118">O valor padrão é `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="4539e-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="4539e-119">Especifica o tempo padrão após o qual o conteúdo é marcado como expirado.</span><span class="sxs-lookup"><span data-stu-id="4539e-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="4539e-120">Atributo policyLevel</span><span class="sxs-lookup"><span data-stu-id="4539e-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="4539e-121">Valor</span><span class="sxs-lookup"><span data-stu-id="4539e-121">Value</span></span>|<span data-ttu-id="4539e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="4539e-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="4539e-123">Retorna o recurso armazenado em cache se o recurso for atualizado, se o tamanho do conteúdo for preciso e os atributos de expiração, modificação e comprimento do conteúdo estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="4539e-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="4539e-124">Retorna o recurso do servidor.</span><span class="sxs-lookup"><span data-stu-id="4539e-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="4539e-125">Retorna o recurso armazenado em cache se o tamanho do conteúdo estiver presente e corresponder ao tamanho da entrada.</span><span class="sxs-lookup"><span data-stu-id="4539e-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="4539e-126">Retornará o recurso armazenado em cache se o comprimento do conteúdo for fornecido e corresponder ao tamanho da entrada; caso contrário, o recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="4539e-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="4539e-127">Retorna o recurso armazenado em cache se o carimbo de data/hora do recurso armazenado em cache for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, armazenado no cache, e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="4539e-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="4539e-128">Baixa o recurso do servidor, armazena-o no cache e retorna o recurso para o chamador.</span><span class="sxs-lookup"><span data-stu-id="4539e-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="4539e-129">Se um recurso armazenado em cache existir, ele será excluído.</span><span class="sxs-lookup"><span data-stu-id="4539e-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="4539e-130">O recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="4539e-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="4539e-131">Atende a uma solicitação usando a cópia armazenada em cache do recurso se o carimbo de data/hora for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, apresentado ao chamador e armazenado no cache,</span><span class="sxs-lookup"><span data-stu-id="4539e-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4539e-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4539e-132">Child Elements</span></span>  
  
|<span data-ttu-id="4539e-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="4539e-133">Element</span></span>|<span data-ttu-id="4539e-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="4539e-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4539e-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="4539e-135">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="4539e-136">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4539e-136">Optional element.</span></span><br /><br /> <span data-ttu-id="4539e-137">Descreve se o cache HTTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="4539e-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="4539e-138">\<Elemento de > defaultFtpCachePolicy (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="4539e-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="4539e-139">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4539e-139">Optional element.</span></span><br /><br /> <span data-ttu-id="4539e-140">Descreve se o cache FTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="4539e-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4539e-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4539e-141">Parent Elements</span></span>  
  
|<span data-ttu-id="4539e-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="4539e-142">Element</span></span>|<span data-ttu-id="4539e-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="4539e-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4539e-144">system.net</span><span class="sxs-lookup"><span data-stu-id="4539e-144">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="4539e-145">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="4539e-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4539e-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4539e-146">Example</span></span>  
 <span data-ttu-id="4539e-147">O exemplo a seguir mostra como desabilitar todo o cache.</span><span class="sxs-lookup"><span data-stu-id="4539e-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4539e-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4539e-148">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="4539e-149">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="4539e-149">Network Settings Schema</span></span>](index.md)
