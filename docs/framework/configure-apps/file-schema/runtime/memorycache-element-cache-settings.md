---
title: Elemento <memoryCache> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153978"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="8b05d-102">\<memóriaElemento> cache (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="8b05d-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="8b05d-103">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="8b05d-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="8b05d-104">A <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> classe define um elemento [memoryCache](memorycache-element-cache-settings.md) que você pode usar para configurar o cache.</span><span class="sxs-lookup"><span data-stu-id="8b05d-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="8b05d-105">Várias instâncias da <xref:System.Runtime.Caching.MemoryCache> classe podem ser usadas em um único aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b05d-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="8b05d-106">Cada `memoryCache` elemento no arquivo de configuração <xref:System.Runtime.Caching.MemoryCache> pode conter configurações para uma instância nomeada.</span><span class="sxs-lookup"><span data-stu-id="8b05d-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
<span data-ttu-id="8b05d-107">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b05d-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8b05d-108">&nbsp;&nbsp;[**\<system.runtime.cache>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8b05d-108">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="8b05d-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<memória>de cache**</span><span class="sxs-lookup"><span data-stu-id="8b05d-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b05d-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b05d-110">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="8b05d-111">Type</span><span class="sxs-lookup"><span data-stu-id="8b05d-111">Type</span></span>  
 <span data-ttu-id="8b05d-112"><xref:System.Runtime.Caching.MemoryCache>Classe.</span><span class="sxs-lookup"><span data-stu-id="8b05d-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b05d-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8b05d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8b05d-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8b05d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b05d-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="8b05d-115">Attributes</span></span>  
  
|<span data-ttu-id="8b05d-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="8b05d-116">Attribute</span></span>|<span data-ttu-id="8b05d-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b05d-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="8b05d-118">O tamanho máximo da memória, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> objeto pode crescer.</span><span class="sxs-lookup"><span data-stu-id="8b05d-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="8b05d-119">O valor padrão é 0, <xref:System.Runtime.Caching.MemoryCache> o que significa que a heurística de autotamanho da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="8b05d-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="8b05d-120">O nome da configuração de cache.</span><span class="sxs-lookup"><span data-stu-id="8b05d-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="8b05d-121">A porcentagem de memória física que pode ser usada pelo cache.</span><span class="sxs-lookup"><span data-stu-id="8b05d-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="8b05d-122">O valor padrão é 0, <xref:System.Runtime.Caching.MemoryCache> o que significa que a heurística de autotamanho da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="8b05d-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="8b05d-123">Um valor que indica o intervalo de tempo após o qual a implementação do cache compara a carga de memória atual com os limites de memória absolutos e baseados em porcentagem definidos para a instância do cache.</span><span class="sxs-lookup"><span data-stu-id="8b05d-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="8b05d-124">O valor é inserido no formato "HH:MM:SS".</span><span class="sxs-lookup"><span data-stu-id="8b05d-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b05d-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8b05d-125">Child Elements</span></span>  
  
|<span data-ttu-id="8b05d-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b05d-126">Element</span></span>|<span data-ttu-id="8b05d-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b05d-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b05d-128">\<chamadoCaches></span><span class="sxs-lookup"><span data-stu-id="8b05d-128">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="8b05d-129">Contém um conjunto de definições de configuração para a instância `namedCache`.</span><span class="sxs-lookup"><span data-stu-id="8b05d-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8b05d-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8b05d-130">Parent Elements</span></span>  
  
|<span data-ttu-id="8b05d-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b05d-131">Element</span></span>|<span data-ttu-id="8b05d-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b05d-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b05d-133">\<>de configuração</span><span class="sxs-lookup"><span data-stu-id="8b05d-133">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="8b05d-134">Especifica o elemento raiz em cada arquivo de configuração que é usado pelos aplicativos common language runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b05d-134">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="8b05d-135">\<system.runtime.cache></span><span class="sxs-lookup"><span data-stu-id="8b05d-135">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="8b05d-136">Contém tipos que permitem implementar o cache de saída em aplicativos incorporados ao Quadro .NET.</span><span class="sxs-lookup"><span data-stu-id="8b05d-136">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b05d-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b05d-137">Remarks</span></span>  
 <span data-ttu-id="8b05d-138">A <xref:System.Runtime.Caching.MemoryCache> aula é uma implementação concreta da classe abstrata. <xref:System.Runtime.Caching.ObjectCache></span><span class="sxs-lookup"><span data-stu-id="8b05d-138">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="8b05d-139">As instâncias da <xref:System.Runtime.Caching.MemoryCache> classe podem ser fornecidas com informações de configuração de arquivos de configuração de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8b05d-139">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="8b05d-140">A seção de `namedCaches` configuração [memoryCache](memorycache-element-cache-settings.md) contém uma coleção de configurações.</span><span class="sxs-lookup"><span data-stu-id="8b05d-140">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="8b05d-141">Quando um objeto de cache baseado em memória é `namedCaches` inicializado, ele primeiro tenta encontrar uma entrada que corresponda ao nome no parâmetro que é passado para o construtor de cache de memória.</span><span class="sxs-lookup"><span data-stu-id="8b05d-141">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="8b05d-142">Se `namedCaches` uma entrada for encontrada, as informações de pesquisa e gerenciamento de memória serão recuperadas do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="8b05d-142">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="8b05d-143">O processo de inicialização determina então se quaisquer entradas de configuração foram substituídas, usando a coleção opcional de pares de informações de configuração de nome/valor no construtor.</span><span class="sxs-lookup"><span data-stu-id="8b05d-143">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="8b05d-144">Se você passar qualquer um dos seguintes valores na coleção de name/value pair, esses valores anulam as informações obtidas no arquivo de configuração:</span><span class="sxs-lookup"><span data-stu-id="8b05d-144">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="8b05d-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b05d-145">Example</span></span>  
 <span data-ttu-id="8b05d-146">O exemplo a seguir mostra como <xref:System.Runtime.Caching.MemoryCache> definir o nome do objeto `name` para o nome do objeto de cache padrão definindo o atributo como "Padrão".</span><span class="sxs-lookup"><span data-stu-id="8b05d-146">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="8b05d-147">O `cacheMemoryLimitMegabytes` atributo `physicalMemoryLimitPercentage` e o atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="8b05d-147">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="8b05d-148">Definir esses atributos como <xref:System.Runtime.Caching.MemoryCache> zero significa que a heurística autosizante é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="8b05d-148">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="8b05d-149">A implementação do cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="8b05d-149">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b05d-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="8b05d-150">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="8b05d-151">\<system.runtime.cacheching> Element (Configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="8b05d-151">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="8b05d-152">\<chamadoCaches> Element (Configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="8b05d-152">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
