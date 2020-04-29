---
title: Definições de configuração de compilação
description: Saiba mais sobre as configurações de tempo de execução que configuram como o compilador JIT funciona para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 4db20ee6d36fe3d3d66f473644b70c02d4e02cb3
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506838"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="7fcfb-103">Opções de configuração de tempo de execução para compilação</span><span class="sxs-lookup"><span data-stu-id="7fcfb-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="7fcfb-104">Compilação em camadas</span><span class="sxs-lookup"><span data-stu-id="7fcfb-104">Tiered compilation</span></span>

- <span data-ttu-id="7fcfb-105">Configura se o compilador JIT (just-in-time) usa compilação em [camadas](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="7fcfb-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="7fcfb-106">A compilação em camadas faz a transição de métodos por meio de duas camadas:</span><span class="sxs-lookup"><span data-stu-id="7fcfb-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="7fcfb-107">A primeira camada gera código mais rapidamente ([JIT rápido](#quick-jit)) ou carrega código pré-compilado ([ReadyToRun](#readytorun)).</span><span class="sxs-lookup"><span data-stu-id="7fcfb-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="7fcfb-108">A segunda camada gera código otimizado em segundo plano ("Otimizando JIT").</span><span class="sxs-lookup"><span data-stu-id="7fcfb-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="7fcfb-109">No .NET Core 3,0 e posterior, a compilação em camadas está habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="7fcfb-110">No .NET Core 2,1 e 2,2, a compilação em camadas está desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="7fcfb-111">Para obter mais informações, consulte o [Guia de compilação em camadas](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="7fcfb-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span></span>

| | <span data-ttu-id="7fcfb-112">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7fcfb-112">Setting name</span></span> | <span data-ttu-id="7fcfb-113">Valores</span><span class="sxs-lookup"><span data-stu-id="7fcfb-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7fcfb-114">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7fcfb-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="7fcfb-115">`true`-habilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-115">`true` - enabled</span></span><br/><span data-ttu-id="7fcfb-116">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-116">`false` - disabled</span></span> |
| <span data-ttu-id="7fcfb-117">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="7fcfb-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="7fcfb-118">`true`-habilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-118">`true` - enabled</span></span><br/><span data-ttu-id="7fcfb-119">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-119">`false` - disabled</span></span> |
| <span data-ttu-id="7fcfb-120">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7fcfb-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="7fcfb-121">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-121">`1` - enabled</span></span><br/><span data-ttu-id="7fcfb-122">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="7fcfb-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7fcfb-123">Examples</span></span>

<span data-ttu-id="7fcfb-124">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="7fcfb-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="7fcfb-125">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="7fcfb-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="7fcfb-126">JIT rápido</span><span class="sxs-lookup"><span data-stu-id="7fcfb-126">Quick JIT</span></span>

- <span data-ttu-id="7fcfb-127">Configura se o compilador JIT usa o *JIT rápido*.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="7fcfb-128">Para métodos que não contêm loops e para os quais o código pré-compilado não está disponível, o JIT rápido compila-os mais rapidamente, mas sem otimizações.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="7fcfb-129">Habilitar o JIT rápido diminui o tempo de inicialização, mas pode produzir código com características de desempenho degradadas.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="7fcfb-130">Por exemplo, o código pode usar mais espaço de pilha, alocar mais memória e executar mais lentamente.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="7fcfb-131">Se o JIT rápido estiver desabilitado, mas a [compilação em camadas](#tiered-compilation) estiver habilitada, somente o código pré-compilado participará da compilação em camadas.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="7fcfb-132">Se um método não for compilado previamente com [ReadyToRun](#readytorun), o comportamento de JIT será o mesmo que se a [compilação em camadas](#tiered-compilation) fosse desabilitada.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="7fcfb-133">No .NET Core 3,0 e posterior, o Quick JIT é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="7fcfb-134">No .NET Core 2,1 e 2,2, o Quick JIT é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="7fcfb-135">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7fcfb-135">Setting name</span></span> | <span data-ttu-id="7fcfb-136">Valores</span><span class="sxs-lookup"><span data-stu-id="7fcfb-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7fcfb-137">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7fcfb-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="7fcfb-138">`true`-habilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-138">`true` - enabled</span></span><br/><span data-ttu-id="7fcfb-139">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-139">`false` - disabled</span></span> |
| <span data-ttu-id="7fcfb-140">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="7fcfb-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="7fcfb-141">`true`-habilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-141">`true` - enabled</span></span><br/><span data-ttu-id="7fcfb-142">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-142">`false` - disabled</span></span> |
| <span data-ttu-id="7fcfb-143">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7fcfb-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="7fcfb-144">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-144">`1` - enabled</span></span><br/><span data-ttu-id="7fcfb-145">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="7fcfb-146">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7fcfb-146">Examples</span></span>

<span data-ttu-id="7fcfb-147">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="7fcfb-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="7fcfb-148">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="7fcfb-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="7fcfb-149">JIT rápido para loops</span><span class="sxs-lookup"><span data-stu-id="7fcfb-149">Quick JIT for loops</span></span>

- <span data-ttu-id="7fcfb-150">Configura se o compilador JIT usa o JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="7fcfb-151">Habilitar o JIT rápido para loops pode melhorar o desempenho de inicialização.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="7fcfb-152">No entanto, loops de longa execução podem ficar presos em código menos otimizado por longos períodos.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="7fcfb-153">Se a opção [JIT rápida](#quick-jit) estiver desabilitada, essa configuração não terá efeito.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="7fcfb-154">Padrão: desabilitado`false`().</span><span class="sxs-lookup"><span data-stu-id="7fcfb-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="7fcfb-155">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7fcfb-155">Setting name</span></span> | <span data-ttu-id="7fcfb-156">Valores</span><span class="sxs-lookup"><span data-stu-id="7fcfb-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7fcfb-157">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="7fcfb-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="7fcfb-158">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-158">`false` - disabled</span></span><br/><span data-ttu-id="7fcfb-159">`true`-habilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-159">`true` - enabled</span></span> |
| <span data-ttu-id="7fcfb-160">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="7fcfb-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="7fcfb-161">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-161">`false` - disabled</span></span><br/><span data-ttu-id="7fcfb-162">`true`-habilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-162">`true` - enabled</span></span> |
| <span data-ttu-id="7fcfb-163">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7fcfb-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="7fcfb-164">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-164">`0` - disabled</span></span><br/><span data-ttu-id="7fcfb-165">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="7fcfb-166">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7fcfb-166">Examples</span></span>

<span data-ttu-id="7fcfb-167">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="7fcfb-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="7fcfb-168">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="7fcfb-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="7fcfb-169">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="7fcfb-169">ReadyToRun</span></span>

- <span data-ttu-id="7fcfb-170">Configura se o tempo de execução do .NET Core usa código pré-compilado para imagens com dados ReadyToRun disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="7fcfb-171">Desabilitar essa opção força o tempo de execução para o código de estrutura JIT-compile.</span><span class="sxs-lookup"><span data-stu-id="7fcfb-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="7fcfb-172">Para obter mais informações, consulte [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="7fcfb-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="7fcfb-173">Padrão: habilitado (`1`).</span><span class="sxs-lookup"><span data-stu-id="7fcfb-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="7fcfb-174">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7fcfb-174">Setting name</span></span> | <span data-ttu-id="7fcfb-175">Valores</span><span class="sxs-lookup"><span data-stu-id="7fcfb-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7fcfb-176">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7fcfb-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="7fcfb-177">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-177">`1` - enabled</span></span><br/><span data-ttu-id="7fcfb-178">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="7fcfb-178">`0` - disabled</span></span> |
