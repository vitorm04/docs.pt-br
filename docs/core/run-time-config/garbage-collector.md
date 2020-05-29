---
title: Definições de configuração do coletor de lixo
description: Saiba mais sobre as configurações de tempo de execução para configurar como o coletor de lixo gerencia a memória para aplicativos .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 0ce2f70204463c1525ef7d29de21ddf5384d0238
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202095"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="83d27-103">Opções de configuração de tempo de execução para coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="83d27-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="83d27-104">Esta página contém informações sobre as configurações de coletor de lixo (GC) que podem ser alteradas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="83d27-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="83d27-105">Se você estiver tentando atingir o desempenho máximo de um aplicativo em execução, considere o uso dessas configurações.</span><span class="sxs-lookup"><span data-stu-id="83d27-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="83d27-106">No entanto, os padrões fornecem um desempenho ideal para a maioria dos aplicativos em situações típicas.</span><span class="sxs-lookup"><span data-stu-id="83d27-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="83d27-107">As configurações são organizadas em grupos nesta página.</span><span class="sxs-lookup"><span data-stu-id="83d27-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="83d27-108">As configurações em cada grupo são comumente usadas em conjunto entre si para obter um resultado específico.</span><span class="sxs-lookup"><span data-stu-id="83d27-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="83d27-109">Essas configurações também podem ser alteradas dinamicamente pelo aplicativo enquanto ele está em execução, portanto, as configurações de tempo de execução definidas podem ser substituídas.</span><span class="sxs-lookup"><span data-stu-id="83d27-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="83d27-110">Algumas configurações, como [nível de latência](../../standard/garbage-collection/latency.md), normalmente são definidas somente por meio da API em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="83d27-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="83d27-111">Essas configurações são omitidas desta página.</span><span class="sxs-lookup"><span data-stu-id="83d27-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="83d27-112">Para valores numéricos, use a notação decimal para as configurações no arquivo *runtimeconfig. JSON* e notação hexadecimal para configurações de variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="83d27-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="83d27-113">Para valores hexadecimais, você pode especificá-los com ou sem o prefixo "0x".</span><span class="sxs-lookup"><span data-stu-id="83d27-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="83d27-114">Tipos de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="83d27-114">Flavors of garbage collection</span></span>

<span data-ttu-id="83d27-115">Os dois tipos principais de coleta de lixo são estação de trabalho GC e GC de servidor.</span><span class="sxs-lookup"><span data-stu-id="83d27-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="83d27-116">Para obter mais informações sobre as diferenças entre as duas, consulte [estação de trabalho e coleta de lixo do servidor](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="83d27-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="83d27-117">Os subtipos de coleta de lixo são em segundo plano e não simultâneos.</span><span class="sxs-lookup"><span data-stu-id="83d27-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="83d27-118">Use as seguintes configurações para selecionar tipos de coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="83d27-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="83d27-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="83d27-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="83d27-120">Define se o aplicativo usa a coleta de lixo da estação de trabalho ou a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="83d27-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="83d27-121">Padrão: coleta de lixo da estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="83d27-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="83d27-122">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="83d27-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="83d27-123">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-123">Setting name</span></span> | <span data-ttu-id="83d27-124">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-124">Values</span></span> | <span data-ttu-id="83d27-125">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-126">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="83d27-127">`false`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="83d27-127">`false` - workstation</span></span><br/><span data-ttu-id="83d27-128">`true`-servidor</span><span class="sxs-lookup"><span data-stu-id="83d27-128">`true` - server</span></span> | <span data-ttu-id="83d27-129">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-130">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="83d27-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="83d27-131">`false`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="83d27-131">`false` - workstation</span></span><br/><span data-ttu-id="83d27-132">`true`-servidor</span><span class="sxs-lookup"><span data-stu-id="83d27-132">`true` - server</span></span> | <span data-ttu-id="83d27-133">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-134">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="83d27-135">`0`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="83d27-135">`0` - workstation</span></span><br/><span data-ttu-id="83d27-136">`1`-servidor</span><span class="sxs-lookup"><span data-stu-id="83d27-136">`1` - server</span></span> | <span data-ttu-id="83d27-137">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-138">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="83d27-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="83d27-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="83d27-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="83d27-140">`false`-Estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="83d27-140">`false` - workstation</span></span><br/><span data-ttu-id="83d27-141">`true`-servidor</span><span class="sxs-lookup"><span data-stu-id="83d27-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="83d27-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="83d27-142">Examples</span></span>

