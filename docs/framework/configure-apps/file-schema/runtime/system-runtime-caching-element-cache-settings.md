---
title: Elemento <system.runtime.caching> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153848"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="5309a-102">Elemento \<system.runtime.caching> (Configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="5309a-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="5309a-103">Fornece a configuração para a implementação padrão na memória <xref:System.Runtime.Caching.ObjectCache> por meio da `memoryCache` entrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5309a-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.caching>**  
  
## <a name="syntax"></a><span data-ttu-id="5309a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5309a-104">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5309a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5309a-105">Attributes and Elements</span></span>

<span data-ttu-id="5309a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5309a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5309a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="5309a-107">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="5309a-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5309a-108">Child Elements</span></span>

|<span data-ttu-id="5309a-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="5309a-109">Element</span></span>|<span data-ttu-id="5309a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5309a-110">Description</span></span>|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="5309a-111">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="5309a-111">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5309a-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5309a-112">Parent Elements</span></span>  
  
|<span data-ttu-id="5309a-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="5309a-113">Element</span></span>|<span data-ttu-id="5309a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5309a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="5309a-115">Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.</span><span class="sxs-lookup"><span data-stu-id="5309a-115">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5309a-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="5309a-116">Remarks</span></span>

<span data-ttu-id="5309a-117">As classes nesse namespace fornecem uma maneira de usar recursos de caching como aqueles em ASP.NET, mas sem uma dependência no `System.Web` assembly.</span><span class="sxs-lookup"><span data-stu-id="5309a-117">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="5309a-118">Para obter mais informações, consulte [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="5309a-118">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5309a-119">A funcionalidade e os tipos de cache de saída no <xref:System.Runtime.Caching> namespace são novos no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5309a-119">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5309a-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5309a-120">Example</span></span>

<span data-ttu-id="5309a-121">O exemplo a seguir mostra como configurar um cache baseado na <xref:System.Runtime.Caching.MemoryCache> classe.</span><span class="sxs-lookup"><span data-stu-id="5309a-121">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="5309a-122">O exemplo mostra como configurar uma instância da `namedCaches` entrada para o cache de memória.</span><span class="sxs-lookup"><span data-stu-id="5309a-122">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="5309a-123">O nome do cache é definido como o nome da entrada de cache padrão, definindo o `name` atributo como "padrão".</span><span class="sxs-lookup"><span data-stu-id="5309a-123">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="5309a-124">O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="5309a-124">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="5309a-125">Definir esses atributos como zero significa que a <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="5309a-125">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="5309a-126">A implementação de cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="5309a-126">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5309a-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="5309a-127">See also</span></span>

- [<span data-ttu-id="5309a-128">\<memoryCache>Elemento (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="5309a-128">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
