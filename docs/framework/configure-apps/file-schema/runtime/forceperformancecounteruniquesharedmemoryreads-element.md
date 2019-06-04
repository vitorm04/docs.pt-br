---
title: Elemento <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26fed0a10b9a25f25a580c7ac9a468cbedeb3671
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489478"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="afaf8-102">\<forcePerformanceCounterUniqueSharedMemoryReads > elemento</span><span class="sxs-lookup"><span data-stu-id="afaf8-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="afaf8-103">Especifica se o PerfCounter.dll usa a configuração de registro CategoryOptions em um aplicativo do .NET Framework versão 1.1 para determinar se é preciso carregar dados do contador de desempenho da memória global ou da memória compartilhada especifica da categoria.</span><span class="sxs-lookup"><span data-stu-id="afaf8-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
 <span data-ttu-id="afaf8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="afaf8-104">\<configuration></span></span>  
<span data-ttu-id="afaf8-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="afaf8-105">\<runtime></span></span>  
<span data-ttu-id="afaf8-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span><span class="sxs-lookup"><span data-stu-id="afaf8-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afaf8-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="afaf8-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afaf8-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="afaf8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="afaf8-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="afaf8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afaf8-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="afaf8-110">Attributes</span></span>  
  
|<span data-ttu-id="afaf8-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="afaf8-111">Attribute</span></span>|<span data-ttu-id="afaf8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="afaf8-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="afaf8-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="afaf8-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="afaf8-114">Indica se o PerfCounter usa a configuração do registro CategoryOptions para determinar se deve carregar dados do contador de desempenho da memória global ou categoria específica memória compartilhada.</span><span class="sxs-lookup"><span data-stu-id="afaf8-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="afaf8-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="afaf8-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="afaf8-116">Valor</span><span class="sxs-lookup"><span data-stu-id="afaf8-116">Value</span></span>|<span data-ttu-id="afaf8-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="afaf8-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="afaf8-118">PerfCounter não usa o CategoryOptions essa configuração de registro é o padrão.</span><span class="sxs-lookup"><span data-stu-id="afaf8-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="afaf8-119">Usa a configuração do registro CategoryOptions PerfCounter.</span><span class="sxs-lookup"><span data-stu-id="afaf8-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afaf8-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="afaf8-120">Child Elements</span></span>  
 <span data-ttu-id="afaf8-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="afaf8-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="afaf8-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="afaf8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="afaf8-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="afaf8-123">Element</span></span>|<span data-ttu-id="afaf8-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="afaf8-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="afaf8-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="afaf8-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="afaf8-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="afaf8-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afaf8-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="afaf8-127">Remarks</span></span>  
 <span data-ttu-id="afaf8-128">Nas versões do .NET Framework antes do .NET Framework 4, a versão do PerfCounter que foi carregado correspondia ao tempo de execução que foi carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="afaf8-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="afaf8-129">Se um computador tiver o .NET Framework versão 1.1 e o [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] instalado, um aplicativo do .NET Framework 1.1 carregaria a versão do .NET Framework 1.1 de PerfCounter.</span><span class="sxs-lookup"><span data-stu-id="afaf8-129">If a computer had both the .NET Framework version 1.1 and the [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="afaf8-130">Começando com o .NET Framework 4, a versão instalada mais recente de PerfCounter é carregada.</span><span class="sxs-lookup"><span data-stu-id="afaf8-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="afaf8-131">Isso significa que um aplicativo do .NET Framework 1.1 carregará a versão do .NET Framework 4 do PerfCounter se o .NET Framework 4 está instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="afaf8-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="afaf8-132">Começando com o .NET Framework 4, durante o consumo de contadores de desempenho, PerfCounter verifica a entrada do registro CategoryOptions para cada provedor determinar se ele deve ler da categoria específica memória compartilhada ou memória compartilhada global.</span><span class="sxs-lookup"><span data-stu-id="afaf8-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="afaf8-133">O PerfCounter do .NET Framework 1.1 não lê essa entrada de registro, porque ele não está ciente da categoria específica memória compartilhada; ele sempre lê na memória compartilhada global.</span><span class="sxs-lookup"><span data-stu-id="afaf8-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="afaf8-134">Para compatibilidade com versões anteriores, o PerfCounter do .NET Framework 4 não verifica a entrada do registro CategoryOptions quando em execução em um aplicativo do .NET Framework 1.1.</span><span class="sxs-lookup"><span data-stu-id="afaf8-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="afaf8-135">Ela simplesmente usa a memória compartilhada global, assim como o PerfCounter do .NET Framework 1.1.</span><span class="sxs-lookup"><span data-stu-id="afaf8-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="afaf8-136">No entanto, você pode instruir o PerfCounter do .NET Framework 4 para verificar a configuração do registro, habilitando o `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento.</span><span class="sxs-lookup"><span data-stu-id="afaf8-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afaf8-137">Habilitando o `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento não garante que a categoria específica memória compartilhada será usada.</span><span class="sxs-lookup"><span data-stu-id="afaf8-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="afaf8-138">Configuração habilitada para `true` apenas faz com que o PerfCounter fazer referência a configuração do registro CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="afaf8-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="afaf8-139">A configuração padrão para CategoryOptions é usar a categoria memória compartilhada; No entanto, você pode alterar CategoryOptions para indicar que a memória compartilhada global deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="afaf8-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="afaf8-140">A chave do registro que contém a configuração CategoryOptions é HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance.</span><span class="sxs-lookup"><span data-stu-id="afaf8-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="afaf8-141">Por padrão, CategoryOptions é definido como 3, que instrui o PerfCounter usar memória compartilhada de categoria específico.</span><span class="sxs-lookup"><span data-stu-id="afaf8-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="afaf8-142">Se CategoryOptions for definido como 0, o PerfCounter usa memória global compartilhada.</span><span class="sxs-lookup"><span data-stu-id="afaf8-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="afaf8-143">Dados da instância serão reutilizados somente se o nome da instância que está sendo criado é idêntico à instância que está sendo reutilizada.</span><span class="sxs-lookup"><span data-stu-id="afaf8-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="afaf8-144">Todas as versões será capazes de gravar na categoria.</span><span class="sxs-lookup"><span data-stu-id="afaf8-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="afaf8-145">Se CategoryOptions for definido como 1, memória compartilhada global é usada, mas os dados de instância podem ser reutilizados se o nome da categoria é o mesmo tamanho que a categoria que está sendo reutilizado.</span><span class="sxs-lookup"><span data-stu-id="afaf8-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="afaf8-146">As configurações de 0 e 1 podem levar a vazamentos de memória e preenchimento de memória do contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="afaf8-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afaf8-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="afaf8-147">Example</span></span>  
 <span data-ttu-id="afaf8-148">O exemplo a seguir mostra como especificar se PerfCounter devem fazer referência a entrada do registro CategoryOptions para determinar se ele deve usar a memória compartilhada de categoria específico.</span><span class="sxs-lookup"><span data-stu-id="afaf8-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="afaf8-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afaf8-149">See also</span></span>

- [<span data-ttu-id="afaf8-150">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="afaf8-150">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="afaf8-151">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="afaf8-151">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
