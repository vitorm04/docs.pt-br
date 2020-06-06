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
ms.openlocfilehash: afee69eb894518b1c88483e34a1d64d452019244
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74802132"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="2b772-102">Elemento \<requestCaching> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="2b772-102">\<requestCaching> Element (Network Settings)</span></span>
<span data-ttu-id="2b772-103">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="2b772-103">Controls the caching mechanism for network requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a><span data-ttu-id="2b772-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b772-104">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh:mm:ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b772-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2b772-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2b772-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2b772-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b772-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="2b772-107">Attributes</span></span>  
  
|<span data-ttu-id="2b772-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="2b772-108">Attribute</span></span>|<span data-ttu-id="2b772-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b772-109">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="2b772-110">Especifica se o cache fornece isolamento entre as informações de diferentes usuários.</span><span class="sxs-lookup"><span data-stu-id="2b772-110">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="2b772-111">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="2b772-111">The default value is `true`.</span></span> <span data-ttu-id="2b772-112">Esse valor deve ser `false` para aplicativos de camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="2b772-112">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="2b772-113">Especifica que o Caching está desabilitado para todas as respostas da Web e não pode ser substituído programaticamente.</span><span class="sxs-lookup"><span data-stu-id="2b772-113">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="2b772-114">Um dos valores na enumeração <xref:System.Net.Cache.RequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="2b772-114">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="2b772-115">O valor padrão é `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="2b772-115">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="2b772-116">Especifica o tempo padrão após o qual o conteúdo é marcado como expirado.</span><span class="sxs-lookup"><span data-stu-id="2b772-116">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="2b772-117">Atributo policyLevel</span><span class="sxs-lookup"><span data-stu-id="2b772-117">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="2b772-118">Valor</span><span class="sxs-lookup"><span data-stu-id="2b772-118">Value</span></span>|<span data-ttu-id="2b772-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b772-119">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="2b772-120">Retorna o recurso armazenado em cache se o recurso for atualizado, se o tamanho do conteúdo for preciso e os atributos de expiração, modificação e comprimento do conteúdo estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="2b772-120">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="2b772-121">Retorna o recurso do servidor.</span><span class="sxs-lookup"><span data-stu-id="2b772-121">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="2b772-122">Retorna o recurso armazenado em cache se o tamanho do conteúdo estiver presente e corresponder ao tamanho da entrada.</span><span class="sxs-lookup"><span data-stu-id="2b772-122">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="2b772-123">Retornará o recurso armazenado em cache se o comprimento do conteúdo for fornecido e corresponder ao tamanho da entrada; caso contrário, o recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="2b772-123">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="2b772-124">Retorna o recurso armazenado em cache se o carimbo de data/hora do recurso armazenado em cache for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, armazenado no cache, e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="2b772-124">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="2b772-125">Baixa o recurso do servidor, armazena-o no cache e retorna o recurso para o chamador.</span><span class="sxs-lookup"><span data-stu-id="2b772-125">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="2b772-126">Se um recurso armazenado em cache existir, ele será excluído.</span><span class="sxs-lookup"><span data-stu-id="2b772-126">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="2b772-127">O recurso é baixado do servidor e retornado para o chamador.</span><span class="sxs-lookup"><span data-stu-id="2b772-127">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="2b772-128">Atende a uma solicitação usando a cópia armazenada em cache do recurso se o carimbo de data/hora for o mesmo que o carimbo de data/hora do recurso no servidor; caso contrário, o recurso será baixado do servidor, apresentado ao chamador e armazenado no cache,</span><span class="sxs-lookup"><span data-stu-id="2b772-128">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b772-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2b772-129">Child Elements</span></span>  
  
|<span data-ttu-id="2b772-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="2b772-130">Element</span></span>|<span data-ttu-id="2b772-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b772-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b772-132">DefaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="2b772-132">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="2b772-133">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2b772-133">Optional element.</span></span><br /><br /> <span data-ttu-id="2b772-134">Descreve se o cache HTTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="2b772-134">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="2b772-135">\<defaultFtpCachePolicy>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="2b772-135">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="2b772-136">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2b772-136">Optional element.</span></span><br /><br /> <span data-ttu-id="2b772-137">Descreve se o cache FTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="2b772-137">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b772-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2b772-138">Parent Elements</span></span>  
  
|<span data-ttu-id="2b772-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="2b772-139">Element</span></span>|<span data-ttu-id="2b772-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b772-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b772-141">system.net</span><span class="sxs-lookup"><span data-stu-id="2b772-141">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="2b772-142">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="2b772-142">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2b772-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b772-143">Example</span></span>  
 <span data-ttu-id="2b772-144">O exemplo a seguir mostra como desabilitar todo o cache.</span><span class="sxs-lookup"><span data-stu-id="2b772-144">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b772-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="2b772-145">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="2b772-146">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="2b772-146">Network Settings Schema</span></span>](index.md)
