---
title: Elemento <add> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: fd6668a551663470a97b07ff131710dbe92a91f5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659025"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="8f63f-102">\<Adicionar > elemento para \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="8f63f-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="8f63f-103">Adiciona uma `namedCache` entrada `namedCaches` à coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="8f63f-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="8f63f-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="8f63f-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="8f63f-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="8f63f-105">\<memoryCache></span></span>  
<span data-ttu-id="8f63f-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="8f63f-106">\<namedCaches></span></span>  
<span data-ttu-id="8f63f-107">\<add></span><span class="sxs-lookup"><span data-stu-id="8f63f-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f63f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f63f-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="8f63f-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="8f63f-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f63f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8f63f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8f63f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8f63f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f63f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f63f-112">Attributes</span></span>  
  
|<span data-ttu-id="8f63f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8f63f-113">Attribute</span></span>|<span data-ttu-id="8f63f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f63f-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="8f63f-115">Um valor inteiro que especifica o tamanho máximo permitido (em megabytes) para o qual uma instância <xref:System.Runtime.Caching.MemoryCache> de um pode crescer.</span><span class="sxs-lookup"><span data-stu-id="8f63f-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="8f63f-116">O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística de dimensionamento automático da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="8f63f-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="8f63f-117">O nome do cache.</span><span class="sxs-lookup"><span data-stu-id="8f63f-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="8f63f-118">Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória do computador fisicamente instalada que pode ser consumida pelo cache.</span><span class="sxs-lookup"><span data-stu-id="8f63f-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="8f63f-119">O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística de dimensionamento automático da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="8f63f-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="8f63f-120">Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em percentual que são definidos para a instância de cache.</span><span class="sxs-lookup"><span data-stu-id="8f63f-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="8f63f-121">Esse valor é inserido no formato "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="8f63f-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f63f-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8f63f-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="8f63f-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8f63f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8f63f-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f63f-124">Element</span></span>|<span data-ttu-id="8f63f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f63f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f63f-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="8f63f-126">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="8f63f-127">Contém uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="8f63f-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f63f-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f63f-128">Remarks</span></span>  
 <span data-ttu-id="8f63f-129">O `add` elemento adiciona uma entrada `namedCaches` à coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="8f63f-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="8f63f-130">Você pode usar o elemento [Clear](clear-element-for-namedcaches.md) antes de usar o `add` elemento para ter certeza de que não há outros caches nomeados na coleção.</span><span class="sxs-lookup"><span data-stu-id="8f63f-130">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="8f63f-131">Esse elemento pode ser usado no arquivo Machine. config e no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="8f63f-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f63f-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f63f-132">Example</span></span>  
 <span data-ttu-id="8f63f-133">O exemplo a seguir mostra como definir configurações para a entrada `namedCache` padrão para a `namedCaches` coleção de um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="8f63f-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8f63f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f63f-134">See also</span></span>

- [<span data-ttu-id="8f63f-135">\<Elemento de > namedCaches (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="8f63f-135">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
