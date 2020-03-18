---
title: Configurações de configuração de coletor de lixo
description: Saiba mais sobre as configurações de tempo de execução para configurar como o coletor de lixo gerencia a memória para aplicativos .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733523"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="842a6-103">Opções de configuração em tempo de execução para coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="842a6-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="842a6-104">Esta página contém informações sobre configurações de coletor de lixo (GC) que podem ser alteradas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="842a6-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="842a6-105">Se você está tentando alcançar o máximo de desempenho de um aplicativo em execução, considere usar essas configurações.</span><span class="sxs-lookup"><span data-stu-id="842a6-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="842a6-106">No entanto, os padrões fornecem um desempenho ideal para a maioria dos aplicativos em situações típicas.</span><span class="sxs-lookup"><span data-stu-id="842a6-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="842a6-107">As configurações são organizadas em grupos nesta página.</span><span class="sxs-lookup"><span data-stu-id="842a6-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="842a6-108">As configurações dentro de cada grupo são comumente usadas em conjunto entre si para obter um resultado específico.</span><span class="sxs-lookup"><span data-stu-id="842a6-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="842a6-109">Essas configurações também podem ser alteradas dinamicamente pelo aplicativo enquanto ele está sendo executado, de modo que quaisquer configurações de tempo de execução que você definir podem ser substituídas.</span><span class="sxs-lookup"><span data-stu-id="842a6-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="842a6-110">Algumas configurações, como o [nível de latência,](../../standard/garbage-collection/latency.md)são normalmente definidas apenas através da API na hora do projeto.</span><span class="sxs-lookup"><span data-stu-id="842a6-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="842a6-111">Essas configurações são omitidas desta página.</span><span class="sxs-lookup"><span data-stu-id="842a6-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="842a6-112">Para valores numério, use notação decimal para configurações no arquivo *runtimeconfig.json* e notação hexadecimal para configurações variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="842a6-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="842a6-113">Para valores hexadecimais, você pode especificá-los com ou sem o prefixo "0x".</span><span class="sxs-lookup"><span data-stu-id="842a6-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="842a6-114">Sabores da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="842a6-114">Flavors of garbage collection</span></span>

<span data-ttu-id="842a6-115">Os dois principais sabores da coleta de lixo são a Estação de Trabalho GC e o servidor GC.</span><span class="sxs-lookup"><span data-stu-id="842a6-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="842a6-116">Para obter mais informações sobre as diferenças entre os dois, consulte [Fundamentos da coleta de lixo](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="842a6-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="842a6-117">Os subsabores da coleta de lixo são de fundo e não são concomitantes.</span><span class="sxs-lookup"><span data-stu-id="842a6-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="842a6-118">Use as seguintes configurações para selecionar sabores de coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="842a6-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="842a6-119">System.GC.Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="842a6-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="842a6-120">Configura se o aplicativo usa coleta de lixo da estação de trabalho ou coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="842a6-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="842a6-121">Padrão: Coleta de`false`lixo da estação de trabalho ( ).</span><span class="sxs-lookup"><span data-stu-id="842a6-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="842a6-122">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-122">Setting name</span></span> | <span data-ttu-id="842a6-123">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-123">Values</span></span> | <span data-ttu-id="842a6-124">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-125">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="842a6-126">`false`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="842a6-126">`false` - workstation</span></span><br/><span data-ttu-id="842a6-127">`true`- servidor</span><span class="sxs-lookup"><span data-stu-id="842a6-127">`true` - server</span></span> | <span data-ttu-id="842a6-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-129">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="842a6-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="842a6-130">`false`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="842a6-130">`false` - workstation</span></span><br/><span data-ttu-id="842a6-131">`true`- servidor</span><span class="sxs-lookup"><span data-stu-id="842a6-131">`true` - server</span></span> | <span data-ttu-id="842a6-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-133">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="842a6-134">`0`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="842a6-134">`0` - workstation</span></span><br/><span data-ttu-id="842a6-135">`1`- servidor</span><span class="sxs-lookup"><span data-stu-id="842a6-135">`1` - server</span></span> | <span data-ttu-id="842a6-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-137">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="842a6-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="842a6-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="842a6-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="842a6-139">`false`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="842a6-139">`false` - workstation</span></span><br/><span data-ttu-id="842a6-140">`true`- servidor</span><span class="sxs-lookup"><span data-stu-id="842a6-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="842a6-141">Exemplos</span><span class="sxs-lookup"><span data-stu-id="842a6-141">Examples</span></span>

