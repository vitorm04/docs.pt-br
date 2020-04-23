---
title: Configurações de configuração de coletor de lixo
description: Saiba mais sobre as configurações de tempo de execução para configurar como o coletor de lixo gerencia a memória para aplicativos .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: ec575bdd17c8a7c290673b7085074bbba94cedef
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102860"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="5212b-103">Opções de configuração em tempo de execução para coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="5212b-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="5212b-104">Esta página contém informações sobre configurações de coletor de lixo (GC) que podem ser alteradas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5212b-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="5212b-105">Se você está tentando alcançar o máximo de desempenho de um aplicativo em execução, considere usar essas configurações.</span><span class="sxs-lookup"><span data-stu-id="5212b-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="5212b-106">No entanto, os padrões fornecem um desempenho ideal para a maioria dos aplicativos em situações típicas.</span><span class="sxs-lookup"><span data-stu-id="5212b-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="5212b-107">As configurações são organizadas em grupos nesta página.</span><span class="sxs-lookup"><span data-stu-id="5212b-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="5212b-108">As configurações dentro de cada grupo são comumente usadas em conjunto entre si para obter um resultado específico.</span><span class="sxs-lookup"><span data-stu-id="5212b-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="5212b-109">Essas configurações também podem ser alteradas dinamicamente pelo aplicativo enquanto ele está sendo executado, de modo que quaisquer configurações de tempo de execução que você definir podem ser substituídas.</span><span class="sxs-lookup"><span data-stu-id="5212b-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="5212b-110">Algumas configurações, como o [nível de latência,](../../standard/garbage-collection/latency.md)são normalmente definidas apenas através da API na hora do projeto.</span><span class="sxs-lookup"><span data-stu-id="5212b-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="5212b-111">Essas configurações são omitidas desta página.</span><span class="sxs-lookup"><span data-stu-id="5212b-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="5212b-112">Para valores numério, use notação decimal para configurações no arquivo *runtimeconfig.json* e notação hexadecimal para configurações variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="5212b-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="5212b-113">Para valores hexadecimais, você pode especificá-los com ou sem o prefixo "0x".</span><span class="sxs-lookup"><span data-stu-id="5212b-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="5212b-114">Sabores da coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="5212b-114">Flavors of garbage collection</span></span>

<span data-ttu-id="5212b-115">Os dois principais sabores da coleta de lixo são a Estação de Trabalho GC e o servidor GC.</span><span class="sxs-lookup"><span data-stu-id="5212b-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="5212b-116">Para obter mais informações sobre as diferenças entre os dois, consulte [Workstation e coleta de lixo do servidor](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="5212b-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="5212b-117">Os subsabores da coleta de lixo são de fundo e não são concomitantes.</span><span class="sxs-lookup"><span data-stu-id="5212b-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="5212b-118">Use as seguintes configurações para selecionar sabores de coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="5212b-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="5212b-119">System.GC.Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="5212b-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="5212b-120">Configura se o aplicativo usa coleta de lixo da estação de trabalho ou coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="5212b-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="5212b-121">Padrão: Coleta de`false`lixo da estação de trabalho ( ).</span><span class="sxs-lookup"><span data-stu-id="5212b-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="5212b-122">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-122">Setting name</span></span> | <span data-ttu-id="5212b-123">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-123">Values</span></span> | <span data-ttu-id="5212b-124">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-125">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="5212b-126">`false`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="5212b-126">`false` - workstation</span></span><br/><span data-ttu-id="5212b-127">`true`- servidor</span><span class="sxs-lookup"><span data-stu-id="5212b-127">`true` - server</span></span> | <span data-ttu-id="5212b-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-129">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="5212b-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="5212b-130">`false`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="5212b-130">`false` - workstation</span></span><br/><span data-ttu-id="5212b-131">`true`- servidor</span><span class="sxs-lookup"><span data-stu-id="5212b-131">`true` - server</span></span> | <span data-ttu-id="5212b-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-133">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="5212b-134">`0`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="5212b-134">`0` - workstation</span></span><br/><span data-ttu-id="5212b-135">`1`- servidor</span><span class="sxs-lookup"><span data-stu-id="5212b-135">`1` - server</span></span> | <span data-ttu-id="5212b-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-137">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5212b-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5212b-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="5212b-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="5212b-139">`false`- estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="5212b-139">`false` - workstation</span></span><br/><span data-ttu-id="5212b-140">`true`- servidor</span><span class="sxs-lookup"><span data-stu-id="5212b-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="5212b-141">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5212b-141">Examples</span></span>

