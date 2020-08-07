---
title: Definições de configuração do coletor de lixo
description: Saiba mais sobre as configurações de tempo de execução para configurar como o coletor de lixo gerencia a memória para aplicativos .NET Core.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 91d155b638c7e69b3d2c0216266a7c0c0410db4c
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915988"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="8d142-103">Opções de configuração de tempo de execução para coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="8d142-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="8d142-104">Esta página contém informações sobre as configurações de coletor de lixo (GC) que podem ser alteradas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8d142-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="8d142-105">Se você estiver tentando atingir o desempenho máximo de um aplicativo em execução, considere o uso dessas configurações.</span><span class="sxs-lookup"><span data-stu-id="8d142-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="8d142-106">No entanto, os padrões fornecem um desempenho ideal para a maioria dos aplicativos em situações típicas.</span><span class="sxs-lookup"><span data-stu-id="8d142-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="8d142-107">As configurações são organizadas em grupos nesta página.</span><span class="sxs-lookup"><span data-stu-id="8d142-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="8d142-108">As configurações em cada grupo são comumente usadas em conjunto entre si para obter um resultado específico.</span><span class="sxs-lookup"><span data-stu-id="8d142-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="8d142-109">Essas configurações também podem ser alteradas dinamicamente pelo aplicativo enquanto ele está em execução, portanto, as configurações de tempo de execução definidas podem ser substituídas.</span><span class="sxs-lookup"><span data-stu-id="8d142-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="8d142-110">Algumas configurações, como [nível de latência](../../standard/garbage-collection/latency.md), normalmente são definidas somente por meio da API em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="8d142-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="8d142-111">Essas configurações são omitidas desta página.</span><span class="sxs-lookup"><span data-stu-id="8d142-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="8d142-112">Para valores numéricos, use a notação decimal para configurações no *runtimeconfig.jsem* notação de arquivo e hexadecimal para configurações de variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="8d142-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="8d142-113">Para valores hexadecimais, você pode especificá-los com ou sem o prefixo "0x".</span><span class="sxs-lookup"><span data-stu-id="8d142-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="8d142-114">Tipos de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="8d142-114">Flavors of garbage collection</span></span>

<span data-ttu-id="8d142-115">Os dois tipos principais de coleta de lixo são estação de trabalho GC e GC de servidor.</span><span class="sxs-lookup"><span data-stu-id="8d142-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="8d142-116">Para obter mais informações sobre as diferenças entre as duas, consulte [estação de trabalho e coleta de lixo do servidor](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="8d142-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="8d142-117">Os subtipos de coleta de lixo são em segundo plano e não simultâneos.</span><span class="sxs-lookup"><span data-stu-id="8d142-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="8d142-118">Use as seguintes configurações para selecionar tipos de coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="8d142-118">Use the following settings to select flavors of garbage collection:</span></span>

