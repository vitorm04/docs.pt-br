---
title: Configurações de configuração de compilação
description: Saiba mais sobre as configurações de tempo de execução que configuram como o compilador JIT funciona para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ac51aa13254b2f2b1fdd8d1dd9c52559831a1659
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989110"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="69afa-103">Opções de configuração em tempo de execução para compilação</span><span class="sxs-lookup"><span data-stu-id="69afa-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="69afa-104">Compilação em camadas</span><span class="sxs-lookup"><span data-stu-id="69afa-104">Tiered compilation</span></span>

- <span data-ttu-id="69afa-105">Configura se o compilador just-in-time (JIT) usa [compilação hierárquica](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="69afa-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="69afa-106">Métodos de transição de compilação hierárquico através de dois níveis:</span><span class="sxs-lookup"><span data-stu-id="69afa-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="69afa-107">O primeiro nível gera código mais rapidamente[(JIT rápido)](#quick-jit)ou carrega código pré-compilado[(ReadyToRun).](#readytorun)</span><span class="sxs-lookup"><span data-stu-id="69afa-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="69afa-108">O segundo nível gera código otimizado em segundo plano ("otimizando o JIT").</span><span class="sxs-lookup"><span data-stu-id="69afa-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="69afa-109">No .NET Core 3.0 e posterior, a compilação hierárquica é habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="69afa-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="69afa-110">No .NET Core 2.1 e 2.2, a compilação hierárquica é desativada por padrão.</span><span class="sxs-lookup"><span data-stu-id="69afa-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="69afa-111">Para obter mais informações, consulte o [guia de compilação hierárquico](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="69afa-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span></span>

| | <span data-ttu-id="69afa-112">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="69afa-112">Setting name</span></span> | <span data-ttu-id="69afa-113">Valores</span><span class="sxs-lookup"><span data-stu-id="69afa-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="69afa-114">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="69afa-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="69afa-115">`true`- habilitado</span><span class="sxs-lookup"><span data-stu-id="69afa-115">`true` - enabled</span></span><br/><span data-ttu-id="69afa-116">`false`- deficientes</span><span class="sxs-lookup"><span data-stu-id="69afa-116">`false` - disabled</span></span> |
| <span data-ttu-id="69afa-117">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="69afa-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="69afa-118">`true`- habilitado</span><span class="sxs-lookup"><span data-stu-id="69afa-118">`true` - enabled</span></span><br/><span data-ttu-id="69afa-119">`false`- deficientes</span><span class="sxs-lookup"><span data-stu-id="69afa-119">`false` - disabled</span></span> |
| <span data-ttu-id="69afa-120">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="69afa-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="69afa-121">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="69afa-121">`1` - enabled</span></span><br/><span data-ttu-id="69afa-122">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="69afa-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="69afa-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="69afa-123">Examples</span></span>

<span data-ttu-id="69afa-124">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="69afa-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="69afa-125">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="69afa-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="69afa-126">JIT Rápido</span><span class="sxs-lookup"><span data-stu-id="69afa-126">Quick JIT</span></span>

- <span data-ttu-id="69afa-127">Configura se o compilador JIT usa *JIT rápido*.</span><span class="sxs-lookup"><span data-stu-id="69afa-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="69afa-128">Para métodos que não contêm loops e para os quais o código pré-compilado não está disponível, o JIT rápido os compila mais rapidamente, mas sem otimizações.</span><span class="sxs-lookup"><span data-stu-id="69afa-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="69afa-129">Permitir jit rápido diminui o tempo de inicialização, mas pode produzir código com características de desempenho degradadas.</span><span class="sxs-lookup"><span data-stu-id="69afa-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="69afa-130">Por exemplo, o código pode usar mais espaço de pilha, alocar mais memória e executar mais devagar.</span><span class="sxs-lookup"><span data-stu-id="69afa-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="69afa-131">Se o JIT rápido estiver desativado, mas [a compilação hierárquica](#tiered-compilation) estiver ativada, apenas o código pré-compilado participará da compilação hierárquica.</span><span class="sxs-lookup"><span data-stu-id="69afa-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="69afa-132">Se um método não for pré-compilado com [ReadyToRun,](#readytorun)o comportamento do JIT é o mesmo que se a [compilação hierárquica](#tiered-compilation) fosse desativada.</span><span class="sxs-lookup"><span data-stu-id="69afa-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="69afa-133">No .NET Core 3.0 e posterior, o JIT rápido é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="69afa-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="69afa-134">No .NET Core 2.1 e 2.2, o JIT rápido é desativado por padrão.</span><span class="sxs-lookup"><span data-stu-id="69afa-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="69afa-135">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="69afa-135">Setting name</span></span> | <span data-ttu-id="69afa-136">Valores</span><span class="sxs-lookup"><span data-stu-id="69afa-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="69afa-137">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="69afa-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="69afa-138">`true`- habilitado</span><span class="sxs-lookup"><span data-stu-id="69afa-138">`true` - enabled</span></span><br/><span data-ttu-id="69afa-139">`false`- deficientes</span><span class="sxs-lookup"><span data-stu-id="69afa-139">`false` - disabled</span></span> |
| <span data-ttu-id="69afa-140">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="69afa-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="69afa-141">`true`- habilitado</span><span class="sxs-lookup"><span data-stu-id="69afa-141">`true` - enabled</span></span><br/><span data-ttu-id="69afa-142">`false`- deficientes</span><span class="sxs-lookup"><span data-stu-id="69afa-142">`false` - disabled</span></span> |
| <span data-ttu-id="69afa-143">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="69afa-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="69afa-144">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="69afa-144">`1` - enabled</span></span><br/><span data-ttu-id="69afa-145">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="69afa-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="69afa-146">Exemplos</span><span class="sxs-lookup"><span data-stu-id="69afa-146">Examples</span></span>

<span data-ttu-id="69afa-147">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="69afa-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="69afa-148">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="69afa-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="69afa-149">JIT rápido para loops</span><span class="sxs-lookup"><span data-stu-id="69afa-149">Quick JIT for loops</span></span>

- <span data-ttu-id="69afa-150">Configura se o compilador JIT usa JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="69afa-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="69afa-151">A habilitação de JIT rápido para loops pode melhorar o desempenho da inicialização.</span><span class="sxs-lookup"><span data-stu-id="69afa-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="69afa-152">No entanto, loops de longa duração podem ficar presos em códigos menos otimizados por longos períodos.</span><span class="sxs-lookup"><span data-stu-id="69afa-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="69afa-153">Se [o JIT rápido](#quick-jit) estiver desativado, esta configuração não tem efeito.</span><span class="sxs-lookup"><span data-stu-id="69afa-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="69afa-154">Padrão: Desabilitado ( ).`false`</span><span class="sxs-lookup"><span data-stu-id="69afa-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="69afa-155">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="69afa-155">Setting name</span></span> | <span data-ttu-id="69afa-156">Valores</span><span class="sxs-lookup"><span data-stu-id="69afa-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="69afa-157">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="69afa-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="69afa-158">`false`- deficientes</span><span class="sxs-lookup"><span data-stu-id="69afa-158">`false` - disabled</span></span><br/><span data-ttu-id="69afa-159">`true`- habilitado</span><span class="sxs-lookup"><span data-stu-id="69afa-159">`true` - enabled</span></span> |
| <span data-ttu-id="69afa-160">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="69afa-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="69afa-161">`false`- deficientes</span><span class="sxs-lookup"><span data-stu-id="69afa-161">`false` - disabled</span></span><br/><span data-ttu-id="69afa-162">`true`- habilitado</span><span class="sxs-lookup"><span data-stu-id="69afa-162">`true` - enabled</span></span> |
| <span data-ttu-id="69afa-163">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="69afa-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="69afa-164">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="69afa-164">`0` - disabled</span></span><br/><span data-ttu-id="69afa-165">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="69afa-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="69afa-166">Exemplos</span><span class="sxs-lookup"><span data-stu-id="69afa-166">Examples</span></span>

<span data-ttu-id="69afa-167">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="69afa-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="69afa-168">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="69afa-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="69afa-169">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="69afa-169">ReadyToRun</span></span>

- <span data-ttu-id="69afa-170">Configura se o tempo de execução do .NET Core usa código pré-compilado para imagens com dados ReadyToRun disponíveis.</span><span class="sxs-lookup"><span data-stu-id="69afa-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="69afa-171">Desativar essa opção força o tempo de execução para o código de estrutura jit-compilar.</span><span class="sxs-lookup"><span data-stu-id="69afa-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="69afa-172">Para obter mais informações, consulte [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="69afa-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="69afa-173">Padrão: Ativado`1`().</span><span class="sxs-lookup"><span data-stu-id="69afa-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="69afa-174">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="69afa-174">Setting name</span></span> | <span data-ttu-id="69afa-175">Valores</span><span class="sxs-lookup"><span data-stu-id="69afa-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="69afa-176">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="69afa-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="69afa-177">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="69afa-177">`1` - enabled</span></span><br/><span data-ttu-id="69afa-178">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="69afa-178">`0` - disabled</span></span> |