<span data-ttu-id="83d27-143">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="83d27-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="83d27-144">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="83d27-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="83d27-145">System. GC. simultaneamente/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="83d27-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="83d27-146">Configura se a coleta de lixo em segundo plano (simultânea) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="83d27-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="83d27-147">Padrão: usar GC em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="83d27-147">Default: Use background GC.</span></span> <span data-ttu-id="83d27-148">Isso é equivalente a definir o valor como `true` .</span><span class="sxs-lookup"><span data-stu-id="83d27-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="83d27-149">Para obter mais informações, consulte [coleta de lixo em segundo plano](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="83d27-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="83d27-150">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-150">Setting name</span></span> | <span data-ttu-id="83d27-151">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-151">Values</span></span> | <span data-ttu-id="83d27-152">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="83d27-154">`true`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="83d27-154">`true` - background GC</span></span><br/><span data-ttu-id="83d27-155">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="83d27-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="83d27-156">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-157">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="83d27-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="83d27-158">`true`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="83d27-158">`true` - background GC</span></span><br/><span data-ttu-id="83d27-159">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="83d27-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="83d27-160">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-161">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="83d27-162">`1`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="83d27-162">`1` - background GC</span></span><br/><span data-ttu-id="83d27-163">`0`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="83d27-163">`0` - non-concurrent GC</span></span> | <span data-ttu-id="83d27-164">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-165">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="83d27-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="83d27-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="83d27-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="83d27-167">`true`-GC em segundo plano</span><span class="sxs-lookup"><span data-stu-id="83d27-167">`true` - background GC</span></span><br/><span data-ttu-id="83d27-168">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="83d27-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="83d27-169">Exemplos</span><span class="sxs-lookup"><span data-stu-id="83d27-169">Examples</span></span>

<span data-ttu-id="83d27-170">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="83d27-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="83d27-171">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="83d27-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="83d27-172">Gerenciar o uso de recursos</span><span class="sxs-lookup"><span data-stu-id="83d27-172">Manage resource usage</span></span>

