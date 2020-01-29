---
title: Definições de configuração do coletor de lixo
description: Saiba mais sobre as configurações de tempo de execução para configurar como o coletor de lixo gerencia a memória para aplicativos .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733523"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="9c976-103">Opções de configuração de tempo de execução para coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="9c976-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="9c976-104">Esta página contém informações sobre as configurações de coletor de lixo (GC) que podem ser alteradas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9c976-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="9c976-105">Se você estiver tentando atingir o desempenho máximo de um aplicativo em execução, considere o uso dessas configurações.</span><span class="sxs-lookup"><span data-stu-id="9c976-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="9c976-106">No entanto, os padrões fornecem um desempenho ideal para a maioria dos aplicativos em situações típicas.</span><span class="sxs-lookup"><span data-stu-id="9c976-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="9c976-107">As configurações são organizadas em grupos nesta página.</span><span class="sxs-lookup"><span data-stu-id="9c976-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="9c976-108">As configurações em cada grupo são comumente usadas em conjunto entre si para obter um resultado específico.</span><span class="sxs-lookup"><span data-stu-id="9c976-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="9c976-109">Essas configurações também podem ser alteradas dinamicamente pelo aplicativo enquanto ele está em execução, portanto, as configurações de tempo de execução definidas podem ser substituídas.</span><span class="sxs-lookup"><span data-stu-id="9c976-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="9c976-110">Algumas configurações, como [nível de latência](../../standard/garbage-collection/latency.md), normalmente são definidas somente por meio da API em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="9c976-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="9c976-111">Essas configurações são omitidas desta página.</span><span class="sxs-lookup"><span data-stu-id="9c976-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="9c976-112">Para valores numéricos, use a notação decimal para as configurações no arquivo *runtimeconfig. JSON* e notação hexadecimal para configurações de variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="9c976-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="9c976-113">Para valores hexadecimais, você pode especificá-los com ou sem o prefixo "0x".</span><span class="sxs-lookup"><span data-stu-id="9c976-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="9c976-114">Tipos de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="9c976-114">Flavors of garbage collection</span></span>

<span data-ttu-id="9c976-115">Os dois tipos principais de coleta de lixo são estação de trabalho GC e GC de servidor.</span><span class="sxs-lookup"><span data-stu-id="9c976-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="9c976-116">Para obter mais informações sobre as diferenças entre os dois, consulte [conceitos básicos da coleta de lixo](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="9c976-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="9c976-117">Os subtipos de coleta de lixo são em segundo plano e não simultâneos.</span><span class="sxs-lookup"><span data-stu-id="9c976-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="9c976-118">Use as seguintes configurações para selecionar tipos de coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="9c976-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="9c976-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="9c976-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="9c976-120">Define se o aplicativo usa a coleta de lixo da estação de trabalho ou a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="9c976-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="9c976-121">Padrão: coleta de lixo da estação de trabalho (`false`).</span><span class="sxs-lookup"><span data-stu-id="9c976-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="9c976-122">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-122">Setting name</span></span> | <span data-ttu-id="9c976-123">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-123">Values</span></span> | <span data-ttu-id="9c976-124">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-125">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="9c976-126">`false`-estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="9c976-126">`false` - workstation</span></span><br/><span data-ttu-id="9c976-127">servidor de `true`</span><span class="sxs-lookup"><span data-stu-id="9c976-127">`true` - server</span></span> | <span data-ttu-id="9c976-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-129">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="9c976-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="9c976-130">`false`-estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="9c976-130">`false` - workstation</span></span><br/><span data-ttu-id="9c976-131">servidor de `true`</span><span class="sxs-lookup"><span data-stu-id="9c976-131">`true` - server</span></span> | <span data-ttu-id="9c976-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-133">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="9c976-134">`0`-estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="9c976-134">`0` - workstation</span></span><br/><span data-ttu-id="9c976-135">servidor de `1`</span><span class="sxs-lookup"><span data-stu-id="9c976-135">`1` - server</span></span> | <span data-ttu-id="9c976-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-137">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="9c976-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="9c976-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="9c976-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="9c976-139">`false`-estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="9c976-139">`false` - workstation</span></span><br/><span data-ttu-id="9c976-140">servidor de `true`</span><span class="sxs-lookup"><span data-stu-id="9c976-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="9c976-141">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9c976-141">Examples</span></span>

