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
ms.openlocfilehash: f0979d2e0caeb0b22b90572aef0ad53235020f1d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697835"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="2f790-102">\<Elemento requestCaching> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="2f790-102">\<requestCaching> Element (Network Settings)</span></span>
<span data-ttu-id="2f790-103">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="2f790-103">Controls the caching mechanism for network requests.</span></span>  
  
[<span data-ttu-id="2f790-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="2f790-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2f790-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2f790-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="2f790-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requestCaching >**</span><span class="sxs-lookup"><span data-stu-id="2f790-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f790-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f790-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f790-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2f790-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2f790-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2f790-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f790-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2f790-110">Attributes</span></span>  
  
|<span data-ttu-id="2f790-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="2f790-111">Attribute</span></span>|<span data-ttu-id="2f790-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f790-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="2f790-113">Especifica se o cache fornece isolamento entre as informações de diferentes usuários.</span><span class="sxs-lookup"><span data-stu-id="2f790-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="2f790-114">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="2f790-114">The default value is `true`.</span></span> <span data-ttu-id="2f790-115">Esse valor deve ser `false` para aplicativos de camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="2f790-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="2f790-116">Especifica que o Caching está desabilitado para todas as respostas da Web e não pode ser substituído programaticamente.</span><span class="sxs-lookup"><span data-stu-id="2f790-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="2f790-117">Um dos valores na enumeração <xref:System.Net.Cache.RequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="2f790-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="2f790-118">O valor padrão é `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="2f790-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="2f790-119">Especifica o tempo padrão após o qual o conteúdo é marcado como expirado.</span><span class="sxs-lookup"><span data-stu-id="2f790-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="2f790-120">Atributo policyLevel</span><span class="sxs-lookup"><span data-stu-id="2f790-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="2f790-121">Valor</span><span class="sxs-lookup"><span data-stu-id="2f790-121">Value</span></span>|<span data-ttu-id="2f790-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f790-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="2f790-123">Retorna o recurso armazenado em cache se o recurso for atualizado, se o tamanho do conteúdo for preciso e os atributos de expiração, modificação e comprimento do conteúdo estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="2f790-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="2f790-124">Retorna o recurso do servidor.</span><span class="sxs-lookup"><span data-stu-id="2f790-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="2f790-125">Retorna o recurso armazenado em cache se o tamanho do conteúdo estiver presente e corresponder ao tamanho da entrada.</span><span class="sxs-lookup"><span data-stu-id="2f790-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="2f790-126">Retornará o recurso armazenado em cache se o comprimento do conteúdo for fornecido e corresponder ao tamanho da entrada; caso contrário, o recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="2f790-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="2f790-127">Retorna o recurso armazenado em cache se o carimbo de data/hora do recurso armazenado em cache for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, armazenado no cache, e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="2f790-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="2f790-128">Baixa o recurso do servidor, armazena-o no cache e retorna o recurso para o chamador.</span><span class="sxs-lookup"><span data-stu-id="2f790-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="2f790-129">Se um recurso armazenado em cache existir, ele será excluído.</span><span class="sxs-lookup"><span data-stu-id="2f790-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="2f790-130">O recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="2f790-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="2f790-131">Atende a uma solicitação usando a cópia armazenada em cache do recurso se o carimbo de data/hora for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, apresentado ao chamador e armazenado no cache,</span><span class="sxs-lookup"><span data-stu-id="2f790-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f790-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2f790-132">Child Elements</span></span>  
  
|<span data-ttu-id="2f790-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="2f790-133">Element</span></span>|<span data-ttu-id="2f790-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f790-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f790-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="2f790-135">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="2f790-136">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2f790-136">Optional element.</span></span><br /><br /> <span data-ttu-id="2f790-137">Descreve se o cache HTTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="2f790-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="2f790-138">\<defaultFtpCachePolicy > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="2f790-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="2f790-139">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2f790-139">Optional element.</span></span><br /><br /> <span data-ttu-id="2f790-140">Descreve se o cache FTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="2f790-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2f790-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2f790-141">Parent Elements</span></span>  
  
|<span data-ttu-id="2f790-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="2f790-142">Element</span></span>|<span data-ttu-id="2f790-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f790-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f790-144">system.net</span><span class="sxs-lookup"><span data-stu-id="2f790-144">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="2f790-145">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="2f790-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2f790-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2f790-146">Example</span></span>  
 <span data-ttu-id="2f790-147">O exemplo a seguir mostra como desabilitar todo o cache.</span><span class="sxs-lookup"><span data-stu-id="2f790-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f790-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f790-148">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="2f790-149">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="2f790-149">Network Settings Schema</span></span>](index.md)