<span data-ttu-id="83d27-173">Use as configurações descritas nesta seção para gerenciar a memória e o uso do processador do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="83d27-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="83d27-174">Para obter mais informações sobre algumas dessas configurações, consulte o meio-termo entre a entrada de blog do [GC de estação de trabalho e servidor](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="83d27-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="83d27-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="83d27-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="83d27-176">Limita o número de heaps criados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="83d27-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="83d27-177">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="83d27-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="83d27-178">Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver habilitada, que é o padrão, a configuração de contagem de heap affinitizes `n` heaps/threads do GC para os primeiros `n` processadores.</span><span class="sxs-lookup"><span data-stu-id="83d27-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="83d27-179">(Use a [máscara relacionar](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou as configurações de [intervalos de relacionar](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) para especificar exatamente quais processadores relacionar.)</span><span class="sxs-lookup"><span data-stu-id="83d27-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="83d27-180">Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desabilitada, essa configuração limitará o número de heaps do GC.</span><span class="sxs-lookup"><span data-stu-id="83d27-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="83d27-181">Para obter mais informações, consulte o [GCHeapCount comentários](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="83d27-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="83d27-182">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-182">Setting name</span></span> | <span data-ttu-id="83d27-183">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-183">Values</span></span> | <span data-ttu-id="83d27-184">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-185">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="83d27-186">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-186">*decimal value*</span></span> | <span data-ttu-id="83d27-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="83d27-188">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="83d27-189">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-189">*hexadecimal value*</span></span> | <span data-ttu-id="83d27-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="83d27-191">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="83d27-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="83d27-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="83d27-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="83d27-193">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-193">*decimal value*</span></span> | <span data-ttu-id="83d27-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="83d27-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="83d27-195">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="83d27-195">Example:</span></span>

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
> <span data-ttu-id="83d27-196">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="83d27-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="83d27-197">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="83d27-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="83d27-198">Por exemplo, para limitar o número de heaps a 16, os valores seriam 16 para o arquivo JSON e 0x10 ou 10 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="83d27-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="83d27-199">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="83d27-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="83d27-200">Especifica os processadores exatos que os threads do coletor de lixo devem usar.</span><span class="sxs-lookup"><span data-stu-id="83d27-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="83d27-201">Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desabilitada, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="83d27-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="83d27-202">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="83d27-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="83d27-203">O valor é uma máscara de bits que define os processadores que estão disponíveis para o processo.</span><span class="sxs-lookup"><span data-stu-id="83d27-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="83d27-204">Por exemplo, um valor decimal de 1023 (ou um valor hexadecimal de 0x3FF ou 3FF se você estiver usando a variável de ambiente) é 0011 1111 1111 em notação binária.</span><span class="sxs-lookup"><span data-stu-id="83d27-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="83d27-205">Isso especifica que os primeiros 10 processadores devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="83d27-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="83d27-206">Para especificar os 10 próximos processadores, ou seja, os processadores 10-19, especifique um valor decimal de 1047552 (ou um valor hexadecimal de 0xFFC00 ou FFC00), que é equivalente a um valor binário de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="83d27-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="83d27-207">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-207">Setting name</span></span> | <span data-ttu-id="83d27-208">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-208">Values</span></span> | <span data-ttu-id="83d27-209">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-210">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="83d27-211">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-211">*decimal value*</span></span> | <span data-ttu-id="83d27-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="83d27-213">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="83d27-214">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-214">*hexadecimal value*</span></span> | <span data-ttu-id="83d27-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="83d27-216">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="83d27-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="83d27-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="83d27-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="83d27-218">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-218">*decimal value*</span></span> | <span data-ttu-id="83d27-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="83d27-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="83d27-220">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="83d27-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="83d27-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="83d27-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="83d27-222">Especifica a lista de processadores a serem usados para threads do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="83d27-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="83d27-223">Essa configuração é semelhante a [System. GC. HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), exceto pelo fato de que ela permite que você especifique mais de 64 processadores.</span><span class="sxs-lookup"><span data-stu-id="83d27-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="83d27-224">Para sistemas operacionais Windows, Prefixe o número do processador ou o intervalo com o [grupo de CPU](/windows/win32/procthread/processor-groups)correspondente, por exemplo, "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="83d27-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="83d27-225">Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desabilitada, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="83d27-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="83d27-226">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="83d27-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="83d27-227">Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.</span><span class="sxs-lookup"><span data-stu-id="83d27-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="83d27-228">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-228">Setting name</span></span> | <span data-ttu-id="83d27-229">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-229">Values</span></span> | <span data-ttu-id="83d27-230">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-231">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="83d27-232">Lista separada por vírgulas de números de processador ou intervalos de números de processador.</span><span class="sxs-lookup"><span data-stu-id="83d27-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="83d27-233">Exemplo de UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="83d27-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="83d27-234">Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="83d27-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="83d27-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="83d27-236">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="83d27-237">Lista separada por vírgulas de números de processador ou intervalos de números de processador.</span><span class="sxs-lookup"><span data-stu-id="83d27-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="83d27-238">Exemplo de UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="83d27-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="83d27-239">Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="83d27-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="83d27-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-240">.NET Core 3.0</span></span> |

