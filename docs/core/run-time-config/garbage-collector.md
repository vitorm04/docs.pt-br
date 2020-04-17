---
title: Configurações de configuração de coletor de lixo
description: Saiba mais sobre as configurações de tempo de execução para configurar como o coletor de lixo gerencia a memória para aplicativos .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: dfb641eeda03d1acaa4771bd6253fcb33c4082a6
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607804"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="dccc8-103">Opções de configuração em tempo de execução para coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="dccc8-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="dccc8-104">Esta página contém informações sobre configurações de coletor de lixo (GC) que podem ser alteradas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dccc8-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="dccc8-105">Se você está tentando alcançar o máximo de desempenho de um aplicativo em execução, considere usar essas configurações.</span><span class="sxs-lookup"><span data-stu-id="dccc8-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="dccc8-106">No entanto, os padrões fornecem um desempenho ideal para a maioria dos aplicativos em situações típicas.</span><span class="sxs-lookup"><span data-stu-id="dccc8-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="dccc8-107">As configurações são organizadas em grupos nesta página.</span><span class="sxs-lookup"><span data-stu-id="dccc8-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="dccc8-108">As configurações dentro de cada grupo são comumente usadas em conjunto entre si para obter um resultado específico.</span><span class="sxs-lookup"><span data-stu-id="dccc8-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="dccc8-109">Essas configurações também podem ser alteradas dinamicamente pelo aplicativo enquanto ele está sendo executado, de modo que quaisquer configurações de tempo de execução que você definir podem ser substituídas.</span><span class="sxs-lookup"><span data-stu-id="dccc8-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="dccc8-110">Algumas configurações, como o [nível de latência,](../../standard/garbage-collection/latency.md)são normalmente definidas apenas através da API na hora do projeto.</span><span class="sxs-lookup"><span data-stu-id="dccc8-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="dccc8-111">Essas configurações são omitidas desta página.</span><span class="sxs-lookup"><span data-stu-id="dccc8-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="dccc8-112">Para valores numério, use notação decimal para configurações no arquivo *runtimeconfig.json* e notação hexadecimal para configurações variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="dccc8-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="dccc8-113">Para valores hexadecimais, você pode especificá-los com ou sem o prefixo "0x".</span><span class="sxs-lookup"><span data-stu-id="dccc8-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="dccc8-114">Sabores da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="dccc8-114">Flavors of garbage collection</span></span>

<span data-ttu-id="dccc8-115">Os dois principais sabores da coleta de lixo são a Estação de Trabalho GC e o servidor GC.</span><span class="sxs-lookup"><span data-stu-id="dccc8-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="dccc8-116">Para obter mais informações sobre as diferenças entre os dois, consulte [Fundamentos da coleta de lixo](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="dccc8-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="dccc8-117">Os subsabores da coleta de lixo são de fundo e não são concomitantes.</span><span class="sxs-lookup"><span data-stu-id="dccc8-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="dccc8-118">Use as seguintes configurações para selecionar sabores de coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="dccc8-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="dccc8-119">System.GC.Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="dccc8-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="dccc8-120">Configura se o aplicativo usa coleta de lixo da estação de trabalho ou coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="dccc8-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="dccc8-121">Padrão: Coleta de`false`lixo da estação de trabalho ( ).</span><span class="sxs-lookup"><span data-stu-id="dccc8-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="dccc8-122">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-122">Setting name</span></span> | <span data-ttu-id="dccc8-123">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-123">Values</span></span> | <span data-ttu-id="dccc8-124">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-125">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="dccc8-126">`false`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="dccc8-126">`false` - workstation</span></span><br/><span data-ttu-id="dccc8-127">`true`- servidor</span><span class="sxs-lookup"><span data-stu-id="dccc8-127">`true` - server</span></span> | <span data-ttu-id="dccc8-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-129">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="dccc8-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="dccc8-130">`false`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="dccc8-130">`false` - workstation</span></span><br/><span data-ttu-id="dccc8-131">`true`- servidor</span><span class="sxs-lookup"><span data-stu-id="dccc8-131">`true` - server</span></span> | <span data-ttu-id="dccc8-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-133">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="dccc8-134">`0`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="dccc8-134">`0` - workstation</span></span><br/><span data-ttu-id="dccc8-135">`1`- servidor</span><span class="sxs-lookup"><span data-stu-id="dccc8-135">`1` - server</span></span> | <span data-ttu-id="dccc8-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-137">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="dccc8-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="dccc8-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="dccc8-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="dccc8-139">`false`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="dccc8-139">`false` - workstation</span></span><br/><span data-ttu-id="dccc8-140">`true`- servidor</span><span class="sxs-lookup"><span data-stu-id="dccc8-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="dccc8-141">Exemplos</span><span class="sxs-lookup"><span data-stu-id="dccc8-141">Examples</span></span>

