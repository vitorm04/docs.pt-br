---
title: Definições de configuração de compilação
description: Saiba mais sobre as configurações de tempo de execução que configuram como o compilador JIT funciona para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0dab3b7b7726a232cf293e338308cf898b370759
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733530"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="a4997-103">Opções de configuração de tempo de execução para compilação</span><span class="sxs-lookup"><span data-stu-id="a4997-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="a4997-104">Compilação em camadas</span><span class="sxs-lookup"><span data-stu-id="a4997-104">Tiered compilation</span></span>

- <span data-ttu-id="a4997-105">Configura se o compilador JIT (just-in-time) usa compilação em [camadas](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="a4997-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="a4997-106">A compilação em camadas faz a transição de métodos por meio de duas camadas:</span><span class="sxs-lookup"><span data-stu-id="a4997-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="a4997-107">A primeira camada gera código mais rapidamente ([JIT rápido](#quick-jit)) ou carrega código pré-compilado ([ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)).</span><span class="sxs-lookup"><span data-stu-id="a4997-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)).</span></span>
  - <span data-ttu-id="a4997-108">A segunda camada gera código otimizado em segundo plano ("Otimizando JIT").</span><span class="sxs-lookup"><span data-stu-id="a4997-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="a4997-109">No .NET Core 3,0 e posterior, a compilação em camadas está habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="a4997-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="a4997-110">No .NET Core 2,1 e 2,2, a compilação em camadas está desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="a4997-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="a4997-111">Para obter mais informações, consulte o [Guia de compilação em camadas](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span><span class="sxs-lookup"><span data-stu-id="a4997-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="a4997-112">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="a4997-112">Setting name</span></span> | <span data-ttu-id="a4997-113">Valores</span><span class="sxs-lookup"><span data-stu-id="a4997-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a4997-114">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a4997-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="a4997-115">habilitado para `true`</span><span class="sxs-lookup"><span data-stu-id="a4997-115">`true` - enabled</span></span><br/><span data-ttu-id="a4997-116">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="a4997-116">`false` - disabled</span></span> |
| <span data-ttu-id="a4997-117">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="a4997-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="a4997-118">habilitado para `true`</span><span class="sxs-lookup"><span data-stu-id="a4997-118">`true` - enabled</span></span><br/><span data-ttu-id="a4997-119">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="a4997-119">`false` - disabled</span></span> |
| <span data-ttu-id="a4997-120">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="a4997-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="a4997-121">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="a4997-121">`1` - enabled</span></span><br/><span data-ttu-id="a4997-122">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="a4997-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="a4997-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a4997-123">Examples</span></span>

<span data-ttu-id="a4997-124">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="a4997-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="a4997-125">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="a4997-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="a4997-126">JIT rápido</span><span class="sxs-lookup"><span data-stu-id="a4997-126">Quick JIT</span></span>

- <span data-ttu-id="a4997-127">Configura se o compilador JIT usa o *JIT rápido*.</span><span class="sxs-lookup"><span data-stu-id="a4997-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="a4997-128">Para métodos que não contêm loops e para os quais o código pré-compilado não está disponível, o JIT rápido compila-os mais rapidamente, mas sem otimizações.</span><span class="sxs-lookup"><span data-stu-id="a4997-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="a4997-129">Habilitar o JIT rápido diminui o tempo de inicialização, mas pode produzir código com características de desempenho degradadas.</span><span class="sxs-lookup"><span data-stu-id="a4997-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="a4997-130">Por exemplo, o código pode usar mais espaço de pilha, alocar mais memória e executar mais lentamente.</span><span class="sxs-lookup"><span data-stu-id="a4997-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="a4997-131">Se o JIT rápido estiver desabilitado, mas a [compilação em camadas](#tiered-compilation) estiver habilitada, somente o código pré-compilado participará da compilação em camadas.</span><span class="sxs-lookup"><span data-stu-id="a4997-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="a4997-132">Se um método não for compilado previamente com [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images), o comportamento de JIT será o mesmo que se a [compilação em camadas](#tiered-compilation) fosse desabilitada.</span><span class="sxs-lookup"><span data-stu-id="a4997-132">If a method is not pre-compiled with [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="a4997-133">No .NET Core 3,0 e posterior, o Quick JIT é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="a4997-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="a4997-134">No .NET Core 2,1 e 2,2, o Quick JIT é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="a4997-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="a4997-135">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="a4997-135">Setting name</span></span> | <span data-ttu-id="a4997-136">Valores</span><span class="sxs-lookup"><span data-stu-id="a4997-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a4997-137">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a4997-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="a4997-138">habilitado para `true`</span><span class="sxs-lookup"><span data-stu-id="a4997-138">`true` - enabled</span></span><br/><span data-ttu-id="a4997-139">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="a4997-139">`false` - disabled</span></span> |
| <span data-ttu-id="a4997-140">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="a4997-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="a4997-141">habilitado para `true`</span><span class="sxs-lookup"><span data-stu-id="a4997-141">`true` - enabled</span></span><br/><span data-ttu-id="a4997-142">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="a4997-142">`false` - disabled</span></span> |
| <span data-ttu-id="a4997-143">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="a4997-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="a4997-144">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="a4997-144">`1` - enabled</span></span><br/><span data-ttu-id="a4997-145">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="a4997-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="a4997-146">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a4997-146">Examples</span></span>

<span data-ttu-id="a4997-147">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="a4997-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="a4997-148">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="a4997-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="a4997-149">JIT rápido para loops</span><span class="sxs-lookup"><span data-stu-id="a4997-149">Quick JIT for loops</span></span>

- <span data-ttu-id="a4997-150">Configura se o compilador JIT usa o JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="a4997-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="a4997-151">Habilitar o JIT rápido para loops pode melhorar o desempenho de inicialização.</span><span class="sxs-lookup"><span data-stu-id="a4997-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="a4997-152">No entanto, loops de longa execução podem ficar presos em código menos otimizado por longos períodos.</span><span class="sxs-lookup"><span data-stu-id="a4997-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="a4997-153">Se a opção [JIT rápida](#quick-jit) estiver desabilitada, essa configuração não terá efeito.</span><span class="sxs-lookup"><span data-stu-id="a4997-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="a4997-154">Padrão: desabilitado (`false`).</span><span class="sxs-lookup"><span data-stu-id="a4997-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="a4997-155">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="a4997-155">Setting name</span></span> | <span data-ttu-id="a4997-156">Valores</span><span class="sxs-lookup"><span data-stu-id="a4997-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a4997-157">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a4997-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="a4997-158">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="a4997-158">`false` - disabled</span></span><br/><span data-ttu-id="a4997-159">habilitado para `true`</span><span class="sxs-lookup"><span data-stu-id="a4997-159">`true` - enabled</span></span> |
| <span data-ttu-id="a4997-160">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="a4997-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="a4997-161">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="a4997-161">`false` - disabled</span></span><br/><span data-ttu-id="a4997-162">habilitado para `true`</span><span class="sxs-lookup"><span data-stu-id="a4997-162">`true` - enabled</span></span> |
| <span data-ttu-id="a4997-163">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="a4997-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="a4997-164">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="a4997-164">`0` - disabled</span></span><br/><span data-ttu-id="a4997-165">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="a4997-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="a4997-166">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a4997-166">Examples</span></span>

<span data-ttu-id="a4997-167">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="a4997-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="a4997-168">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="a4997-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```