<span data-ttu-id="83d27-241">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="83d27-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="83d27-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="83d27-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="83d27-243">Configura se o coletor de lixo usa [grupos de CPU](/windows/win32/procthread/processor-groups) ou não.</span><span class="sxs-lookup"><span data-stu-id="83d27-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="83d27-244">Quando um computador com Windows de 64 bits tem vários grupos de CPU, ou seja, há mais de 64 processadores, a habilitação desse elemento estende a coleta de lixo em todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="83d27-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="83d27-245">O coletor de lixo usa todos os núcleos para criar e balancear heaps.</span><span class="sxs-lookup"><span data-stu-id="83d27-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="83d27-246">Aplica-se à coleta de lixo do servidor somente em sistemas de operação do Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="83d27-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="83d27-247">Padrão: o GC não se estende por grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="83d27-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="83d27-248">Isso é equivalente a definir o valor como `0` .</span><span class="sxs-lookup"><span data-stu-id="83d27-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="83d27-249">Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.</span><span class="sxs-lookup"><span data-stu-id="83d27-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="83d27-250">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-250">Setting name</span></span> | <span data-ttu-id="83d27-251">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-251">Values</span></span> | <span data-ttu-id="83d27-252">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-253">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="83d27-254">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-254">N/A</span></span> | <span data-ttu-id="83d27-255">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-255">N/A</span></span> | <span data-ttu-id="83d27-256">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-256">N/A</span></span> |
| <span data-ttu-id="83d27-257">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="83d27-258">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="83d27-258">`0` - disabled</span></span><br/><span data-ttu-id="83d27-259">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="83d27-259">`1` - enabled</span></span> | <span data-ttu-id="83d27-260">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-261">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="83d27-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="83d27-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="83d27-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="83d27-263">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="83d27-263">`false` - disabled</span></span><br/><span data-ttu-id="83d27-264">`true`-habilitado</span><span class="sxs-lookup"><span data-stu-id="83d27-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="83d27-265">Para configurar o Common Language Runtime (CLR) para também distribuir threads do pool de threads em todos os grupos de CPU, habilite a opção de [elemento Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="83d27-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="83d27-266">Para aplicativos .NET Core, você pode habilitar essa opção definindo o valor da variável de `COMPlus_Thread_UseAllCpuGroups` ambiente como `1` .</span><span class="sxs-lookup"><span data-stu-id="83d27-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="83d27-267">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="83d27-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="83d27-268">Especifica se os threads de coleta de lixo devem ser *relacionardos* com processadores.</span><span class="sxs-lookup"><span data-stu-id="83d27-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="83d27-269">Para relacionar um thread de GC significa que ele só pode ser executado em sua CPU específica.</span><span class="sxs-lookup"><span data-stu-id="83d27-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="83d27-270">Um heap é criado para cada thread do GC.</span><span class="sxs-lookup"><span data-stu-id="83d27-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="83d27-271">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="83d27-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="83d27-272">Padrão: relacionar os threads de coleta de lixo com processadores.</span><span class="sxs-lookup"><span data-stu-id="83d27-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="83d27-273">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="83d27-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="83d27-274">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-274">Setting name</span></span> | <span data-ttu-id="83d27-275">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-275">Values</span></span> | <span data-ttu-id="83d27-276">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-277">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="83d27-278">`false`-relacionar</span><span class="sxs-lookup"><span data-stu-id="83d27-278">`false` - affinitize</span></span><br/><span data-ttu-id="83d27-279">`true`-Não relacionar</span><span class="sxs-lookup"><span data-stu-id="83d27-279">`true` - don't affinitize</span></span> | <span data-ttu-id="83d27-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="83d27-281">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="83d27-282">`0`-relacionar</span><span class="sxs-lookup"><span data-stu-id="83d27-282">`0` - affinitize</span></span><br/><span data-ttu-id="83d27-283">`1`-Não relacionar</span><span class="sxs-lookup"><span data-stu-id="83d27-283">`1` - don't affinitize</span></span> | <span data-ttu-id="83d27-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="83d27-285">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="83d27-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="83d27-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="83d27-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="83d27-287">`false`-relacionar</span><span class="sxs-lookup"><span data-stu-id="83d27-287">`false` - affinitize</span></span><br/><span data-ttu-id="83d27-288">`true`-Não relacionar</span><span class="sxs-lookup"><span data-stu-id="83d27-288">`true` - don't affinitize</span></span> | <span data-ttu-id="83d27-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="83d27-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="83d27-290">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="83d27-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="83d27-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="83d27-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="83d27-292">Especifica o tamanho máximo de confirmação, em bytes, para o heap de GC e a escrituração de GC.</span><span class="sxs-lookup"><span data-stu-id="83d27-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="83d27-293">Essa configuração se aplica somente a computadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="83d27-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="83d27-294">O valor padrão, que se aplica apenas em determinados casos, é o maior de 20 MB ou 75% do limite de memória no contêiner.</span><span class="sxs-lookup"><span data-stu-id="83d27-294">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="83d27-295">O valor padrão se aplica se:</span><span class="sxs-lookup"><span data-stu-id="83d27-295">The default value applies if:</span></span>

  - <span data-ttu-id="83d27-296">O processo está sendo executado dentro de um contêiner que tem um limite de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="83d27-296">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="83d27-297">[System. GC. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) não está definido.</span><span class="sxs-lookup"><span data-stu-id="83d27-297">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="83d27-298">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-298">Setting name</span></span> | <span data-ttu-id="83d27-299">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-299">Values</span></span> | <span data-ttu-id="83d27-300">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-300">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-301">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-301">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="83d27-302">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-302">*decimal value*</span></span> | <span data-ttu-id="83d27-303">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-303">.NET Core 3.0</span></span> |
