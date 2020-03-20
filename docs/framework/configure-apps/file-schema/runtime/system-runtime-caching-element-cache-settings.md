---
title: Elemento <system.runtime.caching> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153848"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="8e172-102">\<system.runtime.cacheching> Element (Configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="8e172-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="8e172-103">Fornece configuração para a <xref:System.Runtime.Caching.ObjectCache> implementação `memoryCache` in-memory padrão através da entrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="8e172-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="8e172-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8e172-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8e172-105">&nbsp;&nbsp;**\<system.runtime.cache>**</span><span class="sxs-lookup"><span data-stu-id="8e172-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e172-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e172-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e172-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8e172-107">Attributes and Elements</span></span>

<span data-ttu-id="8e172-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8e172-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e172-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e172-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="8e172-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8e172-110">Child Elements</span></span>

|<span data-ttu-id="8e172-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e172-111">Element</span></span>|<span data-ttu-id="8e172-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e172-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e172-113">\<memória>de cache</span><span class="sxs-lookup"><span data-stu-id="8e172-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="8e172-114">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="8e172-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e172-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8e172-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8e172-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e172-116">Element</span></span>|<span data-ttu-id="8e172-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e172-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e172-118">\<>de configuração</span><span class="sxs-lookup"><span data-stu-id="8e172-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="8e172-119">Especifica o elemento raiz em cada arquivo de configuração que é usado pelos aplicativos common language runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e172-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e172-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e172-120">Remarks</span></span>

<span data-ttu-id="8e172-121">As aulas neste namespace fornecem uma maneira de usar instalações de cache `System.Web` como as de ASP.NET, mas sem dependência da montagem.</span><span class="sxs-lookup"><span data-stu-id="8e172-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="8e172-122">Para obter mais informações, consulte [Cache em .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="8e172-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e172-123">A funcionalidade de cache de <xref:System.Runtime.Caching> saída e os tipos no namespace são novos no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8e172-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e172-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e172-124">Example</span></span>

<span data-ttu-id="8e172-125">O exemplo a seguir mostra como configurar um <xref:System.Runtime.Caching.MemoryCache> cache baseado na classe.</span><span class="sxs-lookup"><span data-stu-id="8e172-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="8e172-126">O exemplo mostra como configurar uma `namedCaches` instância da entrada para cache de memória.</span><span class="sxs-lookup"><span data-stu-id="8e172-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="8e172-127">O nome do cache é definido como nome `name` de entrada de cache padrão definindo o atributo como "Padrão".</span><span class="sxs-lookup"><span data-stu-id="8e172-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="8e172-128">O `cacheMemoryLimitMegabytes` atributo `physicalMemoryPercentage` e o atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="8e172-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="8e172-129">Definir esses atributos como <xref:System.Runtime.Caching.MemoryCache> zero significa que a heurística autosizante é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="8e172-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="8e172-130">A implementação do cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="8e172-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e172-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="8e172-131">See also</span></span>

- [<span data-ttu-id="8e172-132">\<memóriaElemento> cache (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="8e172-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