<span data-ttu-id="dccc8-142">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="dccc8-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="dccc8-143">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="dccc8-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="dccc8-144">System.GC.Simultânea/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="dccc8-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="dccc8-145">Configura se a coleta de lixo em segundo plano (simultânea) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="dccc8-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="dccc8-146">Padrão: Ativado`true`().</span><span class="sxs-lookup"><span data-stu-id="dccc8-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="dccc8-147">Para obter mais informações, consulte [Coleta de lixo em segundo](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) plano e coleta de lixo do servidor em segundo [plano](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="dccc8-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="dccc8-148">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-148">Setting name</span></span> | <span data-ttu-id="dccc8-149">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-149">Values</span></span> | <span data-ttu-id="dccc8-150">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-151">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="dccc8-152">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="dccc8-152">`true` - background GC</span></span><br/><span data-ttu-id="dccc8-153">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="dccc8-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="dccc8-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-155">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="dccc8-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="dccc8-156">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="dccc8-156">`true` - background GC</span></span><br/><span data-ttu-id="dccc8-157">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="dccc8-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="dccc8-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-159">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="dccc8-160">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="dccc8-160">`true` - background GC</span></span><br/><span data-ttu-id="dccc8-161">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="dccc8-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="dccc8-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-163">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="dccc8-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="dccc8-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="dccc8-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="dccc8-165">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="dccc8-165">`true` - background GC</span></span><br/><span data-ttu-id="dccc8-166">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="dccc8-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="dccc8-167">Exemplos</span><span class="sxs-lookup"><span data-stu-id="dccc8-167">Examples</span></span>

<span data-ttu-id="dccc8-168">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="dccc8-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="dccc8-169">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="dccc8-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="dccc8-170">Gerenciar o uso de recursos</span><span class="sxs-lookup"><span data-stu-id="dccc8-170">Manage resource usage</span></span>