<span data-ttu-id="9c976-142">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="9c976-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="9c976-143">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="9c976-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="9c976-144">System. GC. simultaneamente/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="9c976-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="9c976-145">Configura se a coleta de lixo em segundo plano (simultânea) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="9c976-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="9c976-146">Padrão: habilitado (`true`).</span><span class="sxs-lookup"><span data-stu-id="9c976-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="9c976-147">Para obter mais informações, consulte [coleta de lixo em segundo plano](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) e [coleta de lixo do servidor em segundo plano](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="9c976-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="9c976-148">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-148">Setting name</span></span> | <span data-ttu-id="9c976-149">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-149">Values</span></span> | <span data-ttu-id="9c976-150">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-151">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="9c976-152">GC de `true` em segundo plano</span><span class="sxs-lookup"><span data-stu-id="9c976-152">`true` - background GC</span></span><br/><span data-ttu-id="9c976-153">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="9c976-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="9c976-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-155">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="9c976-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="9c976-156">GC de `true` em segundo plano</span><span class="sxs-lookup"><span data-stu-id="9c976-156">`true` - background GC</span></span><br/><span data-ttu-id="9c976-157">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="9c976-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="9c976-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-159">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="9c976-160">GC de `true` em segundo plano</span><span class="sxs-lookup"><span data-stu-id="9c976-160">`true` - background GC</span></span><br/><span data-ttu-id="9c976-161">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="9c976-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="9c976-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-163">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="9c976-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="9c976-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="9c976-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="9c976-165">GC de `true` em segundo plano</span><span class="sxs-lookup"><span data-stu-id="9c976-165">`true` - background GC</span></span><br/><span data-ttu-id="9c976-166">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="9c976-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="9c976-167">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9c976-167">Examples</span></span>

<span data-ttu-id="9c976-168">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="9c976-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="9c976-169">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="9c976-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="9c976-170">Gerenciar o uso de recursos</span><span class="sxs-lookup"><span data-stu-id="9c976-170">Manage resource usage</span></span>

