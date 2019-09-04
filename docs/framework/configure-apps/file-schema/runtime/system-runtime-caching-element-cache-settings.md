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
ms.openlocfilehash: e36e2ed96a0748a69f2bd9ee32432901f0bf0898
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252285"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="faeeb-102">\<Elemento System. Runtime. Caching > (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="faeeb-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="faeeb-103">Fornece a configuração para a implementação padrão na <xref:System.Runtime.Caching.ObjectCache> memória por meio `memoryCache` da entrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="faeeb-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="faeeb-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="faeeb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="faeeb-105">&nbsp;&nbsp; **\<sistema. Runtime. Caching >**</span><span class="sxs-lookup"><span data-stu-id="faeeb-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faeeb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="faeeb-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="faeeb-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="faeeb-107">Attributes and Elements</span></span>

<span data-ttu-id="faeeb-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="faeeb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="faeeb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="faeeb-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="faeeb-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="faeeb-110">Child Elements</span></span>

|<span data-ttu-id="faeeb-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="faeeb-111">Element</span></span>|<span data-ttu-id="faeeb-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="faeeb-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="faeeb-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="faeeb-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="faeeb-114">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="faeeb-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="faeeb-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="faeeb-115">Parent Elements</span></span>  
  
|<span data-ttu-id="faeeb-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="faeeb-116">Element</span></span>|<span data-ttu-id="faeeb-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="faeeb-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="faeeb-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="faeeb-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="faeeb-119">Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.</span><span class="sxs-lookup"><span data-stu-id="faeeb-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faeeb-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="faeeb-120">Remarks</span></span>

<span data-ttu-id="faeeb-121">As classes nesse namespace fornecem uma maneira de usar recursos de caching como aqueles em ASP.net, mas sem uma dependência no `System.Web` assembly.</span><span class="sxs-lookup"><span data-stu-id="faeeb-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="faeeb-122">Para obter mais informações, consulte [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="faeeb-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="faeeb-123">A funcionalidade e os tipos de cache de <xref:System.Runtime.Caching> saída no namespace são novos no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="faeeb-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="faeeb-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="faeeb-124">Example</span></span>

<span data-ttu-id="faeeb-125">O exemplo a seguir mostra como configurar um cache baseado na <xref:System.Runtime.Caching.MemoryCache> classe.</span><span class="sxs-lookup"><span data-stu-id="faeeb-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="faeeb-126">O exemplo mostra como configurar uma instância da entrada para `namedCaches` o cache de memória.</span><span class="sxs-lookup"><span data-stu-id="faeeb-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="faeeb-127">O nome do cache é definido como o nome da entrada de cache padrão, definindo `name` o atributo como "padrão".</span><span class="sxs-lookup"><span data-stu-id="faeeb-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="faeeb-128">O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="faeeb-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="faeeb-129">Definir esses atributos como zero significa que a <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="faeeb-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="faeeb-130">A implementação de cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="faeeb-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="faeeb-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faeeb-131">See also</span></span>

- [<span data-ttu-id="faeeb-132">\<Elemento de > memoryCache (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="faeeb-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