<span data-ttu-id="5212b-142">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="5212b-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="5212b-143">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="5212b-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="5212b-144">System.GC.Simultânea/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="5212b-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="5212b-145">Configura se a coleta de lixo em segundo plano (simultânea) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="5212b-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="5212b-146">Padrão: Ativado`true`().</span><span class="sxs-lookup"><span data-stu-id="5212b-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="5212b-147">Para obter mais informações, consulte [A coleta de lixo de fundo](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="5212b-147">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="5212b-148">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-148">Setting name</span></span> | <span data-ttu-id="5212b-149">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-149">Values</span></span> | <span data-ttu-id="5212b-150">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-151">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="5212b-152">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="5212b-152">`true` - background GC</span></span><br/><span data-ttu-id="5212b-153">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="5212b-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="5212b-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-155">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="5212b-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="5212b-156">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="5212b-156">`true` - background GC</span></span><br/><span data-ttu-id="5212b-157">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="5212b-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="5212b-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-159">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="5212b-160">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="5212b-160">`true` - background GC</span></span><br/><span data-ttu-id="5212b-161">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="5212b-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="5212b-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-163">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5212b-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5212b-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="5212b-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="5212b-165">`true`- fundo GC</span><span class="sxs-lookup"><span data-stu-id="5212b-165">`true` - background GC</span></span><br/><span data-ttu-id="5212b-166">`false`- GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="5212b-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="5212b-167">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5212b-167">Examples</span></span>

<span data-ttu-id="5212b-168">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="5212b-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="5212b-169">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="5212b-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="5212b-170">Gerenciar o uso de recursos</span><span class="sxs-lookup"><span data-stu-id="5212b-170">Manage resource usage</span></span>