| <span data-ttu-id="83d27-304">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-304">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="83d27-305">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-305">*hexadecimal value*</span></span> | <span data-ttu-id="83d27-306">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-306">.NET Core 3.0</span></span> |

<span data-ttu-id="83d27-307">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="83d27-307">Example:</span></span>

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
> <span data-ttu-id="83d27-308">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="83d27-308">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="83d27-309">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="83d27-309">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="83d27-310">Por exemplo, para especificar um limite rígido de heap de 200 mebibytes (MiB), os valores seriam 209715200 para o arquivo JSON e 0xC800000 ou C800000 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="83d27-310">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="83d27-311">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="83d27-311">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="83d27-312">Especifica o uso de heap de GC permitido como uma porcentagem da memória física total.</span><span class="sxs-lookup"><span data-stu-id="83d27-312">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="83d27-313">Se [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) também for definido, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="83d27-313">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="83d27-314">Essa configuração se aplica somente a computadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="83d27-314">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="83d27-315">Se o processo estiver sendo executado dentro de um contêiner que tem um limite de memória especificado, a porcentagem será calculada como uma porcentagem desse limite de memória.</span><span class="sxs-lookup"><span data-stu-id="83d27-315">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="83d27-316">O valor padrão, que se aplica apenas em determinados casos, é o menor de 20 MB ou 75% do limite de memória no contêiner.</span><span class="sxs-lookup"><span data-stu-id="83d27-316">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="83d27-317">O valor padrão se aplica se:</span><span class="sxs-lookup"><span data-stu-id="83d27-317">The default value applies if:</span></span>

  - <span data-ttu-id="83d27-318">O processo está sendo executado dentro de um contêiner que tem um limite de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="83d27-318">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="83d27-319">[System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) não está definido.</span><span class="sxs-lookup"><span data-stu-id="83d27-319">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="83d27-320">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-320">Setting name</span></span> | <span data-ttu-id="83d27-321">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-321">Values</span></span> | <span data-ttu-id="83d27-322">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-323">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="83d27-324">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-324">*decimal value*</span></span> | <span data-ttu-id="83d27-325">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-325">.NET Core 3.0</span></span> |
| <span data-ttu-id="83d27-326">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-326">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="83d27-327">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-327">*hexadecimal value*</span></span> | <span data-ttu-id="83d27-328">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-328">.NET Core 3.0</span></span> |

