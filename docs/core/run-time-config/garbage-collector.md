---
title: Definições de configuração do coletor de lixo
description: Saiba mais sobre as configurações de tempo de execução para configurar como o coletor de lixo gerencia a memória para aplicativos .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 24e5c47de781e7eed5f76d2c551cac2dce1e8f05
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900103"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="7d819-103">Opções de configuração de tempo de execução para coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="7d819-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="7d819-104">Esta página contém informações sobre as configurações de coletor de lixo (GC) que podem ser alteradas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7d819-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="7d819-105">Se você estiver tentando atingir o desempenho máximo de um aplicativo em execução, considere o uso dessas configurações.</span><span class="sxs-lookup"><span data-stu-id="7d819-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="7d819-106">No entanto, os padrões fornecem um desempenho ideal para a maioria dos aplicativos em situações típicas.</span><span class="sxs-lookup"><span data-stu-id="7d819-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="7d819-107">As configurações são organizadas em grupos nesta página.</span><span class="sxs-lookup"><span data-stu-id="7d819-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="7d819-108">As configurações em cada grupo são comumente usadas em conjunto entre si para obter um resultado específico.</span><span class="sxs-lookup"><span data-stu-id="7d819-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="7d819-109">Essas configurações também podem ser alteradas dinamicamente pelo aplicativo enquanto ele está em execução, portanto, as configurações de tempo de execução definidas podem ser substituídas.</span><span class="sxs-lookup"><span data-stu-id="7d819-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="7d819-110">Algumas configurações, como [nível de latência](../../standard/garbage-collection/latency.md), normalmente são definidas somente por meio da API em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="7d819-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="7d819-111">Essas configurações são omitidas desta página.</span><span class="sxs-lookup"><span data-stu-id="7d819-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="7d819-112">Para valores numéricos, use a notação decimal para as configurações no arquivo *runtimeconfig. JSON* e notação hexadecimal para configurações de variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="7d819-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="7d819-113">Para valores hexadecimais, você pode especificá-los com ou sem o prefixo "0x".</span><span class="sxs-lookup"><span data-stu-id="7d819-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="7d819-114">Tipos de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="7d819-114">Flavors of garbage collection</span></span>

<span data-ttu-id="7d819-115">Os dois tipos principais de coleta de lixo são estação de trabalho GC e GC de servidor.</span><span class="sxs-lookup"><span data-stu-id="7d819-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="7d819-116">Para obter mais informações sobre as diferenças entre os dois, consulte [conceitos básicos da coleta de lixo](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="7d819-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="7d819-117">Os subtipos de coleta de lixo são em segundo plano e não simultâneos.</span><span class="sxs-lookup"><span data-stu-id="7d819-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="7d819-118">Use as seguintes configurações para selecionar tipos de coleta de lixo:</span><span class="sxs-lookup"><span data-stu-id="7d819-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="7d819-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="7d819-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="7d819-120">Define se o aplicativo usa a coleta de lixo da estação de trabalho ou a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="7d819-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="7d819-121">Padrão: coleta de lixo da estação de trabalho (`false`).</span><span class="sxs-lookup"><span data-stu-id="7d819-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="7d819-122">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-122">Setting name</span></span> | <span data-ttu-id="7d819-123">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-123">Values</span></span> | <span data-ttu-id="7d819-124">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-125">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="7d819-126">`false`-estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="7d819-126">`false` - workstation</span></span><br/><span data-ttu-id="7d819-127">servidor de `true`</span><span class="sxs-lookup"><span data-stu-id="7d819-127">`true` - server</span></span> | <span data-ttu-id="7d819-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="7d819-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="7d819-129">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-129">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="7d819-130">`0`-estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="7d819-130">`0` - workstation</span></span><br/><span data-ttu-id="7d819-131">servidor de `1`</span><span class="sxs-lookup"><span data-stu-id="7d819-131">`1` - server</span></span> | <span data-ttu-id="7d819-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="7d819-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="7d819-133">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="7d819-133">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7d819-134">GCServer</span><span class="sxs-lookup"><span data-stu-id="7d819-134">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="7d819-135">`false`-estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="7d819-135">`false` - workstation</span></span><br/><span data-ttu-id="7d819-136">servidor de `true`</span><span class="sxs-lookup"><span data-stu-id="7d819-136">`true` - server</span></span> |  |

