---
title: "&lt;namedCaches&gt; elemento (configurações de Cache)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bdafddcb05dd50f059c9f6804573beec085a4a2a
ms.sourcegitcommit: d0f7646d67db5809cf43ff1d27b399a4020e8ee2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2017
---
# <a name="ltnamedcachesgt-element-cache-settings"></a><span data-ttu-id="c14a8-102">&lt;namedCaches&gt; elemento (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="c14a8-102">&lt;namedCaches&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="c14a8-103">Especifica uma coleção de definições de configuração para nomeado <xref:System.Runtime.Caching.MemoryCache> instâncias.</span><span class="sxs-lookup"><span data-stu-id="c14a8-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="c14a8-104">O <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriedade faz referência a coleção de definições de configuração de um ou mais `namedCaches` elementos do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c14a8-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
 <span data-ttu-id="c14a8-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c14a8-105">\<configuration></span></span>  
<span data-ttu-id="c14a8-106">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="c14a8-106">\< system.runtime.caching></span></span>  
<span data-ttu-id="c14a8-107">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="c14a8-107">\<memoryCache></span></span>  
<span data-ttu-id="c14a8-108">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="c14a8-108">\<namedCaches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c14a8-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c14a8-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="c14a8-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="c14a8-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c14a8-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c14a8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c14a8-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c14a8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c14a8-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="c14a8-113">Attributes</span></span>  
  
|<span data-ttu-id="c14a8-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="c14a8-114">Attribute</span></span>|<span data-ttu-id="c14a8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c14a8-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="c14a8-116">Um valor inteiro que especifica o tamanho máximo permitido, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode atingir.</span><span class="sxs-lookup"><span data-stu-id="c14a8-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="c14a8-117">O valor padrão é 0, o que significa que a heurística de dimensionamento automático do <xref:System.Runtime.Caching.MemoryCache> classe são usadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="c14a8-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="c14a8-118">O nome do cache.</span><span class="sxs-lookup"><span data-stu-id="c14a8-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="c14a8-119">Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória instalada fisicamente do computador que pode ser consumida pelo cache.</span><span class="sxs-lookup"><span data-stu-id="c14a8-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="c14a8-120">O valor padrão é 0, o que significa que a heurística de dimensionamento automático do <xref:System.Runtime.Caching.MemoryCache> classe são usadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="c14a8-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="c14a8-121">Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual em relação as limites de memória absoluto e baseadas em porcentagens que são definidas para a instância de cache.</span><span class="sxs-lookup"><span data-stu-id="c14a8-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="c14a8-122">Esse valor é inserido no formato "Hh".</span><span class="sxs-lookup"><span data-stu-id="c14a8-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c14a8-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c14a8-123">Child Elements</span></span>  
  
|<span data-ttu-id="c14a8-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="c14a8-124">Element</span></span>|<span data-ttu-id="c14a8-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="c14a8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c14a8-126">\<add></span><span class="sxs-lookup"><span data-stu-id="c14a8-126">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|<span data-ttu-id="c14a8-127">Adiciona um cache nomeado à coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="c14a8-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="c14a8-128">\<clear></span><span class="sxs-lookup"><span data-stu-id="c14a8-128">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|<span data-ttu-id="c14a8-129">Limpa a coleção `namedCaches` de um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="c14a8-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="c14a8-130">\<remove></span><span class="sxs-lookup"><span data-stu-id="c14a8-130">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|<span data-ttu-id="c14a8-131">Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="c14a8-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c14a8-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c14a8-132">Parent Elements</span></span>  
  
|<span data-ttu-id="c14a8-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="c14a8-133">Element</span></span>|<span data-ttu-id="c14a8-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="c14a8-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c14a8-135">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="c14a8-135">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="c14a8-136">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="c14a8-136">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c14a8-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="c14a8-137">Remarks</span></span>  
 <span data-ttu-id="c14a8-138">A seção de configuração do cache de memória do arquivo Web. config pode conter `add`, `remove`, e `clear` atributos para o `namedCaches` coleção.</span><span class="sxs-lookup"><span data-stu-id="c14a8-138">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="c14a8-139">Cada `namedCaches` entrada é identificada exclusivamente pelo `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="c14a8-139">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="c14a8-140">Você pode recuperar instâncias de entradas de cache de memória consultando as informações nos arquivos de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c14a8-140">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="c14a8-141">Por padrão, a instância de cache padrão tem uma entrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c14a8-141">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="c14a8-142">A instância de cache padrão é a instância que é retornada de <xref:System.Runtime.Caching.MemoryCache.Default%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c14a8-142">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="c14a8-143">Se você definir o atributo de nome "padrão", o elemento usa a instância padrão do cache de memória.</span><span class="sxs-lookup"><span data-stu-id="c14a8-143">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c14a8-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c14a8-144">Example</span></span>  
 <span data-ttu-id="c14a8-145">O exemplo a seguir mostra como definir o nome do cache para o nome de entrada de cache padrão definindo o `name` atributo como "padrão".</span><span class="sxs-lookup"><span data-stu-id="c14a8-145">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="c14a8-146">O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="c14a8-146">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="c14a8-147">Definir esses atributos como zero significa que a heurística de dimensionamento automático do <xref:System.Runtime.Caching.MemoryCache> classe são usados.</span><span class="sxs-lookup"><span data-stu-id="c14a8-147">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="c14a8-148">A implementação de cache compara a carga de memória atual em relação as limites de memória absoluto e baseadas em porcentagens cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="c14a8-148">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c14a8-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c14a8-149">See Also</span></span>  
 [<span data-ttu-id="c14a8-150">\<memoryCache > elemento (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="c14a8-150">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