<span data-ttu-id="83d27-329">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="83d27-329">Example:</span></span>

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
> <span data-ttu-id="83d27-330">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="83d27-330">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="83d27-331">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="83d27-331">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="83d27-332">Por exemplo, para limitar o uso de heap a 30%, os valores seriam 30 para o arquivo JSON e 0x1E ou 1E para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="83d27-332">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="83d27-333">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="83d27-333">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="83d27-334">Configura se OS segmentos que devem ser excluídos são colocados em uma lista de espera para uso futuro ou são liberados de volta para o sistema operacional (SO).</span><span class="sxs-lookup"><span data-stu-id="83d27-334">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="83d27-335">Padrão: libera segmentos de volta para o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="83d27-335">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="83d27-336">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="83d27-336">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="83d27-337">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-337">Setting name</span></span> | <span data-ttu-id="83d27-338">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-338">Values</span></span> | <span data-ttu-id="83d27-339">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-339">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-340">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-340">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="83d27-341">`false`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="83d27-341">`false` - release to OS</span></span><br/><span data-ttu-id="83d27-342">`true`-colocar em espera</span><span class="sxs-lookup"><span data-stu-id="83d27-342">`true` - put on standby</span></span> | <span data-ttu-id="83d27-343">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-343">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-344">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="83d27-344">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="83d27-345">`false`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="83d27-345">`false` - release to OS</span></span><br/><span data-ttu-id="83d27-346">`true`-colocar em espera</span><span class="sxs-lookup"><span data-stu-id="83d27-346">`true` - put on standby</span></span> | <span data-ttu-id="83d27-347">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-347">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-348">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-348">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="83d27-349">`0`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="83d27-349">`0` - release to OS</span></span><br/><span data-ttu-id="83d27-350">`1`-colocar em espera</span><span class="sxs-lookup"><span data-stu-id="83d27-350">`1` - put on standby</span></span> | <span data-ttu-id="83d27-351">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-351">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="83d27-352">Exemplos</span><span class="sxs-lookup"><span data-stu-id="83d27-352">Examples</span></span>

<span data-ttu-id="83d27-353">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="83d27-353">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="83d27-354">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="83d27-354">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="83d27-355">Páginas grandes</span><span class="sxs-lookup"><span data-stu-id="83d27-355">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="83d27-356">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="83d27-356">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="83d27-357">Especifica se páginas grandes devem ser usadas quando um limite rígido de heap for definido.</span><span class="sxs-lookup"><span data-stu-id="83d27-357">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="83d27-358">Padrão: não use páginas grandes quando um limite rígido de heap for definido.</span><span class="sxs-lookup"><span data-stu-id="83d27-358">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="83d27-359">Isso é equivalente a definir o valor como `0` .</span><span class="sxs-lookup"><span data-stu-id="83d27-359">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="83d27-360">Essa é uma configuração experimental.</span><span class="sxs-lookup"><span data-stu-id="83d27-360">This is an experimental setting.</span></span>