<span data-ttu-id="842a6-142">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="842a6-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="842a6-143">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="842a6-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="842a6-144">System.GC.Simultânea/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="842a6-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="842a6-145">Configura se a coleta de lixo em segundo plano (simultânea) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="842a6-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="842a6-146">Padrão: Ativado`true`().</span><span class="sxs-lookup"><span data-stu-id="842a6-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="842a6-147">Para obter mais informações, consulte [Coleta de lixo em segundo](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) plano e coleta de lixo do servidor em segundo [plano](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="842a6-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="842a6-148">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-148">Setting name</span></span> | <span data-ttu-id="842a6-149">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-149">Values</span></span> | <span data-ttu-id="842a6-150">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-151">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="842a6-152">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="842a6-152">`true` - background GC</span></span><br/><span data-ttu-id="842a6-153">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="842a6-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="842a6-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-155">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="842a6-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="842a6-156">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="842a6-156">`true` - background GC</span></span><br/><span data-ttu-id="842a6-157">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="842a6-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="842a6-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-159">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="842a6-160">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="842a6-160">`true` - background GC</span></span><br/><span data-ttu-id="842a6-161">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="842a6-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="842a6-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-163">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="842a6-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="842a6-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="842a6-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="842a6-165">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="842a6-165">`true` - background GC</span></span><br/><span data-ttu-id="842a6-166">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="842a6-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="842a6-167">Exemplos</span><span class="sxs-lookup"><span data-stu-id="842a6-167">Examples</span></span>

<span data-ttu-id="842a6-168">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="842a6-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="842a6-169">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="842a6-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="842a6-170">Gerenciar o uso de recursos</span><span class="sxs-lookup"><span data-stu-id="842a6-170">Manage resource usage</span></span>

