---
title: '&lt;requestCaching&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9c0c8d80182931f9ac14e687a337b7be55a5a9a5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltrequestcachinggt-element-network-settings"></a><span data-ttu-id="ce0a0-102">&lt;requestCaching&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="ce0a0-102">&lt;requestCaching&gt; Element (Network Settings)</span></span>
<span data-ttu-id="ce0a0-103">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="ce0a0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ce0a0-104">\<configuration></span></span>  
<span data-ttu-id="ce0a0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="ce0a0-105">\<system.net></span></span>  
<span data-ttu-id="ce0a0-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="ce0a0-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce0a0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce0a0-107">Syntax</span></span>  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce0a0-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ce0a0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ce0a0-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce0a0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ce0a0-110">Attributes</span></span>  
  
|<span data-ttu-id="ce0a0-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ce0a0-111">Attribute</span></span>|<span data-ttu-id="ce0a0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce0a0-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="ce0a0-113">Especifica se o cache fornece isolamento entre as informações de usuários diferentes.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="ce0a0-114">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-114">The default value is `true`.</span></span> <span data-ttu-id="ce0a0-115">Esse valor deve ser `false` para aplicativos de camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="ce0a0-116">Especifica que o cache está desabilitado para todas as respostas de Web e não pode ser substituído por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="ce0a0-117">Um dos valores na enumeração <xref:System.Net.Cache.RequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="ce0a0-118">O valor padrão é `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="ce0a0-119">Especifica o tempo padrão depois que o conteúdo seja marcado como expirada.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="ce0a0-120">policyLevel atributo</span><span class="sxs-lookup"><span data-stu-id="ce0a0-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="ce0a0-121">Valor</span><span class="sxs-lookup"><span data-stu-id="ce0a0-121">Value</span></span>|<span data-ttu-id="ce0a0-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce0a0-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="ce0a0-123">Retorna o recurso em cache se o recurso for atualizado, o comprimento do conteúdo é preciso e a expiração, modificação e atributos de comprimento de conteúdo estão presentes.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="ce0a0-124">Retorna o recurso do servidor.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="ce0a0-125">Retorna o recurso em cache se o comprimento do conteúdo está presente e corresponde ao tamanho de entrada.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="ce0a0-126">Retorna o recurso em cache se o comprimento do conteúdo for fornecido e corresponda ao tamanho de entrada; Caso contrário, o recurso é baixado do servidor e é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="ce0a0-127">Retorna o recurso em cache se o carimbo de hora do recurso em cache é o mesmo que o carimbo de hora do recurso no servidor. Caso contrário, o recurso é baixado do servidor, armazenado em cache e é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="ce0a0-128">Baixe o recurso do servidor, armazena em cache e retorna o recurso para o chamador.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="ce0a0-129">Se existe um recurso de cache, ele será excluído.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="ce0a0-130">O recurso é baixado do servidor e é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="ce0a0-131">Atenda a uma solicitação usando a cópia armazenada em cache do recurso se o carimbo de hora é o mesmo que o carimbo de hora do recurso no servidor. Caso contrário, o recurso é baixado do servidor, apresentado para o chamador e é armazenado no cache,</span><span class="sxs-lookup"><span data-stu-id="ce0a0-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce0a0-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ce0a0-132">Child Elements</span></span>  
  
|<span data-ttu-id="ce0a0-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="ce0a0-133">Element</span></span>|<span data-ttu-id="ce0a0-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce0a0-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce0a0-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="ce0a0-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="ce0a0-136">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-136">Optional element.</span></span><br /><br /> <span data-ttu-id="ce0a0-137">Descreve se o cache de HTTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="ce0a0-138">\<defaultFtpCachePolicy > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="ce0a0-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="ce0a0-139">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-139">Optional element.</span></span><br /><br /> <span data-ttu-id="ce0a0-140">Descreve se o cache de FTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce0a0-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ce0a0-141">Parent Elements</span></span>  
  
|<span data-ttu-id="ce0a0-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="ce0a0-142">Element</span></span>|<span data-ttu-id="ce0a0-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce0a0-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce0a0-144">System.NET</span><span class="sxs-lookup"><span data-stu-id="ce0a0-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="ce0a0-145">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ce0a0-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ce0a0-146">Example</span></span>  
 <span data-ttu-id="ce0a0-147">O exemplo a seguir mostra como desabilitar todo o cache.</span><span class="sxs-lookup"><span data-stu-id="ce0a0-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce0a0-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce0a0-148">See Also</span></span>  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [<span data-ttu-id="ce0a0-149">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="ce0a0-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
