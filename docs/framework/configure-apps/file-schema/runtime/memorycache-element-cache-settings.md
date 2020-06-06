---
title: Elemento <memoryCache> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153978"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="00613-102">Elemento \<memoryCache> (Configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="00613-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="00613-103">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="00613-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="00613-104">A <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> classe define um elemento [MemoryCache](memorycache-element-cache-settings.md) que você pode usar para configurar o cache.</span><span class="sxs-lookup"><span data-stu-id="00613-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="00613-105">Várias instâncias da <xref:System.Runtime.Caching.MemoryCache> classe podem ser usadas em um único aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00613-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="00613-106">Cada `memoryCache` elemento no arquivo de configuração pode conter configurações para uma <xref:System.Runtime.Caching.MemoryCache> instância nomeada.</span><span class="sxs-lookup"><span data-stu-id="00613-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a><span data-ttu-id="00613-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00613-107">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="00613-108">Type</span><span class="sxs-lookup"><span data-stu-id="00613-108">Type</span></span>  
 <span data-ttu-id="00613-109"><xref:System.Runtime.Caching.MemoryCache>classes.</span><span class="sxs-lookup"><span data-stu-id="00613-109"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00613-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="00613-110">Attributes and Elements</span></span>  
 <span data-ttu-id="00613-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="00613-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00613-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="00613-112">Attributes</span></span>  
  
|<span data-ttu-id="00613-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="00613-113">Attribute</span></span>|<span data-ttu-id="00613-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="00613-114">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="00613-115">O tamanho máximo da memória, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> objeto pode aumentar para.</span><span class="sxs-lookup"><span data-stu-id="00613-115">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="00613-116">O valor padrão é 0, o que significa que a <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="00613-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="00613-117">O nome da configuração de cache.</span><span class="sxs-lookup"><span data-stu-id="00613-117">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="00613-118">A porcentagem de memória física que pode ser usada pelo cache.</span><span class="sxs-lookup"><span data-stu-id="00613-118">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="00613-119">O valor padrão é 0, o que significa que a <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="00613-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="00613-120">Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em percentual que são definidos para a instância de cache.</span><span class="sxs-lookup"><span data-stu-id="00613-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="00613-121">O valor é inserido no formato "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="00613-121">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00613-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="00613-122">Child Elements</span></span>  
  
|<span data-ttu-id="00613-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="00613-123">Element</span></span>|<span data-ttu-id="00613-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="00613-124">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="00613-125">Contém um conjunto de definições de configuração para a instância `namedCache`.</span><span class="sxs-lookup"><span data-stu-id="00613-125">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00613-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="00613-126">Parent Elements</span></span>  
  
|<span data-ttu-id="00613-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="00613-127">Element</span></span>|<span data-ttu-id="00613-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="00613-128">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="00613-129">Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.</span><span class="sxs-lookup"><span data-stu-id="00613-129">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="00613-130">Contém tipos que permitem implementar o cache de saída em aplicativos que são criados no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00613-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00613-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="00613-131">Remarks</span></span>  
 <span data-ttu-id="00613-132">A <xref:System.Runtime.Caching.MemoryCache> classe é uma implementação concreta da classe abstrata <xref:System.Runtime.Caching.ObjectCache> .</span><span class="sxs-lookup"><span data-stu-id="00613-132">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="00613-133">As instâncias da <xref:System.Runtime.Caching.MemoryCache> classe podem ser fornecidas com informações de configuração dos arquivos de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00613-133">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="00613-134">A seção de configuração [MemoryCache](memorycache-element-cache-settings.md) contém uma `namedCaches` coleção de configuração.</span><span class="sxs-lookup"><span data-stu-id="00613-134">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="00613-135">Quando um objeto de cache baseado em memória é inicializado, ele primeiro tenta encontrar uma `namedCaches` entrada que corresponda ao nome no parâmetro que é passado para o construtor de cache de memória.</span><span class="sxs-lookup"><span data-stu-id="00613-135">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="00613-136">Se uma `namedCaches` entrada for encontrada, as informações de gerenciamento de memória e sondagem serão recuperadas do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="00613-136">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="00613-137">Em seguida, o processo de inicialização determina se as entradas de configuração foram substituídas, usando a coleção opcional de pares de nome/valor de informações de configuração no construtor.</span><span class="sxs-lookup"><span data-stu-id="00613-137">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="00613-138">Se você passar qualquer um dos valores a seguir na coleção de pares nome/valor, esses valores substituirão as informações obtidas do arquivo de configuração:</span><span class="sxs-lookup"><span data-stu-id="00613-138">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="00613-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00613-139">Example</span></span>  
 <span data-ttu-id="00613-140">O exemplo a seguir mostra como definir o nome do <xref:System.Runtime.Caching.MemoryCache> objeto como o nome do objeto de cache padrão, definindo o `name` atributo como "default".</span><span class="sxs-lookup"><span data-stu-id="00613-140">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="00613-141">O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryLimitPercentage` atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="00613-141">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="00613-142">Definir esses atributos como zero significa que a <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="00613-142">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="00613-143">A implementação de cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="00613-143">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="00613-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="00613-144">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="00613-145">\<system.runtime.caching>Elemento (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="00613-145">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="00613-146">\<namedCaches>Elemento (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="00613-146">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
