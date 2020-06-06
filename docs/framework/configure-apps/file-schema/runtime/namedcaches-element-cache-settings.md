---
title: Elemento <namedCaches> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153952"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="c1b9d-102">Elemento \<namedCaches> (Configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="c1b9d-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="c1b9d-103">Especifica uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="c1b9d-104">A <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> propriedade faz referência à coleção de definições de configuração de um ou mais `namedCaches` elementos do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="c1b9d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1b9d-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="c1b9d-106">Type</span><span class="sxs-lookup"><span data-stu-id="c1b9d-106">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1b9d-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c1b9d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c1b9d-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1b9d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="c1b9d-109">Attributes</span></span>  
  
|<span data-ttu-id="c1b9d-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="c1b9d-110">Attribute</span></span>|<span data-ttu-id="c1b9d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1b9d-111">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="c1b9d-112">Um valor inteiro que especifica o tamanho máximo permitido, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode aumentar para.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-112">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="c1b9d-113">O valor padrão é 0, o que significa que a heurística de dimensionamento automático da <xref:System.Runtime.Caching.MemoryCache> classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-113">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="c1b9d-114">O nome do cache.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-114">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="c1b9d-115">Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória do computador fisicamente instalada que pode ser consumida pelo cache.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-115">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="c1b9d-116">O valor padrão é 0, o que significa que a heurística de dimensionamento automático da <xref:System.Runtime.Caching.MemoryCache> classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-116">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="c1b9d-117">Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em percentual que são definidos para a instância de cache.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-117">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="c1b9d-118">Esse valor é inserido no formato "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="c1b9d-118">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1b9d-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c1b9d-119">Child Elements</span></span>  
  
|<span data-ttu-id="c1b9d-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="c1b9d-120">Element</span></span>|<span data-ttu-id="c1b9d-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1b9d-121">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="c1b9d-122">Adiciona um cache nomeado à coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-122">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="c1b9d-123">Limpa a coleção `namedCaches` de um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-123">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="c1b9d-124">Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-124">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1b9d-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c1b9d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c1b9d-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="c1b9d-126">Element</span></span>|<span data-ttu-id="c1b9d-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1b9d-127">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="c1b9d-128">Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-128">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="c1b9d-129">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-129">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="c1b9d-130">Contém tipos que permitem implementar o cache de saída em aplicativos que são criados no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1b9d-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1b9d-131">Remarks</span></span>  
 <span data-ttu-id="c1b9d-132">A seção de configuração de cache de memória do arquivo Web. config pode conter `add` `remove` atributos, e `clear` para a `namedCaches` coleção.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-132">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="c1b9d-133">Cada `namedCaches` entrada é identificada exclusivamente pelo `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-133">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="c1b9d-134">Você pode recuperar instâncias de entradas de cache de memória referenciando as informações nos arquivos de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-134">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="c1b9d-135">Por padrão, somente a instância de cache padrão tem uma entrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-135">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="c1b9d-136">A instância de cache padrão é a instância que é retornada da <xref:System.Runtime.Caching.MemoryCache.Default%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-136">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="c1b9d-137">Se você definir o atributo Name como "default", o elemento usará a instância de cache de memória padrão.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-137">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1b9d-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c1b9d-138">Example</span></span>  
 <span data-ttu-id="c1b9d-139">O exemplo a seguir mostra como definir o nome do cache para o nome de entrada de cache padrão, definindo o `name` atributo como "default".</span><span class="sxs-lookup"><span data-stu-id="c1b9d-139">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="c1b9d-140">O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-140">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="c1b9d-141">Definir esses atributos como zero significa que a heurística de dimensionamento automático da <xref:System.Runtime.Caching.MemoryCache> classe é usada.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-141">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="c1b9d-142">A implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-142">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1b9d-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="c1b9d-143">See also</span></span>

- [<span data-ttu-id="c1b9d-144">\<memoryCache>Elemento (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="c1b9d-144">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
