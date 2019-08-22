---
title: Elemento <memoryCache> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 46f430f7cf112da40aa3b25bfb280c5014612eae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663612"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="dc3b0-102">\<Elemento de > memoryCache (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="dc3b0-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="dc3b0-103">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="dc3b0-104">A <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> classe define um elemento [MemoryCache](memorycache-element-cache-settings.md) que você pode usar para configurar o cache.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="dc3b0-105">Várias instâncias da <xref:System.Runtime.Caching.MemoryCache> classe podem ser usadas em um único aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="dc3b0-106">Cada `memoryCache` elemento no arquivo de configuração pode conter configurações para uma instância <xref:System.Runtime.Caching.MemoryCache> nomeada.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
 <span data-ttu-id="dc3b0-107">\<configuration></span><span class="sxs-lookup"><span data-stu-id="dc3b0-107">\<configuration></span></span>  
<span data-ttu-id="dc3b0-108">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="dc3b0-108">\<system.runtime.caching></span></span>  
<span data-ttu-id="dc3b0-109">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="dc3b0-109">\<memoryCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc3b0-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc3b0-110">Syntax</span></span>  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="dc3b0-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="dc3b0-111">Type</span></span>  
 <span data-ttu-id="dc3b0-112"><xref:System.Runtime.Caching.MemoryCache>classes.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc3b0-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dc3b0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="dc3b0-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc3b0-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="dc3b0-115">Attributes</span></span>  
  
|<span data-ttu-id="dc3b0-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="dc3b0-116">Attribute</span></span>|<span data-ttu-id="dc3b0-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc3b0-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="dc3b0-118">O tamanho máximo da memória, em megabytes, que uma instância de <xref:System.Runtime.Caching.MemoryCache> um objeto pode aumentar para.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="dc3b0-119">O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística de dimensionamento automático da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="dc3b0-120">O nome da configuração de cache.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="dc3b0-121">A porcentagem de memória física que pode ser usada pelo cache.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="dc3b0-122">O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística de dimensionamento automático da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="dc3b0-123">Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em percentual que são definidos para a instância de cache.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="dc3b0-124">O valor é inserido no formato "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="dc3b0-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc3b0-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dc3b0-125">Child Elements</span></span>  
  
|<span data-ttu-id="dc3b0-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="dc3b0-126">Element</span></span>|<span data-ttu-id="dc3b0-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc3b0-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc3b0-128">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="dc3b0-128">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="dc3b0-129">Contém um conjunto de definições de configuração para a instância `namedCache`.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc3b0-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dc3b0-130">Parent Elements</span></span>  
  
|<span data-ttu-id="dc3b0-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="dc3b0-131">Element</span></span>|<span data-ttu-id="dc3b0-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc3b0-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc3b0-133">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="dc3b0-133">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="dc3b0-134">Contém tipos que permitem implementar o cache de saída em aplicativos que são criados no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-134">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc3b0-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="dc3b0-135">Remarks</span></span>  
 <span data-ttu-id="dc3b0-136">A <xref:System.Runtime.Caching.MemoryCache> classe é uma implementação concreta da classe abstrata <xref:System.Runtime.Caching.ObjectCache> .</span><span class="sxs-lookup"><span data-stu-id="dc3b0-136">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="dc3b0-137">As instâncias da <xref:System.Runtime.Caching.MemoryCache> classe podem ser fornecidas com informações de configuração dos arquivos de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-137">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="dc3b0-138">A seção de configuração [MemoryCache](memorycache-element-cache-settings.md) contém `namedCaches` uma coleção de configuração.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-138">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="dc3b0-139">Quando um objeto de cache baseado em memória é inicializado, ele primeiro tenta encontrar `namedCaches` uma entrada que corresponda ao nome no parâmetro que é passado para o construtor de cache de memória.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-139">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="dc3b0-140">Se uma `namedCaches` entrada for encontrada, as informações de gerenciamento de memória e sondagem serão recuperadas do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-140">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="dc3b0-141">Em seguida, o processo de inicialização determina se as entradas de configuração foram substituídas, usando a coleção opcional de pares de nome/valor de informações de configuração no construtor.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-141">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="dc3b0-142">Se você passar qualquer um dos valores a seguir na coleção de pares nome/valor, esses valores substituirão as informações obtidas do arquivo de configuração:</span><span class="sxs-lookup"><span data-stu-id="dc3b0-142">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="dc3b0-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc3b0-143">Example</span></span>  
 <span data-ttu-id="dc3b0-144">O exemplo a seguir mostra como definir o nome do <xref:System.Runtime.Caching.MemoryCache> objeto como o nome do objeto de cache padrão, definindo o `name` atributo como "default".</span><span class="sxs-lookup"><span data-stu-id="dc3b0-144">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="dc3b0-145">O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryLimitPercentage` atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-145">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="dc3b0-146">Definir esses atributos como zero significa que a <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-146">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="dc3b0-147">A implementação de cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="dc3b0-147">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc3b0-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc3b0-148">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="dc3b0-149">\<Elemento System. Runtime. Caching > (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="dc3b0-149">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="dc3b0-150">\<Elemento de > namedCaches (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="dc3b0-150">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
