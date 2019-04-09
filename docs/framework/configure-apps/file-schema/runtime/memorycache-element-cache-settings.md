---
title: <memoryCache> Elemento (configurações de Cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: dbb46e7cf2580635add9d3100c8177c99cbae6bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126809"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="fb3ac-102">\<memoryCache > (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="fb3ac-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="fb3ac-103">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="fb3ac-104">O <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> classe define um [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) elemento que você pode usar para configurar o cache.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="fb3ac-105">Várias instâncias do <xref:System.Runtime.Caching.MemoryCache> classe pode ser usada em um único aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="fb3ac-106">Cada `memoryCache` elemento no arquivo de configuração pode conter configurações para uma nomeada <xref:System.Runtime.Caching.MemoryCache> instância.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
 <span data-ttu-id="fb3ac-107">\<configuration></span><span class="sxs-lookup"><span data-stu-id="fb3ac-107">\<configuration></span></span>  
<span data-ttu-id="fb3ac-108">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="fb3ac-108">\<system.runtime.caching></span></span>  
<span data-ttu-id="fb3ac-109">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="fb3ac-109">\<memoryCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb3ac-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb3ac-110">Syntax</span></span>  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="fb3ac-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="fb3ac-111">Type</span></span>  
 <xref:System.Runtime.Caching.MemoryCache> <span data-ttu-id="fb3ac-112">.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-112">class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb3ac-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fb3ac-113">Attributes and Elements</span></span>  
 <span data-ttu-id="fb3ac-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb3ac-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="fb3ac-115">Attributes</span></span>  
  
|<span data-ttu-id="fb3ac-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="fb3ac-116">Attribute</span></span>|<span data-ttu-id="fb3ac-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb3ac-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="fb3ac-118">O tamanho máximo de memória, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> objeto pode atingir.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="fb3ac-119">O valor padrão é 0, o que significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de autosize da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="fb3ac-120">O nome da configuração do cache.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="fb3ac-121">A porcentagem de memória física que pode ser usada pelo cache.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="fb3ac-122">O valor padrão é 0, o que significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de autosize da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="fb3ac-123">Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absoluto e baseado em percentual que são definidas para a instância do cache.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="fb3ac-124">O valor é inserido no formato "Hh".</span><span class="sxs-lookup"><span data-stu-id="fb3ac-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb3ac-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fb3ac-125">Child Elements</span></span>  
  
|<span data-ttu-id="fb3ac-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb3ac-126">Element</span></span>|<span data-ttu-id="fb3ac-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb3ac-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb3ac-128">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="fb3ac-128">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="fb3ac-129">Contém um conjunto de definições de configuração para a instância `namedCache`.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb3ac-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fb3ac-130">Parent Elements</span></span>  
  
|<span data-ttu-id="fb3ac-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb3ac-131">Element</span></span>|<span data-ttu-id="fb3ac-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb3ac-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb3ac-133">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="fb3ac-133">\<system.runtime.caching></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="fb3ac-134">Contém tipos que permitem implementar o cache de saída em aplicativos que integram o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fb3ac-134">Contains types that let you implement output caching in applications that are built into the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb3ac-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb3ac-135">Remarks</span></span>  
 <span data-ttu-id="fb3ac-136">O <xref:System.Runtime.Caching.MemoryCache> classe é uma implementação concreta do resumo <xref:System.Runtime.Caching.ObjectCache> classe.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-136">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="fb3ac-137">Instâncias do <xref:System.Runtime.Caching.MemoryCache> classe pode ser fornecido com informações de configuração de arquivos de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-137">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="fb3ac-138">O [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) seção de configuração contém um `namedCaches` coleção de configuração.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-138">The [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="fb3ac-139">Quando um objeto de cache baseadas em memória é inicializado, ele primeiro tenta encontrar um `namedCaches` entrada que corresponde ao nome no parâmetro que é passado para o construtor de cache de memória.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-139">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="fb3ac-140">Se um `namedCaches` entrada for encontrada, a sondagem e informações de gerenciamento de memória são recuperados do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-140">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="fb3ac-141">O processo de inicialização, em seguida, determina se todas as entradas de configuração foram substituídas usando a coleção opcional de pares nome/valor das informações de configuração no construtor.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-141">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="fb3ac-142">Se você passar qualquer um dos seguintes valores na coleção de par nome/valor, esses valores substituem as informações obtidas do arquivo de configuração:</span><span class="sxs-lookup"><span data-stu-id="fb3ac-142">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="fb3ac-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb3ac-143">Example</span></span>  
 <span data-ttu-id="fb3ac-144">O exemplo a seguir mostra como definir o nome da <xref:System.Runtime.Caching.MemoryCache> objeto para o nome do objeto de cache padrão definindo a `name` atributo como "default".</span><span class="sxs-lookup"><span data-stu-id="fb3ac-144">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="fb3ac-145">O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryLimitPercentage` atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-145">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="fb3ac-146">Definir esses atributos como zero significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-146">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="fb3ac-147">A implementação de cache deve comparar a carga de memória atual em relação as limites de memória absoluto e baseado em percentual cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="fb3ac-147">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb3ac-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb3ac-148">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="fb3ac-149">\<System.Runtime.Caching > (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="fb3ac-149">\<system.runtime.caching> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="fb3ac-150">\<namedCaches > (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="fb3ac-150">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
