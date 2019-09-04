---
title: Elemento <add> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 076d940e0c15cf48013480fef68b8fac42cf76e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252886"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="1d0b4-102">\<Adicionar > elemento para \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="1d0b4-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="1d0b4-103">Adiciona uma `namedCache` entrada `namedCaches` à coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="1d0b4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1d0b4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1d0b4-105">&nbsp;&nbsp;[ **\<sistema. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1d0b4-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="1d0b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> memoryCache**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1d0b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="1d0b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> namedCaches**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1d0b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="1d0b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="1d0b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d0b4-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d0b4-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="1d0b4-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="1d0b4-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d0b4-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1d0b4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1d0b4-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d0b4-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="1d0b4-113">Attributes</span></span>  
  
|<span data-ttu-id="1d0b4-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="1d0b4-114">Attribute</span></span>|<span data-ttu-id="1d0b4-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d0b4-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="1d0b4-116">Um valor inteiro que especifica o tamanho máximo permitido (em megabytes) para o qual uma instância <xref:System.Runtime.Caching.MemoryCache> de um pode crescer.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="1d0b4-117">O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística de dimensionamento automático da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="1d0b4-118">O nome do cache.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="1d0b4-119">Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória do computador fisicamente instalada que pode ser consumida pelo cache.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="1d0b4-120">O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística de dimensionamento automático da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="1d0b4-121">Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em percentual que são definidos para a instância de cache.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="1d0b4-122">Esse valor é inserido no formato "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="1d0b4-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d0b4-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1d0b4-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="1d0b4-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1d0b4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1d0b4-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d0b4-125">Element</span></span>|<span data-ttu-id="1d0b4-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d0b4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d0b4-127">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="1d0b4-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="1d0b4-128">Contém uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d0b4-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d0b4-129">Remarks</span></span>  
 <span data-ttu-id="1d0b4-130">O `add` elemento adiciona uma entrada `namedCaches` à coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="1d0b4-131">Você pode usar o elemento [Clear](clear-element-for-namedcaches.md) antes de usar o `add` elemento para ter certeza de que não há outros caches nomeados na coleção.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="1d0b4-132">Esse elemento pode ser usado no arquivo Machine. config e no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d0b4-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d0b4-133">Example</span></span>  
 <span data-ttu-id="1d0b4-134">O exemplo a seguir mostra como definir configurações para a entrada `namedCache` padrão para a `namedCaches` coleção de um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="1d0b4-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d0b4-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d0b4-135">See also</span></span>

- [<span data-ttu-id="1d0b4-136">\<Elemento de > namedCaches (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="1d0b4-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
