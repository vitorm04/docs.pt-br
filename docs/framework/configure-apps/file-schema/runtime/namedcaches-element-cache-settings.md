---
title: Elemento <namedCaches> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 9cedd462aa539745ddab844dff158912914cb024
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663575"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="13e13-102">\<Elemento de > namedCaches (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="13e13-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="13e13-103">Especifica uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="13e13-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="13e13-104">A <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Propriedade faz referência à coleção de definições de configuração de um `namedCaches` ou mais elementos do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="13e13-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
 <span data-ttu-id="13e13-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="13e13-105">\<configuration></span></span>  
<span data-ttu-id="13e13-106">\<sistema. Runtime. Caching ></span><span class="sxs-lookup"><span data-stu-id="13e13-106">\< system.runtime.caching></span></span>  
<span data-ttu-id="13e13-107">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="13e13-107">\<memoryCache></span></span>  
<span data-ttu-id="13e13-108">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="13e13-108">\<namedCaches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e13-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13e13-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="13e13-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="13e13-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13e13-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13e13-111">Attributes and Elements</span></span>  
 <span data-ttu-id="13e13-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="13e13-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13e13-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="13e13-113">Attributes</span></span>  
  
|<span data-ttu-id="13e13-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="13e13-114">Attribute</span></span>|<span data-ttu-id="13e13-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="13e13-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="13e13-116">Um valor inteiro que especifica o tamanho máximo permitido, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode aumentar para.</span><span class="sxs-lookup"><span data-stu-id="13e13-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="13e13-117">O valor padrão é 0, o que significa que a heurística de dimensionamento automático <xref:System.Runtime.Caching.MemoryCache> da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="13e13-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="13e13-118">O nome do cache.</span><span class="sxs-lookup"><span data-stu-id="13e13-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="13e13-119">Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória do computador fisicamente instalada que pode ser consumida pelo cache.</span><span class="sxs-lookup"><span data-stu-id="13e13-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="13e13-120">O valor padrão é 0, o que significa que a heurística de dimensionamento automático <xref:System.Runtime.Caching.MemoryCache> da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="13e13-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="13e13-121">Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em percentual que são definidos para a instância de cache.</span><span class="sxs-lookup"><span data-stu-id="13e13-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="13e13-122">Esse valor é inserido no formato "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="13e13-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13e13-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="13e13-123">Child Elements</span></span>  
  
|<span data-ttu-id="13e13-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="13e13-124">Element</span></span>|<span data-ttu-id="13e13-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="13e13-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13e13-126">\<add></span><span class="sxs-lookup"><span data-stu-id="13e13-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="13e13-127">Adiciona um cache nomeado à coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="13e13-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="13e13-128">\<clear></span><span class="sxs-lookup"><span data-stu-id="13e13-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="13e13-129">Limpa a coleção `namedCaches` de um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="13e13-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="13e13-130">\<remove></span><span class="sxs-lookup"><span data-stu-id="13e13-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="13e13-131">Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="13e13-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13e13-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="13e13-132">Parent Elements</span></span>  
  
|<span data-ttu-id="13e13-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="13e13-133">Element</span></span>|<span data-ttu-id="13e13-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="13e13-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13e13-135">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="13e13-135">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="13e13-136">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="13e13-136">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13e13-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="13e13-137">Remarks</span></span>  
 <span data-ttu-id="13e13-138">A seção de configuração de cache de memória do arquivo Web. config `add`pode `remove`conter atributos `clear` , e para `namedCaches` a coleção.</span><span class="sxs-lookup"><span data-stu-id="13e13-138">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="13e13-139">Cada `namedCaches` entrada é identificada exclusivamente `name` pelo atributo.</span><span class="sxs-lookup"><span data-stu-id="13e13-139">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="13e13-140">Você pode recuperar instâncias de entradas de cache de memória referenciando as informações nos arquivos de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13e13-140">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="13e13-141">Por padrão, somente a instância de cache padrão tem uma entrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="13e13-141">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="13e13-142">A instância de cache padrão é a instância que é retornada da <xref:System.Runtime.Caching.MemoryCache.Default%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="13e13-142">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="13e13-143">Se você definir o atributo Name como "default", o elemento usará a instância de cache de memória padrão.</span><span class="sxs-lookup"><span data-stu-id="13e13-143">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13e13-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13e13-144">Example</span></span>  
 <span data-ttu-id="13e13-145">O exemplo a seguir mostra como definir o nome do cache para o nome de entrada de cache padrão, definindo `name` o atributo como "default".</span><span class="sxs-lookup"><span data-stu-id="13e13-145">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="13e13-146">O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="13e13-146">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="13e13-147">Definir esses atributos como zero significa que a heurística de dimensionamento automático da <xref:System.Runtime.Caching.MemoryCache> classe é usada.</span><span class="sxs-lookup"><span data-stu-id="13e13-147">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="13e13-148">A implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="13e13-148">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13e13-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13e13-149">See also</span></span>

- [<span data-ttu-id="13e13-150">\<Elemento de > memoryCache (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="13e13-150">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