<span data-ttu-id="842a6-171">Use as configurações descritas nesta seção para gerenciar o uso da memória e do processador do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="842a6-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="842a6-172">Para obter mais informações sobre algumas dessas configurações, consulte o meio termo entre a [estação de trabalho e a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) entrada do blog gc do servidor.</span><span class="sxs-lookup"><span data-stu-id="842a6-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="842a6-173">System.GC.Heapcount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="842a6-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="842a6-174">Limita o número de montes criados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="842a6-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="842a6-175">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="842a6-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="842a6-176">Se a afinidade do processador GC estiver ativada, que é `n` o padrão, a configuração `n` de contagem de pilhas adiaos pilhas/threads GC para os primeiros processadores.</span><span class="sxs-lookup"><span data-stu-id="842a6-176">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="842a6-177">(Use as configurações de intervalos de afeitização ou aderiss para especificar exatamente quais processadores aparticipar.)</span><span class="sxs-lookup"><span data-stu-id="842a6-177">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="842a6-178">Se a afinidade do processador GC estiver desativada, essa configuração limita o número de pilhas gc.</span><span class="sxs-lookup"><span data-stu-id="842a6-178">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="842a6-179">Para obter mais informações, consulte as observações do [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="842a6-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="842a6-180">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-180">Setting name</span></span> | <span data-ttu-id="842a6-181">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-181">Values</span></span> | <span data-ttu-id="842a6-182">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-183">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="842a6-184">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-184">*decimal value*</span></span> | <span data-ttu-id="842a6-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="842a6-186">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="842a6-187">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-187">*hexadecimal value*</span></span> | <span data-ttu-id="842a6-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="842a6-189">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="842a6-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="842a6-190">GCHeapcount</span><span class="sxs-lookup"><span data-stu-id="842a6-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="842a6-191">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-191">*decimal value*</span></span> | <span data-ttu-id="842a6-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="842a6-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="842a6-193">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="842a6-193">Example:</span></span>

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
> <span data-ttu-id="842a6-194">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="842a6-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="842a6-195">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="842a6-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="842a6-196">Por exemplo, para limitar o número de pilhas a 16, os valores seriam 16 para o arquivo JSON e 0x10 ou 10 para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="842a6-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="842a6-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="842a6-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="842a6-198">Especifica os processadores exatos que os segmentos coletores de lixo devem usar.</span><span class="sxs-lookup"><span data-stu-id="842a6-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="842a6-199">Se a afinidade do `System.GC.NoAffinitize` `true`processador estiver desativada por configuração para , esta configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="842a6-199">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="842a6-200">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="842a6-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="842a6-201">O valor é uma máscara de bit que define os processadores disponíveis para o processo.</span><span class="sxs-lookup"><span data-stu-id="842a6-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="842a6-202">Por exemplo, um valor decimal de 1023 (ou um valor hexadecimal de 0x3FF ou 3FF se você estiver usando a variável ambiente) é 0011 1111 1111 em notação binária.</span><span class="sxs-lookup"><span data-stu-id="842a6-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="842a6-203">Isso especifica que os primeiros 10 processadores devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="842a6-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="842a6-204">Para especificar os próximos 10 processadores, ou seja, processadores 10-19, especifique um valor decimal de 1047552 (ou um valor hexadecimal de 0xFFC00 ou FFC00), que equivale a um valor binário de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="842a6-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="842a6-205">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-205">Setting name</span></span> | <span data-ttu-id="842a6-206">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-206">Values</span></span> | <span data-ttu-id="842a6-207">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-208">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="842a6-209">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-209">*decimal value*</span></span> | <span data-ttu-id="842a6-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="842a6-211">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="842a6-212">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-212">*hexadecimal value*</span></span> | <span data-ttu-id="842a6-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="842a6-214">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="842a6-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="842a6-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="842a6-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="842a6-216">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-216">*decimal value*</span></span> | <span data-ttu-id="842a6-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="842a6-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="842a6-218">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="842a6-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="842a6-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="842a6-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="842a6-220">Especifica a lista de processadores a serem usados para segmentos coletores de lixo.</span><span class="sxs-lookup"><span data-stu-id="842a6-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="842a6-221">Esta configuração `System.GC.HeapAffinitizeMask`é semelhante a , exceto que permite especificar mais de 64 processadores.</span><span class="sxs-lookup"><span data-stu-id="842a6-221">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="842a6-222">Para sistemas operacionais Windows, prefixe o número do processador ou o intervalo com o grupo de [CPU](/windows/win32/procthread/processor-groups)correspondente, por exemplo, "0:1-10,0:12,1:50-52,1:70".</span><span class="sxs-lookup"><span data-stu-id="842a6-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="842a6-223">Se a afinidade do `System.GC.NoAffinitize` `true`processador estiver desativada por configuração para , esta configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="842a6-223">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="842a6-224">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="842a6-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="842a6-225">Para obter mais informações, consulte [Tornando a configuração da CPU melhor para GC em máquinas com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog de Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="842a6-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="842a6-226">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-226">Setting name</span></span> | <span data-ttu-id="842a6-227">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-227">Values</span></span> | <span data-ttu-id="842a6-228">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-229">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="842a6-230">Lista separada por comma de números de processadores ou faixas de números de processadores.</span><span class="sxs-lookup"><span data-stu-id="842a6-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="842a6-231">Exemplo unix: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="842a6-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="842a6-232">Exemplo do Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="842a6-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="842a6-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="842a6-234">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="842a6-235">Lista separada por comma de números de processadores ou faixas de números de processadores.</span><span class="sxs-lookup"><span data-stu-id="842a6-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="842a6-236">Exemplo unix: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="842a6-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="842a6-237">Exemplo do Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="842a6-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="842a6-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-238">.NET Core 3.0</span></span> |

<span data-ttu-id="842a6-239">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="842a6-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="842a6-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="842a6-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="842a6-241">Configura se o coletor de lixo usa ou não [grupos de CPU.](/windows/win32/procthread/processor-groups)</span><span class="sxs-lookup"><span data-stu-id="842a6-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="842a6-242">Quando um computador Windows de 64 bits tem vários grupos de CPU, ou seja, há mais de 64 processadores, permitindo que esse elemento estenda a coleta de lixo em todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="842a6-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="842a6-243">O coletor de lixo usa todos os núcleos para criar e equilibrar pilhas.</span><span class="sxs-lookup"><span data-stu-id="842a6-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="842a6-244">Aplica-se à coleta de lixo do servidor apenas em sistemas de operação Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="842a6-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="842a6-245">Padrão: Desabilitado ( ).`0`</span><span class="sxs-lookup"><span data-stu-id="842a6-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="842a6-246">Para obter mais informações, consulte [Tornando a configuração da CPU melhor para GC em máquinas com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog de Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="842a6-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="842a6-247">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-247">Setting name</span></span> | <span data-ttu-id="842a6-248">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-248">Values</span></span> | <span data-ttu-id="842a6-249">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-250">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="842a6-251">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-251">N/A</span></span> | <span data-ttu-id="842a6-252">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-252">N/A</span></span> | <span data-ttu-id="842a6-253">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-253">N/A</span></span> |
| <span data-ttu-id="842a6-254">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="842a6-255">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="842a6-255">`0` - disabled</span></span><br/><span data-ttu-id="842a6-256">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="842a6-256">`1` - enabled</span></span> | <span data-ttu-id="842a6-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-258">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="842a6-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="842a6-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="842a6-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="842a6-260">`false`- deficientes</span><span class="sxs-lookup"><span data-stu-id="842a6-260">`false` - disabled</span></span><br/><span data-ttu-id="842a6-261">`true`- habilitado</span><span class="sxs-lookup"><span data-stu-id="842a6-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="842a6-262">Para configurar o tempo de execução de idioma comum (CLR) para também distribuir threads do pool de segmentos em todos os grupos da CPU, habilite a opção [de elemento Thread_UseAllCpuGroups.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)</span><span class="sxs-lookup"><span data-stu-id="842a6-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="842a6-263">Para aplicativos .NET Core, você pode habilitar `COMPlus_Thread_UseAllCpuGroups` essa opção `1`definindo o valor da variável ambiente para .</span><span class="sxs-lookup"><span data-stu-id="842a6-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="842a6-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="842a6-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="842a6-265">Especifica se é *a adesão dos* segmentos de coleta de lixo com processadores.</span><span class="sxs-lookup"><span data-stu-id="842a6-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="842a6-266">Adenar um segmento GC significa que ele só pode ser executado em sua CPU específica.</span><span class="sxs-lookup"><span data-stu-id="842a6-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="842a6-267">Um monte é criado para cada segmento GC.</span><span class="sxs-lookup"><span data-stu-id="842a6-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="842a6-268">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="842a6-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="842a6-269">Padrão: Afena os fios de coleta`false`de lixo com processadores ().</span><span class="sxs-lookup"><span data-stu-id="842a6-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="842a6-270">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-270">Setting name</span></span> | <span data-ttu-id="842a6-271">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-271">Values</span></span> | <span data-ttu-id="842a6-272">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-273">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="842a6-274">`false`- afeição</span><span class="sxs-lookup"><span data-stu-id="842a6-274">`false` - affinitize</span></span><br/><span data-ttu-id="842a6-275">`true`- não afete</span><span class="sxs-lookup"><span data-stu-id="842a6-275">`true` - don't affinitize</span></span> | <span data-ttu-id="842a6-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="842a6-277">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="842a6-278">`0`- afeição</span><span class="sxs-lookup"><span data-stu-id="842a6-278">`0` - affinitize</span></span><br/><span data-ttu-id="842a6-279">`1`- não afete</span><span class="sxs-lookup"><span data-stu-id="842a6-279">`1` - don't affinitize</span></span> | <span data-ttu-id="842a6-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="842a6-281">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="842a6-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="842a6-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="842a6-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="842a6-283">`false`- afeição</span><span class="sxs-lookup"><span data-stu-id="842a6-283">`false` - affinitize</span></span><br/><span data-ttu-id="842a6-284">`true`- não afete</span><span class="sxs-lookup"><span data-stu-id="842a6-284">`true` - don't affinitize</span></span> | <span data-ttu-id="842a6-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="842a6-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="842a6-286">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="842a6-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="842a6-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="842a6-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="842a6-288">Especifica o tamanho máximo de confirmação, em bytes, para a contabilidade GC heap e GC.</span><span class="sxs-lookup"><span data-stu-id="842a6-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="842a6-289">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-289">Setting name</span></span> | <span data-ttu-id="842a6-290">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-290">Values</span></span> | <span data-ttu-id="842a6-291">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-291">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-292">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-292">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="842a6-293">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-293">*decimal value*</span></span> | <span data-ttu-id="842a6-294">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-294">.NET Core 3.0</span></span> |
| <span data-ttu-id="842a6-295">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-295">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="842a6-296">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-296">*hexadecimal value*</span></span> | <span data-ttu-id="842a6-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-297">.NET Core 3.0</span></span> |

<span data-ttu-id="842a6-298">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="842a6-298">Example:</span></span>

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
> <span data-ttu-id="842a6-299">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="842a6-299">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="842a6-300">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="842a6-300">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="842a6-301">Por exemplo, para especificar um limite rígido de 200 mebibytes (MiB), os valores seriam 209715200 para o arquivo JSON e 0xC800000 ou C800000 para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="842a6-301">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="842a6-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="842a6-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="842a6-303">Especifica o uso do heap GC como uma porcentagem da memória total.</span><span class="sxs-lookup"><span data-stu-id="842a6-303">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="842a6-304">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-304">Setting name</span></span> | <span data-ttu-id="842a6-305">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-305">Values</span></span> | <span data-ttu-id="842a6-306">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-306">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-307">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-307">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="842a6-308">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-308">*decimal value*</span></span> | <span data-ttu-id="842a6-309">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-309">.NET Core 3.0</span></span> |
| <span data-ttu-id="842a6-310">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-310">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="842a6-311">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-311">*hexadecimal value*</span></span> | <span data-ttu-id="842a6-312">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-312">.NET Core 3.0</span></span> |

<span data-ttu-id="842a6-313">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="842a6-313">Example:</span></span>

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
> <span data-ttu-id="842a6-314">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="842a6-314">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="842a6-315">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="842a6-315">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="842a6-316">Por exemplo, para limitar o uso do heap a 30%, os valores seriam 30 para o arquivo JSON e 0x1E ou 1E para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="842a6-316">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="842a6-317">System.GC.RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="842a6-317">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="842a6-318">Configura se os segmentos que devem ser excluídos são colocados em uma lista de espera para uso futuro ou são liberados de volta para o sistema operacional (OS).</span><span class="sxs-lookup"><span data-stu-id="842a6-318">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="842a6-319">Padrão: Liberar segmentos de`false`volta ao sistema operacional ( ).</span><span class="sxs-lookup"><span data-stu-id="842a6-319">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="842a6-320">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-320">Setting name</span></span> | <span data-ttu-id="842a6-321">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-321">Values</span></span> | <span data-ttu-id="842a6-322">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-323">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-323">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="842a6-324">`false`- lançamento para os SO</span><span class="sxs-lookup"><span data-stu-id="842a6-324">`false` - release to OS</span></span><br/><span data-ttu-id="842a6-325">`true`- colocar em espera</span><span class="sxs-lookup"><span data-stu-id="842a6-325">`true` - put on standby</span></span> | <span data-ttu-id="842a6-326">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-326">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-327">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="842a6-327">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="842a6-328">`false`- lançamento para os SO</span><span class="sxs-lookup"><span data-stu-id="842a6-328">`false` - release to OS</span></span><br/><span data-ttu-id="842a6-329">`true`- colocar em espera</span><span class="sxs-lookup"><span data-stu-id="842a6-329">`true` - put on standby</span></span> | <span data-ttu-id="842a6-330">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-330">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-331">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-331">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="842a6-332">`0`- lançamento para os SO</span><span class="sxs-lookup"><span data-stu-id="842a6-332">`0` - release to OS</span></span><br/><span data-ttu-id="842a6-333">`1`- colocar em espera</span><span class="sxs-lookup"><span data-stu-id="842a6-333">`1` - put on standby</span></span> | <span data-ttu-id="842a6-334">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-334">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="842a6-335">Exemplos</span><span class="sxs-lookup"><span data-stu-id="842a6-335">Examples</span></span>

<span data-ttu-id="842a6-336">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="842a6-336">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="842a6-337">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="842a6-337">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="842a6-338">Páginas grandes</span><span class="sxs-lookup"><span data-stu-id="842a6-338">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="842a6-339">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="842a6-339">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="842a6-340">Especifica se páginas grandes devem ser usadas quando um limite rígido de pilha é definido.</span><span class="sxs-lookup"><span data-stu-id="842a6-340">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="842a6-341">Padrão: Desabilitado ( ).`0`</span><span class="sxs-lookup"><span data-stu-id="842a6-341">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="842a6-342">Este é um cenário experimental.</span><span class="sxs-lookup"><span data-stu-id="842a6-342">This is an experimental setting.</span></span>

| | <span data-ttu-id="842a6-343">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-343">Setting name</span></span> | <span data-ttu-id="842a6-344">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-344">Values</span></span> | <span data-ttu-id="842a6-345">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-346">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-346">**runtimeconfig.json**</span></span> | <span data-ttu-id="842a6-347">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-347">N/A</span></span> | <span data-ttu-id="842a6-348">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-348">N/A</span></span> | <span data-ttu-id="842a6-349">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-349">N/A</span></span> |
| <span data-ttu-id="842a6-350">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-350">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="842a6-351">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="842a6-351">`0` - disabled</span></span><br/><span data-ttu-id="842a6-352">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="842a6-352">`1` - enabled</span></span> | <span data-ttu-id="842a6-353">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="842a6-353">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="842a6-354">Objetos grandes</span><span class="sxs-lookup"><span data-stu-id="842a6-354">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="842a6-355">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="842a6-355">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="842a6-356">Configura suporte a coletores de lixo em plataformas de 64 bits para arrays maiores que 2 gigabytes (GB) em tamanho total.</span><span class="sxs-lookup"><span data-stu-id="842a6-356">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="842a6-357">Padrão: Ativado`1`().</span><span class="sxs-lookup"><span data-stu-id="842a6-357">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="842a6-358">Essa opção pode se tornar obsoleta em uma versão futura do .NET.</span><span class="sxs-lookup"><span data-stu-id="842a6-358">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="842a6-359">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-359">Setting name</span></span> | <span data-ttu-id="842a6-360">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-360">Values</span></span> | <span data-ttu-id="842a6-361">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-361">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-362">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-362">**runtimeconfig.json**</span></span> | <span data-ttu-id="842a6-363">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-363">N/A</span></span> | <span data-ttu-id="842a6-364">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-364">N/A</span></span> | <span data-ttu-id="842a6-365">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-365">N/A</span></span> |
| <span data-ttu-id="842a6-366">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-366">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="842a6-367">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="842a6-367">`1` - enabled</span></span><br/> <span data-ttu-id="842a6-368">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="842a6-368">`0` - disabled</span></span> | <span data-ttu-id="842a6-369">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-369">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-370">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="842a6-370">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="842a6-371">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="842a6-371">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="842a6-372">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="842a6-372">`1` - enabled</span></span><br/> <span data-ttu-id="842a6-373">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="842a6-373">`0` - disabled</span></span> | <span data-ttu-id="842a6-374">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="842a6-374">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="842a6-375">Grande limiar de pilha de objetos</span><span class="sxs-lookup"><span data-stu-id="842a6-375">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="842a6-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="842a6-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="842a6-377">Especifica o tamanho do limiar, em bytes, que faz com que os objetos vão para o heap de objeto grande (LOH).</span><span class="sxs-lookup"><span data-stu-id="842a6-377">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="842a6-378">O limite padrão é de 85.000 bytes.</span><span class="sxs-lookup"><span data-stu-id="842a6-378">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="842a6-379">O valor especificado deve ser maior do que o limite padrão.</span><span class="sxs-lookup"><span data-stu-id="842a6-379">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="842a6-380">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-380">Setting name</span></span> | <span data-ttu-id="842a6-381">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-381">Values</span></span> | <span data-ttu-id="842a6-382">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-382">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-383">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-383">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="842a6-384">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-384">*decimal value*</span></span> | <span data-ttu-id="842a6-385">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-385">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-386">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-386">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="842a6-387">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-387">*hexadecimal value*</span></span> | <span data-ttu-id="842a6-388">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="842a6-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="842a6-389">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="842a6-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="842a6-390">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="842a6-390">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="842a6-391">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="842a6-391">*decimal value*</span></span> | <span data-ttu-id="842a6-392">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="842a6-392">.NET Framework 4.8</span></span> |

<span data-ttu-id="842a6-393">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="842a6-393">Example:</span></span>

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
> <span data-ttu-id="842a6-394">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="842a6-394">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="842a6-395">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="842a6-395">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="842a6-396">Por exemplo, para definir um tamanho de limite de 120.000 bytes, os valores seriam 120000 000 para o arquivo JSON e 0x1D4C0 ou 1D4C0 para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="842a6-396">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="842a6-397">GC autônomo</span><span class="sxs-lookup"><span data-stu-id="842a6-397">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="842a6-398">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="842a6-398">COMPlus_GCName</span></span>

- <span data-ttu-id="842a6-399">Especifica um caminho para a biblioteca contendo o coletor de lixo que o tempo de execução pretende carregar.</span><span class="sxs-lookup"><span data-stu-id="842a6-399">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="842a6-400">Para obter mais informações, consulte [o design do carregador GC autônomo](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="842a6-400">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="842a6-401">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="842a6-401">Setting name</span></span> | <span data-ttu-id="842a6-402">Valores</span><span class="sxs-lookup"><span data-stu-id="842a6-402">Values</span></span> | <span data-ttu-id="842a6-403">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="842a6-403">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="842a6-404">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="842a6-404">**runtimeconfig.json**</span></span> | <span data-ttu-id="842a6-405">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-405">N/A</span></span> | <span data-ttu-id="842a6-406">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-406">N/A</span></span> | <span data-ttu-id="842a6-407">N/D</span><span class="sxs-lookup"><span data-stu-id="842a6-407">N/A</span></span> |
| <span data-ttu-id="842a6-408">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="842a6-408">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="842a6-409">*string_path*</span><span class="sxs-lookup"><span data-stu-id="842a6-409">*string_path*</span></span> | <span data-ttu-id="842a6-410">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="842a6-410">.NET Core 2.0</span></span> |
