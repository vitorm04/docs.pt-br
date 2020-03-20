---
title: Elemento <add> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154499"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="94b0a-102">\<adicionar> \<Element para> chamados Caches</span><span class="sxs-lookup"><span data-stu-id="94b0a-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="94b0a-103">Adiciona `namedCache` uma entrada `namedCaches` à coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="94b0a-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="94b0a-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="94b0a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="94b0a-105">&nbsp;&nbsp;[**\<system.runtime.cache>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="94b0a-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="94b0a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memória>de cache**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="94b0a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="94b0a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<chamadoCaches>**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="94b0a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="94b0a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**</span><span class="sxs-lookup"><span data-stu-id="94b0a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94b0a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94b0a-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="94b0a-110">Type</span><span class="sxs-lookup"><span data-stu-id="94b0a-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94b0a-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="94b0a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="94b0a-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="94b0a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94b0a-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="94b0a-113">Attributes</span></span>  
  
|<span data-ttu-id="94b0a-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="94b0a-114">Attribute</span></span>|<span data-ttu-id="94b0a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="94b0a-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="94b0a-116">Um valor inteiro que especifica o tamanho máximo permitido (em megabytes) que uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode crescer.</span><span class="sxs-lookup"><span data-stu-id="94b0a-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="94b0a-117">O valor padrão é 0, <xref:System.Runtime.Caching.MemoryCache> o que significa que a heurística autosizante da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="94b0a-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="94b0a-118">O nome do cache.</span><span class="sxs-lookup"><span data-stu-id="94b0a-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="94b0a-119">Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória do computador fisicamente instalada que pode ser consumida pelo cache.</span><span class="sxs-lookup"><span data-stu-id="94b0a-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="94b0a-120">O valor padrão é 0, <xref:System.Runtime.Caching.MemoryCache> o que significa que a heurística autosizante da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="94b0a-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="94b0a-121">Um valor que indica o intervalo de tempo após o qual a implementação do cache compara a carga de memória atual com os limites de memória absolutos e baseados em porcentagem definidos para a instância do cache.</span><span class="sxs-lookup"><span data-stu-id="94b0a-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="94b0a-122">Esse valor é inserido no formato "HH:MM:SS".</span><span class="sxs-lookup"><span data-stu-id="94b0a-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94b0a-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="94b0a-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="94b0a-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="94b0a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="94b0a-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="94b0a-125">Element</span></span>|<span data-ttu-id="94b0a-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="94b0a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94b0a-127">\<chamadoCaches></span><span class="sxs-lookup"><span data-stu-id="94b0a-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="94b0a-128">Contém uma coleção de configurações <xref:System.Runtime.Caching.MemoryCache> para as instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="94b0a-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94b0a-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="94b0a-129">Remarks</span></span>  
 <span data-ttu-id="94b0a-130">O `add` elemento adiciona uma `namedCaches` entrada à coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="94b0a-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="94b0a-131">Você pode [clear](clear-element-for-namedcaches.md) usar o elemento `add` claro antes de usar o elemento para ter certeza de que não há outros caches nomeados na coleção.</span><span class="sxs-lookup"><span data-stu-id="94b0a-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="94b0a-132">Este elemento pode ser usado no arquivo machine.config e no arquivo Web.config.</span><span class="sxs-lookup"><span data-stu-id="94b0a-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94b0a-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94b0a-133">Example</span></span>  
 <span data-ttu-id="94b0a-134">O exemplo a seguir mostra como `namedCache` definir as `namedCaches` configurações para a entrada padrão na coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="94b0a-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="94b0a-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="94b0a-135">See also</span></span>

- [<span data-ttu-id="94b0a-136">\<chamadoCaches> Element (Configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="94b0a-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
