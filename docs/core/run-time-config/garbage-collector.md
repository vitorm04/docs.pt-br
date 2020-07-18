---
title: Definições de configuração do coletor de lixo
description: Saiba mais sobre as configurações de tempo de execução para configurar como o coletor de lixo gerencia a memória para aplicativos .NET Core.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 6ae5b7447fb0df4978ea9dcaa5e76fcc7a6cc4ca
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441396"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="c7c5c-103">Opções de configuração de tempo de execução para coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="c7c5c-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="c7c5c-104">Esta página contém informações sobre as configurações de coletor de lixo (GC) que podem ser alteradas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="c7c5c-105">Se você estiver tentando atingir o desempenho máximo de um aplicativo em execução, considere o uso dessas configurações.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="c7c5c-106">No entanto, os padrões fornecem um desempenho ideal para a maioria dos aplicativos em situações típicas.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="c7c5c-107">As configurações são organizadas em grupos nesta página.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="c7c5c-108">As configurações em cada grupo são comumente usadas em conjunto entre si para obter um resultado específico.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="c7c5c-109">Essas configurações também podem ser alteradas dinamicamente pelo aplicativo enquanto ele está em execução, portanto, as configurações de tempo de execução definidas podem ser substituídas.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="c7c5c-110">Algumas configurações, como [nível de latência](../../standard/garbage-collection/latency.md), normalmente são definidas somente por meio da API em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="c7c5c-111">Essas configurações são omitidas desta página.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="c7c5c-112">Para valores numéricos, use a notação decimal para configurações no *runtimeconfig.jsem* notação de arquivo e hexadecimal para configurações de variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="c7c5c-113">Para valores hexadecimais, você pode especificá-los com ou sem o prefixo "0x".</span><span class="sxs-lookup"><span data-stu-id="c7c5c-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="c7c5c-114">Tipos de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="c7c5c-114">Flavors of garbage collection</span></span>

