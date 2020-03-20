---
title: Elemento <namedCaches> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153952"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="0d5e0-102">\<chamadoCaches> Element (Configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="0d5e0-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="0d5e0-103">Especifica uma coleção de configurações <xref:System.Runtime.Caching.MemoryCache> para as instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="0d5e0-104">A <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriedade faz referência à coleção de `namedCaches` configurações de um ou mais elementos do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
<span data-ttu-id="0d5e0-105">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d5e0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0d5e0-106">&nbsp;&nbsp;[**\<system.runtime.cache>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0d5e0-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="0d5e0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memória>de cache**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0d5e0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="0d5e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chamadoCaches>**</span><span class="sxs-lookup"><span data-stu-id="0d5e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d5e0-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d5e0-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="0d5e0-110">Type</span><span class="sxs-lookup"><span data-stu-id="0d5e0-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d5e0-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0d5e0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0d5e0-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d5e0-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="0d5e0-113">Attributes</span></span>  
  
|<span data-ttu-id="0d5e0-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="0d5e0-114">Attribute</span></span>|<span data-ttu-id="0d5e0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d5e0-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="0d5e0-116">Um valor inteiro que especifica o tamanho máximo permitido, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode crescer.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="0d5e0-117">O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística autosizante da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="0d5e0-118">O nome do cache.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="0d5e0-119">Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória do computador fisicamente instalada que pode ser consumida pelo cache.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="0d5e0-120">O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística autosizante da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="0d5e0-121">Um valor que indica o intervalo de tempo após o qual a implementação do cache compara a carga de memória atual com os limites de memória absolutos e baseados em porcentagem definidos para a instância do cache.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="0d5e0-122">Esse valor é inserido no formato "HH:MM:SS".</span><span class="sxs-lookup"><span data-stu-id="0d5e0-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d5e0-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0d5e0-123">Child Elements</span></span>  
  
|<span data-ttu-id="0d5e0-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d5e0-124">Element</span></span>|<span data-ttu-id="0d5e0-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d5e0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d5e0-126">\<adicionar></span><span class="sxs-lookup"><span data-stu-id="0d5e0-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="0d5e0-127">Adiciona um cache nomeado à coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="0d5e0-128">\<claro></span><span class="sxs-lookup"><span data-stu-id="0d5e0-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="0d5e0-129">Limpa a coleção `namedCaches` de um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="0d5e0-130">\<remover></span><span class="sxs-lookup"><span data-stu-id="0d5e0-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="0d5e0-131">Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d5e0-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0d5e0-132">Parent Elements</span></span>  
  
|<span data-ttu-id="0d5e0-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d5e0-133">Element</span></span>|<span data-ttu-id="0d5e0-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d5e0-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d5e0-135">\<>de configuração</span><span class="sxs-lookup"><span data-stu-id="0d5e0-135">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="0d5e0-136">Especifica o elemento raiz em cada arquivo de configuração que é usado pelos aplicativos common language runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-136">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="0d5e0-137">\<memória>de cache</span><span class="sxs-lookup"><span data-stu-id="0d5e0-137">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="0d5e0-138">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-138">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[<span data-ttu-id="0d5e0-139">\<system.runtime.cache></span><span class="sxs-lookup"><span data-stu-id="0d5e0-139">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="0d5e0-140">Contém tipos que permitem implementar o cache de saída em aplicativos incorporados ao Quadro .NET.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-140">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d5e0-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d5e0-141">Remarks</span></span>  
 <span data-ttu-id="0d5e0-142">A seção de configuração de cache `add`de `remove`memória `clear` do arquivo `namedCaches` Web.config pode conter , e atributos para a coleção.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-142">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="0d5e0-143">Cada `namedCaches` entrada é identificada `name` exclusivamente pelo atributo.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-143">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="0d5e0-144">Você pode recuperar instâncias de entradas de cache de memória fazendo referência às informações nos arquivos de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-144">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="0d5e0-145">Por padrão, apenas a instância de cache padrão tem uma entrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-145">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="0d5e0-146">A instância de cache padrão é a <xref:System.Runtime.Caching.MemoryCache.Default%2A> instância que é devolvida da propriedade.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-146">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="0d5e0-147">Se você definir o atributo nome como "padrão", o elemento usará a instância de cache de memória padrão.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-147">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d5e0-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d5e0-148">Example</span></span>  
 <span data-ttu-id="0d5e0-149">O exemplo a seguir mostra como definir o nome do cache `name` para o nome de entrada de cache padrão, definindo o atributo como "padrão".</span><span class="sxs-lookup"><span data-stu-id="0d5e0-149">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="0d5e0-150">O `cacheMemoryLimitMegabytes` atributo `physicalMemoryPercentage` e o atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-150">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="0d5e0-151">Definir esses atributos como zero significa que a <xref:System.Runtime.Caching.MemoryCache> heurística autosizante da classe é usada.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-151">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="0d5e0-152">A implementação do cache compara a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="0d5e0-152">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d5e0-153">Confira também</span><span class="sxs-lookup"><span data-stu-id="0d5e0-153">See also</span></span>

- [<span data-ttu-id="0d5e0-154">\<memóriaElemento> cache (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="0d5e0-154">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