<span data-ttu-id="5212b-171">Use as configurações descritas nesta seção para gerenciar o uso da memória e do processador do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="5212b-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="5212b-172">Para obter mais informações sobre algumas dessas configurações, consulte o meio termo entre a [estação de trabalho e a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) entrada do blog gc do servidor.</span><span class="sxs-lookup"><span data-stu-id="5212b-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="5212b-173">System.GC.Heapcount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="5212b-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="5212b-174">Limita o número de montes criados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="5212b-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="5212b-175">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="5212b-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5212b-176">Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver ativada, que é `n` o padrão, a configuração `n` de contagem de pilhas adiaos pilhas/threads GC para os primeiros processadores.</span><span class="sxs-lookup"><span data-stu-id="5212b-176">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="5212b-177">(Use as configurações de [intervalos de afeitização](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou [aderiss para](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) especificar exatamente quais processadores aparticipar.)</span><span class="sxs-lookup"><span data-stu-id="5212b-177">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="5212b-178">Se [a afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desativada, essa configuração limita o número de pilhas gc.</span><span class="sxs-lookup"><span data-stu-id="5212b-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="5212b-179">Para obter mais informações, consulte as observações do [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="5212b-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="5212b-180">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-180">Setting name</span></span> | <span data-ttu-id="5212b-181">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-181">Values</span></span> | <span data-ttu-id="5212b-182">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-183">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="5212b-184">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-184">*decimal value*</span></span> | <span data-ttu-id="5212b-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="5212b-186">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="5212b-187">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-187">*hexadecimal value*</span></span> | <span data-ttu-id="5212b-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="5212b-189">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5212b-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5212b-190">GCHeapcount</span><span class="sxs-lookup"><span data-stu-id="5212b-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="5212b-191">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-191">*decimal value*</span></span> | <span data-ttu-id="5212b-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="5212b-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="5212b-193">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="5212b-193">Example:</span></span>

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
> <span data-ttu-id="5212b-194">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="5212b-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5212b-195">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="5212b-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5212b-196">Por exemplo, para limitar o número de pilhas a 16, os valores seriam 16 para o arquivo JSON e 0x10 ou 10 para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="5212b-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="5212b-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="5212b-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="5212b-198">Especifica os processadores exatos que os segmentos coletores de lixo devem usar.</span><span class="sxs-lookup"><span data-stu-id="5212b-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="5212b-199">Se [a afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desativada, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="5212b-199">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="5212b-200">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="5212b-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5212b-201">O valor é uma máscara de bit que define os processadores disponíveis para o processo.</span><span class="sxs-lookup"><span data-stu-id="5212b-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="5212b-202">Por exemplo, um valor decimal de 1023 (ou um valor hexadecimal de 0x3FF ou 3FF se você estiver usando a variável ambiente) é 0011 1111 1111 em notação binária.</span><span class="sxs-lookup"><span data-stu-id="5212b-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="5212b-203">Isso especifica que os primeiros 10 processadores devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="5212b-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="5212b-204">Para especificar os próximos 10 processadores, ou seja, processadores 10-19, especifique um valor decimal de 1047552 (ou um valor hexadecimal de 0xFFC00 ou FFC00), que equivale a um valor binário de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="5212b-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="5212b-205">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-205">Setting name</span></span> | <span data-ttu-id="5212b-206">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-206">Values</span></span> | <span data-ttu-id="5212b-207">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-208">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="5212b-209">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-209">*decimal value*</span></span> | <span data-ttu-id="5212b-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="5212b-211">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="5212b-212">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-212">*hexadecimal value*</span></span> | <span data-ttu-id="5212b-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="5212b-214">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5212b-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5212b-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="5212b-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="5212b-216">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-216">*decimal value*</span></span> | <span data-ttu-id="5212b-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="5212b-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="5212b-218">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="5212b-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="5212b-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="5212b-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="5212b-220">Especifica a lista de processadores a serem usados para segmentos coletores de lixo.</span><span class="sxs-lookup"><span data-stu-id="5212b-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="5212b-221">Esta configuração é semelhante ao [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), exceto que permite especificar mais de 64 processadores.</span><span class="sxs-lookup"><span data-stu-id="5212b-221">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="5212b-222">Para sistemas operacionais Windows, prefixe o número do processador ou o intervalo com o grupo de [CPU](/windows/win32/procthread/processor-groups)correspondente, por exemplo, "0:1-10,0:12,1:50-52,1:70".</span><span class="sxs-lookup"><span data-stu-id="5212b-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="5212b-223">Se [a afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desativada, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="5212b-223">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="5212b-224">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="5212b-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5212b-225">Para obter mais informações, consulte [Tornando a configuração da CPU melhor para GC em máquinas com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog de Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="5212b-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="5212b-226">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-226">Setting name</span></span> | <span data-ttu-id="5212b-227">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-227">Values</span></span> | <span data-ttu-id="5212b-228">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-229">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="5212b-230">Lista separada por comma de números de processadores ou faixas de números de processadores.</span><span class="sxs-lookup"><span data-stu-id="5212b-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="5212b-231">Exemplo unix: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="5212b-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="5212b-232">Exemplo do Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="5212b-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="5212b-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="5212b-234">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="5212b-235">Lista separada por comma de números de processadores ou faixas de números de processadores.</span><span class="sxs-lookup"><span data-stu-id="5212b-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="5212b-236">Exemplo unix: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="5212b-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="5212b-237">Exemplo do Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="5212b-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="5212b-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-238">.NET Core 3.0</span></span> |

<span data-ttu-id="5212b-239">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="5212b-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="5212b-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="5212b-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="5212b-241">Configura se o coletor de lixo usa ou não [grupos de CPU.](/windows/win32/procthread/processor-groups)</span><span class="sxs-lookup"><span data-stu-id="5212b-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="5212b-242">Quando um computador Windows de 64 bits tem vários grupos de CPU, ou seja, há mais de 64 processadores, permitindo que esse elemento estenda a coleta de lixo em todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="5212b-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="5212b-243">O coletor de lixo usa todos os núcleos para criar e equilibrar pilhas.</span><span class="sxs-lookup"><span data-stu-id="5212b-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="5212b-244">Aplica-se à coleta de lixo do servidor apenas em sistemas de operação Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5212b-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="5212b-245">Padrão: Desabilitado ( ).`0`</span><span class="sxs-lookup"><span data-stu-id="5212b-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="5212b-246">Para obter mais informações, consulte [Tornando a configuração da CPU melhor para GC em máquinas com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog de Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="5212b-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="5212b-247">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-247">Setting name</span></span> | <span data-ttu-id="5212b-248">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-248">Values</span></span> | <span data-ttu-id="5212b-249">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-250">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="5212b-251">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-251">N/A</span></span> | <span data-ttu-id="5212b-252">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-252">N/A</span></span> | <span data-ttu-id="5212b-253">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-253">N/A</span></span> |
| <span data-ttu-id="5212b-254">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="5212b-255">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="5212b-255">`0` - disabled</span></span><br/><span data-ttu-id="5212b-256">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="5212b-256">`1` - enabled</span></span> | <span data-ttu-id="5212b-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-258">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5212b-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5212b-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="5212b-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="5212b-260">`false`- deficientes</span><span class="sxs-lookup"><span data-stu-id="5212b-260">`false` - disabled</span></span><br/><span data-ttu-id="5212b-261">`true`- habilitado</span><span class="sxs-lookup"><span data-stu-id="5212b-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="5212b-262">Para configurar o tempo de execução de idioma comum (CLR) para também distribuir threads do pool de segmentos em todos os grupos da CPU, habilite a opção [de elemento Thread_UseAllCpuGroups.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)</span><span class="sxs-lookup"><span data-stu-id="5212b-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="5212b-263">Para aplicativos .NET Core, você pode habilitar `COMPlus_Thread_UseAllCpuGroups` essa opção `1`definindo o valor da variável ambiente para .</span><span class="sxs-lookup"><span data-stu-id="5212b-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="5212b-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="5212b-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="5212b-265">Especifica se é *a adesão dos* segmentos de coleta de lixo com processadores.</span><span class="sxs-lookup"><span data-stu-id="5212b-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="5212b-266">Adenar um segmento GC significa que ele só pode ser executado em sua CPU específica.</span><span class="sxs-lookup"><span data-stu-id="5212b-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="5212b-267">Um monte é criado para cada segmento GC.</span><span class="sxs-lookup"><span data-stu-id="5212b-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="5212b-268">Aplica-se apenas à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="5212b-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5212b-269">Padrão: Afena os fios de coleta`false`de lixo com processadores ().</span><span class="sxs-lookup"><span data-stu-id="5212b-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="5212b-270">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-270">Setting name</span></span> | <span data-ttu-id="5212b-271">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-271">Values</span></span> | <span data-ttu-id="5212b-272">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-273">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="5212b-274">`false`- afeição</span><span class="sxs-lookup"><span data-stu-id="5212b-274">`false` - affinitize</span></span><br/><span data-ttu-id="5212b-275">`true`- não afete</span><span class="sxs-lookup"><span data-stu-id="5212b-275">`true` - don't affinitize</span></span> | <span data-ttu-id="5212b-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="5212b-277">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="5212b-278">`0`- afeição</span><span class="sxs-lookup"><span data-stu-id="5212b-278">`0` - affinitize</span></span><br/><span data-ttu-id="5212b-279">`1`- não afete</span><span class="sxs-lookup"><span data-stu-id="5212b-279">`1` - don't affinitize</span></span> | <span data-ttu-id="5212b-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="5212b-281">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5212b-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5212b-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="5212b-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="5212b-283">`false`- afeição</span><span class="sxs-lookup"><span data-stu-id="5212b-283">`false` - affinitize</span></span><br/><span data-ttu-id="5212b-284">`true`- não afete</span><span class="sxs-lookup"><span data-stu-id="5212b-284">`true` - don't affinitize</span></span> | <span data-ttu-id="5212b-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="5212b-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="5212b-286">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="5212b-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="5212b-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="5212b-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="5212b-288">Especifica o tamanho máximo de confirmação, em bytes, para a contabilidade GC heap e GC.</span><span class="sxs-lookup"><span data-stu-id="5212b-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="5212b-289">Esta configuração só se aplica a computadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5212b-289">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="5212b-290">O valor padrão, que só se aplica em certos casos, é o maior de 20 MB ou 75% do limite de memória no recipiente.</span><span class="sxs-lookup"><span data-stu-id="5212b-290">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="5212b-291">O valor padrão se aplica se:</span><span class="sxs-lookup"><span data-stu-id="5212b-291">The default value applies if:</span></span>

  - <span data-ttu-id="5212b-292">O processo está sendo executado dentro de um recipiente que tem um limite de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="5212b-292">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="5212b-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) não está definido.</span><span class="sxs-lookup"><span data-stu-id="5212b-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="5212b-294">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-294">Setting name</span></span> | <span data-ttu-id="5212b-295">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-295">Values</span></span> | <span data-ttu-id="5212b-296">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-296">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-297">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-297">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="5212b-298">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-298">*decimal value*</span></span> | <span data-ttu-id="5212b-299">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-299">.NET Core 3.0</span></span> |
| <span data-ttu-id="5212b-300">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-300">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="5212b-301">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-301">*hexadecimal value*</span></span> | <span data-ttu-id="5212b-302">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-302">.NET Core 3.0</span></span> |

<span data-ttu-id="5212b-303">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="5212b-303">Example:</span></span>

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
> <span data-ttu-id="5212b-304">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="5212b-304">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5212b-305">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="5212b-305">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5212b-306">Por exemplo, para especificar um limite rígido de 200 mebibytes (MiB), os valores seriam 209715200 para o arquivo JSON e 0xC800000 ou C800000 para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="5212b-306">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="5212b-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="5212b-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="5212b-308">Especifica o uso permitido do heap GC como uma porcentagem da memória física total.</span><span class="sxs-lookup"><span data-stu-id="5212b-308">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="5212b-309">Se [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) também estiver definido, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="5212b-309">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="5212b-310">Esta configuração só se aplica a computadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5212b-310">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="5212b-311">Se o processo estiver sendo executado dentro de um recipiente que tenha um limite de memória especificado, a porcentagem será calculada como uma porcentagem desse limite de memória.</span><span class="sxs-lookup"><span data-stu-id="5212b-311">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="5212b-312">O valor padrão, que só se aplica em certos casos, é o menor de 20 MB ou 75% do limite de memória no recipiente.</span><span class="sxs-lookup"><span data-stu-id="5212b-312">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="5212b-313">O valor padrão se aplica se:</span><span class="sxs-lookup"><span data-stu-id="5212b-313">The default value applies if:</span></span>

  - <span data-ttu-id="5212b-314">O processo está sendo executado dentro de um recipiente que tem um limite de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="5212b-314">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="5212b-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) não está definido.</span><span class="sxs-lookup"><span data-stu-id="5212b-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="5212b-316">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-316">Setting name</span></span> | <span data-ttu-id="5212b-317">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-317">Values</span></span> | <span data-ttu-id="5212b-318">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-318">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-319">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-319">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="5212b-320">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-320">*decimal value*</span></span> | <span data-ttu-id="5212b-321">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-321">.NET Core 3.0</span></span> |
| <span data-ttu-id="5212b-322">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-322">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="5212b-323">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-323">*hexadecimal value*</span></span> | <span data-ttu-id="5212b-324">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-324">.NET Core 3.0</span></span> |

<span data-ttu-id="5212b-325">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="5212b-325">Example:</span></span>

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
> <span data-ttu-id="5212b-326">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="5212b-326">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5212b-327">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="5212b-327">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5212b-328">Por exemplo, para limitar o uso do heap a 30%, os valores seriam 30 para o arquivo JSON e 0x1E ou 1E para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="5212b-328">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="5212b-329">System.GC.RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="5212b-329">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="5212b-330">Configura se os segmentos que devem ser excluídos são colocados em uma lista de espera para uso futuro ou são liberados de volta para o sistema operacional (OS).</span><span class="sxs-lookup"><span data-stu-id="5212b-330">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="5212b-331">Padrão: Liberar segmentos de`false`volta ao sistema operacional ( ).</span><span class="sxs-lookup"><span data-stu-id="5212b-331">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="5212b-332">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-332">Setting name</span></span> | <span data-ttu-id="5212b-333">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-333">Values</span></span> | <span data-ttu-id="5212b-334">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-334">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-335">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-335">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="5212b-336">`false`- lançamento para os SO</span><span class="sxs-lookup"><span data-stu-id="5212b-336">`false` - release to OS</span></span><br/><span data-ttu-id="5212b-337">`true`- colocar em espera</span><span class="sxs-lookup"><span data-stu-id="5212b-337">`true` - put on standby</span></span> | <span data-ttu-id="5212b-338">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-338">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-339">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="5212b-339">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="5212b-340">`false`- lançamento para os SO</span><span class="sxs-lookup"><span data-stu-id="5212b-340">`false` - release to OS</span></span><br/><span data-ttu-id="5212b-341">`true`- colocar em espera</span><span class="sxs-lookup"><span data-stu-id="5212b-341">`true` - put on standby</span></span> | <span data-ttu-id="5212b-342">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-342">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-343">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-343">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="5212b-344">`0`- lançamento para os SO</span><span class="sxs-lookup"><span data-stu-id="5212b-344">`0` - release to OS</span></span><br/><span data-ttu-id="5212b-345">`1`- colocar em espera</span><span class="sxs-lookup"><span data-stu-id="5212b-345">`1` - put on standby</span></span> | <span data-ttu-id="5212b-346">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-346">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="5212b-347">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5212b-347">Examples</span></span>

<span data-ttu-id="5212b-348">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="5212b-348">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="5212b-349">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="5212b-349">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="5212b-350">Páginas grandes</span><span class="sxs-lookup"><span data-stu-id="5212b-350">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="5212b-351">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="5212b-351">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="5212b-352">Especifica se páginas grandes devem ser usadas quando um limite rígido de pilha é definido.</span><span class="sxs-lookup"><span data-stu-id="5212b-352">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="5212b-353">Padrão: Desabilitado ( ).`0`</span><span class="sxs-lookup"><span data-stu-id="5212b-353">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="5212b-354">Este é um cenário experimental.</span><span class="sxs-lookup"><span data-stu-id="5212b-354">This is an experimental setting.</span></span>

| | <span data-ttu-id="5212b-355">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-355">Setting name</span></span> | <span data-ttu-id="5212b-356">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-356">Values</span></span> | <span data-ttu-id="5212b-357">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-358">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-358">**runtimeconfig.json**</span></span> | <span data-ttu-id="5212b-359">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-359">N/A</span></span> | <span data-ttu-id="5212b-360">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-360">N/A</span></span> | <span data-ttu-id="5212b-361">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-361">N/A</span></span> |
| <span data-ttu-id="5212b-362">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-362">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="5212b-363">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="5212b-363">`0` - disabled</span></span><br/><span data-ttu-id="5212b-364">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="5212b-364">`1` - enabled</span></span> | <span data-ttu-id="5212b-365">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5212b-365">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="5212b-366">Objetos grandes</span><span class="sxs-lookup"><span data-stu-id="5212b-366">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="5212b-367">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="5212b-367">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="5212b-368">Configura suporte a coletores de lixo em plataformas de 64 bits para arrays maiores que 2 gigabytes (GB) em tamanho total.</span><span class="sxs-lookup"><span data-stu-id="5212b-368">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="5212b-369">Padrão: Ativado`1`().</span><span class="sxs-lookup"><span data-stu-id="5212b-369">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="5212b-370">Essa opção pode se tornar obsoleta em uma versão futura do .NET.</span><span class="sxs-lookup"><span data-stu-id="5212b-370">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="5212b-371">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-371">Setting name</span></span> | <span data-ttu-id="5212b-372">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-372">Values</span></span> | <span data-ttu-id="5212b-373">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-373">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-374">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-374">**runtimeconfig.json**</span></span> | <span data-ttu-id="5212b-375">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-375">N/A</span></span> | <span data-ttu-id="5212b-376">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-376">N/A</span></span> | <span data-ttu-id="5212b-377">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-377">N/A</span></span> |
| <span data-ttu-id="5212b-378">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-378">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="5212b-379">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="5212b-379">`1` - enabled</span></span><br/> <span data-ttu-id="5212b-380">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="5212b-380">`0` - disabled</span></span> | <span data-ttu-id="5212b-381">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-381">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-382">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5212b-382">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5212b-383">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="5212b-383">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="5212b-384">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="5212b-384">`1` - enabled</span></span><br/> <span data-ttu-id="5212b-385">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="5212b-385">`0` - disabled</span></span> | <span data-ttu-id="5212b-386">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="5212b-386">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="5212b-387">Grande limiar de pilha de objetos</span><span class="sxs-lookup"><span data-stu-id="5212b-387">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="5212b-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="5212b-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="5212b-389">Especifica o tamanho do limiar, em bytes, que faz com que os objetos vão para o heap de objeto grande (LOH).</span><span class="sxs-lookup"><span data-stu-id="5212b-389">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="5212b-390">O limite padrão é de 85.000 bytes.</span><span class="sxs-lookup"><span data-stu-id="5212b-390">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="5212b-391">O valor especificado deve ser maior do que o limite padrão.</span><span class="sxs-lookup"><span data-stu-id="5212b-391">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="5212b-392">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-392">Setting name</span></span> | <span data-ttu-id="5212b-393">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-393">Values</span></span> | <span data-ttu-id="5212b-394">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-394">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-395">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-395">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="5212b-396">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-396">*decimal value*</span></span> | <span data-ttu-id="5212b-397">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-397">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-398">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-398">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="5212b-399">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-399">*hexadecimal value*</span></span> | <span data-ttu-id="5212b-400">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5212b-400">.NET Core 1.0</span></span> |
| <span data-ttu-id="5212b-401">**app.config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5212b-401">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5212b-402">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="5212b-402">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="5212b-403">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="5212b-403">*decimal value*</span></span> | <span data-ttu-id="5212b-404">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="5212b-404">.NET Framework 4.8</span></span> |

<span data-ttu-id="5212b-405">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="5212b-405">Example:</span></span>

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
> <span data-ttu-id="5212b-406">Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="5212b-406">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5212b-407">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="5212b-407">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5212b-408">Por exemplo, para definir um tamanho de limite de 120.000 bytes, os valores seriam 120000 000 para o arquivo JSON e 0x1D4C0 ou 1D4C0 para a variável ambiente.</span><span class="sxs-lookup"><span data-stu-id="5212b-408">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="5212b-409">GC autônomo</span><span class="sxs-lookup"><span data-stu-id="5212b-409">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="5212b-410">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="5212b-410">COMPlus_GCName</span></span>

- <span data-ttu-id="5212b-411">Especifica um caminho para a biblioteca contendo o coletor de lixo que o tempo de execução pretende carregar.</span><span class="sxs-lookup"><span data-stu-id="5212b-411">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="5212b-412">Para obter mais informações, consulte [o design do carregador GC autônomo](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="5212b-412">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="5212b-413">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="5212b-413">Setting name</span></span> | <span data-ttu-id="5212b-414">Valores</span><span class="sxs-lookup"><span data-stu-id="5212b-414">Values</span></span> | <span data-ttu-id="5212b-415">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5212b-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5212b-416">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="5212b-416">**runtimeconfig.json**</span></span> | <span data-ttu-id="5212b-417">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-417">N/A</span></span> | <span data-ttu-id="5212b-418">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-418">N/A</span></span> | <span data-ttu-id="5212b-419">N/D</span><span class="sxs-lookup"><span data-stu-id="5212b-419">N/A</span></span> |
| <span data-ttu-id="5212b-420">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="5212b-420">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="5212b-421">*string_path*</span><span class="sxs-lookup"><span data-stu-id="5212b-421">*string_path*</span></span> | <span data-ttu-id="5212b-422">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5212b-422">.NET Core 2.0</span></span> |