<span data-ttu-id="7d819-137">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7d819-137">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="7d819-138">System. GC. simultaneamente/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="7d819-138">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="7d819-139">Configura se a coleta de lixo em segundo plano (simultânea) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="7d819-139">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="7d819-140">Padrão: habilitado (`true`).</span><span class="sxs-lookup"><span data-stu-id="7d819-140">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="7d819-141">Para obter mais informações, consulte [coleta de lixo em segundo plano](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) e [coleta de lixo do servidor em segundo plano](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="7d819-141">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="7d819-142">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-142">Setting name</span></span> | <span data-ttu-id="7d819-143">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-143">Values</span></span> | <span data-ttu-id="7d819-144">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-144">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-145">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-145">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="7d819-146">GC de `true` em segundo plano</span><span class="sxs-lookup"><span data-stu-id="7d819-146">`true` - background GC</span></span><br/><span data-ttu-id="7d819-147">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="7d819-147">`false` - non-concurrent GC</span></span> | <span data-ttu-id="7d819-148">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="7d819-148">.NET Core 1.0</span></span> |
| <span data-ttu-id="7d819-149">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-149">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="7d819-150">GC de `true` em segundo plano</span><span class="sxs-lookup"><span data-stu-id="7d819-150">`true` - background GC</span></span><br/><span data-ttu-id="7d819-151">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="7d819-151">`false` - non-concurrent GC</span></span> | <span data-ttu-id="7d819-152">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="7d819-152">.NET Core 1.0</span></span> |
| <span data-ttu-id="7d819-153">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="7d819-153">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7d819-154">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="7d819-154">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="7d819-155">GC de `true` em segundo plano</span><span class="sxs-lookup"><span data-stu-id="7d819-155">`true` - background GC</span></span><br/><span data-ttu-id="7d819-156">`false`-GC não simultâneo</span><span class="sxs-lookup"><span data-stu-id="7d819-156">`false` - non-concurrent GC</span></span> |  |

<span data-ttu-id="7d819-157">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7d819-157">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

## <a name="manage-resource-usage"></a><span data-ttu-id="7d819-158">Gerenciar o uso de recursos</span><span class="sxs-lookup"><span data-stu-id="7d819-158">Manage resource usage</span></span>

