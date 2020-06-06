---
title: Elemento <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154134"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="5cec0-102">Elemento \<forcePerformanceCounterUniqueSharedMemoryReads></span><span class="sxs-lookup"><span data-stu-id="5cec0-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="5cec0-103">Especifica se o PerfCounter.dll usa a configuração de registro CategoryOptions em um aplicativo do .NET Framework versão 1.1 para determinar se é preciso carregar dados do contador de desempenho da memória global ou da memória compartilhada especifica da categoria.</span><span class="sxs-lookup"><span data-stu-id="5cec0-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a><span data-ttu-id="5cec0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5cec0-104">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cec0-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5cec0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5cec0-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5cec0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cec0-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="5cec0-107">Attributes</span></span>  
  
|<span data-ttu-id="5cec0-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="5cec0-108">Attribute</span></span>|<span data-ttu-id="5cec0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cec0-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5cec0-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="5cec0-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="5cec0-111">Indica se PerfCounter. dll usa a configuração do registro CategoryOptions para determinar se os dados do contador de desempenho devem ser carregados de uma memória compartilhada específica da categoria ou da memória global.</span><span class="sxs-lookup"><span data-stu-id="5cec0-111">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5cec0-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="5cec0-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="5cec0-113">Valor</span><span class="sxs-lookup"><span data-stu-id="5cec0-113">Value</span></span>|<span data-ttu-id="5cec0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cec0-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5cec0-115">PerfCounter. dll não usa a configuração de registro CategoryOptions, que é o padrão.</span><span class="sxs-lookup"><span data-stu-id="5cec0-115">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="5cec0-116">PerfCounter. dll usa a configuração do registro CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="5cec0-116">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5cec0-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5cec0-117">Child Elements</span></span>  
 <span data-ttu-id="5cec0-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5cec0-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5cec0-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5cec0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5cec0-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="5cec0-120">Element</span></span>|<span data-ttu-id="5cec0-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cec0-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5cec0-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5cec0-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5cec0-123">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5cec0-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cec0-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="5cec0-124">Remarks</span></span>  
 <span data-ttu-id="5cec0-125">Nas versões do .NET Framework antes do .NET Framework 4, a versão de PerfCounter. dll que foi carregada corresponde ao tempo de execução que foi carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="5cec0-125">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="5cec0-126">Se um computador tiver o .NET Framework versão 1,1 e o .NET Framework 2,0 instalados, um aplicativo .NET Framework 1,1 carregará a versão .NET Framework 1,1 do PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="5cec0-126">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="5cec0-127">A partir do .NET Framework 4, a versão mais recente instalada do PerfCounter. dll é carregada.</span><span class="sxs-lookup"><span data-stu-id="5cec0-127">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="5cec0-128">Isso significa que um aplicativo .NET Framework 1,1 carregará a versão .NET Framework 4 do PerfCounter. dll se o .NET Framework 4 estiver instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="5cec0-128">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="5cec0-129">Começando com o .NET Framework 4, ao consumir contadores de desempenho, PerfCounter. dll verifica a entrada de registro CategoryOptions para cada provedor para determinar se ele deve ser lido de uma memória compartilhada específica da categoria ou da memória compartilhada global.</span><span class="sxs-lookup"><span data-stu-id="5cec0-129">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="5cec0-130">O .NET Framework 1,1 PerfCounter. dll não lê essa entrada de registro, pois não está ciente da memória compartilhada específica da categoria; Ele sempre lê da memória compartilhada global.</span><span class="sxs-lookup"><span data-stu-id="5cec0-130">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="5cec0-131">Para compatibilidade com versões anteriores, o .NET Framework 4 PerfCounter. dll não verifica a entrada de registro CategoryOptions quando executado em um aplicativo .NET Framework 1,1.</span><span class="sxs-lookup"><span data-stu-id="5cec0-131">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="5cec0-132">Ele simplesmente usa a memória compartilhada global, assim como o .NET Framework 1,1 PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="5cec0-132">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="5cec0-133">No entanto, você pode instruir o .NET Framework 4 PerfCounter. dll para verificar a configuração do registro habilitando o `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento.</span><span class="sxs-lookup"><span data-stu-id="5cec0-133">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5cec0-134">Habilitar o `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento não garante que a memória compartilhada específica da categoria será usada.</span><span class="sxs-lookup"><span data-stu-id="5cec0-134">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="5cec0-135">A configuração habilitada `true` só faz com que PerfCounter. dll referencie a configuração do registro CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="5cec0-135">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="5cec0-136">A configuração padrão para CategoryOptions é usar a memória compartilhada específica da categoria; no entanto, você pode alterar CategoryOptions para indicar que a memória compartilhada global deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="5cec0-136">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="5cec0-137">A chave do registro que contém a configuração CategoryOptions é HKEY_LOCAL_MACHINE \System\CurrentControlSet\Services \\<NomeDaCategoria \> \Performance.</span><span class="sxs-lookup"><span data-stu-id="5cec0-137">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="5cec0-138">Por padrão, CategoryOptions é definido como 3, o que instrui o PerfCounter. dll a usar a memória compartilhada específica da categoria.</span><span class="sxs-lookup"><span data-stu-id="5cec0-138">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="5cec0-139">Se CategoryOptions for definido como 0, PerfCounter. dll usará a memória compartilhada global.</span><span class="sxs-lookup"><span data-stu-id="5cec0-139">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="5cec0-140">Os dados da instância serão reutilizados somente se o nome da instância que está sendo criada for idêntico à instância que está sendo reutilizada.</span><span class="sxs-lookup"><span data-stu-id="5cec0-140">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="5cec0-141">Todas as versões poderão gravar na categoria.</span><span class="sxs-lookup"><span data-stu-id="5cec0-141">All versions will be able to write to the category.</span></span> <span data-ttu-id="5cec0-142">Se CategoryOptions for definido como 1, a memória compartilhada global será usada, mas os dados da instância poderão ser reutilizados se o nome da categoria tiver o mesmo comprimento que a categoria que está sendo reutilizada.</span><span class="sxs-lookup"><span data-stu-id="5cec0-142">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="5cec0-143">As configurações 0 e 1 podem levar a vazamentos de memória e o preenchimento da memória do contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="5cec0-143">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cec0-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5cec0-144">Example</span></span>  
 <span data-ttu-id="5cec0-145">O exemplo a seguir mostra como especificar que PerfCounter. dll deve fazer referência à entrada de registro CategoryOptions para determinar se ela deve usar a memória compartilhada específica da categoria.</span><span class="sxs-lookup"><span data-stu-id="5cec0-145">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cec0-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="5cec0-146">See also</span></span>

- [<span data-ttu-id="5cec0-147">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="5cec0-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5cec0-148">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="5cec0-148">Configuration File Schema</span></span>](../index.md)
