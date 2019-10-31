---
title: Elemento <system.runtime.caching> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 70573f92f1799a54116bc91f7a39d157a7ae5b36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115512"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="4fe2d-102">\<o elemento System. Runtime. Caching > (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="4fe2d-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="4fe2d-103">Fornece a configuração para a implementação de <xref:System.Runtime.Caching.ObjectCache> na memória padrão por meio da entrada de `memoryCache` no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="4fe2d-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="4fe2d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4fe2d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4fe2d-105">&nbsp;&nbsp; **\<System. Runtime. caching >**</span><span class="sxs-lookup"><span data-stu-id="4fe2d-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe2d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fe2d-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fe2d-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4fe2d-107">Attributes and Elements</span></span>

<span data-ttu-id="4fe2d-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4fe2d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fe2d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="4fe2d-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="4fe2d-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4fe2d-110">Child Elements</span></span>

|<span data-ttu-id="4fe2d-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="4fe2d-111">Element</span></span>|<span data-ttu-id="4fe2d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fe2d-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fe2d-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="4fe2d-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="4fe2d-114">Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="4fe2d-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4fe2d-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4fe2d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4fe2d-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="4fe2d-116">Element</span></span>|<span data-ttu-id="4fe2d-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fe2d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fe2d-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4fe2d-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="4fe2d-119">Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4fe2d-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fe2d-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="4fe2d-120">Remarks</span></span>

<span data-ttu-id="4fe2d-121">As classes nesse namespace fornecem uma maneira de usar recursos de caching como aqueles em ASP.NET, mas sem uma dependência no assembly `System.Web`.</span><span class="sxs-lookup"><span data-stu-id="4fe2d-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="4fe2d-122">Para obter mais informações, consulte [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="4fe2d-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fe2d-123">A funcionalidade e os tipos de cache de saída no namespace <xref:System.Runtime.Caching> são novos no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4fe2d-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fe2d-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4fe2d-124">Example</span></span>

<span data-ttu-id="4fe2d-125">O exemplo a seguir mostra como configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="4fe2d-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="4fe2d-126">O exemplo mostra como configurar uma instância da entrada de `namedCaches` para o cache de memória.</span><span class="sxs-lookup"><span data-stu-id="4fe2d-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="4fe2d-127">O nome do cache é definido como o nome da entrada de cache padrão, definindo o atributo `name` como "padrão".</span><span class="sxs-lookup"><span data-stu-id="4fe2d-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="4fe2d-128">O atributo `cacheMemoryLimitMegabytes` e o atributo `physicalMemoryPercentage` são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="4fe2d-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="4fe2d-129">Definir esses atributos como zero significa que a heurística de dimensionamento automático de <xref:System.Runtime.Caching.MemoryCache> é usada por padrão.</span><span class="sxs-lookup"><span data-stu-id="4fe2d-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="4fe2d-130">A implementação de cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.</span><span class="sxs-lookup"><span data-stu-id="4fe2d-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4fe2d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4fe2d-131">See also</span></span>

- [<span data-ttu-id="4fe2d-132">\<elemento de > memoryCache (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="4fe2d-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