<span data-ttu-id="9c976-171">Use as configurações descritas nesta seção para gerenciar a memória e o uso do processador do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="9c976-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="9c976-172">Para obter mais informações sobre algumas dessas configurações, consulte o meio-termo entre a entrada de blog do [GC de estação de trabalho e servidor](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="9c976-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="9c976-173">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="9c976-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="9c976-174">Limita o número de heaps criados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="9c976-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="9c976-175">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="9c976-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="9c976-176">Se a afinidade do processador GC estiver habilitada, que é o padrão, a configuração de contagem de heap affinitizes `n` heaps/threads do GC para os primeiros processadores de `n`.</span><span class="sxs-lookup"><span data-stu-id="9c976-176">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="9c976-177">(Use a máscara relacionar ou as configurações de intervalos de relacionar para especificar exatamente quais processadores relacionar.)</span><span class="sxs-lookup"><span data-stu-id="9c976-177">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="9c976-178">Se a afinidade do processador GC estiver desabilitada, essa configuração limitará o número de heaps do GC.</span><span class="sxs-lookup"><span data-stu-id="9c976-178">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="9c976-179">Para obter mais informações, consulte o [GCHeapCount comentários](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="9c976-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="9c976-180">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-180">Setting name</span></span> | <span data-ttu-id="9c976-181">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-181">Values</span></span> | <span data-ttu-id="9c976-182">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-183">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="9c976-184">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-184">*decimal value*</span></span> | <span data-ttu-id="9c976-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="9c976-186">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="9c976-187">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-187">*hexadecimal value*</span></span> | <span data-ttu-id="9c976-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="9c976-189">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="9c976-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="9c976-190">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="9c976-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="9c976-191">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-191">*decimal value*</span></span> | <span data-ttu-id="9c976-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="9c976-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="9c976-193">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="9c976-193">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="9c976-194">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="9c976-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="9c976-195">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="9c976-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="9c976-196">Por exemplo, para limitar o número de heaps a 16, os valores seriam 16 para o arquivo JSON e 0x10 ou 10 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="9c976-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="9c976-197">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="9c976-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="9c976-198">Especifica os processadores exatos que os threads do coletor de lixo devem usar.</span><span class="sxs-lookup"><span data-stu-id="9c976-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="9c976-199">Se a afinidade do processador estiver desabilitada ao definir `System.GC.NoAffinitize` como `true`, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="9c976-199">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="9c976-200">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="9c976-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="9c976-201">O valor é uma máscara de bits que define os processadores que estão disponíveis para o processo.</span><span class="sxs-lookup"><span data-stu-id="9c976-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="9c976-202">Por exemplo, um valor decimal de 1023 (ou um valor hexadecimal de 0x3FF ou 3FF se você estiver usando a variável de ambiente) é 0011 1111 1111 em notação binária.</span><span class="sxs-lookup"><span data-stu-id="9c976-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="9c976-203">Isso especifica que os primeiros 10 processadores devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="9c976-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="9c976-204">Para especificar os 10 próximos processadores, ou seja, os processadores 10-19, especifique um valor decimal de 1047552 (ou um valor hexadecimal de 0xFFC00 ou FFC00), que é equivalente a um valor binário de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="9c976-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="9c976-205">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-205">Setting name</span></span> | <span data-ttu-id="9c976-206">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-206">Values</span></span> | <span data-ttu-id="9c976-207">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-208">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="9c976-209">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-209">*decimal value*</span></span> | <span data-ttu-id="9c976-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="9c976-211">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="9c976-212">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-212">*hexadecimal value*</span></span> | <span data-ttu-id="9c976-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="9c976-214">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="9c976-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="9c976-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="9c976-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="9c976-216">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-216">*decimal value*</span></span> | <span data-ttu-id="9c976-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="9c976-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="9c976-218">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="9c976-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="9c976-219">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="9c976-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="9c976-220">Especifica a lista de processadores a serem usados para threads do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="9c976-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="9c976-221">Essa configuração é semelhante à `System.GC.HeapAffinitizeMask`, exceto pelo fato de que ela permite que você especifique mais de 64 processadores.</span><span class="sxs-lookup"><span data-stu-id="9c976-221">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="9c976-222">Para sistemas operacionais Windows, Prefixe o número do processador ou o intervalo com o [grupo de CPU](/windows/win32/procthread/processor-groups)correspondente, por exemplo, "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="9c976-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="9c976-223">Se a afinidade do processador estiver desabilitada ao definir `System.GC.NoAffinitize` como `true`, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="9c976-223">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="9c976-224">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="9c976-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="9c976-225">Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.</span><span class="sxs-lookup"><span data-stu-id="9c976-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="9c976-226">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-226">Setting name</span></span> | <span data-ttu-id="9c976-227">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-227">Values</span></span> | <span data-ttu-id="9c976-228">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-229">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="9c976-230">Lista separada por vírgulas de números de processador ou intervalos de números de processador.</span><span class="sxs-lookup"><span data-stu-id="9c976-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="9c976-231">Exemplo de UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="9c976-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="9c976-232">Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="9c976-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="9c976-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="9c976-234">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="9c976-235">Lista separada por vírgulas de números de processador ou intervalos de números de processador.</span><span class="sxs-lookup"><span data-stu-id="9c976-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="9c976-236">Exemplo de UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="9c976-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="9c976-237">Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="9c976-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="9c976-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-238">.NET Core 3.0</span></span> |

