---
title: Elemento <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54bccd134a2f77925e80bfc681770b28c05f77a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252598"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="390df-102">\<Elemento de > forcePerformanceCounterUniqueSharedMemoryReads</span><span class="sxs-lookup"><span data-stu-id="390df-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="390df-103">Especifica se o PerfCounter.dll usa a configuração de registro CategoryOptions em um aplicativo do .NET Framework versão 1.1 para determinar se é preciso carregar dados do contador de desempenho da memória global ou da memória compartilhada especifica da categoria.</span><span class="sxs-lookup"><span data-stu-id="390df-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
<span data-ttu-id="390df-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="390df-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="390df-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="390df-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="390df-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<forcePerformanceCounterUniqueSharedMemoryReads>**</span><span class="sxs-lookup"><span data-stu-id="390df-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="390df-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="390df-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="390df-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="390df-108">Attributes and Elements</span></span>  
 <span data-ttu-id="390df-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="390df-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="390df-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="390df-110">Attributes</span></span>  
  
|<span data-ttu-id="390df-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="390df-111">Attribute</span></span>|<span data-ttu-id="390df-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="390df-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="390df-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="390df-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="390df-114">Indica se PerfCounter. dll usa a configuração do registro CategoryOptions para determinar se os dados do contador de desempenho devem ser carregados de uma memória compartilhada específica da categoria ou da memória global.</span><span class="sxs-lookup"><span data-stu-id="390df-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="390df-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="390df-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="390df-116">Valor</span><span class="sxs-lookup"><span data-stu-id="390df-116">Value</span></span>|<span data-ttu-id="390df-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="390df-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="390df-118">PerfCounter. dll não usa a configuração de registro CategoryOptions, que é o padrão.</span><span class="sxs-lookup"><span data-stu-id="390df-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="390df-119">PerfCounter. dll usa a configuração do registro CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="390df-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="390df-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="390df-120">Child Elements</span></span>  
 <span data-ttu-id="390df-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="390df-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="390df-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="390df-122">Parent Elements</span></span>  
  
|<span data-ttu-id="390df-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="390df-123">Element</span></span>|<span data-ttu-id="390df-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="390df-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="390df-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="390df-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="390df-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="390df-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="390df-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="390df-127">Remarks</span></span>  
 <span data-ttu-id="390df-128">Nas versões do .NET Framework antes do .NET Framework 4, a versão de PerfCounter. dll que foi carregada corresponde ao tempo de execução que foi carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="390df-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="390df-129">Se um computador tiver o .NET Framework versão 1,1 e o .NET Framework 2,0 instalados, um aplicativo .NET Framework 1,1 carregará a versão .NET Framework 1,1 do PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="390df-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="390df-130">A partir do .NET Framework 4, a versão mais recente instalada do PerfCounter. dll é carregada.</span><span class="sxs-lookup"><span data-stu-id="390df-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="390df-131">Isso significa que um aplicativo .NET Framework 1,1 carregará a versão .NET Framework 4 do PerfCounter. dll se o .NET Framework 4 estiver instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="390df-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="390df-132">Começando com o .NET Framework 4, ao consumir contadores de desempenho, PerfCounter. dll verifica a entrada de registro CategoryOptions para cada provedor para determinar se ele deve ser lido de uma memória compartilhada específica da categoria ou da memória compartilhada global.</span><span class="sxs-lookup"><span data-stu-id="390df-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="390df-133">O .NET Framework 1,1 PerfCounter. dll não lê essa entrada de registro, pois não está ciente da memória compartilhada específica da categoria; Ele sempre lê da memória compartilhada global.</span><span class="sxs-lookup"><span data-stu-id="390df-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="390df-134">Para compatibilidade com versões anteriores, o .NET Framework 4 PerfCounter. dll não verifica a entrada de registro CategoryOptions quando executado em um aplicativo .NET Framework 1,1.</span><span class="sxs-lookup"><span data-stu-id="390df-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="390df-135">Ele simplesmente usa a memória compartilhada global, assim como o .NET Framework 1,1 PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="390df-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="390df-136">No entanto, você pode instruir o .NET Framework 4 PerfCounter. dll para verificar a configuração do `<forcePerformanceCounterUniqueSharedMemoryReads>` registro habilitando o elemento.</span><span class="sxs-lookup"><span data-stu-id="390df-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="390df-137">Habilitar o `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento não garante que a memória compartilhada específica da categoria será usada.</span><span class="sxs-lookup"><span data-stu-id="390df-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="390df-138">A `true` configuração habilitada só faz com que PerfCounter. dll referencie a configuração do registro CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="390df-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="390df-139">A configuração padrão para CategoryOptions é usar a memória compartilhada específica da categoria; no entanto, você pode alterar CategoryOptions para indicar que a memória compartilhada global deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="390df-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="390df-140">A chave do registro que contém a configuração CategoryOptions é\\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services <\>NomeDaCategoria \Performance.</span><span class="sxs-lookup"><span data-stu-id="390df-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="390df-141">Por padrão, CategoryOptions é definido como 3, o que instrui o PerfCounter. dll a usar a memória compartilhada específica da categoria.</span><span class="sxs-lookup"><span data-stu-id="390df-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="390df-142">Se CategoryOptions for definido como 0, PerfCounter. dll usará a memória compartilhada global.</span><span class="sxs-lookup"><span data-stu-id="390df-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="390df-143">Os dados da instância serão reutilizados somente se o nome da instância que está sendo criada for idêntico à instância que está sendo reutilizada.</span><span class="sxs-lookup"><span data-stu-id="390df-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="390df-144">Todas as versões poderão gravar na categoria.</span><span class="sxs-lookup"><span data-stu-id="390df-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="390df-145">Se CategoryOptions for definido como 1, a memória compartilhada global será usada, mas os dados da instância poderão ser reutilizados se o nome da categoria tiver o mesmo comprimento que a categoria que está sendo reutilizada.</span><span class="sxs-lookup"><span data-stu-id="390df-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="390df-146">As configurações 0 e 1 podem levar a vazamentos de memória e o preenchimento da memória do contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="390df-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="390df-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="390df-147">Example</span></span>  
 <span data-ttu-id="390df-148">O exemplo a seguir mostra como especificar que PerfCounter. dll deve fazer referência à entrada de registro CategoryOptions para determinar se ela deve usar a memória compartilhada específica da categoria.</span><span class="sxs-lookup"><span data-stu-id="390df-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="390df-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="390df-149">See also</span></span>

- [<span data-ttu-id="390df-150">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="390df-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="390df-151">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="390df-151">Configuration File Schema</span></span>](../index.md)