- [<span data-ttu-id="8d142-119">Estação de trabalho vs. servidor GC</span><span class="sxs-lookup"><span data-stu-id="8d142-119">Workstation vs. server GC</span></span>](#workstation-vs-server)
- [<span data-ttu-id="8d142-120">GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="8d142-120">Background GC</span></span>](#background-gc)

### <a name="workstation-vs-server"></a><span data-ttu-id="8d142-121">Estação de trabalho versus servidor</span><span class="sxs-lookup"><span data-stu-id="8d142-121">Workstation vs. server</span></span>

- <span data-ttu-id="8d142-122">Define se o aplicativo usa a coleta de lixo da estação de trabalho ou a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="8d142-122">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="8d142-123">Padrão: coleta de lixo da estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8d142-123">Default: Workstation garbage collection.</span></span> <span data-ttu-id="8d142-124">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="8d142-124">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="8d142-125">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-125">Setting name</span></span> | <span data-ttu-id="8d142-126">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-126">Values</span></span> | <span data-ttu-id="8d142-127">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-127">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-128">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-128">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="8d142-129">`false`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="8d142-129">`false` - workstation</span></span><br/><span data-ttu-id="8d142-130">`true`-servidor</span><span class="sxs-lookup"><span data-stu-id="8d142-130">`true` - server</span></span> | <span data-ttu-id="8d142-131">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-131">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-132">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="8d142-132">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="8d142-133">`false`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="8d142-133">`false` - workstation</span></span><br/><span data-ttu-id="8d142-134">`true`-servidor</span><span class="sxs-lookup"><span data-stu-id="8d142-134">`true` - server</span></span> | <span data-ttu-id="8d142-135">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-135">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-136">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-136">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="8d142-137">`0`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="8d142-137">`0` - workstation</span></span><br/><span data-ttu-id="8d142-138">`1`-servidor</span><span class="sxs-lookup"><span data-stu-id="8d142-138">`1` - server</span></span> | <span data-ttu-id="8d142-139">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-139">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-140">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="8d142-140">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8d142-141">GCServer</span><span class="sxs-lookup"><span data-stu-id="8d142-141">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="8d142-142">`false`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="8d142-142">`false` - workstation</span></span><br/><span data-ttu-id="8d142-143">`true`-servidor</span><span class="sxs-lookup"><span data-stu-id="8d142-143">`true` - server</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="8d142-144">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8d142-144">Examples</span></span>

<span data-ttu-id="8d142-145">*runtimeconfig.jsno* arquivo:</span><span class="sxs-lookup"><span data-stu-id="8d142-145">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="8d142-146">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="8d142-146">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="background-gc"></a><span data-ttu-id="8d142-147">GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="8d142-147">Background GC</span></span>

- <span data-ttu-id="8d142-148">Configura se a coleta de lixo em segundo plano (simultânea) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="8d142-148">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="8d142-149">Padrão: usar GC em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="8d142-149">Default: Use background GC.</span></span> <span data-ttu-id="8d142-150">Isso é equivalente a definir o valor como `true` .</span><span class="sxs-lookup"><span data-stu-id="8d142-150">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="8d142-151">Para obter mais informações, consulte [coleta de lixo em segundo plano](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="8d142-151">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="8d142-152">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-152">Setting name</span></span> | <span data-ttu-id="8d142-153">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-153">Values</span></span> | <span data-ttu-id="8d142-154">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-154">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-155">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-155">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="8d142-156">`true`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="8d142-156">`true` - background GC</span></span><br/><span data-ttu-id="8d142-157">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="8d142-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="8d142-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-159">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="8d142-159">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="8d142-160">`true`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="8d142-160">`true` - background GC</span></span><br/><span data-ttu-id="8d142-161">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="8d142-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="8d142-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-163">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-163">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="8d142-164">`1`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="8d142-164">`1` - background GC</span></span><br/><span data-ttu-id="8d142-165">`0`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="8d142-165">`0` - non-concurrent GC</span></span> | <span data-ttu-id="8d142-166">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-166">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-167">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="8d142-167">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8d142-168">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="8d142-168">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="8d142-169">`true`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="8d142-169">`true` - background GC</span></span><br/><span data-ttu-id="8d142-170">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="8d142-170">`false` - non-concurrent GC</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="8d142-171">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8d142-171">Examples</span></span>

<span data-ttu-id="8d142-172">*runtimeconfig.jsno* arquivo:</span><span class="sxs-lookup"><span data-stu-id="8d142-172">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="8d142-173">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="8d142-173">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="8d142-174">Gerenciar o uso de recursos</span><span class="sxs-lookup"><span data-stu-id="8d142-174">Manage resource usage</span></span>

<span data-ttu-id="8d142-175">Use as configurações a seguir para gerenciar a memória e o uso do processador do coletor de lixo:</span><span class="sxs-lookup"><span data-stu-id="8d142-175">Use the following settings to manage the garbage collector's memory and processor usage:</span></span>

- [<span data-ttu-id="8d142-176">Relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-176">Affinitize</span></span>](#affinitize)
- [<span data-ttu-id="8d142-177">Máscara de relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-177">Affinitize mask</span></span>](#affinitize-mask)
- [<span data-ttu-id="8d142-178">Intervalos de relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-178">Affinitize ranges</span></span>](#affinitize-ranges)
- [<span data-ttu-id="8d142-179">Grupos de CPU</span><span class="sxs-lookup"><span data-stu-id="8d142-179">CPU groups</span></span>](#cpu-groups)
- [<span data-ttu-id="8d142-180">Contagem de heaps</span><span class="sxs-lookup"><span data-stu-id="8d142-180">Heap count</span></span>](#heap-count)
- [<span data-ttu-id="8d142-181">Limite de heap</span><span class="sxs-lookup"><span data-stu-id="8d142-181">Heap limit</span></span>](#heap-limit)
- [<span data-ttu-id="8d142-182">Percentual de limite de heap</span><span class="sxs-lookup"><span data-stu-id="8d142-182">Heap limit percent</span></span>](#heap-limit-percent)
- [<span data-ttu-id="8d142-183">Porcentagem de memória alta</span><span class="sxs-lookup"><span data-stu-id="8d142-183">High memory percent</span></span>](#high-memory-percent)
- [<span data-ttu-id="8d142-184">Limites por objeto-heap</span><span class="sxs-lookup"><span data-stu-id="8d142-184">Per-object-heap limits</span></span>](#per-object-heap-limits)
- [<span data-ttu-id="8d142-185">Porcentagem de limite por objeto-heap</span><span class="sxs-lookup"><span data-stu-id="8d142-185">Per-object-heap limit percents</span></span>](#per-object-heap-limit-percents)
- [<span data-ttu-id="8d142-186">Reter VM</span><span class="sxs-lookup"><span data-stu-id="8d142-186">Retain VM</span></span>](#retain-vm)

<span data-ttu-id="8d142-187">Para obter mais informações sobre algumas dessas configurações, consulte o meio-termo entre a entrada de blog do [GC de estação de trabalho e servidor](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="8d142-187">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="heap-count"></a><span data-ttu-id="8d142-188">Contagem de heaps</span><span class="sxs-lookup"><span data-stu-id="8d142-188">Heap count</span></span>

- <span data-ttu-id="8d142-189">Limita o número de heaps criados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="8d142-189">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="8d142-190">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="8d142-190">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8d142-191">Se a [afinidade do processador GC](#affinitize) estiver habilitada, que é o padrão, a configuração de contagem de heap affinitizes `n` heaps/threads do GC para os primeiros `n` processadores.</span><span class="sxs-lookup"><span data-stu-id="8d142-191">If [GC processor affinity](#affinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="8d142-192">(Use a [máscara relacionar](#affinitize-mask) ou as configurações de [intervalos de relacionar](#affinitize-ranges) para especificar exatamente quais processadores relacionar.)</span><span class="sxs-lookup"><span data-stu-id="8d142-192">(Use the [affinitize mask](#affinitize-mask) or [affinitize ranges](#affinitize-ranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="8d142-193">Se a [afinidade do processador GC](#affinitize) estiver desabilitada, essa configuração limitará o número de heaps do GC.</span><span class="sxs-lookup"><span data-stu-id="8d142-193">If [GC processor affinity](#affinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="8d142-194">Para obter mais informações, consulte o [GCHeapCount comentários](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="8d142-194">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="8d142-195">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-195">Setting name</span></span> | <span data-ttu-id="8d142-196">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-196">Values</span></span> | <span data-ttu-id="8d142-197">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-197">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-198">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-198">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="8d142-199">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-199">*decimal value*</span></span> | <span data-ttu-id="8d142-200">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-200">.NET Core 3.0</span></span> |
| <span data-ttu-id="8d142-201">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-201">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="8d142-202">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-202">*hexadecimal value*</span></span> | <span data-ttu-id="8d142-203">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-203">.NET Core 3.0</span></span> |
| <span data-ttu-id="8d142-204">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="8d142-204">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8d142-205">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="8d142-205">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="8d142-206">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-206">*decimal value*</span></span> | <span data-ttu-id="8d142-207">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="8d142-207">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="8d142-208">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="8d142-208">Example:</span></span>

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
> <span data-ttu-id="8d142-209">Se você estiver definindo a opção em *runtimeconfig.jsem*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-209">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8d142-210">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-210">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8d142-211">Por exemplo, para limitar o número de heaps a 16, os valores seriam 16 para o arquivo JSON e 0x10 ou 10 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="8d142-211">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="affinitize-mask"></a><span data-ttu-id="8d142-212">Máscara de relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-212">Affinitize mask</span></span>

- <span data-ttu-id="8d142-213">Especifica os processadores exatos que os threads do coletor de lixo devem usar.</span><span class="sxs-lookup"><span data-stu-id="8d142-213">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="8d142-214">Se a [afinidade do processador GC](#affinitize) estiver desabilitada, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="8d142-214">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="8d142-215">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="8d142-215">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8d142-216">O valor é uma máscara de bits que define os processadores que estão disponíveis para o processo.</span><span class="sxs-lookup"><span data-stu-id="8d142-216">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="8d142-217">Por exemplo, um valor decimal de 1023 (ou um valor hexadecimal de 0x3FF ou 3FF se você estiver usando a variável de ambiente) é 0011 1111 1111 em notação binária.</span><span class="sxs-lookup"><span data-stu-id="8d142-217">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="8d142-218">Isso especifica que os primeiros 10 processadores devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="8d142-218">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="8d142-219">Para especificar os 10 próximos processadores, ou seja, os processadores 10-19, especifique um valor decimal de 1047552 (ou um valor hexadecimal de 0xFFC00 ou FFC00), que é equivalente a um valor binário de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="8d142-219">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="8d142-220">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-220">Setting name</span></span> | <span data-ttu-id="8d142-221">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-221">Values</span></span> | <span data-ttu-id="8d142-222">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-222">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-223">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-223">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="8d142-224">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-224">*decimal value*</span></span> | <span data-ttu-id="8d142-225">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-225">.NET Core 3.0</span></span> |
| <span data-ttu-id="8d142-226">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-226">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="8d142-227">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-227">*hexadecimal value*</span></span> | <span data-ttu-id="8d142-228">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-228">.NET Core 3.0</span></span> |
| <span data-ttu-id="8d142-229">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="8d142-229">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8d142-230">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="8d142-230">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="8d142-231">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-231">*decimal value*</span></span> | <span data-ttu-id="8d142-232">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="8d142-232">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="8d142-233">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="8d142-233">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="affinitize-ranges"></a><span data-ttu-id="8d142-234">Intervalos de relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-234">Affinitize ranges</span></span>

- <span data-ttu-id="8d142-235">Especifica a lista de processadores a serem usados para threads do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="8d142-235">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="8d142-236">Essa configuração é semelhante a [System. GC. HeapAffinitizeMask](#affinitize-mask), exceto pelo fato de que ela permite que você especifique mais de 64 processadores.</span><span class="sxs-lookup"><span data-stu-id="8d142-236">This setting is similar to [System.GC.HeapAffinitizeMask](#affinitize-mask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="8d142-237">Para sistemas operacionais Windows, Prefixe o número do processador ou o intervalo com o [grupo de CPU](/windows/win32/procthread/processor-groups)correspondente, por exemplo, "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="8d142-237">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="8d142-238">Se a [afinidade do processador GC](#affinitize) estiver desabilitada, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="8d142-238">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="8d142-239">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="8d142-239">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8d142-240">Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.</span><span class="sxs-lookup"><span data-stu-id="8d142-240">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="8d142-241">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-241">Setting name</span></span> | <span data-ttu-id="8d142-242">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-242">Values</span></span> | <span data-ttu-id="8d142-243">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-243">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-244">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-244">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="8d142-245">Lista separada por vírgulas de números de processador ou intervalos de números de processador.</span><span class="sxs-lookup"><span data-stu-id="8d142-245">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="8d142-246">Exemplo de UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="8d142-246">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="8d142-247">Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="8d142-247">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="8d142-248">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-248">.NET Core 3.0</span></span> |
| <span data-ttu-id="8d142-249">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-249">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="8d142-250">Lista separada por vírgulas de números de processador ou intervalos de números de processador.</span><span class="sxs-lookup"><span data-stu-id="8d142-250">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="8d142-251">Exemplo de UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="8d142-251">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="8d142-252">Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="8d142-252">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="8d142-253">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-253">.NET Core 3.0</span></span> |

<span data-ttu-id="8d142-254">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="8d142-254">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="cpu-groups"></a><span data-ttu-id="8d142-255">Grupos de CPU</span><span class="sxs-lookup"><span data-stu-id="8d142-255">CPU groups</span></span>

- <span data-ttu-id="8d142-256">Configura se o coletor de lixo usa [grupos de CPU](/windows/win32/procthread/processor-groups) ou não.</span><span class="sxs-lookup"><span data-stu-id="8d142-256">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="8d142-257">Quando um computador com Windows de 64 bits tem vários grupos de CPU, ou seja, há mais de 64 processadores, a habilitação desse elemento estende a coleta de lixo em todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="8d142-257">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="8d142-258">O coletor de lixo usa todos os núcleos para criar e balancear heaps.</span><span class="sxs-lookup"><span data-stu-id="8d142-258">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="8d142-259">Aplica-se à coleta de lixo do servidor somente em sistemas de operação do Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8d142-259">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="8d142-260">Padrão: o GC não se estende por grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="8d142-260">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="8d142-261">Isso é equivalente a definir o valor como `0` .</span><span class="sxs-lookup"><span data-stu-id="8d142-261">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="8d142-262">Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.</span><span class="sxs-lookup"><span data-stu-id="8d142-262">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="8d142-263">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-263">Setting name</span></span> | <span data-ttu-id="8d142-264">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-264">Values</span></span> | <span data-ttu-id="8d142-265">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-265">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-266">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-266">**runtimeconfig.json**</span></span> | `System.GC.CpuGroup` | <span data-ttu-id="8d142-267">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-267">`0` - disabled</span></span><br/><span data-ttu-id="8d142-268">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-268">`1` - enabled</span></span> | <span data-ttu-id="8d142-269">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-269">.NET 5.0</span></span> |
| <span data-ttu-id="8d142-270">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-270">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="8d142-271">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-271">`0` - disabled</span></span><br/><span data-ttu-id="8d142-272">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-272">`1` - enabled</span></span> | <span data-ttu-id="8d142-273">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-273">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-274">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="8d142-274">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8d142-275">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="8d142-275">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="8d142-276">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-276">`false` - disabled</span></span><br/><span data-ttu-id="8d142-277">`true`-habilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-277">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="8d142-278">Para configurar o Common Language Runtime (CLR) para também distribuir threads do pool de threads em todos os grupos de CPU, habilite a opção de [elemento Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="8d142-278">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="8d142-279">Para aplicativos .NET Core, você pode habilitar essa opção definindo o valor da variável de `COMPlus_Thread_UseAllCpuGroups` ambiente como `1` .</span><span class="sxs-lookup"><span data-stu-id="8d142-279">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="affinitize"></a><span data-ttu-id="8d142-280">Relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-280">Affinitize</span></span>

- <span data-ttu-id="8d142-281">Especifica se os threads de coleta de lixo devem ser *relacionardos* com processadores.</span><span class="sxs-lookup"><span data-stu-id="8d142-281">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="8d142-282">Para relacionar um thread de GC significa que ele só pode ser executado em sua CPU específica.</span><span class="sxs-lookup"><span data-stu-id="8d142-282">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="8d142-283">Um heap é criado para cada thread do GC.</span><span class="sxs-lookup"><span data-stu-id="8d142-283">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="8d142-284">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="8d142-284">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8d142-285">Padrão: relacionar os threads de coleta de lixo com processadores.</span><span class="sxs-lookup"><span data-stu-id="8d142-285">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="8d142-286">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="8d142-286">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="8d142-287">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-287">Setting name</span></span> | <span data-ttu-id="8d142-288">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-288">Values</span></span> | <span data-ttu-id="8d142-289">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-289">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-290">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-290">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="8d142-291">`false`-relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-291">`false` - affinitize</span></span><br/><span data-ttu-id="8d142-292">`true`-Não relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-292">`true` - don't affinitize</span></span> | <span data-ttu-id="8d142-293">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-293">.NET Core 3.0</span></span> |
| <span data-ttu-id="8d142-294">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-294">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="8d142-295">`0`-relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-295">`0` - affinitize</span></span><br/><span data-ttu-id="8d142-296">`1`-Não relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-296">`1` - don't affinitize</span></span> | <span data-ttu-id="8d142-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="8d142-298">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="8d142-298">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8d142-299">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="8d142-299">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="8d142-300">`false`-relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-300">`false` - affinitize</span></span><br/><span data-ttu-id="8d142-301">`true`-Não relacionar</span><span class="sxs-lookup"><span data-stu-id="8d142-301">`true` - don't affinitize</span></span> | <span data-ttu-id="8d142-302">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="8d142-302">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="8d142-303">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="8d142-303">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="heap-limit"></a><span data-ttu-id="8d142-304">Limite de heap</span><span class="sxs-lookup"><span data-stu-id="8d142-304">Heap limit</span></span>

- <span data-ttu-id="8d142-305">Especifica o tamanho máximo de confirmação, em bytes, para o heap de GC e a escrituração de GC.</span><span class="sxs-lookup"><span data-stu-id="8d142-305">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="8d142-306">Essa configuração se aplica somente a computadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8d142-306">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="8d142-307">Essa configuração será ignorada se os [limites por objeto-heap](#per-object-heap-limits) estiverem configurados.</span><span class="sxs-lookup"><span data-stu-id="8d142-307">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="8d142-308">O valor padrão, que se aplica apenas em determinados casos, é o maior de 20 MB ou 75% do limite de memória no contêiner.</span><span class="sxs-lookup"><span data-stu-id="8d142-308">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="8d142-309">O valor padrão se aplica se:</span><span class="sxs-lookup"><span data-stu-id="8d142-309">The default value applies if:</span></span>

  - <span data-ttu-id="8d142-310">O processo está sendo executado dentro de um contêiner que tem um limite de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="8d142-310">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="8d142-311">[System. GC. HeapHardLimitPercent](#heap-limit-percent) não está definido.</span><span class="sxs-lookup"><span data-stu-id="8d142-311">[System.GC.HeapHardLimitPercent](#heap-limit-percent) is not set.</span></span>

| | <span data-ttu-id="8d142-312">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-312">Setting name</span></span> | <span data-ttu-id="8d142-313">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-313">Values</span></span> | <span data-ttu-id="8d142-314">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-314">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-315">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-315">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="8d142-316">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-316">*decimal value*</span></span> | <span data-ttu-id="8d142-317">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-317">.NET Core 3.0</span></span> |
| <span data-ttu-id="8d142-318">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-318">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="8d142-319">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-319">*hexadecimal value*</span></span> | <span data-ttu-id="8d142-320">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-320">.NET Core 3.0</span></span> |

<span data-ttu-id="8d142-321">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="8d142-321">Example:</span></span>

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
> <span data-ttu-id="8d142-322">Se você estiver definindo a opção em *runtimeconfig.jsem*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-322">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8d142-323">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-323">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8d142-324">Por exemplo, para especificar um limite rígido de heap de 200 mebibytes (MiB), os valores seriam 209715200 para o arquivo JSON e 0xC800000 ou C800000 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="8d142-324">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="heap-limit-percent"></a><span data-ttu-id="8d142-325">Percentual de limite de heap</span><span class="sxs-lookup"><span data-stu-id="8d142-325">Heap limit percent</span></span>

- <span data-ttu-id="8d142-326">Especifica o uso de heap de GC permitido como uma porcentagem da memória física total.</span><span class="sxs-lookup"><span data-stu-id="8d142-326">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="8d142-327">Se [System. GC. HeapHardLimit](#heap-limit) também for definido, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="8d142-327">If [System.GC.HeapHardLimit](#heap-limit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="8d142-328">Essa configuração se aplica somente a computadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8d142-328">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="8d142-329">Se o processo estiver sendo executado dentro de um contêiner que tem um limite de memória especificado, a porcentagem será calculada como uma porcentagem desse limite de memória.</span><span class="sxs-lookup"><span data-stu-id="8d142-329">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="8d142-330">Essa configuração será ignorada se os [limites por objeto-heap](#per-object-heap-limits) estiverem configurados.</span><span class="sxs-lookup"><span data-stu-id="8d142-330">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="8d142-331">O valor padrão, que se aplica apenas em determinados casos, é o menor de 20 MB ou 75% do limite de memória no contêiner.</span><span class="sxs-lookup"><span data-stu-id="8d142-331">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="8d142-332">O valor padrão se aplica se:</span><span class="sxs-lookup"><span data-stu-id="8d142-332">The default value applies if:</span></span>

  - <span data-ttu-id="8d142-333">O processo está sendo executado dentro de um contêiner que tem um limite de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="8d142-333">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="8d142-334">[System. GC. HeapHardLimit](#heap-limit) não está definido.</span><span class="sxs-lookup"><span data-stu-id="8d142-334">[System.GC.HeapHardLimit](#heap-limit) is not set.</span></span>

| | <span data-ttu-id="8d142-335">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-335">Setting name</span></span> | <span data-ttu-id="8d142-336">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-336">Values</span></span> | <span data-ttu-id="8d142-337">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-337">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-338">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-338">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="8d142-339">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-339">*decimal value*</span></span> | <span data-ttu-id="8d142-340">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-340">.NET Core 3.0</span></span> |
| <span data-ttu-id="8d142-341">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-341">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="8d142-342">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-342">*hexadecimal value*</span></span> | <span data-ttu-id="8d142-343">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-343">.NET Core 3.0</span></span> |

<span data-ttu-id="8d142-344">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="8d142-344">Example:</span></span>

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
> <span data-ttu-id="8d142-345">Se você estiver definindo a opção em *runtimeconfig.jsem*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-345">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8d142-346">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-346">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8d142-347">Por exemplo, para limitar o uso de heap a 30%, os valores seriam 30 para o arquivo JSON e 0x1E ou 1E para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="8d142-347">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="8d142-348">Limites por objeto-heap</span><span class="sxs-lookup"><span data-stu-id="8d142-348">Per-object-heap limits</span></span>

<span data-ttu-id="8d142-349">Você pode especificar o uso de heap permitido do GC em uma base por objeto-heap.</span><span class="sxs-lookup"><span data-stu-id="8d142-349">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="8d142-350">Os heaps diferentes são o LOH (heap de objeto grande), SOH (heap de objeto pequeno) e POH (heap de objeto fixado).</span><span class="sxs-lookup"><span data-stu-id="8d142-350">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="8d142-351">Se você especificar um valor para qualquer uma das `COMPLUS_GCHeapHardLimitSOH` `COMPLUS_GCHeapHardLimitLOH` configurações, ou `COMPLUS_GCHeapHardLimitPOH` , também deverá especificar um valor para `COMPLUS_GCHeapHardLimitSOH` e `COMPLUS_GCHeapHardLimitLOH` .</span><span class="sxs-lookup"><span data-stu-id="8d142-351">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="8d142-352">Se você não fizer isso, o tempo de execução falhará ao inicializar.</span><span class="sxs-lookup"><span data-stu-id="8d142-352">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="8d142-353">O valor padrão de `COMPLUS_GCHeapHardLimitPOH` é 0.</span><span class="sxs-lookup"><span data-stu-id="8d142-353">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="8d142-354">`COMPLUS_GCHeapHardLimitSOH`e `COMPLUS_GCHeapHardLimitLOH` não têm valores padrão.</span><span class="sxs-lookup"><span data-stu-id="8d142-354">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="8d142-355">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-355">Setting name</span></span> | <span data-ttu-id="8d142-356">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-356">Values</span></span> | <span data-ttu-id="8d142-357">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-358">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-358">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOH` | <span data-ttu-id="8d142-359">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-359">*decimal value*</span></span> | <span data-ttu-id="8d142-360">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-360">.NET 5.0</span></span> |
| <span data-ttu-id="8d142-361">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-361">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="8d142-362">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-362">*hexadecimal value*</span></span> | <span data-ttu-id="8d142-363">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-363">.NET 5.0</span></span> |

| | <span data-ttu-id="8d142-364">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-364">Setting name</span></span> | <span data-ttu-id="8d142-365">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-365">Values</span></span> | <span data-ttu-id="8d142-366">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-366">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-367">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-367">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOH` | <span data-ttu-id="8d142-368">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-368">*decimal value*</span></span> | <span data-ttu-id="8d142-369">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-369">.NET 5.0</span></span> |
| <span data-ttu-id="8d142-370">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-370">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="8d142-371">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-371">*hexadecimal value*</span></span> | <span data-ttu-id="8d142-372">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-372">.NET 5.0</span></span> |

| | <span data-ttu-id="8d142-373">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-373">Setting name</span></span> | <span data-ttu-id="8d142-374">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-374">Values</span></span> | <span data-ttu-id="8d142-375">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-375">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-376">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-376">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOH` | <span data-ttu-id="8d142-377">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-377">*decimal value*</span></span> | <span data-ttu-id="8d142-378">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-378">.NET 5.0</span></span> |
| <span data-ttu-id="8d142-379">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-379">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="8d142-380">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-380">*hexadecimal value*</span></span> | <span data-ttu-id="8d142-381">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-381">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="8d142-382">Se você estiver definindo a opção em *runtimeconfig.jsem*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-382">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8d142-383">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-383">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8d142-384">Por exemplo, para especificar um limite rígido de heap de 200 mebibytes (MiB), os valores seriam 209715200 para o arquivo JSON e 0xC800000 ou C800000 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="8d142-384">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="per-object-heap-limit-percents"></a><span data-ttu-id="8d142-385">Porcentagem de limite por objeto-heap</span><span class="sxs-lookup"><span data-stu-id="8d142-385">Per-object-heap limit percents</span></span>

<span data-ttu-id="8d142-386">Você pode especificar o uso de heap permitido do GC em uma base por objeto-heap.</span><span class="sxs-lookup"><span data-stu-id="8d142-386">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="8d142-387">Os heaps diferentes são o LOH (heap de objeto grande), SOH (heap de objeto pequeno) e POH (heap de objeto fixado).</span><span class="sxs-lookup"><span data-stu-id="8d142-387">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="8d142-388">Se você especificar um valor para qualquer uma das `COMPLUS_GCHeapHardLimitSOHPercent` `COMPLUS_GCHeapHardLimitLOHPercent` configurações, ou `COMPLUS_GCHeapHardLimitPOHPercent` , também deverá especificar um valor para `COMPLUS_GCHeapHardLimitSOHPercent` e `COMPLUS_GCHeapHardLimitLOHPercent` .</span><span class="sxs-lookup"><span data-stu-id="8d142-388">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="8d142-389">Se você não fizer isso, o tempo de execução falhará ao inicializar.</span><span class="sxs-lookup"><span data-stu-id="8d142-389">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="8d142-390">Essas configurações serão ignoradas se `COMPLUS_GCHeapHardLimitSOH` , `COMPLUS_GCHeapHardLimitLOH` e `COMPLUS_GCHeapHardLimitPOH` forem especificadas.</span><span class="sxs-lookup"><span data-stu-id="8d142-390">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="8d142-391">Um valor de 1 significa que o GC usa 1% da memória física total para esse heap de objeto.</span><span class="sxs-lookup"><span data-stu-id="8d142-391">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="8d142-392">Cada valor deve ser maior que zero e menor que 100.</span><span class="sxs-lookup"><span data-stu-id="8d142-392">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="8d142-393">Além disso, a soma dos três valores percentuais deve ser menor que 100.</span><span class="sxs-lookup"><span data-stu-id="8d142-393">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="8d142-394">Caso contrário, o tempo de execução não será inicializado.</span><span class="sxs-lookup"><span data-stu-id="8d142-394">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="8d142-395">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-395">Setting name</span></span> | <span data-ttu-id="8d142-396">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-396">Values</span></span> | <span data-ttu-id="8d142-397">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-397">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-398">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-398">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOHPercent` | <span data-ttu-id="8d142-399">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-399">*decimal value*</span></span> | <span data-ttu-id="8d142-400">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-400">.NET 5.0</span></span> |
| <span data-ttu-id="8d142-401">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-401">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="8d142-402">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-402">*hexadecimal value*</span></span> | <span data-ttu-id="8d142-403">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-403">.NET 5.0</span></span> |

| | <span data-ttu-id="8d142-404">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-404">Setting name</span></span> | <span data-ttu-id="8d142-405">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-405">Values</span></span> | <span data-ttu-id="8d142-406">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-406">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-407">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-407">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOHPercent` | <span data-ttu-id="8d142-408">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-408">*decimal value*</span></span> | <span data-ttu-id="8d142-409">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-409">.NET 5.0</span></span> |
| <span data-ttu-id="8d142-410">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-410">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="8d142-411">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-411">*hexadecimal value*</span></span> | <span data-ttu-id="8d142-412">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-412">.NET 5.0</span></span> |

| | <span data-ttu-id="8d142-413">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-413">Setting name</span></span> | <span data-ttu-id="8d142-414">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-414">Values</span></span> | <span data-ttu-id="8d142-415">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-416">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-416">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOHPercent` | <span data-ttu-id="8d142-417">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-417">*decimal value*</span></span> | <span data-ttu-id="8d142-418">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-418">.NET 5.0</span></span> |
| <span data-ttu-id="8d142-419">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-419">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="8d142-420">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-420">*hexadecimal value*</span></span> | <span data-ttu-id="8d142-421">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-421">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="8d142-422">Se você estiver definindo a opção em *runtimeconfig.jsem*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-422">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8d142-423">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-423">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8d142-424">Por exemplo, para limitar o uso de heap a 30%, os valores seriam 30 para o arquivo JSON e 0x1E ou 1E para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="8d142-424">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="high-memory-percent"></a><span data-ttu-id="8d142-425">Porcentagem de memória alta</span><span class="sxs-lookup"><span data-stu-id="8d142-425">High memory percent</span></span>

<span data-ttu-id="8d142-426">A carga de memória é indicada pela porcentagem de memória física em uso.</span><span class="sxs-lookup"><span data-stu-id="8d142-426">Memory load is indicated by the percentage of physical memory in use.</span></span> <span data-ttu-id="8d142-427">Por padrão, quando a carga de memória física atinge **90%**, a coleta de lixo torna-se mais agressiva sobre a realização de coleções de lixo completas e compactadas para evitar a paginação.</span><span class="sxs-lookup"><span data-stu-id="8d142-427">By default, when the physical memory load reaches **90%**, garbage collection becomes more aggressive about doing full, compacting garbage collections to avoid paging.</span></span> <span data-ttu-id="8d142-428">Quando a carga de memória está abaixo de 90%, o GC favorece coleções em segundo plano para coleções de lixo completas, que têm pausas mais curtas, mas não reduzem o tamanho total do heap por muito tempo.</span><span class="sxs-lookup"><span data-stu-id="8d142-428">When memory load is below 90%, GC favors background collections for full garbage collections, which have shorter pauses but don't reduce the total heap size by much.</span></span> <span data-ttu-id="8d142-429">Em computadores com uma quantidade significativa de memória (80 GB ou mais), o limite de carga padrão é entre 90% e 97%.</span><span class="sxs-lookup"><span data-stu-id="8d142-429">On machines with a significant amount of memory (80GB or more), the default load threshold is between 90% and 97%.</span></span>

<span data-ttu-id="8d142-430">O limite de carga de memória alta pode ser ajustado pela `COMPlus_GCHighMemPercent` variável de ambiente ou `System.GC.HighMemoryPercent` definição de configuração JSON.</span><span class="sxs-lookup"><span data-stu-id="8d142-430">The high memory load threshold can be adjusted by the `COMPlus_GCHighMemPercent` environment variable or `System.GC.HighMemoryPercent` JSON configuration setting.</span></span> <span data-ttu-id="8d142-431">Considere ajustar o limite se você quiser controlar o tamanho do heap.</span><span class="sxs-lookup"><span data-stu-id="8d142-431">Consider adjusting the threshold if you want to control heap size.</span></span> <span data-ttu-id="8d142-432">Por exemplo, para o processo dominante em um computador com 64 GB de memória, é razoável que o GC comece a reagir quando há 10% da memória disponível.</span><span class="sxs-lookup"><span data-stu-id="8d142-432">For example, for the dominant process on a machine with 64GB of memory, it's reasonable for GC to start reacting when there's 10% of memory available.</span></span> <span data-ttu-id="8d142-433">Mas, para processos menores, por exemplo, um processo que consome apenas 1GB de memória, o GC pode ser executado com menos de 10% da memória disponível.</span><span class="sxs-lookup"><span data-stu-id="8d142-433">But for smaller processes, for example, a process that only consumes 1GB of memory, GC can comfortably run with less than 10% of memory available.</span></span> <span data-ttu-id="8d142-434">Para esses processos menores, considere definir o limite mais alto.</span><span class="sxs-lookup"><span data-stu-id="8d142-434">For these smaller processes, consider setting the threshold higher.</span></span> <span data-ttu-id="8d142-435">Por outro lado, se você quiser que processos maiores tenham tamanhos de heap menores (mesmo quando houver muita memória física disponível), reduzir esse limite é uma maneira eficaz para que o GC reaja mais cedo para compactar o heap.</span><span class="sxs-lookup"><span data-stu-id="8d142-435">On the other hand, if you want larger processes to have smaller heap sizes (even when there's plenty of physical memory available), lowering this threshold is an effective way for GC to react sooner to compact the heap down.</span></span>

> [!NOTE]
> <span data-ttu-id="8d142-436">Para processos em execução em um contêiner, o GC considera a memória física com base no limite do contêiner.</span><span class="sxs-lookup"><span data-stu-id="8d142-436">For processes running in a container, GC considers the physical memory based on the container limit.</span></span>

| | <span data-ttu-id="8d142-437">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-437">Setting name</span></span> | <span data-ttu-id="8d142-438">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-438">Values</span></span> | <span data-ttu-id="8d142-439">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-439">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-440">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-440">**runtimeconfig.json**</span></span> | `System.GC.HighMemoryPercent` | <span data-ttu-id="8d142-441">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-441">*decimal value*</span></span> | <span data-ttu-id="8d142-442">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d142-442">.NET 5.0</span></span> |
| <span data-ttu-id="8d142-443">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-443">**Environment variable**</span></span> | `COMPlus_GCHighMemPercent` | <span data-ttu-id="8d142-444">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-444">*hexadecimal value*</span></span> | |

> [!TIP]
> <span data-ttu-id="8d142-445">Se você estiver definindo a opção em *runtimeconfig.jsem*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-445">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8d142-446">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-446">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8d142-447">Por exemplo, para definir o limite de memória alto para 75%, os valores seriam 75 para o arquivo JSON e 0x4B ou 4B para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="8d142-447">For example, to set the high memory threshold to 75%, the values would be 75 for the JSON file and 0x4B or 4B for the environment variable.</span></span>

### <a name="retain-vm"></a><span data-ttu-id="8d142-448">Reter VM</span><span class="sxs-lookup"><span data-stu-id="8d142-448">Retain VM</span></span>

- <span data-ttu-id="8d142-449">Configura se OS segmentos que devem ser excluídos são colocados em uma lista de espera para uso futuro ou são liberados de volta para o sistema operacional (SO).</span><span class="sxs-lookup"><span data-stu-id="8d142-449">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="8d142-450">Padrão: libera segmentos de volta para o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="8d142-450">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="8d142-451">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="8d142-451">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="8d142-452">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-452">Setting name</span></span> | <span data-ttu-id="8d142-453">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-453">Values</span></span> | <span data-ttu-id="8d142-454">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-454">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-455">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-455">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="8d142-456">`false`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="8d142-456">`false` - release to OS</span></span><br/><span data-ttu-id="8d142-457">`true`-colocar em espera</span><span class="sxs-lookup"><span data-stu-id="8d142-457">`true` - put on standby</span></span> | <span data-ttu-id="8d142-458">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-458">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-459">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="8d142-459">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="8d142-460">`false`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="8d142-460">`false` - release to OS</span></span><br/><span data-ttu-id="8d142-461">`true`-colocar em espera</span><span class="sxs-lookup"><span data-stu-id="8d142-461">`true` - put on standby</span></span> | <span data-ttu-id="8d142-462">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-462">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-463">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-463">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="8d142-464">`0`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="8d142-464">`0` - release to OS</span></span><br/><span data-ttu-id="8d142-465">`1`-colocar em espera</span><span class="sxs-lookup"><span data-stu-id="8d142-465">`1` - put on standby</span></span> | <span data-ttu-id="8d142-466">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-466">.NET Core 1.0</span></span> |

#### <a name="examples"></a><span data-ttu-id="8d142-467">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8d142-467">Examples</span></span>

<span data-ttu-id="8d142-468">*runtimeconfig.jsno* arquivo:</span><span class="sxs-lookup"><span data-stu-id="8d142-468">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="8d142-469">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="8d142-469">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="8d142-470">Páginas grandes</span><span class="sxs-lookup"><span data-stu-id="8d142-470">Large pages</span></span>

- <span data-ttu-id="8d142-471">Especifica se páginas grandes devem ser usadas quando um limite rígido de heap for definido.</span><span class="sxs-lookup"><span data-stu-id="8d142-471">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="8d142-472">Padrão: não use páginas grandes quando um limite rígido de heap for definido.</span><span class="sxs-lookup"><span data-stu-id="8d142-472">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="8d142-473">Isso é equivalente a definir o valor como `0` .</span><span class="sxs-lookup"><span data-stu-id="8d142-473">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="8d142-474">Essa é uma configuração experimental.</span><span class="sxs-lookup"><span data-stu-id="8d142-474">This is an experimental setting.</span></span>

| | <span data-ttu-id="8d142-475">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-475">Setting name</span></span> | <span data-ttu-id="8d142-476">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-476">Values</span></span> | <span data-ttu-id="8d142-477">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-477">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-478">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-478">**runtimeconfig.json**</span></span> | <span data-ttu-id="8d142-479">N/D</span><span class="sxs-lookup"><span data-stu-id="8d142-479">N/A</span></span> | <span data-ttu-id="8d142-480">N/D</span><span class="sxs-lookup"><span data-stu-id="8d142-480">N/A</span></span> | <span data-ttu-id="8d142-481">N/D</span><span class="sxs-lookup"><span data-stu-id="8d142-481">N/A</span></span> |
| <span data-ttu-id="8d142-482">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-482">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="8d142-483">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-483">`0` - disabled</span></span><br/><span data-ttu-id="8d142-484">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-484">`1` - enabled</span></span> | <span data-ttu-id="8d142-485">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8d142-485">.NET Core 3.0</span></span> |

## <a name="allow-large-objects"></a><span data-ttu-id="8d142-486">Permitir objetos grandes</span><span class="sxs-lookup"><span data-stu-id="8d142-486">Allow large objects</span></span>

- <span data-ttu-id="8d142-487">Configura o suporte ao coletor de lixo em plataformas de 64 bits para matrizes com mais de 2 gigabytes (GB) no tamanho total.</span><span class="sxs-lookup"><span data-stu-id="8d142-487">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="8d142-488">Padrão: o GC dá suporte a matrizes maiores que 2 GB.</span><span class="sxs-lookup"><span data-stu-id="8d142-488">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="8d142-489">Isso é equivalente a definir o valor como `1` .</span><span class="sxs-lookup"><span data-stu-id="8d142-489">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="8d142-490">Essa opção pode se tornar obsoleta em uma versão futura do .NET.</span><span class="sxs-lookup"><span data-stu-id="8d142-490">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="8d142-491">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-491">Setting name</span></span> | <span data-ttu-id="8d142-492">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-492">Values</span></span> | <span data-ttu-id="8d142-493">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-493">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-494">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-494">**runtimeconfig.json**</span></span> | <span data-ttu-id="8d142-495">N/D</span><span class="sxs-lookup"><span data-stu-id="8d142-495">N/A</span></span> | <span data-ttu-id="8d142-496">N/D</span><span class="sxs-lookup"><span data-stu-id="8d142-496">N/A</span></span> | <span data-ttu-id="8d142-497">N/D</span><span class="sxs-lookup"><span data-stu-id="8d142-497">N/A</span></span> |
| <span data-ttu-id="8d142-498">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-498">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="8d142-499">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-499">`1` - enabled</span></span><br/> <span data-ttu-id="8d142-500">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-500">`0` - disabled</span></span> | <span data-ttu-id="8d142-501">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-501">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-502">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="8d142-502">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8d142-503">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="8d142-503">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="8d142-504">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-504">`1` - enabled</span></span><br/> <span data-ttu-id="8d142-505">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="8d142-505">`0` - disabled</span></span> | <span data-ttu-id="8d142-506">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="8d142-506">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="8d142-507">Limite de heap de objeto grande</span><span class="sxs-lookup"><span data-stu-id="8d142-507">Large object heap threshold</span></span>

- <span data-ttu-id="8d142-508">Especifica o tamanho do limite, em bytes, que faz com que os objetos vá para o LOH (heap de objeto grande).</span><span class="sxs-lookup"><span data-stu-id="8d142-508">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="8d142-509">O limite padrão é de 85.000 bytes.</span><span class="sxs-lookup"><span data-stu-id="8d142-509">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="8d142-510">O valor especificado deve ser maior que o limite padrão.</span><span class="sxs-lookup"><span data-stu-id="8d142-510">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="8d142-511">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-511">Setting name</span></span> | <span data-ttu-id="8d142-512">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-512">Values</span></span> | <span data-ttu-id="8d142-513">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-513">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-514">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-514">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="8d142-515">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-515">*decimal value*</span></span> | <span data-ttu-id="8d142-516">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-516">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-517">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-517">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="8d142-518">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-518">*hexadecimal value*</span></span> | <span data-ttu-id="8d142-519">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d142-519">.NET Core 1.0</span></span> |
| <span data-ttu-id="8d142-520">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="8d142-520">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8d142-521">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="8d142-521">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="8d142-522">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="8d142-522">*decimal value*</span></span> | <span data-ttu-id="8d142-523">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="8d142-523">.NET Framework 4.8</span></span> |

<span data-ttu-id="8d142-524">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="8d142-524">Example:</span></span>

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
> <span data-ttu-id="8d142-525">Se você estiver definindo a opção em *runtimeconfig.jsem*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-525">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8d142-526">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="8d142-526">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8d142-527">Por exemplo, para definir um tamanho de limite de 120.000 bytes, os valores seriam 120000 para o arquivo JSON e 0x1D4C0 ou 1D4C0 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="8d142-527">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="8d142-528">GC autônomo</span><span class="sxs-lookup"><span data-stu-id="8d142-528">Standalone GC</span></span>

- <span data-ttu-id="8d142-529">Especifica um caminho para a biblioteca que contém o coletor de lixo que o tempo de execução pretende carregar.</span><span class="sxs-lookup"><span data-stu-id="8d142-529">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="8d142-530">Para obter mais informações, consulte [design de carregador de GC autônomo](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="8d142-530">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="8d142-531">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="8d142-531">Setting name</span></span> | <span data-ttu-id="8d142-532">Valores</span><span class="sxs-lookup"><span data-stu-id="8d142-532">Values</span></span> | <span data-ttu-id="8d142-533">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8d142-533">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8d142-534">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="8d142-534">**runtimeconfig.json**</span></span> | <span data-ttu-id="8d142-535">N/D</span><span class="sxs-lookup"><span data-stu-id="8d142-535">N/A</span></span> | <span data-ttu-id="8d142-536">N/D</span><span class="sxs-lookup"><span data-stu-id="8d142-536">N/A</span></span> | <span data-ttu-id="8d142-537">N/D</span><span class="sxs-lookup"><span data-stu-id="8d142-537">N/A</span></span> |
| <span data-ttu-id="8d142-538">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="8d142-538">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="8d142-539">*string_path*</span><span class="sxs-lookup"><span data-stu-id="8d142-539">*string_path*</span></span> | <span data-ttu-id="8d142-540">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8d142-540">.NET Core 2.0</span></span> |
