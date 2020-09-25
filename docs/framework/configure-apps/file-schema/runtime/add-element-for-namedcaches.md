---
title: Elemento <add> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: cd920b58290050fcc30ea5d0a1ac113a333902fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195357"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="b6a99-102">Elemento \<add> para \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="b6a99-102">\<add> Element for \<namedCaches></span></span>

<span data-ttu-id="b6a99-103">Adiciona uma `namedCache` entrada à `namedCaches` coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="b6a99-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="b6a99-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6a99-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="b6a99-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="b6a99-105">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6a99-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b6a99-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b6a99-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b6a99-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6a99-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="b6a99-108">Attributes</span></span>  
  
|<span data-ttu-id="b6a99-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="b6a99-109">Attribute</span></span>|<span data-ttu-id="b6a99-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6a99-110">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="b6a99-111">Um valor inteiro que especifica o tamanho máximo permitido (em megabytes) para o qual uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode crescer.</span><span class="sxs-lookup"><span data-stu-id="b6a99-111">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="b6a99-112">O valor padrão é 0, o que significa que a <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="b6a99-112">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="b6a99-113">O nome do cache.</span><span class="sxs-lookup"><span data-stu-id="b6a99-113">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="b6a99-114">Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória do computador fisicamente instalada que pode ser consumida pelo cache.</span><span class="sxs-lookup"><span data-stu-id="b6a99-114">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="b6a99-115">O valor padrão é 0, o que significa que a <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático da classe é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="b6a99-115">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="b6a99-116">Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em percentual que são definidos para a instância de cache.</span><span class="sxs-lookup"><span data-stu-id="b6a99-116">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="b6a99-117">Esse valor é inserido no formato "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="b6a99-117">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6a99-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b6a99-118">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="b6a99-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b6a99-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b6a99-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="b6a99-120">Element</span></span>|<span data-ttu-id="b6a99-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6a99-121">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="b6a99-122">Contém uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="b6a99-122">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6a99-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6a99-123">Remarks</span></span>  

 <span data-ttu-id="b6a99-124">O `add` elemento adiciona uma entrada à `namedCaches` coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="b6a99-124">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="b6a99-125">Você pode usar o elemento [Clear](clear-element-for-namedcaches.md) antes de usar o `add` elemento para ter certeza de que não há outros caches nomeados na coleção.</span><span class="sxs-lookup"><span data-stu-id="b6a99-125">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="b6a99-126">Esse elemento pode ser usado no arquivo de machine.config e no arquivo Web.config.</span><span class="sxs-lookup"><span data-stu-id="b6a99-126">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6a99-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6a99-127">Example</span></span>  

 <span data-ttu-id="b6a99-128">O exemplo a seguir mostra como definir configurações para a `namedCache` entrada padrão para a `namedCaches` coleção de um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="b6a99-128">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b6a99-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="b6a99-129">See also</span></span>

- [<span data-ttu-id="b6a99-130">\<namedCaches> Elemento (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="b6a99-130">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