<span data-ttu-id="7d819-159">Use as configurações descritas nesta seção para gerenciar a memória e o uso do processador do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="7d819-159">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="7d819-160">Para obter mais informações sobre algumas dessas configurações, consulte o meio-termo entre a entrada de blog do [GC de estação de trabalho e servidor](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="7d819-160">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="7d819-161">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="7d819-161">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="7d819-162">Limita o número de heaps criados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="7d819-162">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="7d819-163">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="7d819-163">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="7d819-164">Se a afinidade do processador GC estiver habilitada, que é o padrão, a configuração de contagem de heap affinitizes `n` heaps/threads do GC para os primeiros processadores de `n`.</span><span class="sxs-lookup"><span data-stu-id="7d819-164">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="7d819-165">(Use a máscara relacionar ou as configurações de intervalos de relacionar para especificar exatamente quais processadores relacionar.)</span><span class="sxs-lookup"><span data-stu-id="7d819-165">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="7d819-166">Se a afinidade do processador GC estiver desabilitada, essa configuração limitará o número de heaps do GC.</span><span class="sxs-lookup"><span data-stu-id="7d819-166">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="7d819-167">Para obter mais informações, consulte o [GCHeapCount comentários](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="7d819-167">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="7d819-168">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-168">Setting name</span></span> | <span data-ttu-id="7d819-169">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-169">Values</span></span> | <span data-ttu-id="7d819-170">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-170">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-171">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-171">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="7d819-172">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-172">*decimal value*</span></span> | <span data-ttu-id="7d819-173">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-173">.NET Core 3.0</span></span> |
| <span data-ttu-id="7d819-174">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-174">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="7d819-175">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-175">*hexadecimal value*</span></span> | <span data-ttu-id="7d819-176">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-176">.NET Core 3.0</span></span> |
| <span data-ttu-id="7d819-177">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="7d819-177">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7d819-178">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="7d819-178">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="7d819-179">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-179">*decimal value*</span></span> | <span data-ttu-id="7d819-180">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="7d819-180">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="7d819-181">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7d819-181">Example:</span></span>

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
> <span data-ttu-id="7d819-182">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="7d819-182">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="7d819-183">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="7d819-183">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="7d819-184">Por exemplo, para limitar o número de heaps a 16, os valores seriam 16 para o arquivo JSON e 0x10 ou 10 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="7d819-184">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="7d819-185">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="7d819-185">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="7d819-186">Especifica os processadores exatos que os threads do coletor de lixo devem usar.</span><span class="sxs-lookup"><span data-stu-id="7d819-186">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="7d819-187">Se a afinidade do processador estiver desabilitada ao definir `System.GC.NoAffinitize` como `true`, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="7d819-187">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="7d819-188">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="7d819-188">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="7d819-189">O valor é uma máscara de bits que define os processadores que estão disponíveis para o processo.</span><span class="sxs-lookup"><span data-stu-id="7d819-189">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="7d819-190">Por exemplo, um valor decimal de 1023 (ou um valor hexadecimal de 0x3FF ou 3FF se você estiver usando a variável de ambiente) é 0011 1111 1111 em notação binária.</span><span class="sxs-lookup"><span data-stu-id="7d819-190">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="7d819-191">Isso especifica que os primeiros 10 processadores devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="7d819-191">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="7d819-192">Para especificar os 10 próximos processadores, ou seja, os processadores 10-19, especifique um valor decimal de 1047552 (ou um valor hexadecimal de 0xFFC00 ou FFC00), que é equivalente a um valor binário de 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="7d819-192">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="7d819-193">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-193">Setting name</span></span> | <span data-ttu-id="7d819-194">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-194">Values</span></span> | <span data-ttu-id="7d819-195">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-195">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-196">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-196">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="7d819-197">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-197">*decimal value*</span></span> | <span data-ttu-id="7d819-198">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-198">.NET Core 3.0</span></span> |
| <span data-ttu-id="7d819-199">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-199">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="7d819-200">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-200">*hexadecimal value*</span></span> | <span data-ttu-id="7d819-201">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-201">.NET Core 3.0</span></span> |
| <span data-ttu-id="7d819-202">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="7d819-202">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7d819-203">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="7d819-203">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="7d819-204">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-204">*decimal value*</span></span> | <span data-ttu-id="7d819-205">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="7d819-205">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="7d819-206">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7d819-206">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="7d819-207">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="7d819-207">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="7d819-208">Especifica a lista de processadores a serem usados para threads do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="7d819-208">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="7d819-209">Essa configuração é semelhante à `System.GC.HeapAffinitizeMask`, exceto pelo fato de que ela permite que você especifique mais de 64 processadores.</span><span class="sxs-lookup"><span data-stu-id="7d819-209">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="7d819-210">Para sistemas operacionais Windows, Prefixe o número do processador ou o intervalo com o [grupo de CPU](/windows/win32/procthread/processor-groups)correspondente, por exemplo, "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="7d819-210">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="7d819-211">Se a afinidade do processador estiver desabilitada ao definir `System.GC.NoAffinitize` como `true`, essa configuração será ignorada.</span><span class="sxs-lookup"><span data-stu-id="7d819-211">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="7d819-212">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="7d819-212">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="7d819-213">Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.</span><span class="sxs-lookup"><span data-stu-id="7d819-213">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="7d819-214">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-214">Setting name</span></span> | <span data-ttu-id="7d819-215">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-215">Values</span></span> | <span data-ttu-id="7d819-216">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-216">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-217">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-217">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="7d819-218">Lista separada por vírgulas de números de processador ou intervalos de números de processador.</span><span class="sxs-lookup"><span data-stu-id="7d819-218">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="7d819-219">Exemplo de UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="7d819-219">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="7d819-220">Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="7d819-220">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="7d819-221">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-221">.NET Core 3.0</span></span> |
| <span data-ttu-id="7d819-222">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-222">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="7d819-223">Lista separada por vírgulas de números de processador ou intervalos de números de processador.</span><span class="sxs-lookup"><span data-stu-id="7d819-223">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="7d819-224">Exemplo de UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="7d819-224">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="7d819-225">Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="7d819-225">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="7d819-226">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-226">.NET Core 3.0</span></span> |

<span data-ttu-id="7d819-227">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7d819-227">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="7d819-228">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="7d819-228">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="7d819-229">Configura se o coletor de lixo usa [grupos de CPU](/windows/win32/procthread/processor-groups) ou não.</span><span class="sxs-lookup"><span data-stu-id="7d819-229">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="7d819-230">Quando um computador com Windows de 64 bits tem vários grupos de CPU, ou seja, há mais de 64 processadores, a habilitação desse elemento estende a coleta de lixo em todos os grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="7d819-230">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="7d819-231">O coletor de lixo usa todos os núcleos para criar e balancear heaps.</span><span class="sxs-lookup"><span data-stu-id="7d819-231">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="7d819-232">Aplica-se à coleta de lixo do servidor somente em sistemas de operação do Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7d819-232">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="7d819-233">Padrão: desabilitado (`0`).</span><span class="sxs-lookup"><span data-stu-id="7d819-233">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="7d819-234">Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.</span><span class="sxs-lookup"><span data-stu-id="7d819-234">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="7d819-235">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-235">Setting name</span></span> | <span data-ttu-id="7d819-236">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-236">Values</span></span> | <span data-ttu-id="7d819-237">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-237">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-238">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-238">**runtimeconfig.json**</span></span> | <span data-ttu-id="7d819-239">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-239">N/A</span></span> | <span data-ttu-id="7d819-240">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-240">N/A</span></span> | <span data-ttu-id="7d819-241">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-241">N/A</span></span> |
| <span data-ttu-id="7d819-242">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-242">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="7d819-243">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7d819-243">`0` - disabled</span></span><br/><span data-ttu-id="7d819-244">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="7d819-244">`1` - enabled</span></span> | <span data-ttu-id="7d819-245">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="7d819-245">.NET Core 1.0</span></span> |
| <span data-ttu-id="7d819-246">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="7d819-246">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7d819-247">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="7d819-247">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="7d819-248">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7d819-248">`false` - disabled</span></span><br/><span data-ttu-id="7d819-249">habilitado para `true`</span><span class="sxs-lookup"><span data-stu-id="7d819-249">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="7d819-250">Para configurar o Common Language Runtime (CLR) para também distribuir threads do pool de threads em todos os grupos de CPU, habilite a opção de [elemento Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="7d819-250">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="7d819-251">Para aplicativos .NET Core, você pode habilitar essa opção definindo o valor da variável de ambiente `COMPlus_Thread_UseAllCpuGroups` como `1`.</span><span class="sxs-lookup"><span data-stu-id="7d819-251">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="7d819-252">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="7d819-252">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="7d819-253">Especifica se os threads de coleta de lixo devem ser *relacionardos* com processadores.</span><span class="sxs-lookup"><span data-stu-id="7d819-253">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="7d819-254">Para relacionar um thread de GC significa que ele só pode ser executado em sua CPU específica.</span><span class="sxs-lookup"><span data-stu-id="7d819-254">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="7d819-255">Um heap é criado para cada thread do GC.</span><span class="sxs-lookup"><span data-stu-id="7d819-255">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="7d819-256">Aplica-se somente à coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="7d819-256">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="7d819-257">Padrão: relacionar os threads de coleta de lixo com processadores (`false`).</span><span class="sxs-lookup"><span data-stu-id="7d819-257">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="7d819-258">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-258">Setting name</span></span> | <span data-ttu-id="7d819-259">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-259">Values</span></span> | <span data-ttu-id="7d819-260">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-260">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-261">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-261">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="7d819-262">`false`-relacionar</span><span class="sxs-lookup"><span data-stu-id="7d819-262">`false` - affinitize</span></span><br/><span data-ttu-id="7d819-263">`true`-não relacionar</span><span class="sxs-lookup"><span data-stu-id="7d819-263">`true` - don't affinitize</span></span> | <span data-ttu-id="7d819-264">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-264">.NET Core 3.0</span></span> |
| <span data-ttu-id="7d819-265">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-265">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="7d819-266">`0`-relacionar</span><span class="sxs-lookup"><span data-stu-id="7d819-266">`0` - affinitize</span></span><br/><span data-ttu-id="7d819-267">`1`-não relacionar</span><span class="sxs-lookup"><span data-stu-id="7d819-267">`1` - don't affinitize</span></span> | <span data-ttu-id="7d819-268">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-268">.NET Core 3.0</span></span> |
| <span data-ttu-id="7d819-269">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="7d819-269">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7d819-270">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="7d819-270">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="7d819-271">`false`-relacionar</span><span class="sxs-lookup"><span data-stu-id="7d819-271">`false` - affinitize</span></span><br/><span data-ttu-id="7d819-272">`true`-não relacionar</span><span class="sxs-lookup"><span data-stu-id="7d819-272">`true` - don't affinitize</span></span> | <span data-ttu-id="7d819-273">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="7d819-273">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="7d819-274">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7d819-274">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="7d819-275">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="7d819-275">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="7d819-276">Especifica o tamanho máximo de confirmação, em bytes, para o heap de GC e a escrituração de GC.</span><span class="sxs-lookup"><span data-stu-id="7d819-276">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="7d819-277">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-277">Setting name</span></span> | <span data-ttu-id="7d819-278">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-278">Values</span></span> | <span data-ttu-id="7d819-279">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-279">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-280">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-280">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="7d819-281">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-281">*decimal value*</span></span> | <span data-ttu-id="7d819-282">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-282">.NET Core 3.0</span></span> |
| <span data-ttu-id="7d819-283">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-283">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="7d819-284">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-284">*hexadecimal value*</span></span> | <span data-ttu-id="7d819-285">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-285">.NET Core 3.0</span></span> |

<span data-ttu-id="7d819-286">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7d819-286">Example:</span></span>

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
> <span data-ttu-id="7d819-287">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="7d819-287">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="7d819-288">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="7d819-288">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="7d819-289">Por exemplo, para especificar um limite rígido de heap de 200 mebibytes (MiB), os valores seriam 209715200 para o arquivo JSON e 0xC800000 ou C800000 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="7d819-289">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="7d819-290">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="7d819-290">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="7d819-291">Especifica o uso de heap do GC como uma porcentagem da memória total.</span><span class="sxs-lookup"><span data-stu-id="7d819-291">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="7d819-292">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-292">Setting name</span></span> | <span data-ttu-id="7d819-293">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-293">Values</span></span> | <span data-ttu-id="7d819-294">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-294">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-295">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-295">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="7d819-296">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-296">*decimal value*</span></span> | <span data-ttu-id="7d819-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="7d819-298">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-298">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="7d819-299">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-299">*hexadecimal value*</span></span> | <span data-ttu-id="7d819-300">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-300">.NET Core 3.0</span></span> |

<span data-ttu-id="7d819-301">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7d819-301">Example:</span></span>

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
> <span data-ttu-id="7d819-302">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="7d819-302">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="7d819-303">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="7d819-303">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="7d819-304">Por exemplo, para limitar o uso de heap a 30%, os valores seriam 30 para o arquivo JSON e 0x1E ou 1E para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="7d819-304">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="7d819-305">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="7d819-305">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="7d819-306">Configura se OS segmentos que devem ser excluídos são colocados em uma lista de espera para uso futuro ou são liberados de volta para o sistema operacional (SO).</span><span class="sxs-lookup"><span data-stu-id="7d819-306">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="7d819-307">Padrão: liberar segmentos de volta para o sistema operacional (`false`).</span><span class="sxs-lookup"><span data-stu-id="7d819-307">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="7d819-308">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-308">Setting name</span></span> | <span data-ttu-id="7d819-309">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-309">Values</span></span> | <span data-ttu-id="7d819-310">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-310">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-311">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-311">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="7d819-312">`false`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="7d819-312">`false` - release to OS</span></span><br/><span data-ttu-id="7d819-313">`true`-Put em espera</span><span class="sxs-lookup"><span data-stu-id="7d819-313">`true` - put on standby</span></span>| <span data-ttu-id="7d819-314">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="7d819-314">.NET Core 1.0</span></span> |
| <span data-ttu-id="7d819-315">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-315">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="7d819-316">`0`-versão para o sistema operacional</span><span class="sxs-lookup"><span data-stu-id="7d819-316">`0` - release to OS</span></span><br/><span data-ttu-id="7d819-317">`1`-Put em espera</span><span class="sxs-lookup"><span data-stu-id="7d819-317">`1` - put on standby</span></span> | <span data-ttu-id="7d819-318">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="7d819-318">.NET Core 1.0</span></span> |

<span data-ttu-id="7d819-319">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7d819-319">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

## <a name="large-pages"></a><span data-ttu-id="7d819-320">Páginas grandes</span><span class="sxs-lookup"><span data-stu-id="7d819-320">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="7d819-321">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="7d819-321">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="7d819-322">Especifica se páginas grandes devem ser usadas quando um limite rígido de heap for definido.</span><span class="sxs-lookup"><span data-stu-id="7d819-322">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="7d819-323">Padrão: desabilitado (`0`).</span><span class="sxs-lookup"><span data-stu-id="7d819-323">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="7d819-324">Essa é uma configuração experimental.</span><span class="sxs-lookup"><span data-stu-id="7d819-324">This is an experimental setting.</span></span>

| | <span data-ttu-id="7d819-325">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-325">Setting name</span></span> | <span data-ttu-id="7d819-326">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-326">Values</span></span> | <span data-ttu-id="7d819-327">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-327">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-328">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-328">**runtimeconfig.json**</span></span> | <span data-ttu-id="7d819-329">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-329">N/A</span></span> | <span data-ttu-id="7d819-330">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-330">N/A</span></span> | <span data-ttu-id="7d819-331">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-331">N/A</span></span> |
| <span data-ttu-id="7d819-332">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-332">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="7d819-333">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7d819-333">`0` - disabled</span></span><br/><span data-ttu-id="7d819-334">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="7d819-334">`1` - enabled</span></span> | <span data-ttu-id="7d819-335">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d819-335">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="7d819-336">Objetos grandes</span><span class="sxs-lookup"><span data-stu-id="7d819-336">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="7d819-337">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="7d819-337">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="7d819-338">Configura o suporte ao coletor de lixo em plataformas de 64 bits para matrizes com mais de 2 gigabytes (GB) no tamanho total.</span><span class="sxs-lookup"><span data-stu-id="7d819-338">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="7d819-339">Padrão: habilitado (`1`).</span><span class="sxs-lookup"><span data-stu-id="7d819-339">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="7d819-340">Essa opção pode se tornar obsoleta em uma versão futura do .NET.</span><span class="sxs-lookup"><span data-stu-id="7d819-340">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="7d819-341">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-341">Setting name</span></span> | <span data-ttu-id="7d819-342">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-342">Values</span></span> | <span data-ttu-id="7d819-343">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-343">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-344">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-344">**runtimeconfig.json**</span></span> | <span data-ttu-id="7d819-345">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-345">N/A</span></span> | <span data-ttu-id="7d819-346">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-346">N/A</span></span> | <span data-ttu-id="7d819-347">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-347">N/A</span></span> |
| <span data-ttu-id="7d819-348">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-348">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="7d819-349">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="7d819-349">`1` - enabled</span></span><br/> <span data-ttu-id="7d819-350">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7d819-350">`0` - disabled</span></span> | <span data-ttu-id="7d819-351">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="7d819-351">.NET Core 1.0</span></span> |
| <span data-ttu-id="7d819-352">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="7d819-352">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7d819-353">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="7d819-353">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="7d819-354">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="7d819-354">`1` - enabled</span></span><br/> <span data-ttu-id="7d819-355">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7d819-355">`0` - disabled</span></span> | <span data-ttu-id="7d819-356">{1&gt;{2&gt;.NET Framework 4.5&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-356">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="7d819-357">Limite de heap de objeto grande</span><span class="sxs-lookup"><span data-stu-id="7d819-357">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="7d819-358">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="7d819-358">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="7d819-359">Especifica o tamanho do limite, em bytes, que faz com que os objetos vá para o LOH (heap de objeto grande).</span><span class="sxs-lookup"><span data-stu-id="7d819-359">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="7d819-360">O limite padrão é de 85.000 bytes.</span><span class="sxs-lookup"><span data-stu-id="7d819-360">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="7d819-361">O valor especificado deve ser maior que o limite padrão.</span><span class="sxs-lookup"><span data-stu-id="7d819-361">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="7d819-362">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-362">Setting name</span></span> | <span data-ttu-id="7d819-363">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-363">Values</span></span> | <span data-ttu-id="7d819-364">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-364">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-365">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-365">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="7d819-366">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-366">*decimal value*</span></span> | <span data-ttu-id="7d819-367">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="7d819-367">.NET Core 1.0</span></span> |
| <span data-ttu-id="7d819-368">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-368">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="7d819-369">*valor hexadecimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-369">*hexadecimal value*</span></span> | <span data-ttu-id="7d819-370">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="7d819-370">.NET Core 1.0</span></span> |
| <span data-ttu-id="7d819-371">**App. config para .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="7d819-371">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7d819-372">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="7d819-372">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="7d819-373">*valor decimal*</span><span class="sxs-lookup"><span data-stu-id="7d819-373">*decimal value*</span></span> | <span data-ttu-id="7d819-374">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="7d819-374">.NET Framework 4.8</span></span> |

<span data-ttu-id="7d819-375">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="7d819-375">Example:</span></span>

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
> <span data-ttu-id="7d819-376">Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal.</span><span class="sxs-lookup"><span data-stu-id="7d819-376">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="7d819-377">Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="7d819-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="7d819-378">Por exemplo, para definir um tamanho de limite de 120.000 bytes, os valores seriam 120000 para o arquivo JSON e 0x1D4C0 ou 1D4C0 para a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="7d819-378">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="7d819-379">GC autônomo</span><span class="sxs-lookup"><span data-stu-id="7d819-379">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="7d819-380">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="7d819-380">COMPlus_GCName</span></span>

- <span data-ttu-id="7d819-381">Especifica um caminho para a biblioteca que contém o coletor de lixo que o tempo de execução pretende carregar.</span><span class="sxs-lookup"><span data-stu-id="7d819-381">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="7d819-382">Para obter mais informações, consulte [design de carregador de GC autônomo](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="7d819-382">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="7d819-383">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d819-383">Setting name</span></span> | <span data-ttu-id="7d819-384">Valores</span><span class="sxs-lookup"><span data-stu-id="7d819-384">Values</span></span> | <span data-ttu-id="7d819-385">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7d819-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7d819-386">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7d819-386">**runtimeconfig.json**</span></span> | <span data-ttu-id="7d819-387">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-387">N/A</span></span> | <span data-ttu-id="7d819-388">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-388">N/A</span></span> | <span data-ttu-id="7d819-389">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7d819-389">N/A</span></span> |
| <span data-ttu-id="7d819-390">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d819-390">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="7d819-391">*string_path*</span><span class="sxs-lookup"><span data-stu-id="7d819-391">*string_path*</span></span> | <span data-ttu-id="7d819-392">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="7d819-392">.NET Core 2.0</span></span> |
