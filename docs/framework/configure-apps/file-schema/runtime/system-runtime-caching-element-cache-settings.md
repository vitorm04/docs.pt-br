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
ms.openlocfilehash: da059e1be7c685eba7792045abf4ffa691525d2e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131350"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="2154f-102">\<System.Runtime.Caching > (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="2154f-102">\<system.runtime.caching> Element (Cache Settings)</span></span>
<span data-ttu-id="2154f-103">Fornece configuração para a padrão de memória <xref:System.Runtime.Caching.ObjectCache> implementação por meio de `memoryCache` entrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2154f-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="2154f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2154f-104">\<configuration></span></span>  
<span data-ttu-id="2154f-105">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="2154f-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2154f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2154f-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2154f-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2154f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2154f-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2154f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2154f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="2154f-109">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="2154f-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2154f-110">Child Elements</span></span>  
  
|<span data-ttu-id="2154f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="2154f-111">Element</span></span>|<span data-ttu-id="2154f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2154f-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2154f-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="2154f-113">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="2154f-114">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="2154f-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2154f-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2154f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2154f-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="2154f-116">Element</span></span>|<span data-ttu-id="2154f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2154f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2154f-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2154f-118">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="2154f-119">Especifica o elemento raiz em cada arquivo de configuração que é usado pelo common language runtime e [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2154f-119">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2154f-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="2154f-120">Remarks</span></span>  
 <span data-ttu-id="2154f-121">As classes nesse namespace fornecem uma maneira de usar recursos de armazenamento em cache, como aqueles no ASP.NET, mas sem uma dependência no `System.Web` assembly.</span><span class="sxs-lookup"><span data-stu-id="2154f-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="2154f-122">Para obter mais informações, consulte [cache em aplicativos do .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="2154f-122">For more information, see [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2154f-123">A saída de cache de funcionalidade e tipos na <xref:System.Runtime.Caching> namespace são novos no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2154f-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="2154f-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2154f-124">Example</span></span>  
 <span data-ttu-id="2154f-125">O exemplo a seguir mostra como configurar um cache que se baseia o <xref:System.Runtime.Caching.MemoryCache> classe.</span><span class="sxs-lookup"><span data-stu-id="2154f-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="2154f-126">O exemplo mostra como configurar uma instância da `namedCaches` entrada para o cache de memória.</span><span class="sxs-lookup"><span data-stu-id="2154f-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="2154f-127">O nome do cache é definido para o nome de entrada de cache padrão definindo a `name` atributo como "default".</span><span class="sxs-lookup"><span data-stu-id="2154f-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="2154f-128">O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="2154f-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="2154f-129">Definir esses atributos como zero significa que o <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="2154f-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="2154f-130">A implementação de cache deve comparar a carga de memória atual em relação as limites de memória absoluto e baseado em percentual cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="2154f-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2154f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2154f-131">See also</span></span>

- [<span data-ttu-id="2154f-132">\<memoryCache > (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="2154f-132">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