<span data-ttu-id="9c976-239">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="9c976-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="9c976-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="9c976-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="9c976-241">Configura se o coletor de lixo usa [grupos de CPU](/windows/win32/procthread/processor-groups) ou não.</span><span class="sxs-lookup"><span data-stu-id="9c976-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="9c976-242">Quando um computador com Windows de 64 bits tem vários grupos de CPU, ou seja, há mais de 64 processadores, a habilitação desse elemento estende a coleta de lixo em todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="9c976-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="9c976-243">O coletor de lixo usa todos os núcleos para criar e balancear heaps.</span><span class="sxs-lookup"><span data-stu-id="9c976-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="9c976-244">Aplica-se à coleta de lixo do servidor somente em sistemas de operação do Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="9c976-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="9c976-245">Padrão: desabilitado (`0`).</span><span class="sxs-lookup"><span data-stu-id="9c976-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="9c976-246">Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.</span><span class="sxs-lookup"><span data-stu-id="9c976-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="9c976-247">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-247">Setting name</span></span> | <span data-ttu-id="9c976-248">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-248">Values</span></span> | <span data-ttu-id="9c976-249">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-250">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="9c976-251">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-251">N/A</span></span> | <span data-ttu-id="9c976-252">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-252">N/A</span></span> | <span data-ttu-id="9c976-253">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-253">N/A</span></span> |
| <span data-ttu-id="9c976-254">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="9c976-255">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="9c976-255">`0` - disabled</span></span><br/><span data-ttu-id="9c976-256">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="9c976-256">`1` - enabled</span></span> | <span data-ttu-id="9c976-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-258">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="9c976-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="9c976-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="9c976-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="9c976-260">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="9c976-260">`false` - disabled</span></span><br/><span data-ttu-id="9c976-261">habilitado para `true`</span><span class="sxs-lookup"><span data-stu-id="9c976-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="9c976-262">Para configurar o Common Language Runtime (CLR) para também distribuir threads do pool de threads em todos os grupos de CPU, habilite a opção de [elemento Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="9c976-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="9c976-263">Para aplicativos .NET Core, você pode habilitar essa opção definindo o valor da variável de ambiente `COMPlus_Thread_UseAllCpuGroups` como `1`.</span><span class="sxs-lookup"><span data-stu-id="9c976-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="9c976-264">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="9c976-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="9c976-265">Especifica se os threads de coleta de lixo devem ser *relacionardos* com processadores.</span><span class="sxs-lookup"><span data-stu-id="9c976-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="9c976-266">Para relacionar um thread de GC significa que ele só pode ser executado em sua CPU específica.</span><span class="sxs-lookup"><span data-stu-id="9c976-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="9c976-267">Um heap é criado para cada thread do GC.</span><span class="sxs-lookup"><span data-stu-id="9c976-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="9c976-268">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="9c976-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="9c976-269">Padrão: relacionar os threads de coleta de lixo com processadores (`false`).</span><span class="sxs-lookup"><span data-stu-id="9c976-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="9c976-270">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-270">Setting name</span></span> | <span data-ttu-id="9c976-271">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-271">Values</span></span> | <span data-ttu-id="9c976-272">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-273">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="9c976-274">`false`-relacionar</span><span class="sxs-lookup"><span data-stu-id="9c976-274">`false` - affinitize</span></span><br/><span data-ttu-id="9c976-275">`true`-não relacionar</span><span class="sxs-lookup"><span data-stu-id="9c976-275">`true` - don't affinitize</span></span> | <span data-ttu-id="9c976-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="9c976-277">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="9c976-278">`0`-relacionar</span><span class="sxs-lookup"><span data-stu-id="9c976-278">`0` - affinitize</span></span><br/><span data-ttu-id="9c976-279">`1`-não relacionar</span><span class="sxs-lookup"><span data-stu-id="9c976-279">`1` - don't affinitize</span></span> | <span data-ttu-id="9c976-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="9c976-281">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="9c976-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="9c976-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="9c976-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="9c976-283">`false`-relacionar</span><span class="sxs-lookup"><span data-stu-id="9c976-283">`false` - affinitize</span></span><br/><span data-ttu-id="9c976-284">`true`-não relacionar</span><span class="sxs-lookup"><span data-stu-id="9c976-284">`true` - don't affinitize</span></span> | <span data-ttu-id="9c976-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="9c976-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="9c976-286">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="9c976-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="9c976-287">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="9c976-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="9c976-288">Especifica o tamanho máximo de confirmação, em bytes, para o heap de GC e a escrituração de GC.</span><span class="sxs-lookup"><span data-stu-id="9c976-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="9c976-289">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-289">Setting name</span></span> | <span data-ttu-id="9c976-290">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-290">Values</span></span> | <span data-ttu-id="9c976-291">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-291">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-292">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-292">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="9c976-293">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-293">*decimal value*</span></span> | <span data-ttu-id="9c976-294">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-294">.NET Core 3.0</span></span> |
| <span data-ttu-id="9c976-295">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-295">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="9c976-296">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-296">*hexadecimal value*</span></span> | <span data-ttu-id="9c976-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-297">.NET Core 3.0</span></span> |

<span data-ttu-id="9c976-298">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="9c976-298">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="9c976-299">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="9c976-299">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="9c976-300">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="9c976-300">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="9c976-301">Por exemplo, para especificar um limite rígido de heap de 200 mebibytes (MiB), os valores seriam 209715200 para o arquivo JSON e 0xC800000 ou C800000 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="9c976-301">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="9c976-302">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="9c976-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="9c976-303">Especifica o uso de heap do GC como uma porcentagem da memória total.</span><span class="sxs-lookup"><span data-stu-id="9c976-303">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="9c976-304">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-304">Setting name</span></span> | <span data-ttu-id="9c976-305">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-305">Values</span></span> | <span data-ttu-id="9c976-306">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-306">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-307">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-307">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="9c976-308">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-308">*decimal value*</span></span> | <span data-ttu-id="9c976-309">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-309">.NET Core 3.0</span></span> |
| <span data-ttu-id="9c976-310">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-310">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="9c976-311">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-311">*hexadecimal value*</span></span> | <span data-ttu-id="9c976-312">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-312">.NET Core 3.0</span></span> |

<span data-ttu-id="9c976-313">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="9c976-313">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="9c976-314">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="9c976-314">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="9c976-315">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="9c976-315">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="9c976-316">Por exemplo, para limitar o uso de heap a 30%, os valores seriam 30 para o arquivo JSON e 0x1E ou 1E para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="9c976-316">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="9c976-317">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="9c976-317">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="9c976-318">Configura se OS segmentos que devem ser excluídos são colocados em uma lista de espera para uso futuro ou são liberados de volta para o sistema operacional (SO).</span><span class="sxs-lookup"><span data-stu-id="9c976-318">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="9c976-319">Padrão: liberar segmentos de volta para o sistema operacional (`false`).</span><span class="sxs-lookup"><span data-stu-id="9c976-319">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="9c976-320">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-320">Setting name</span></span> | <span data-ttu-id="9c976-321">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-321">Values</span></span> | <span data-ttu-id="9c976-322">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-323">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="9c976-324">`false`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9c976-324">`false` - release to OS</span></span><br/><span data-ttu-id="9c976-325">`true`-Put em espera</span><span class="sxs-lookup"><span data-stu-id="9c976-325">`true` - put on standby</span></span> | <span data-ttu-id="9c976-326">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-326">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-327">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="9c976-327">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="9c976-328">`false`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9c976-328">`false` - release to OS</span></span><br/><span data-ttu-id="9c976-329">`true`-Put em espera</span><span class="sxs-lookup"><span data-stu-id="9c976-329">`true` - put on standby</span></span> | <span data-ttu-id="9c976-330">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-330">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-331">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-331">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="9c976-332">`0`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9c976-332">`0` - release to OS</span></span><br/><span data-ttu-id="9c976-333">`1`-Put em espera</span><span class="sxs-lookup"><span data-stu-id="9c976-333">`1` - put on standby</span></span> | <span data-ttu-id="9c976-334">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-334">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="9c976-335">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9c976-335">Examples</span></span>

<span data-ttu-id="9c976-336">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="9c976-336">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="9c976-337">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="9c976-337">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="9c976-338">Páginas grandes</span><span class="sxs-lookup"><span data-stu-id="9c976-338">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="9c976-339">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="9c976-339">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="9c976-340">Especifica se páginas grandes devem ser usadas quando um limite rígido de heap for definido.</span><span class="sxs-lookup"><span data-stu-id="9c976-340">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="9c976-341">Padrão: desabilitado (`0`).</span><span class="sxs-lookup"><span data-stu-id="9c976-341">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="9c976-342">Essa é uma configuração experimental.</span><span class="sxs-lookup"><span data-stu-id="9c976-342">This is an experimental setting.</span></span>

| | <span data-ttu-id="9c976-343">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-343">Setting name</span></span> | <span data-ttu-id="9c976-344">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-344">Values</span></span> | <span data-ttu-id="9c976-345">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-346">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-346">**runtimeconfig.json**</span></span> | <span data-ttu-id="9c976-347">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-347">N/A</span></span> | <span data-ttu-id="9c976-348">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-348">N/A</span></span> | <span data-ttu-id="9c976-349">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-349">N/A</span></span> |
| <span data-ttu-id="9c976-350">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-350">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="9c976-351">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="9c976-351">`0` - disabled</span></span><br/><span data-ttu-id="9c976-352">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="9c976-352">`1` - enabled</span></span> | <span data-ttu-id="9c976-353">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9c976-353">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="9c976-354">Objetos grandes</span><span class="sxs-lookup"><span data-stu-id="9c976-354">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="9c976-355">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="9c976-355">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="9c976-356">Configura o suporte ao coletor de lixo em plataformas de 64 bits para matrizes com mais de 2 gigabytes (GB) no tamanho total.</span><span class="sxs-lookup"><span data-stu-id="9c976-356">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="9c976-357">Padrão: habilitado (`1`).</span><span class="sxs-lookup"><span data-stu-id="9c976-357">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="9c976-358">Essa opção pode se tornar obsoleta em uma versão futura do .NET.</span><span class="sxs-lookup"><span data-stu-id="9c976-358">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="9c976-359">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-359">Setting name</span></span> | <span data-ttu-id="9c976-360">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-360">Values</span></span> | <span data-ttu-id="9c976-361">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-361">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-362">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-362">**runtimeconfig.json**</span></span> | <span data-ttu-id="9c976-363">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-363">N/A</span></span> | <span data-ttu-id="9c976-364">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-364">N/A</span></span> | <span data-ttu-id="9c976-365">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-365">N/A</span></span> |
| <span data-ttu-id="9c976-366">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-366">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="9c976-367">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="9c976-367">`1` - enabled</span></span><br/> <span data-ttu-id="9c976-368">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="9c976-368">`0` - disabled</span></span> | <span data-ttu-id="9c976-369">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-369">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-370">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="9c976-370">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="9c976-371">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="9c976-371">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="9c976-372">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="9c976-372">`1` - enabled</span></span><br/> <span data-ttu-id="9c976-373">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="9c976-373">`0` - disabled</span></span> | <span data-ttu-id="9c976-374">{1&gt;{2&gt;.NET Framework 4.5&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-374">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="9c976-375">Limite de heap de objeto grande</span><span class="sxs-lookup"><span data-stu-id="9c976-375">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="9c976-376">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="9c976-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="9c976-377">Especifica o tamanho do limite, em bytes, que faz com que os objetos vá para o LOH (heap de objeto grande).</span><span class="sxs-lookup"><span data-stu-id="9c976-377">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="9c976-378">O limite padrão é de 85.000 bytes.</span><span class="sxs-lookup"><span data-stu-id="9c976-378">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="9c976-379">O valor especificado deve ser maior que o limite padrão.</span><span class="sxs-lookup"><span data-stu-id="9c976-379">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="9c976-380">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-380">Setting name</span></span> | <span data-ttu-id="9c976-381">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-381">Values</span></span> | <span data-ttu-id="9c976-382">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-382">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-383">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-383">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="9c976-384">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-384">*decimal value*</span></span> | <span data-ttu-id="9c976-385">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-385">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-386">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-386">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="9c976-387">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-387">*hexadecimal value*</span></span> | <span data-ttu-id="9c976-388">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9c976-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="9c976-389">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="9c976-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="9c976-390">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="9c976-390">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="9c976-391">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="9c976-391">*decimal value*</span></span> | <span data-ttu-id="9c976-392">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="9c976-392">.NET Framework 4.8</span></span> |

<span data-ttu-id="9c976-393">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="9c976-393">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="9c976-394">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="9c976-394">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="9c976-395">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="9c976-395">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="9c976-396">Por exemplo, para definir um tamanho de limite de 120.000 bytes, os valores seriam 120000 para o arquivo JSON e 0x1D4C0 ou 1D4C0 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="9c976-396">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="9c976-397">GC autônomo</span><span class="sxs-lookup"><span data-stu-id="9c976-397">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="9c976-398">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="9c976-398">COMPlus_GCName</span></span>

- <span data-ttu-id="9c976-399">Especifica um caminho para a biblioteca que contém o coletor de lixo que o tempo de execução pretende carregar.</span><span class="sxs-lookup"><span data-stu-id="9c976-399">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="9c976-400">Para obter mais informações, consulte [design de carregador de GC autônomo](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="9c976-400">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="9c976-401">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="9c976-401">Setting name</span></span> | <span data-ttu-id="9c976-402">Valores</span><span class="sxs-lookup"><span data-stu-id="9c976-402">Values</span></span> | <span data-ttu-id="9c976-403">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9c976-403">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="9c976-404">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="9c976-404">**runtimeconfig.json**</span></span> | <span data-ttu-id="9c976-405">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-405">N/A</span></span> | <span data-ttu-id="9c976-406">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-406">N/A</span></span> | <span data-ttu-id="9c976-407">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c976-407">N/A</span></span> |
| <span data-ttu-id="9c976-408">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="9c976-408">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="9c976-409">*string_path*</span><span class="sxs-lookup"><span data-stu-id="9c976-409">*string_path*</span></span> | <span data-ttu-id="9c976-410">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9c976-410">.NET Core 2.0</span></span> |
