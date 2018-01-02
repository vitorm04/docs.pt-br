---
title: "&lt;System.Runtime.Caching&gt; elemento (configurações de Cache)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83964d3a6e07267eaa946fa306301bc6d0d16e8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemruntimecachinggt-element-cache-settings"></a><span data-ttu-id="d90b1-102">&lt;System.Runtime.Caching&gt; elemento (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="d90b1-102">&lt;system.runtime.caching&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="d90b1-103">Fornece configuração para a padrão de memória <xref:System.Runtime.Caching.ObjectCache> implementação por meio de `memoryCache` entrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d90b1-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="d90b1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d90b1-104">\<configuration></span></span>  
<span data-ttu-id="d90b1-105">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="d90b1-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d90b1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d90b1-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d90b1-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d90b1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d90b1-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d90b1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d90b1-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d90b1-109">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="d90b1-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d90b1-110">Child Elements</span></span>  
  
|<span data-ttu-id="d90b1-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="d90b1-111">Element</span></span>|<span data-ttu-id="d90b1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d90b1-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d90b1-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="d90b1-113">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="d90b1-114">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="d90b1-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d90b1-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d90b1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d90b1-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="d90b1-116">Element</span></span>|<span data-ttu-id="d90b1-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d90b1-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d90b1-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d90b1-118">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="d90b1-119">Especifica o elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d90b1-119">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d90b1-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="d90b1-120">Remarks</span></span>  
 <span data-ttu-id="d90b1-121">As classes nesse namespace fornecem uma maneira de usar recursos de cache como aqueles no ASP.NET, mas sem uma dependência no `System.Web` assembly.</span><span class="sxs-lookup"><span data-stu-id="d90b1-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="d90b1-122">Para obter mais informações, consulte [cache em aplicativos do .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="d90b1-122">For more information, see [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d90b1-123">A saída de cache de funcionalidade e tipos no <xref:System.Runtime.Caching> namespace são novos no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d90b1-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="d90b1-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d90b1-124">Example</span></span>  
 <span data-ttu-id="d90b1-125">O exemplo a seguir mostra como configurar um cache que se baseia o <xref:System.Runtime.Caching.MemoryCache> classe.</span><span class="sxs-lookup"><span data-stu-id="d90b1-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="d90b1-126">O exemplo mostra como configurar uma instância de `namedCaches` entrada de cache de memória.</span><span class="sxs-lookup"><span data-stu-id="d90b1-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="d90b1-127">O nome do cache é definido para o nome de entrada de cache padrão definindo o `name` atributo como "padrão".</span><span class="sxs-lookup"><span data-stu-id="d90b1-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="d90b1-128">O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="d90b1-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="d90b1-129">Definir esses atributos como zero significa que o <xref:System.Runtime.Caching.MemoryCache> dimensionando heurística é usadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="d90b1-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="d90b1-130">A implementação de cache deve comparar a carga de memória atual em relação as limites de memória absoluto e baseadas em porcentagens cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="d90b1-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d90b1-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d90b1-131">See Also</span></span>  
 [<span data-ttu-id="d90b1-132">\<memoryCache > elemento (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="d90b1-132">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
