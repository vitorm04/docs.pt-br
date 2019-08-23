---
title: Elemento <system.runtime.caching> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67ead643afd34b4c3422d85e6f7876879de477ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927236"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="810c7-102">\<Elemento System. Runtime. Caching > (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="810c7-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="810c7-103">Fornece a configuração para a implementação padrão na <xref:System.Runtime.Caching.ObjectCache> memória por meio `memoryCache` da entrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="810c7-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="810c7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="810c7-104">\<configuration></span></span>  
<span data-ttu-id="810c7-105">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="810c7-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="810c7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="810c7-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="810c7-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="810c7-107">Attributes and Elements</span></span>

<span data-ttu-id="810c7-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="810c7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="810c7-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="810c7-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="810c7-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="810c7-110">Child Elements</span></span>

|<span data-ttu-id="810c7-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="810c7-111">Element</span></span>|<span data-ttu-id="810c7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="810c7-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="810c7-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="810c7-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="810c7-114">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="810c7-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="810c7-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="810c7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="810c7-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="810c7-116">Element</span></span>|<span data-ttu-id="810c7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="810c7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="810c7-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="810c7-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="810c7-119">Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.</span><span class="sxs-lookup"><span data-stu-id="810c7-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="810c7-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="810c7-120">Remarks</span></span>

<span data-ttu-id="810c7-121">As classes nesse namespace fornecem uma maneira de usar recursos de caching como aqueles em ASP.net, mas sem uma dependência no `System.Web` assembly.</span><span class="sxs-lookup"><span data-stu-id="810c7-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="810c7-122">Para obter mais informações, consulte [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="810c7-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="810c7-123">A funcionalidade e os tipos de cache de <xref:System.Runtime.Caching> saída no namespace são novos no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="810c7-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="810c7-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="810c7-124">Example</span></span>

<span data-ttu-id="810c7-125">O exemplo a seguir mostra como configurar um cache baseado na <xref:System.Runtime.Caching.MemoryCache> classe.</span><span class="sxs-lookup"><span data-stu-id="810c7-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="810c7-126">O exemplo mostra como configurar uma instância da entrada para `namedCaches` o cache de memória.</span><span class="sxs-lookup"><span data-stu-id="810c7-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="810c7-127">O nome do cache é definido como o nome da entrada de cache padrão, definindo `name` o atributo como "padrão".</span><span class="sxs-lookup"><span data-stu-id="810c7-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="810c7-128">O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="810c7-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="810c7-129">Definir esses atributos como zero significa que a <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="810c7-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="810c7-130">A implementação de cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="810c7-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="810c7-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="810c7-131">See also</span></span>

- [<span data-ttu-id="810c7-132">\<Elemento de > memoryCache (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="810c7-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