<span data-ttu-id="dccc8-171">Use as configurações descritas nesta seção para gerenciar o uso da memória e do processador do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="dccc8-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="dccc8-172">Para obter mais informações sobre algumas dessas configurações, consulte o meio termo entre a [estação de trabalho e a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) entrada do blog gc do servidor.</span><span class="sxs-lookup"><span data-stu-id="dccc8-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="dccc8-173">System.GC.Heapcount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="dccc8-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="dccc8-174">Limita o número de montes criados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="dccc8-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="dccc8-175">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="dccc8-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="dccc8-176">Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver ativada, que é `n` o padrão, a configuração `n` de contagem de pilhas adiaos pilhas/threads GC para os primeiros processadores.</span><span class="sxs-lookup"><span data-stu-id="dccc8-176">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="dccc8-177">(Use as configurações de [intervalos de afeitização](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou [aderiss para](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) especificar exatamente quais processadores aparticipar.)</span><span class="sxs-lookup"><span data-stu-id="dccc8-177">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="dccc8-178">Se [a afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desativada, essa configuração limita o número de pilhas gc.</span><span class="sxs-lookup"><span data-stu-id="dccc8-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="dccc8-179">Para obter mais informações, consulte as observações do [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="dccc8-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="dccc8-180">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-180">Setting name</span></span> | <span data-ttu-id="dccc8-181">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-181">Values</span></span> | <span data-ttu-id="dccc8-182">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-183">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="dccc8-184">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-184">*decimal value*</span></span> | <span data-ttu-id="dccc8-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="dccc8-186">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="dccc8-187">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-187">*hexadecimal value*</span></span> | <span data-ttu-id="dccc8-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="dccc8-189">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="dccc8-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="dccc8-190">GCHeapcount</span><span class="sxs-lookup"><span data-stu-id="dccc8-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="dccc8-191">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-191">*decimal value*</span></span> | <span data-ttu-id="dccc8-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="dccc8-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="dccc8-193">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="dccc8-193">Example:</span></span>

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
> <span data-ttu-id="dccc8-194">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="dccc8-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="dccc8-195">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="dccc8-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="dccc8-196">Por exemplo, para limitar o número de pilhas a 16, os valores seriam 16 para o arquivo JSON e 0x10 ou 10 para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="dccc8-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="dccc8-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="dccc8-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="dccc8-198">Especifica os processadores exatos que os segmentos coletores de lixo devem usar.</span><span class="sxs-lookup"><span data-stu-id="dccc8-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="dccc8-199">Se [a afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desativada, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="dccc8-199">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="dccc8-200">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="dccc8-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="dccc8-201">O valor é uma máscara de bit que define os processadores disponíveis para o processo.</span><span class="sxs-lookup"><span data-stu-id="dccc8-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="dccc8-202">Por exemplo, um valor decimal de 1023 (ou um valor hexadecimal de 0x3FF ou 3FF se você estiver usando a variável ambiente) é 0011 1111 1111 em notação binária.</span><span class="sxs-lookup"><span data-stu-id="dccc8-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="dccc8-203">Isso especifica que os primeiros 10 processadores devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="dccc8-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="dccc8-204">Para especificar os próximos 10 processadores, ou seja, processadores 10-19, especifique um valor decimal de 1047552 (ou um valor hexadecimal de 0xFFC00 ou FFC00), que equivale a um valor binário de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="dccc8-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="dccc8-205">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-205">Setting name</span></span> | <span data-ttu-id="dccc8-206">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-206">Values</span></span> | <span data-ttu-id="dccc8-207">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-208">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="dccc8-209">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-209">*decimal value*</span></span> | <span data-ttu-id="dccc8-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="dccc8-211">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="dccc8-212">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-212">*hexadecimal value*</span></span> | <span data-ttu-id="dccc8-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="dccc8-214">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="dccc8-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="dccc8-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="dccc8-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="dccc8-216">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-216">*decimal value*</span></span> | <span data-ttu-id="dccc8-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="dccc8-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="dccc8-218">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="dccc8-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="dccc8-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="dccc8-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="dccc8-220">Especifica a lista de processadores a serem usados para segmentos coletores de lixo.</span><span class="sxs-lookup"><span data-stu-id="dccc8-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="dccc8-221">Esta configuração é semelhante ao [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), exceto que permite especificar mais de 64 processadores.</span><span class="sxs-lookup"><span data-stu-id="dccc8-221">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="dccc8-222">Para sistemas operacionais Windows, prefixe o número do processador ou o intervalo com o grupo de [CPU](/windows/win32/procthread/processor-groups)correspondente, por exemplo, "0:1-10,0:12,1:50-52,1:70".</span><span class="sxs-lookup"><span data-stu-id="dccc8-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="dccc8-223">Se [a afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desativada, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="dccc8-223">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="dccc8-224">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="dccc8-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="dccc8-225">Para obter mais informações, consulte [Tornando a configuração da CPU melhor para GC em máquinas com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog de Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="dccc8-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="dccc8-226">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-226">Setting name</span></span> | <span data-ttu-id="dccc8-227">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-227">Values</span></span> | <span data-ttu-id="dccc8-228">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-229">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="dccc8-230">Lista separada por comma de números de processadores ou faixas de números de processadores.</span><span class="sxs-lookup"><span data-stu-id="dccc8-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="dccc8-231">Exemplo unix: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="dccc8-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="dccc8-232">Exemplo do Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="dccc8-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="dccc8-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="dccc8-234">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="dccc8-235">Lista separada por comma de números de processadores ou faixas de números de processadores.</span><span class="sxs-lookup"><span data-stu-id="dccc8-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="dccc8-236">Exemplo unix: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="dccc8-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="dccc8-237">Exemplo do Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="dccc8-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="dccc8-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-238">.NET Core 3.0</span></span> |

<span data-ttu-id="dccc8-239">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="dccc8-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="dccc8-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="dccc8-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="dccc8-241">Configura se o coletor de lixo usa ou não [grupos de CPU.](/windows/win32/procthread/processor-groups)</span><span class="sxs-lookup"><span data-stu-id="dccc8-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="dccc8-242">Quando um computador Windows de 64 bits tem vários grupos de CPU, ou seja, há mais de 64 processadores, permitindo que esse elemento estenda a coleta de lixo em todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="dccc8-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="dccc8-243">O coletor de lixo usa todos os núcleos para criar e equilibrar pilhas.</span><span class="sxs-lookup"><span data-stu-id="dccc8-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="dccc8-244">Aplica-se à coleta de lixo do servidor apenas em sistemas de operação Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="dccc8-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="dccc8-245">Padrão: Desabilitado ( ).`0`</span><span class="sxs-lookup"><span data-stu-id="dccc8-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="dccc8-246">Para obter mais informações, consulte [Tornando a configuração da CPU melhor para GC em máquinas com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog de Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="dccc8-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="dccc8-247">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-247">Setting name</span></span> | <span data-ttu-id="dccc8-248">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-248">Values</span></span> | <span data-ttu-id="dccc8-249">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-250">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="dccc8-251">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-251">N/A</span></span> | <span data-ttu-id="dccc8-252">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-252">N/A</span></span> | <span data-ttu-id="dccc8-253">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-253">N/A</span></span> |
| <span data-ttu-id="dccc8-254">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="dccc8-255">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="dccc8-255">`0` - disabled</span></span><br/><span data-ttu-id="dccc8-256">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="dccc8-256">`1` - enabled</span></span> | <span data-ttu-id="dccc8-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-258">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="dccc8-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="dccc8-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="dccc8-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="dccc8-260">`false`- deficientes</span><span class="sxs-lookup"><span data-stu-id="dccc8-260">`false` - disabled</span></span><br/><span data-ttu-id="dccc8-261">`true`- habilitado</span><span class="sxs-lookup"><span data-stu-id="dccc8-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="dccc8-262">Para configurar o tempo de execução de idioma comum (CLR) para também distribuir threads do pool de segmentos em todos os grupos da CPU, habilite a opção [de elemento Thread_UseAllCpuGroups.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)</span><span class="sxs-lookup"><span data-stu-id="dccc8-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="dccc8-263">Para aplicativos .NET Core, você pode habilitar `COMPlus_Thread_UseAllCpuGroups` essa opção `1`definindo o valor da variável ambiente para .</span><span class="sxs-lookup"><span data-stu-id="dccc8-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="dccc8-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="dccc8-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="dccc8-265">Especifica se é *a adesão dos* segmentos de coleta de lixo com processadores.</span><span class="sxs-lookup"><span data-stu-id="dccc8-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="dccc8-266">Adenar um segmento GC significa que ele só pode ser executado em sua CPU específica.</span><span class="sxs-lookup"><span data-stu-id="dccc8-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="dccc8-267">Um monte é criado para cada segmento GC.</span><span class="sxs-lookup"><span data-stu-id="dccc8-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="dccc8-268">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="dccc8-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="dccc8-269">Padrão: Afena os fios de coleta`false`de lixo com processadores ().</span><span class="sxs-lookup"><span data-stu-id="dccc8-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="dccc8-270">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-270">Setting name</span></span> | <span data-ttu-id="dccc8-271">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-271">Values</span></span> | <span data-ttu-id="dccc8-272">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-273">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="dccc8-274">`false`- afeição</span><span class="sxs-lookup"><span data-stu-id="dccc8-274">`false` - affinitize</span></span><br/><span data-ttu-id="dccc8-275">`true`- não afete</span><span class="sxs-lookup"><span data-stu-id="dccc8-275">`true` - don't affinitize</span></span> | <span data-ttu-id="dccc8-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="dccc8-277">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="dccc8-278">`0`- afeição</span><span class="sxs-lookup"><span data-stu-id="dccc8-278">`0` - affinitize</span></span><br/><span data-ttu-id="dccc8-279">`1`- não afete</span><span class="sxs-lookup"><span data-stu-id="dccc8-279">`1` - don't affinitize</span></span> | <span data-ttu-id="dccc8-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="dccc8-281">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="dccc8-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="dccc8-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="dccc8-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="dccc8-283">`false`- afeição</span><span class="sxs-lookup"><span data-stu-id="dccc8-283">`false` - affinitize</span></span><br/><span data-ttu-id="dccc8-284">`true`- não afete</span><span class="sxs-lookup"><span data-stu-id="dccc8-284">`true` - don't affinitize</span></span> | <span data-ttu-id="dccc8-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="dccc8-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="dccc8-286">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="dccc8-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="dccc8-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="dccc8-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="dccc8-288">Especifica o tamanho máximo de confirmação, em bytes, para a contabilidade GC heap e GC.</span><span class="sxs-lookup"><span data-stu-id="dccc8-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="dccc8-289">Esta configuração só se aplica a computadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="dccc8-289">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="dccc8-290">O valor padrão, que só se aplica em certos casos, é o menor de 20 MB ou 75% do limite de memória no recipiente.</span><span class="sxs-lookup"><span data-stu-id="dccc8-290">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="dccc8-291">O valor padrão se aplica se:</span><span class="sxs-lookup"><span data-stu-id="dccc8-291">The default value applies if:</span></span>

  - <span data-ttu-id="dccc8-292">O processo está sendo executado dentro de um recipiente que tem um limite de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="dccc8-292">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="dccc8-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) não está definido.</span><span class="sxs-lookup"><span data-stu-id="dccc8-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="dccc8-294">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-294">Setting name</span></span> | <span data-ttu-id="dccc8-295">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-295">Values</span></span> | <span data-ttu-id="dccc8-296">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-296">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-297">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-297">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="dccc8-298">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-298">*decimal value*</span></span> | <span data-ttu-id="dccc8-299">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-299">.NET Core 3.0</span></span> |
| <span data-ttu-id="dccc8-300">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-300">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="dccc8-301">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-301">*hexadecimal value*</span></span> | <span data-ttu-id="dccc8-302">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-302">.NET Core 3.0</span></span> |

<span data-ttu-id="dccc8-303">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="dccc8-303">Example:</span></span>

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
> <span data-ttu-id="dccc8-304">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="dccc8-304">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="dccc8-305">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="dccc8-305">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="dccc8-306">Por exemplo, para especificar um limite rígido de 200 mebibytes (MiB), os valores seriam 209715200 para o arquivo JSON e 0xC800000 ou C800000 para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="dccc8-306">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="dccc8-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="dccc8-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="dccc8-308">Especifica o uso permitido do heap GC como uma porcentagem da memória física total.</span><span class="sxs-lookup"><span data-stu-id="dccc8-308">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="dccc8-309">Se [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) também estiver definido, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="dccc8-309">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="dccc8-310">Esta configuração só se aplica a computadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="dccc8-310">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="dccc8-311">Se o processo estiver sendo executado dentro de um recipiente que tenha um limite de memória especificado, a porcentagem será calculada como uma porcentagem desse limite de memória.</span><span class="sxs-lookup"><span data-stu-id="dccc8-311">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="dccc8-312">O valor padrão, que só se aplica em certos casos, é o menor de 20 MB ou 75% do limite de memória no recipiente.</span><span class="sxs-lookup"><span data-stu-id="dccc8-312">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="dccc8-313">O valor padrão se aplica se:</span><span class="sxs-lookup"><span data-stu-id="dccc8-313">The default value applies if:</span></span>

  - <span data-ttu-id="dccc8-314">O processo está sendo executado dentro de um recipiente que tem um limite de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="dccc8-314">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="dccc8-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) não está definido.</span><span class="sxs-lookup"><span data-stu-id="dccc8-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="dccc8-316">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-316">Setting name</span></span> | <span data-ttu-id="dccc8-317">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-317">Values</span></span> | <span data-ttu-id="dccc8-318">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-318">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-319">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-319">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="dccc8-320">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-320">*decimal value*</span></span> | <span data-ttu-id="dccc8-321">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-321">.NET Core 3.0</span></span> |
| <span data-ttu-id="dccc8-322">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-322">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="dccc8-323">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-323">*hexadecimal value*</span></span> | <span data-ttu-id="dccc8-324">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-324">.NET Core 3.0</span></span> |

<span data-ttu-id="dccc8-325">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="dccc8-325">Example:</span></span>

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
> <span data-ttu-id="dccc8-326">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="dccc8-326">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="dccc8-327">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="dccc8-327">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="dccc8-328">Por exemplo, para limitar o uso do heap a 30%, os valores seriam 30 para o arquivo JSON e 0x1E ou 1E para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="dccc8-328">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="dccc8-329">System.GC.RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="dccc8-329">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="dccc8-330">Configura se os segmentos que devem ser excluídos são colocados em uma lista de espera para uso futuro ou são liberados de volta para o sistema operacional (OS).</span><span class="sxs-lookup"><span data-stu-id="dccc8-330">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="dccc8-331">Padrão: Liberar segmentos de`false`volta ao sistema operacional ( ).</span><span class="sxs-lookup"><span data-stu-id="dccc8-331">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="dccc8-332">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-332">Setting name</span></span> | <span data-ttu-id="dccc8-333">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-333">Values</span></span> | <span data-ttu-id="dccc8-334">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-334">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-335">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-335">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="dccc8-336">`false`- lançamento para os SO</span><span class="sxs-lookup"><span data-stu-id="dccc8-336">`false` - release to OS</span></span><br/><span data-ttu-id="dccc8-337">`true`- colocar em espera</span><span class="sxs-lookup"><span data-stu-id="dccc8-337">`true` - put on standby</span></span> | <span data-ttu-id="dccc8-338">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-338">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-339">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="dccc8-339">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="dccc8-340">`false`- lançamento para os SO</span><span class="sxs-lookup"><span data-stu-id="dccc8-340">`false` - release to OS</span></span><br/><span data-ttu-id="dccc8-341">`true`- colocar em espera</span><span class="sxs-lookup"><span data-stu-id="dccc8-341">`true` - put on standby</span></span> | <span data-ttu-id="dccc8-342">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-342">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-343">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-343">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="dccc8-344">`0`- lançamento para os SO</span><span class="sxs-lookup"><span data-stu-id="dccc8-344">`0` - release to OS</span></span><br/><span data-ttu-id="dccc8-345">`1`- colocar em espera</span><span class="sxs-lookup"><span data-stu-id="dccc8-345">`1` - put on standby</span></span> | <span data-ttu-id="dccc8-346">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-346">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="dccc8-347">Exemplos</span><span class="sxs-lookup"><span data-stu-id="dccc8-347">Examples</span></span>

<span data-ttu-id="dccc8-348">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="dccc8-348">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="dccc8-349">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="dccc8-349">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="dccc8-350">Páginas grandes</span><span class="sxs-lookup"><span data-stu-id="dccc8-350">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="dccc8-351">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="dccc8-351">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="dccc8-352">Especifica se páginas grandes devem ser usadas quando um limite rígido de pilha é definido.</span><span class="sxs-lookup"><span data-stu-id="dccc8-352">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="dccc8-353">Padrão: Desabilitado ( ).`0`</span><span class="sxs-lookup"><span data-stu-id="dccc8-353">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="dccc8-354">Este é um cenário experimental.</span><span class="sxs-lookup"><span data-stu-id="dccc8-354">This is an experimental setting.</span></span>

| | <span data-ttu-id="dccc8-355">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-355">Setting name</span></span> | <span data-ttu-id="dccc8-356">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-356">Values</span></span> | <span data-ttu-id="dccc8-357">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-358">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-358">**runtimeconfig.json**</span></span> | <span data-ttu-id="dccc8-359">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-359">N/A</span></span> | <span data-ttu-id="dccc8-360">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-360">N/A</span></span> | <span data-ttu-id="dccc8-361">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-361">N/A</span></span> |
| <span data-ttu-id="dccc8-362">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-362">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="dccc8-363">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="dccc8-363">`0` - disabled</span></span><br/><span data-ttu-id="dccc8-364">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="dccc8-364">`1` - enabled</span></span> | <span data-ttu-id="dccc8-365">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-365">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="dccc8-366">Objetos grandes</span><span class="sxs-lookup"><span data-stu-id="dccc8-366">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="dccc8-367">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="dccc8-367">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="dccc8-368">Configura suporte a coletores de lixo em plataformas de 64 bits para arrays maiores que 2 gigabytes (GB) em tamanho total.</span><span class="sxs-lookup"><span data-stu-id="dccc8-368">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="dccc8-369">Padrão: Ativado`1`().</span><span class="sxs-lookup"><span data-stu-id="dccc8-369">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="dccc8-370">Essa opção pode se tornar obsoleta em uma versão futura do .NET.</span><span class="sxs-lookup"><span data-stu-id="dccc8-370">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="dccc8-371">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-371">Setting name</span></span> | <span data-ttu-id="dccc8-372">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-372">Values</span></span> | <span data-ttu-id="dccc8-373">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-373">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-374">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-374">**runtimeconfig.json**</span></span> | <span data-ttu-id="dccc8-375">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-375">N/A</span></span> | <span data-ttu-id="dccc8-376">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-376">N/A</span></span> | <span data-ttu-id="dccc8-377">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-377">N/A</span></span> |
| <span data-ttu-id="dccc8-378">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-378">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="dccc8-379">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="dccc8-379">`1` - enabled</span></span><br/> <span data-ttu-id="dccc8-380">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="dccc8-380">`0` - disabled</span></span> | <span data-ttu-id="dccc8-381">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-381">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-382">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="dccc8-382">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="dccc8-383">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="dccc8-383">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="dccc8-384">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="dccc8-384">`1` - enabled</span></span><br/> <span data-ttu-id="dccc8-385">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="dccc8-385">`0` - disabled</span></span> | <span data-ttu-id="dccc8-386">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="dccc8-386">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="dccc8-387">Grande limiar de pilha de objetos</span><span class="sxs-lookup"><span data-stu-id="dccc8-387">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="dccc8-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="dccc8-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="dccc8-389">Especifica o tamanho do limiar, em bytes, que faz com que os objetos vão para o heap de objeto grande (LOH).</span><span class="sxs-lookup"><span data-stu-id="dccc8-389">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="dccc8-390">O limite padrão é de 85.000 bytes.</span><span class="sxs-lookup"><span data-stu-id="dccc8-390">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="dccc8-391">O valor especificado deve ser maior do que o limite padrão.</span><span class="sxs-lookup"><span data-stu-id="dccc8-391">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="dccc8-392">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-392">Setting name</span></span> | <span data-ttu-id="dccc8-393">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-393">Values</span></span> | <span data-ttu-id="dccc8-394">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-394">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-395">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-395">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="dccc8-396">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-396">*decimal value*</span></span> | <span data-ttu-id="dccc8-397">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-397">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-398">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-398">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="dccc8-399">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-399">*hexadecimal value*</span></span> | <span data-ttu-id="dccc8-400">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-400">.NET Core 1.0</span></span> |
| <span data-ttu-id="dccc8-401">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="dccc8-401">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="dccc8-402">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="dccc8-402">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="dccc8-403">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="dccc8-403">*decimal value*</span></span> | <span data-ttu-id="dccc8-404">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="dccc8-404">.NET Framework 4.8</span></span> |

<span data-ttu-id="dccc8-405">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="dccc8-405">Example:</span></span>

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
> <span data-ttu-id="dccc8-406">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="dccc8-406">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="dccc8-407">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="dccc8-407">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="dccc8-408">Por exemplo, para definir um tamanho de limite de 120.000 bytes, os valores seriam 120000 000 para o arquivo JSON e 0x1D4C0 ou 1D4C0 para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="dccc8-408">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="dccc8-409">GC autônomo</span><span class="sxs-lookup"><span data-stu-id="dccc8-409">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="dccc8-410">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="dccc8-410">COMPlus_GCName</span></span>

- <span data-ttu-id="dccc8-411">Especifica um caminho para a biblioteca contendo o coletor de lixo que o tempo de execução pretende carregar.</span><span class="sxs-lookup"><span data-stu-id="dccc8-411">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="dccc8-412">Para obter mais informações, consulte [o design do carregador GC autônomo](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="dccc8-412">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="dccc8-413">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="dccc8-413">Setting name</span></span> | <span data-ttu-id="dccc8-414">Valores</span><span class="sxs-lookup"><span data-stu-id="dccc8-414">Values</span></span> | <span data-ttu-id="dccc8-415">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dccc8-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="dccc8-416">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="dccc8-416">**runtimeconfig.json**</span></span> | <span data-ttu-id="dccc8-417">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-417">N/A</span></span> | <span data-ttu-id="dccc8-418">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-418">N/A</span></span> | <span data-ttu-id="dccc8-419">N/D</span><span class="sxs-lookup"><span data-stu-id="dccc8-419">N/A</span></span> |
| <span data-ttu-id="dccc8-420">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="dccc8-420">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="dccc8-421">*string_path*</span><span class="sxs-lookup"><span data-stu-id="dccc8-421">*string_path*</span></span> | <span data-ttu-id="dccc8-422">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="dccc8-422">.NET Core 2.0</span></span> |
