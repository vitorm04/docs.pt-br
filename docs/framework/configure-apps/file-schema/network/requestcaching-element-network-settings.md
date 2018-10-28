---
title: '&lt;requestCaching&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: fecb3c71e0686a557b8a4b0c85b7d91a9846204f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194963"
---
# <a name="ltrequestcachinggt-element-network-settings"></a><span data-ttu-id="74bea-102">&lt;requestCaching&gt; (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="74bea-102">&lt;requestCaching&gt; Element (Network Settings)</span></span>
<span data-ttu-id="74bea-103">Controla o mecanismo de cache para solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="74bea-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="74bea-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="74bea-104">\<configuration></span></span>  
<span data-ttu-id="74bea-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="74bea-105">\<system.net></span></span>  
<span data-ttu-id="74bea-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="74bea-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74bea-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74bea-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74bea-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="74bea-108">Attributes and Elements</span></span>  
 <span data-ttu-id="74bea-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="74bea-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74bea-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="74bea-110">Attributes</span></span>  
  
|<span data-ttu-id="74bea-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="74bea-111">Attribute</span></span>|<span data-ttu-id="74bea-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="74bea-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="74bea-113">Especifica se o cache fornece isolamento entre as informações de usuários diferentes.</span><span class="sxs-lookup"><span data-stu-id="74bea-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="74bea-114">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="74bea-114">The default value is `true`.</span></span> <span data-ttu-id="74bea-115">Esse valor deve ser `false` para aplicativos de camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="74bea-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="74bea-116">Especifica que o cache está desabilitado para todas as respostas da Web e não pode ser substituído por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="74bea-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="74bea-117">Um dos valores na enumeração <xref:System.Net.Cache.RequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="74bea-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="74bea-118">O valor padrão é `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="74bea-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="74bea-119">Especifica o tempo padrão após o qual o conteúdo seja marcado como expirada.</span><span class="sxs-lookup"><span data-stu-id="74bea-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="74bea-120">policyLevel atributo</span><span class="sxs-lookup"><span data-stu-id="74bea-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="74bea-121">Valor</span><span class="sxs-lookup"><span data-stu-id="74bea-121">Value</span></span>|<span data-ttu-id="74bea-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="74bea-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="74bea-123">Retorna o recurso armazenado em cache se o recurso estiver atualizado, o comprimento do conteúdo é preciso e a expiração, modificação e atributos de comprimento de conteúdo estão presentes.</span><span class="sxs-lookup"><span data-stu-id="74bea-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="74bea-124">Retorna o recursos do servidor.</span><span class="sxs-lookup"><span data-stu-id="74bea-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="74bea-125">Retorna o recurso armazenado em cache se o comprimento do conteúdo está presente e corresponde ao tamanho de entrada.</span><span class="sxs-lookup"><span data-stu-id="74bea-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="74bea-126">Retorna o recurso armazenado em cache se o comprimento do conteúdo é fornecido e corresponde o tamanho da entrada. Caso contrário, o recurso é baixado do servidor e é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="74bea-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="74bea-127">Retorna o recurso armazenado em cache se o carimbo de hora do recurso em cache é o mesmo que o carimbo de hora do recurso no servidor. Caso contrário, o recurso é baixado do servidor, armazenado no cache e é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="74bea-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="74bea-128">Baixa o recurso do servidor, armazena em cache e retorna o recurso para o chamador.</span><span class="sxs-lookup"><span data-stu-id="74bea-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="74bea-129">Se existir um recurso armazenado em cache, ele será excluído.</span><span class="sxs-lookup"><span data-stu-id="74bea-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="74bea-130">O recurso é baixado do servidor e é retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="74bea-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="74bea-131">Atende a uma solicitação usando a cópia armazenada em cache do recurso se o carimbo de hora é o mesmo que o carimbo de hora do recurso no servidor. Caso contrário, o recurso é baixado do servidor, apresentado ao chamador e é armazenado no cache,</span><span class="sxs-lookup"><span data-stu-id="74bea-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74bea-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="74bea-132">Child Elements</span></span>  
  
|<span data-ttu-id="74bea-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="74bea-133">Element</span></span>|<span data-ttu-id="74bea-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="74bea-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74bea-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="74bea-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="74bea-136">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="74bea-136">Optional element.</span></span><br /><br /> <span data-ttu-id="74bea-137">Descreve se o cache de HTTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="74bea-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="74bea-138">\<defaultFtpCachePolicy > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="74bea-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="74bea-139">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="74bea-139">Optional element.</span></span><br /><br /> <span data-ttu-id="74bea-140">Descreve se o cache de FTP está ativo e descreve a política de cache padrão.</span><span class="sxs-lookup"><span data-stu-id="74bea-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74bea-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="74bea-141">Parent Elements</span></span>  
  
|<span data-ttu-id="74bea-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="74bea-142">Element</span></span>|<span data-ttu-id="74bea-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="74bea-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74bea-144">System.NET</span><span class="sxs-lookup"><span data-stu-id="74bea-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="74bea-145">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="74bea-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="74bea-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74bea-146">Example</span></span>  
 <span data-ttu-id="74bea-147">O exemplo a seguir mostra como desabilitar todo o cache.</span><span class="sxs-lookup"><span data-stu-id="74bea-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74bea-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74bea-148">See Also</span></span>  
- <xref:System.Net.Cache?displayProperty=nameWithType>  
- [<span data-ttu-id="74bea-149">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="74bea-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
