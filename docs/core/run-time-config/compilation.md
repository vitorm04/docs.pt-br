---
title: Definições de configuração de compilação
description: Saiba mais sobre as configurações de tempo de execução que configuram como o compilador JIT funciona para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: e5f9e1245b749864787fb808527d022665197edf
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654836"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="40b8e-103">Opções de configuração de tempo de execução para compilação</span><span class="sxs-lookup"><span data-stu-id="40b8e-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="40b8e-104">Compilação em camadas</span><span class="sxs-lookup"><span data-stu-id="40b8e-104">Tiered compilation</span></span>

- <span data-ttu-id="40b8e-105">Configura se o compilador JIT (just-in-time) usa compilação em [camadas](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="40b8e-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="40b8e-106">A compilação em camadas faz a transição de métodos por meio de duas camadas:</span><span class="sxs-lookup"><span data-stu-id="40b8e-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="40b8e-107">A primeira camada gera código mais rapidamente ([JIT rápido](#quick-jit)) ou carrega código pré-compilado ([ReadyToRun](#readytorun)).</span><span class="sxs-lookup"><span data-stu-id="40b8e-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="40b8e-108">A segunda camada gera código otimizado em segundo plano ("Otimizando JIT").</span><span class="sxs-lookup"><span data-stu-id="40b8e-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="40b8e-109">No .NET Core 3,0 e posterior, a compilação em camadas está habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="40b8e-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="40b8e-110">No .NET Core 2,1 e 2,2, a compilação em camadas está desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="40b8e-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="40b8e-111">Para obter mais informações, consulte o [Guia de compilação em camadas](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="40b8e-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span></span>

| | <span data-ttu-id="40b8e-112">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="40b8e-112">Setting name</span></span> | <span data-ttu-id="40b8e-113">Valores</span><span class="sxs-lookup"><span data-stu-id="40b8e-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="40b8e-114">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="40b8e-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="40b8e-115">`true` -habilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-115">`true` - enabled</span></span><br/><span data-ttu-id="40b8e-116">`false` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-116">`false` - disabled</span></span> |
| <span data-ttu-id="40b8e-117">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="40b8e-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="40b8e-118">`true` -habilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-118">`true` - enabled</span></span><br/><span data-ttu-id="40b8e-119">`false` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-119">`false` - disabled</span></span> |
| <span data-ttu-id="40b8e-120">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="40b8e-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="40b8e-121">`1` -habilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-121">`1` - enabled</span></span><br/><span data-ttu-id="40b8e-122">`0` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="40b8e-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="40b8e-123">Examples</span></span>

<span data-ttu-id="40b8e-124">*runtimeconfig.jsno* arquivo:</span><span class="sxs-lookup"><span data-stu-id="40b8e-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="40b8e-125">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="40b8e-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="40b8e-126">JIT rápido</span><span class="sxs-lookup"><span data-stu-id="40b8e-126">Quick JIT</span></span>

- <span data-ttu-id="40b8e-127">Configura se o compilador JIT usa o *JIT rápido*.</span><span class="sxs-lookup"><span data-stu-id="40b8e-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="40b8e-128">Para métodos que não contêm loops e para os quais o código pré-compilado não está disponível, o JIT rápido compila-os mais rapidamente, mas sem otimizações.</span><span class="sxs-lookup"><span data-stu-id="40b8e-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="40b8e-129">Habilitar o JIT rápido diminui o tempo de inicialização, mas pode produzir código com características de desempenho degradadas.</span><span class="sxs-lookup"><span data-stu-id="40b8e-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="40b8e-130">Por exemplo, o código pode usar mais espaço de pilha, alocar mais memória e executar mais lentamente.</span><span class="sxs-lookup"><span data-stu-id="40b8e-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="40b8e-131">Se o JIT rápido estiver desabilitado, mas a [compilação em camadas](#tiered-compilation) estiver habilitada, somente o código pré-compilado participará da compilação em camadas.</span><span class="sxs-lookup"><span data-stu-id="40b8e-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="40b8e-132">Se um método não for compilado previamente com [ReadyToRun](#readytorun), o comportamento de JIT será o mesmo que se a [compilação em camadas](#tiered-compilation) fosse desabilitada.</span><span class="sxs-lookup"><span data-stu-id="40b8e-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="40b8e-133">No .NET Core 3,0 e posterior, o Quick JIT é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="40b8e-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="40b8e-134">No .NET Core 2,1 e 2,2, o Quick JIT é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="40b8e-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="40b8e-135">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="40b8e-135">Setting name</span></span> | <span data-ttu-id="40b8e-136">Valores</span><span class="sxs-lookup"><span data-stu-id="40b8e-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="40b8e-137">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="40b8e-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="40b8e-138">`true` -habilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-138">`true` - enabled</span></span><br/><span data-ttu-id="40b8e-139">`false` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-139">`false` - disabled</span></span> |
| <span data-ttu-id="40b8e-140">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="40b8e-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="40b8e-141">`true` -habilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-141">`true` - enabled</span></span><br/><span data-ttu-id="40b8e-142">`false` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-142">`false` - disabled</span></span> |
| <span data-ttu-id="40b8e-143">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="40b8e-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="40b8e-144">`1` -habilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-144">`1` - enabled</span></span><br/><span data-ttu-id="40b8e-145">`0` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="40b8e-146">Exemplos</span><span class="sxs-lookup"><span data-stu-id="40b8e-146">Examples</span></span>

<span data-ttu-id="40b8e-147">*runtimeconfig.jsno* arquivo:</span><span class="sxs-lookup"><span data-stu-id="40b8e-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="40b8e-148">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="40b8e-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="40b8e-149">JIT rápido para loops</span><span class="sxs-lookup"><span data-stu-id="40b8e-149">Quick JIT for loops</span></span>

- <span data-ttu-id="40b8e-150">Configura se o compilador JIT usa o JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="40b8e-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="40b8e-151">Habilitar o JIT rápido para loops pode melhorar o desempenho de inicialização.</span><span class="sxs-lookup"><span data-stu-id="40b8e-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="40b8e-152">No entanto, loops de longa execução podem ficar presos em código menos otimizado por longos períodos.</span><span class="sxs-lookup"><span data-stu-id="40b8e-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="40b8e-153">Se a opção [JIT rápida](#quick-jit) estiver desabilitada, essa configuração não terá efeito.</span><span class="sxs-lookup"><span data-stu-id="40b8e-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="40b8e-154">Se você omitir essa configuração, o JIT rápido não será usado para métodos que contenham loops.</span><span class="sxs-lookup"><span data-stu-id="40b8e-154">If you omit this setting, quick JIT is not used for methods that contain loops.</span></span> <span data-ttu-id="40b8e-155">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="40b8e-155">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="40b8e-156">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="40b8e-156">Setting name</span></span> | <span data-ttu-id="40b8e-157">Valores</span><span class="sxs-lookup"><span data-stu-id="40b8e-157">Values</span></span> |
| - | - | - |
| <span data-ttu-id="40b8e-158">**runtimeconfig.jsem**</span><span class="sxs-lookup"><span data-stu-id="40b8e-158">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="40b8e-159">`false` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-159">`false` - disabled</span></span><br/><span data-ttu-id="40b8e-160">`true` -habilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-160">`true` - enabled</span></span> |
| <span data-ttu-id="40b8e-161">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="40b8e-161">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="40b8e-162">`false` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-162">`false` - disabled</span></span><br/><span data-ttu-id="40b8e-163">`true` -habilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-163">`true` - enabled</span></span> |
| <span data-ttu-id="40b8e-164">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="40b8e-164">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="40b8e-165">`0` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-165">`0` - disabled</span></span><br/><span data-ttu-id="40b8e-166">`1` -habilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-166">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="40b8e-167">Exemplos</span><span class="sxs-lookup"><span data-stu-id="40b8e-167">Examples</span></span>

<span data-ttu-id="40b8e-168">*runtimeconfig.jsno* arquivo:</span><span class="sxs-lookup"><span data-stu-id="40b8e-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="40b8e-169">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="40b8e-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="40b8e-170">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="40b8e-170">ReadyToRun</span></span>

- <span data-ttu-id="40b8e-171">Configura se o tempo de execução do .NET Core usa código pré-compilado para imagens com dados ReadyToRun disponíveis.</span><span class="sxs-lookup"><span data-stu-id="40b8e-171">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="40b8e-172">Desabilitar essa opção força o tempo de execução para o código de estrutura JIT-compile.</span><span class="sxs-lookup"><span data-stu-id="40b8e-172">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="40b8e-173">Para obter mais informações, consulte [pronto para executar](../deploying/ready-to-run.md).</span><span class="sxs-lookup"><span data-stu-id="40b8e-173">For more information, see [Ready to Run](../deploying/ready-to-run.md).</span></span>
- <span data-ttu-id="40b8e-174">Se você omitir essa configuração, o .NET usará os dados do ReadyToRun quando ele estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="40b8e-174">If you omit this setting, .NET uses ReadyToRun data when it's available.</span></span> <span data-ttu-id="40b8e-175">Isso é equivalente a definir o valor como `1` .</span><span class="sxs-lookup"><span data-stu-id="40b8e-175">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="40b8e-176">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="40b8e-176">Setting name</span></span> | <span data-ttu-id="40b8e-177">Valores</span><span class="sxs-lookup"><span data-stu-id="40b8e-177">Values</span></span> |
| - | - | - |
| <span data-ttu-id="40b8e-178">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="40b8e-178">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="40b8e-179">`1` -habilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-179">`1` - enabled</span></span><br/><span data-ttu-id="40b8e-180">`0` -desabilitado</span><span class="sxs-lookup"><span data-stu-id="40b8e-180">`0` - disabled</span></span> |