<span data-ttu-id="c7c5c-115">Os dois tipos principais de coleta de lixo são estação de trabalho GC e GC de servidor.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="c7c5c-116">Para obter mais informações sobre as diferenças entre as duas, consulte [estação de trabalho e coleta de lixo do servidor](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="c7c5c-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="c7c5c-117">Os subtipos de coleta de lixo são em segundo plano e não simultâneos.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="c7c5c-118">Use as seguintes configurações para selecionar tipos de coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="c7c5c-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="c7c5c-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="c7c5c-120">Define se o aplicativo usa a coleta de lixo da estação de trabalho ou a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="c7c5c-121">Padrão: coleta de lixo da estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="c7c5c-122">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="c7c5c-123">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-123">Setting name</span></span> | <span data-ttu-id="c7c5c-124">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-124">Values</span></span> | <span data-ttu-id="c7c5c-125">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-126">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="c7c5c-127">`false`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="c7c5c-127">`false` - workstation</span></span><br/><span data-ttu-id="c7c5c-128">`true`-servidor</span><span class="sxs-lookup"><span data-stu-id="c7c5c-128">`true` - server</span></span> | <span data-ttu-id="c7c5c-129">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-130">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="c7c5c-131">`false`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="c7c5c-131">`false` - workstation</span></span><br/><span data-ttu-id="c7c5c-132">`true`-servidor</span><span class="sxs-lookup"><span data-stu-id="c7c5c-132">`true` - server</span></span> | <span data-ttu-id="c7c5c-133">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-134">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="c7c5c-135">`0`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="c7c5c-135">`0` - workstation</span></span><br/><span data-ttu-id="c7c5c-136">`1`-servidor</span><span class="sxs-lookup"><span data-stu-id="c7c5c-136">`1` - server</span></span> | <span data-ttu-id="c7c5c-137">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-138">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c7c5c-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="c7c5c-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="c7c5c-140">`false`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="c7c5c-140">`false` - workstation</span></span><br/><span data-ttu-id="c7c5c-141">`true`-servidor</span><span class="sxs-lookup"><span data-stu-id="c7c5c-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="c7c5c-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c7c5c-142">Examples</span></span>

<span data-ttu-id="c7c5c-143">*runtimeconfig.jsno* arquivo:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="c7c5c-144">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="c7c5c-145">System. GC. simultaneamente/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="c7c5c-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="c7c5c-146">Configura se a coleta de lixo em segundo plano (simultânea) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="c7c5c-147">Padrão: usar GC em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-147">Default: Use background GC.</span></span> <span data-ttu-id="c7c5c-148">Isso é equivalente a definir o valor como `true` .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="c7c5c-149">Para obter mais informações, consulte [coleta de lixo em segundo plano](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="c7c5c-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="c7c5c-150">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-150">Setting name</span></span> | <span data-ttu-id="c7c5c-151">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-151">Values</span></span> | <span data-ttu-id="c7c5c-152">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-153">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="c7c5c-154">`true`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="c7c5c-154">`true` - background GC</span></span><br/><span data-ttu-id="c7c5c-155">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="c7c5c-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="c7c5c-156">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-157">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="c7c5c-158">`true`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="c7c5c-158">`true` - background GC</span></span><br/><span data-ttu-id="c7c5c-159">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="c7c5c-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="c7c5c-160">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-161">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="c7c5c-162">`1`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="c7c5c-162">`1` - background GC</span></span><br/><span data-ttu-id="c7c5c-163">`0`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="c7c5c-163">`0` - non-concurrent GC</span></span> | <span data-ttu-id="c7c5c-164">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-165">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c7c5c-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="c7c5c-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="c7c5c-167">`true`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="c7c5c-167">`true` - background GC</span></span><br/><span data-ttu-id="c7c5c-168">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="c7c5c-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="c7c5c-169">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c7c5c-169">Examples</span></span>

<span data-ttu-id="c7c5c-170">*runtimeconfig.jsno* arquivo:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="c7c5c-171">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="c7c5c-172">Gerenciar o uso de recursos</span><span class="sxs-lookup"><span data-stu-id="c7c5c-172">Manage resource usage</span></span>

<span data-ttu-id="c7c5c-173">Use as configurações descritas nesta seção para gerenciar a memória e o uso do processador do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="c7c5c-174">Para obter mais informações sobre algumas dessas configurações, consulte o meio-termo entre a entrada de blog do [GC de estação de trabalho e servidor](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="c7c5c-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="c7c5c-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="c7c5c-176">Limita o número de heaps criados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="c7c5c-177">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="c7c5c-178">Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver habilitada, que é o padrão, a configuração de contagem de heap affinitizes `n` heaps/threads do GC para os primeiros `n` processadores.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="c7c5c-179">(Use a [máscara relacionar](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou as configurações de [intervalos de relacionar](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) para especificar exatamente quais processadores relacionar.)</span><span class="sxs-lookup"><span data-stu-id="c7c5c-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="c7c5c-180">Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desabilitada, essa configuração limitará o número de heaps do GC.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="c7c5c-181">Para obter mais informações, consulte o [GCHeapCount comentários](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="c7c5c-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="c7c5c-182">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-182">Setting name</span></span> | <span data-ttu-id="c7c5c-183">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-183">Values</span></span> | <span data-ttu-id="c7c5c-184">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-185">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="c7c5c-186">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-186">*decimal value*</span></span> | <span data-ttu-id="c7c5c-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="c7c5c-188">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="c7c5c-189">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-189">*hexadecimal value*</span></span> | <span data-ttu-id="c7c5c-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="c7c5c-191">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c7c5c-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="c7c5c-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="c7c5c-193">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-193">*decimal value*</span></span> | <span data-ttu-id="c7c5c-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="c7c5c-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="c7c5c-195">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-195">Example:</span></span>

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
> <span data-ttu-id="c7c5c-196">Se você estiver definindo a opção em *runtimeconfig.jsem*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="c7c5c-197">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="c7c5c-198">Por exemplo, para limitar o número de heaps a 16, os valores seriam 16 para o arquivo JSON e 0x10 ou 10 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="c7c5c-199">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="c7c5c-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="c7c5c-200">Especifica os processadores exatos que os threads do coletor de lixo devem usar.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="c7c5c-201">Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desabilitada, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="c7c5c-202">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="c7c5c-203">O valor é uma máscara de bits que define os processadores que estão disponíveis para o processo.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="c7c5c-204">Por exemplo, um valor decimal de 1023 (ou um valor hexadecimal de 0x3FF ou 3FF se você estiver usando a variável de ambiente) é 0011 1111 1111 em notação binária.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="c7c5c-205">Isso especifica que os primeiros 10 processadores devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="c7c5c-206">Para especificar os 10 próximos processadores, ou seja, os processadores 10-19, especifique um valor decimal de 1047552 (ou um valor hexadecimal de 0xFFC00 ou FFC00), que é equivalente a um valor binário de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="c7c5c-207">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-207">Setting name</span></span> | <span data-ttu-id="c7c5c-208">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-208">Values</span></span> | <span data-ttu-id="c7c5c-209">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-210">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="c7c5c-211">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-211">*decimal value*</span></span> | <span data-ttu-id="c7c5c-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="c7c5c-213">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="c7c5c-214">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-214">*hexadecimal value*</span></span> | <span data-ttu-id="c7c5c-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="c7c5c-216">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c7c5c-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="c7c5c-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="c7c5c-218">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-218">*decimal value*</span></span> | <span data-ttu-id="c7c5c-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="c7c5c-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="c7c5c-220">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="c7c5c-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="c7c5c-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="c7c5c-222">Especifica a lista de processadores a serem usados para threads do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="c7c5c-223">Essa configuração é semelhante a [System. GC. HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), exceto pelo fato de que ela permite que você especifique mais de 64 processadores.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="c7c5c-224">Para sistemas operacionais Windows, Prefixe o número do processador ou o intervalo com o [grupo de CPU](/windows/win32/procthread/processor-groups)correspondente, por exemplo, "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="c7c5c-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="c7c5c-225">Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desabilitada, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="c7c5c-226">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="c7c5c-227">Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="c7c5c-228">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-228">Setting name</span></span> | <span data-ttu-id="c7c5c-229">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-229">Values</span></span> | <span data-ttu-id="c7c5c-230">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-231">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="c7c5c-232">Lista separada por vírgulas de números de processador ou intervalos de números de processador.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="c7c5c-233">Exemplo de UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="c7c5c-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="c7c5c-234">Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="c7c5c-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="c7c5c-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="c7c5c-236">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="c7c5c-237">Lista separada por vírgulas de números de processador ou intervalos de números de processador.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="c7c5c-238">Exemplo de UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="c7c5c-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="c7c5c-239">Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="c7c5c-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="c7c5c-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-240">.NET Core 3.0</span></span> |

<span data-ttu-id="c7c5c-241">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="c7c5c-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="c7c5c-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="c7c5c-243">Configura se o coletor de lixo usa [grupos de CPU](/windows/win32/procthread/processor-groups) ou não.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="c7c5c-244">Quando um computador com Windows de 64 bits tem vários grupos de CPU, ou seja, há mais de 64 processadores, a habilitação desse elemento estende a coleta de lixo em todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="c7c5c-245">O coletor de lixo usa todos os núcleos para criar e balancear heaps.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="c7c5c-246">Aplica-se à coleta de lixo do servidor somente em sistemas de operação do Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="c7c5c-247">Padrão: o GC não se estende por grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="c7c5c-248">Isso é equivalente a definir o valor como `0` .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="c7c5c-249">Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="c7c5c-250">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-250">Setting name</span></span> | <span data-ttu-id="c7c5c-251">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-251">Values</span></span> | <span data-ttu-id="c7c5c-252">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-253">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="c7c5c-254">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-254">N/A</span></span> | <span data-ttu-id="c7c5c-255">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-255">N/A</span></span> | <span data-ttu-id="c7c5c-256">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-256">N/A</span></span> |
| <span data-ttu-id="c7c5c-257">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="c7c5c-258">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="c7c5c-258">`0` - disabled</span></span><br/><span data-ttu-id="c7c5c-259">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="c7c5c-259">`1` - enabled</span></span> | <span data-ttu-id="c7c5c-260">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-261">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c7c5c-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="c7c5c-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="c7c5c-263">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="c7c5c-263">`false` - disabled</span></span><br/><span data-ttu-id="c7c5c-264">`true`-habilitado</span><span class="sxs-lookup"><span data-stu-id="c7c5c-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="c7c5c-265">Para configurar o Common Language Runtime (CLR) para também distribuir threads do pool de threads em todos os grupos de CPU, habilite a opção de [elemento Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="c7c5c-266">Para aplicativos .NET Core, você pode habilitar essa opção definindo o valor da variável de `COMPlus_Thread_UseAllCpuGroups` ambiente como `1` .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="c7c5c-267">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="c7c5c-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="c7c5c-268">Especifica se os threads de coleta de lixo devem ser *relacionardos* com processadores.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="c7c5c-269">Para relacionar um thread de GC significa que ele só pode ser executado em sua CPU específica.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="c7c5c-270">Um heap é criado para cada thread do GC.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="c7c5c-271">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="c7c5c-272">Padrão: relacionar os threads de coleta de lixo com processadores.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="c7c5c-273">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="c7c5c-274">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-274">Setting name</span></span> | <span data-ttu-id="c7c5c-275">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-275">Values</span></span> | <span data-ttu-id="c7c5c-276">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-277">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="c7c5c-278">`false`-relacionar</span><span class="sxs-lookup"><span data-stu-id="c7c5c-278">`false` - affinitize</span></span><br/><span data-ttu-id="c7c5c-279">`true`-Não relacionar</span><span class="sxs-lookup"><span data-stu-id="c7c5c-279">`true` - don't affinitize</span></span> | <span data-ttu-id="c7c5c-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="c7c5c-281">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="c7c5c-282">`0`-relacionar</span><span class="sxs-lookup"><span data-stu-id="c7c5c-282">`0` - affinitize</span></span><br/><span data-ttu-id="c7c5c-283">`1`-Não relacionar</span><span class="sxs-lookup"><span data-stu-id="c7c5c-283">`1` - don't affinitize</span></span> | <span data-ttu-id="c7c5c-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="c7c5c-285">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c7c5c-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="c7c5c-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="c7c5c-287">`false`-relacionar</span><span class="sxs-lookup"><span data-stu-id="c7c5c-287">`false` - affinitize</span></span><br/><span data-ttu-id="c7c5c-288">`true`-Não relacionar</span><span class="sxs-lookup"><span data-stu-id="c7c5c-288">`true` - don't affinitize</span></span> | <span data-ttu-id="c7c5c-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="c7c5c-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="c7c5c-290">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="c7c5c-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="c7c5c-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="c7c5c-292">Especifica o tamanho máximo de confirmação, em bytes, para o heap de GC e a escrituração de GC.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="c7c5c-293">Essa configuração se aplica somente a computadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="c7c5c-294">Essa configuração será ignorada se os [limites por objeto-heap](#per-object-heap-limits) estiverem configurados.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-294">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="c7c5c-295">O valor padrão, que se aplica apenas em determinados casos, é o maior de 20 MB ou 75% do limite de memória no contêiner.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-295">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="c7c5c-296">O valor padrão se aplica se:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-296">The default value applies if:</span></span>

  - <span data-ttu-id="c7c5c-297">O processo está sendo executado dentro de um contêiner que tem um limite de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-297">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="c7c5c-298">[System. GC. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) não está definido.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-298">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="c7c5c-299">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-299">Setting name</span></span> | <span data-ttu-id="c7c5c-300">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-300">Values</span></span> | <span data-ttu-id="c7c5c-301">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-301">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-302">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-302">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="c7c5c-303">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-303">*decimal value*</span></span> | <span data-ttu-id="c7c5c-304">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-304">.NET Core 3.0</span></span> |
| <span data-ttu-id="c7c5c-305">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-305">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="c7c5c-306">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-306">*hexadecimal value*</span></span> | <span data-ttu-id="c7c5c-307">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-307">.NET Core 3.0</span></span> |

<span data-ttu-id="c7c5c-308">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-308">Example:</span></span>

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
> <span data-ttu-id="c7c5c-309">Se você estiver definindo a opção em *runtimeconfig.jsem*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-309">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="c7c5c-310">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-310">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="c7c5c-311">Por exemplo, para especificar um limite rígido de heap de 200 mebibytes (MiB), os valores seriam 209715200 para o arquivo JSON e 0xC800000 ou C800000 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-311">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="c7c5c-312">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="c7c5c-312">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="c7c5c-313">Especifica o uso de heap de GC permitido como uma porcentagem da memória física total.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-313">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="c7c5c-314">Se [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) também for definido, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-314">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="c7c5c-315">Essa configuração se aplica somente a computadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-315">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="c7c5c-316">Se o processo estiver sendo executado dentro de um contêiner que tem um limite de memória especificado, a porcentagem será calculada como uma porcentagem desse limite de memória.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-316">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="c7c5c-317">Essa configuração será ignorada se os [limites por objeto-heap](#per-object-heap-limits) estiverem configurados.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-317">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="c7c5c-318">O valor padrão, que se aplica apenas em determinados casos, é o menor de 20 MB ou 75% do limite de memória no contêiner.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-318">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="c7c5c-319">O valor padrão se aplica se:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-319">The default value applies if:</span></span>

  - <span data-ttu-id="c7c5c-320">O processo está sendo executado dentro de um contêiner que tem um limite de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-320">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="c7c5c-321">[System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) não está definido.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-321">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="c7c5c-322">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-322">Setting name</span></span> | <span data-ttu-id="c7c5c-323">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-323">Values</span></span> | <span data-ttu-id="c7c5c-324">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-324">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-325">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-325">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="c7c5c-326">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-326">*decimal value*</span></span> | <span data-ttu-id="c7c5c-327">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-327">.NET Core 3.0</span></span> |
| <span data-ttu-id="c7c5c-328">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-328">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="c7c5c-329">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-329">*hexadecimal value*</span></span> | <span data-ttu-id="c7c5c-330">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-330">.NET Core 3.0</span></span> |

<span data-ttu-id="c7c5c-331">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-331">Example:</span></span>

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
> <span data-ttu-id="c7c5c-332">Se você estiver definindo a opção em *runtimeconfig.jsem*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-332">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="c7c5c-333">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-333">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="c7c5c-334">Por exemplo, para limitar o uso de heap a 30%, os valores seriam 30 para o arquivo JSON e 0x1E ou 1E para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-334">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="c7c5c-335">Limites por objeto-heap</span><span class="sxs-lookup"><span data-stu-id="c7c5c-335">Per-object-heap limits</span></span>

<span data-ttu-id="c7c5c-336">Você pode especificar o uso de heap permitido do GC em uma base por objeto-heap.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-336">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="c7c5c-337">Os heaps diferentes são o LOH (heap de objeto grande), SOH (heap de objeto pequeno) e POH (heap de objeto fixado).</span><span class="sxs-lookup"><span data-stu-id="c7c5c-337">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

#### <a name="complus_gcheaphardlimitsoh-complus_gcheaphardlimitloh-complus_gcheaphardlimitpoh"></a><span data-ttu-id="c7c5c-338">COMPLUS_GCHeapHardLimitSOH, COMPLUS_GCHeapHardLimitLOH, COMPLUS_GCHeapHardLimitPOH</span><span class="sxs-lookup"><span data-stu-id="c7c5c-338">COMPLUS_GCHeapHardLimitSOH, COMPLUS_GCHeapHardLimitLOH, COMPLUS_GCHeapHardLimitPOH</span></span>

- <span data-ttu-id="c7c5c-339">Se você especificar um valor para qualquer uma das `COMPLUS_GCHeapHardLimitSOH` `COMPLUS_GCHeapHardLimitLOH` configurações, ou `COMPLUS_GCHeapHardLimitPOH` , também deverá especificar um valor para `COMPLUS_GCHeapHardLimitSOH` e `COMPLUS_GCHeapHardLimitLOH` .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-339">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="c7c5c-340">Se você não fizer isso, o tempo de execução falhará ao inicializar.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-340">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="c7c5c-341">O valor padrão de `COMPLUS_GCHeapHardLimitPOH` é 0.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-341">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="c7c5c-342">`COMPLUS_GCHeapHardLimitSOH`e `COMPLUS_GCHeapHardLimitLOH` não têm valores padrão.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-342">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="c7c5c-343">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-343">Setting name</span></span> | <span data-ttu-id="c7c5c-344">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-344">Values</span></span> | <span data-ttu-id="c7c5c-345">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-346">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-346">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="c7c5c-347">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-347">*hexadecimal value*</span></span> | <span data-ttu-id="c7c5c-348">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-348">.NET 5.0</span></span> |
| <span data-ttu-id="c7c5c-349">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-349">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="c7c5c-350">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-350">*hexadecimal value*</span></span> | <span data-ttu-id="c7c5c-351">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-351">.NET 5.0</span></span> |
| <span data-ttu-id="c7c5c-352">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-352">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="c7c5c-353">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-353">*hexadecimal value*</span></span> | <span data-ttu-id="c7c5c-354">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-354">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="c7c5c-355">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-355">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="c7c5c-356">Por exemplo, para especificar um limite rígido de heap de 200 mebibytes (MiB), o valor seria 0xC800000 ou C800000.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-356">For example, to specify a heap hard limit of 200 mebibytes (MiB), the value would be 0xC800000 or C800000.</span></span>

#### <a name="complus_gcheaphardlimitsohpercent-complus_gcheaphardlimitlohpercent-complus_gcheaphardlimitpohpercent"></a><span data-ttu-id="c7c5c-357">COMPLUS_GCHeapHardLimitSOHPercent, COMPLUS_GCHeapHardLimitLOHPercent, COMPLUS_GCHeapHardLimitPOHPercent</span><span class="sxs-lookup"><span data-stu-id="c7c5c-357">COMPLUS_GCHeapHardLimitSOHPercent, COMPLUS_GCHeapHardLimitLOHPercent, COMPLUS_GCHeapHardLimitPOHPercent</span></span>

- <span data-ttu-id="c7c5c-358">Se você especificar um valor para qualquer uma das `COMPLUS_GCHeapHardLimitSOHPercent` `COMPLUS_GCHeapHardLimitLOHPercent` configurações, ou `COMPLUS_GCHeapHardLimitPOHPercent` , também deverá especificar um valor para `COMPLUS_GCHeapHardLimitSOHPercent` e `COMPLUS_GCHeapHardLimitLOHPercent` .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-358">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="c7c5c-359">Se você não fizer isso, o tempo de execução falhará ao inicializar.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-359">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="c7c5c-360">Essas configurações serão ignoradas se `COMPLUS_GCHeapHardLimitSOH` , `COMPLUS_GCHeapHardLimitLOH` e `COMPLUS_GCHeapHardLimitPOH` forem especificadas.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-360">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="c7c5c-361">Um valor de 1 significa que o GC usa 1% da memória física total para esse heap de objeto.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-361">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="c7c5c-362">Cada valor deve ser maior que zero e menor que 100.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-362">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="c7c5c-363">Além disso, a soma dos três valores percentuais deve ser menor que 100.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-363">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="c7c5c-364">Caso contrário, o tempo de execução não será inicializado.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-364">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="c7c5c-365">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-365">Setting name</span></span> | <span data-ttu-id="c7c5c-366">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-366">Values</span></span> | <span data-ttu-id="c7c5c-367">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-367">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-368">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-368">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="c7c5c-369">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-369">*hexadecimal value*</span></span> | <span data-ttu-id="c7c5c-370">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-370">.NET 5.0</span></span> |
| <span data-ttu-id="c7c5c-371">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-371">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="c7c5c-372">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-372">*hexadecimal value*</span></span> | <span data-ttu-id="c7c5c-373">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-373">.NET 5.0</span></span> |
| <span data-ttu-id="c7c5c-374">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-374">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="c7c5c-375">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-375">*hexadecimal value*</span></span> | <span data-ttu-id="c7c5c-376">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-376">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="c7c5c-377">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="c7c5c-378">Por exemplo, para limitar o uso de heap a 30%, o valor seria 0x1E ou 1E.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-378">For example, to limit the heap usage to 30%, the value would be 0x1E or 1E.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="c7c5c-379">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="c7c5c-379">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="c7c5c-380">Configura se OS segmentos que devem ser excluídos são colocados em uma lista de espera para uso futuro ou são liberados de volta para o sistema operacional (SO).</span><span class="sxs-lookup"><span data-stu-id="c7c5c-380">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="c7c5c-381">Padrão: libera segmentos de volta para o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-381">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="c7c5c-382">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-382">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="c7c5c-383">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-383">Setting name</span></span> | <span data-ttu-id="c7c5c-384">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-384">Values</span></span> | <span data-ttu-id="c7c5c-385">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-386">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-386">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="c7c5c-387">`false`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="c7c5c-387">`false` - release to OS</span></span><br/><span data-ttu-id="c7c5c-388">`true`-colocar em espera</span><span class="sxs-lookup"><span data-stu-id="c7c5c-388">`true` - put on standby</span></span> | <span data-ttu-id="c7c5c-389">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-389">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-390">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-390">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="c7c5c-391">`false`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="c7c5c-391">`false` - release to OS</span></span><br/><span data-ttu-id="c7c5c-392">`true`-colocar em espera</span><span class="sxs-lookup"><span data-stu-id="c7c5c-392">`true` - put on standby</span></span> | <span data-ttu-id="c7c5c-393">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-393">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-394">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-394">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="c7c5c-395">`0`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="c7c5c-395">`0` - release to OS</span></span><br/><span data-ttu-id="c7c5c-396">`1`-colocar em espera</span><span class="sxs-lookup"><span data-stu-id="c7c5c-396">`1` - put on standby</span></span> | <span data-ttu-id="c7c5c-397">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-397">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="c7c5c-398">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c7c5c-398">Examples</span></span>

<span data-ttu-id="c7c5c-399">*runtimeconfig.jsno* arquivo:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-399">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="c7c5c-400">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-400">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="c7c5c-401">Páginas grandes</span><span class="sxs-lookup"><span data-stu-id="c7c5c-401">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="c7c5c-402">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="c7c5c-402">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="c7c5c-403">Especifica se páginas grandes devem ser usadas quando um limite rígido de heap for definido.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-403">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="c7c5c-404">Padrão: não use páginas grandes quando um limite rígido de heap for definido.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-404">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="c7c5c-405">Isso é equivalente a definir o valor como `0` .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-405">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="c7c5c-406">Essa é uma configuração experimental.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-406">This is an experimental setting.</span></span>

| | <span data-ttu-id="c7c5c-407">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-407">Setting name</span></span> | <span data-ttu-id="c7c5c-408">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-408">Values</span></span> | <span data-ttu-id="c7c5c-409">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-409">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-410">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-410">**runtimeconfig.json**</span></span> | <span data-ttu-id="c7c5c-411">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-411">N/A</span></span> | <span data-ttu-id="c7c5c-412">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-412">N/A</span></span> | <span data-ttu-id="c7c5c-413">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-413">N/A</span></span> |
| <span data-ttu-id="c7c5c-414">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-414">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="c7c5c-415">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="c7c5c-415">`0` - disabled</span></span><br/><span data-ttu-id="c7c5c-416">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="c7c5c-416">`1` - enabled</span></span> | <span data-ttu-id="c7c5c-417">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-417">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="c7c5c-418">Objetos grandes</span><span class="sxs-lookup"><span data-stu-id="c7c5c-418">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="c7c5c-419">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="c7c5c-419">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="c7c5c-420">Configura o suporte ao coletor de lixo em plataformas de 64 bits para matrizes com mais de 2 gigabytes (GB) no tamanho total.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-420">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="c7c5c-421">Padrão: o GC dá suporte a matrizes maiores que 2 GB.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-421">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="c7c5c-422">Isso é equivalente a definir o valor como `1` .</span><span class="sxs-lookup"><span data-stu-id="c7c5c-422">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="c7c5c-423">Essa opção pode se tornar obsoleta em uma versão futura do .NET.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-423">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="c7c5c-424">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-424">Setting name</span></span> | <span data-ttu-id="c7c5c-425">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-425">Values</span></span> | <span data-ttu-id="c7c5c-426">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-426">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-427">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-427">**runtimeconfig.json**</span></span> | <span data-ttu-id="c7c5c-428">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-428">N/A</span></span> | <span data-ttu-id="c7c5c-429">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-429">N/A</span></span> | <span data-ttu-id="c7c5c-430">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-430">N/A</span></span> |
| <span data-ttu-id="c7c5c-431">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-431">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="c7c5c-432">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="c7c5c-432">`1` - enabled</span></span><br/> <span data-ttu-id="c7c5c-433">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="c7c5c-433">`0` - disabled</span></span> | <span data-ttu-id="c7c5c-434">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-434">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-435">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-435">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c7c5c-436">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="c7c5c-436">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="c7c5c-437">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="c7c5c-437">`1` - enabled</span></span><br/> <span data-ttu-id="c7c5c-438">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="c7c5c-438">`0` - disabled</span></span> | <span data-ttu-id="c7c5c-439">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="c7c5c-439">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="c7c5c-440">Limite de heap de objeto grande</span><span class="sxs-lookup"><span data-stu-id="c7c5c-440">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="c7c5c-441">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="c7c5c-441">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="c7c5c-442">Especifica o tamanho do limite, em bytes, que faz com que os objetos vá para o LOH (heap de objeto grande).</span><span class="sxs-lookup"><span data-stu-id="c7c5c-442">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="c7c5c-443">O limite padrão é de 85.000 bytes.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-443">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="c7c5c-444">O valor especificado deve ser maior que o limite padrão.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-444">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="c7c5c-445">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-445">Setting name</span></span> | <span data-ttu-id="c7c5c-446">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-446">Values</span></span> | <span data-ttu-id="c7c5c-447">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-447">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-448">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-448">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="c7c5c-449">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-449">*decimal value*</span></span> | <span data-ttu-id="c7c5c-450">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-450">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-451">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-451">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="c7c5c-452">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-452">*hexadecimal value*</span></span> | <span data-ttu-id="c7c5c-453">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-453">.NET Core 1.0</span></span> |
| <span data-ttu-id="c7c5c-454">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-454">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="c7c5c-455">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="c7c5c-455">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="c7c5c-456">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-456">*decimal value*</span></span> | <span data-ttu-id="c7c5c-457">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="c7c5c-457">.NET Framework 4.8</span></span> |

<span data-ttu-id="c7c5c-458">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="c7c5c-458">Example:</span></span>

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
> <span data-ttu-id="c7c5c-459">Se você estiver definindo a opção em *runtimeconfig.jsem*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-459">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="c7c5c-460">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-460">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="c7c5c-461">Por exemplo, para definir um tamanho de limite de 120.000 bytes, os valores seriam 120000 para o arquivo JSON e 0x1D4C0 ou 1D4C0 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-461">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="c7c5c-462">GC autônomo</span><span class="sxs-lookup"><span data-stu-id="c7c5c-462">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="c7c5c-463">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="c7c5c-463">COMPlus_GCName</span></span>

- <span data-ttu-id="c7c5c-464">Especifica um caminho para a biblioteca que contém o coletor de lixo que o tempo de execução pretende carregar.</span><span class="sxs-lookup"><span data-stu-id="c7c5c-464">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="c7c5c-465">Para obter mais informações, consulte [design de carregador de GC autônomo](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="c7c5c-465">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="c7c5c-466">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c7c5c-466">Setting name</span></span> | <span data-ttu-id="c7c5c-467">Valores</span><span class="sxs-lookup"><span data-stu-id="c7c5c-467">Values</span></span> | <span data-ttu-id="c7c5c-468">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c7c5c-468">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c7c5c-469">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-469">**runtimeconfig.json**</span></span> | <span data-ttu-id="c7c5c-470">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-470">N/A</span></span> | <span data-ttu-id="c7c5c-471">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-471">N/A</span></span> | <span data-ttu-id="c7c5c-472">N/D</span><span class="sxs-lookup"><span data-stu-id="c7c5c-472">N/A</span></span> |
| <span data-ttu-id="c7c5c-473">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c7c5c-473">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="c7c5c-474">*string_path*</span><span class="sxs-lookup"><span data-stu-id="c7c5c-474">*string_path*</span></span> | <span data-ttu-id="c7c5c-475">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c7c5c-475">.NET Core 2.0</span></span> |
