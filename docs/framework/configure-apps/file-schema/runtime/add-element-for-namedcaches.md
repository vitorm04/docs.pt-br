---
title: '&lt;Adicionar&gt; elemento para &lt;namedCaches&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0baafcb53bf79a25618dad56c2dcf1412e48624b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a><span data-ttu-id="9b4a5-102">&lt;Adicionar&gt; elemento para &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="9b4a5-102">&lt;add&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="9b4a5-103">Adiciona um `namedCache` entrada para o `namedCaches` coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="9b4a5-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="9b4a5-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="9b4a5-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="9b4a5-105">\<memoryCache></span></span>  
<span data-ttu-id="9b4a5-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="9b4a5-106">\<namedCaches></span></span>  
<span data-ttu-id="9b4a5-107">\<add></span><span class="sxs-lookup"><span data-stu-id="9b4a5-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b4a5-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b4a5-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="9b4a5-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="9b4a5-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b4a5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9b4a5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9b4a5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b4a5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9b4a5-112">Attributes</span></span>  
  
|<span data-ttu-id="9b4a5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="9b4a5-113">Attribute</span></span>|<span data-ttu-id="9b4a5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b4a5-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="9b4a5-115">Um valor inteiro que especifica o tamanho máximo (em megabytes) que uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode atingir.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="9b4a5-116">O valor padrão é 0, o que significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático da classe é usadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="9b4a5-117">O nome do cache.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="9b4a5-118">Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória instalada fisicamente do computador que pode ser consumida pelo cache.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="9b4a5-119">O valor padrão é 0, o que significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático da classe é usadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="9b4a5-120">Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual em relação as limites de memória absoluto e baseadas em porcentagens que são definidas para a instância de cache.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="9b4a5-121">Esse valor é inserido no formato "Hh".</span><span class="sxs-lookup"><span data-stu-id="9b4a5-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b4a5-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9b4a5-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="9b4a5-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9b4a5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9b4a5-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="9b4a5-124">Element</span></span>|<span data-ttu-id="9b4a5-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b4a5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b4a5-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="9b4a5-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="9b4a5-127">Contém uma coleção de definições de configuração para nomeado <xref:System.Runtime.Caching.MemoryCache> instâncias.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b4a5-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b4a5-128">Remarks</span></span>  
 <span data-ttu-id="9b4a5-129">O `add` elemento adiciona uma entrada para o `namedCaches` coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="9b4a5-130">Você pode usar o [limpar](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) elemento antes de usar o `add` elemento certificar-se de que não haja nenhum outro denominado caches na coleção.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="9b4a5-131">Esse elemento pode ser usado no arquivo Machine. config e no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b4a5-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b4a5-132">Example</span></span>  
 <span data-ttu-id="9b4a5-133">O exemplo a seguir mostra como definir as configurações para o padrão `namedCache` entrada para o `namedCaches` coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="9b4a5-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b4a5-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b4a5-134">See Also</span></span>  
 [<span data-ttu-id="9b4a5-135">\<namedCaches > elemento (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="9b4a5-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