| | <span data-ttu-id="83d27-361">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-361">Setting name</span></span> | <span data-ttu-id="83d27-362">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-362">Values</span></span> | <span data-ttu-id="83d27-363">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-363">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-364">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-364">**runtimeconfig.json**</span></span> | <span data-ttu-id="83d27-365">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-365">N/A</span></span> | <span data-ttu-id="83d27-366">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-366">N/A</span></span> | <span data-ttu-id="83d27-367">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-367">N/A</span></span> |
| <span data-ttu-id="83d27-368">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-368">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="83d27-369">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="83d27-369">`0` - disabled</span></span><br/><span data-ttu-id="83d27-370">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="83d27-370">`1` - enabled</span></span> | <span data-ttu-id="83d27-371">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="83d27-371">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="83d27-372">Objetos grandes</span><span class="sxs-lookup"><span data-stu-id="83d27-372">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="83d27-373">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="83d27-373">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="83d27-374">Configura o suporte ao coletor de lixo em plataformas de 64 bits para matrizes com mais de 2 gigabytes (GB) no tamanho total.</span><span class="sxs-lookup"><span data-stu-id="83d27-374">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="83d27-375">Padrão: o GC dá suporte a matrizes maiores que 2 GB.</span><span class="sxs-lookup"><span data-stu-id="83d27-375">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="83d27-376">Isso é equivalente a definir o valor como `1` .</span><span class="sxs-lookup"><span data-stu-id="83d27-376">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="83d27-377">Essa opção pode se tornar obsoleta em uma versão futura do .NET.</span><span class="sxs-lookup"><span data-stu-id="83d27-377">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="83d27-378">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-378">Setting name</span></span> | <span data-ttu-id="83d27-379">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-379">Values</span></span> | <span data-ttu-id="83d27-380">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-380">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-381">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-381">**runtimeconfig.json**</span></span> | <span data-ttu-id="83d27-382">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-382">N/A</span></span> | <span data-ttu-id="83d27-383">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-383">N/A</span></span> | <span data-ttu-id="83d27-384">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-384">N/A</span></span> |
| <span data-ttu-id="83d27-385">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-385">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="83d27-386">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="83d27-386">`1` - enabled</span></span><br/> <span data-ttu-id="83d27-387">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="83d27-387">`0` - disabled</span></span> | <span data-ttu-id="83d27-388">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-389">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="83d27-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="83d27-390">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="83d27-390">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="83d27-391">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="83d27-391">`1` - enabled</span></span><br/> <span data-ttu-id="83d27-392">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="83d27-392">`0` - disabled</span></span> | <span data-ttu-id="83d27-393">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="83d27-393">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="83d27-394">Limite de heap de objeto grande</span><span class="sxs-lookup"><span data-stu-id="83d27-394">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="83d27-395">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="83d27-395">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="83d27-396">Especifica o tamanho do limite, em bytes, que faz com que os objetos vá para o LOH (heap de objeto grande).</span><span class="sxs-lookup"><span data-stu-id="83d27-396">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="83d27-397">O limite padrão é de 85.000 bytes.</span><span class="sxs-lookup"><span data-stu-id="83d27-397">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="83d27-398">O valor especificado deve ser maior que o limite padrão.</span><span class="sxs-lookup"><span data-stu-id="83d27-398">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="83d27-399">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-399">Setting name</span></span> | <span data-ttu-id="83d27-400">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-400">Values</span></span> | <span data-ttu-id="83d27-401">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-401">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-402">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-402">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="83d27-403">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-403">*decimal value*</span></span> | <span data-ttu-id="83d27-404">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-404">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-405">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-405">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="83d27-406">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-406">*hexadecimal value*</span></span> | <span data-ttu-id="83d27-407">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="83d27-407">.NET Core 1.0</span></span> |
| <span data-ttu-id="83d27-408">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="83d27-408">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="83d27-409">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="83d27-409">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="83d27-410">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="83d27-410">*decimal value*</span></span> | <span data-ttu-id="83d27-411">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="83d27-411">.NET Framework 4.8</span></span> |

<span data-ttu-id="83d27-412">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="83d27-412">Example:</span></span>

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
> <span data-ttu-id="83d27-413">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="83d27-413">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="83d27-414">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="83d27-414">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="83d27-415">Por exemplo, para definir um tamanho de limite de 120.000 bytes, os valores seriam 120000 para o arquivo JSON e 0x1D4C0 ou 1D4C0 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="83d27-415">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="83d27-416">GC autônomo</span><span class="sxs-lookup"><span data-stu-id="83d27-416">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="83d27-417">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="83d27-417">COMPlus_GCName</span></span>

- <span data-ttu-id="83d27-418">Especifica um caminho para a biblioteca que contém o coletor de lixo que o tempo de execução pretende carregar.</span><span class="sxs-lookup"><span data-stu-id="83d27-418">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="83d27-419">Para obter mais informações, consulte [design de carregador de GC autônomo](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="83d27-419">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="83d27-420">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="83d27-420">Setting name</span></span> | <span data-ttu-id="83d27-421">Valores</span><span class="sxs-lookup"><span data-stu-id="83d27-421">Values</span></span> | <span data-ttu-id="83d27-422">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83d27-422">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="83d27-423">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="83d27-423">**runtimeconfig.json**</span></span> | <span data-ttu-id="83d27-424">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-424">N/A</span></span> | <span data-ttu-id="83d27-425">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-425">N/A</span></span> | <span data-ttu-id="83d27-426">N/D</span><span class="sxs-lookup"><span data-stu-id="83d27-426">N/A</span></span> |
| <span data-ttu-id="83d27-427">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="83d27-427">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="83d27-428">*string_path*</span><span class="sxs-lookup"><span data-stu-id="83d27-428">*string_path*</span></span> | <span data-ttu-id="83d27-429">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="83d27-429">.NET Core 2.0</span></span> |
