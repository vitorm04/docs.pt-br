---
title: Depuração configurações de configuração de configuração de perfil
description: Saiba mais sobre as configurações de tempo de execução que configuram a depuração e o perfil dos aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802795"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="7d3eb-103">Opções de configuração em tempo de execução para depuração e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7d3eb-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="7d3eb-104">Habilitar diagnósticos</span><span class="sxs-lookup"><span data-stu-id="7d3eb-104">Enable diagnostics</span></span>

- <span data-ttu-id="7d3eb-105">Configura se o depurador, o profiler e o diagnóstico EventPipe estão ativados ou desativados.</span><span class="sxs-lookup"><span data-stu-id="7d3eb-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="7d3eb-106">Padrão: Ativado`1`().</span><span class="sxs-lookup"><span data-stu-id="7d3eb-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="7d3eb-107">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d3eb-107">Setting name</span></span> | <span data-ttu-id="7d3eb-108">Valores</span><span class="sxs-lookup"><span data-stu-id="7d3eb-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7d3eb-109">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="7d3eb-110">N/D</span><span class="sxs-lookup"><span data-stu-id="7d3eb-110">N/A</span></span> | <span data-ttu-id="7d3eb-111">N/D</span><span class="sxs-lookup"><span data-stu-id="7d3eb-111">N/A</span></span> |
| <span data-ttu-id="7d3eb-112">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="7d3eb-113">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="7d3eb-113">`1` - enabled</span></span><br/><span data-ttu-id="7d3eb-114">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="7d3eb-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="7d3eb-115">Habilitar criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7d3eb-115">Enable profiling</span></span>

- <span data-ttu-id="7d3eb-116">Configura se o perfil está ativado para o processo em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="7d3eb-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="7d3eb-117">Padrão: Desabilitado ( ).`0`</span><span class="sxs-lookup"><span data-stu-id="7d3eb-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="7d3eb-118">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d3eb-118">Setting name</span></span> | <span data-ttu-id="7d3eb-119">Valores</span><span class="sxs-lookup"><span data-stu-id="7d3eb-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7d3eb-120">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="7d3eb-121">N/D</span><span class="sxs-lookup"><span data-stu-id="7d3eb-121">N/A</span></span> | <span data-ttu-id="7d3eb-122">N/D</span><span class="sxs-lookup"><span data-stu-id="7d3eb-122">N/A</span></span> |
| <span data-ttu-id="7d3eb-123">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="7d3eb-124">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="7d3eb-124">`0` - disabled</span></span><br/><span data-ttu-id="7d3eb-125">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="7d3eb-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="7d3eb-126">GUIA DO Profiler</span><span class="sxs-lookup"><span data-stu-id="7d3eb-126">Profiler GUID</span></span>

- <span data-ttu-id="7d3eb-127">Especifica o GUID do profiler para carregar no processo em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="7d3eb-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="7d3eb-128">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d3eb-128">Setting name</span></span> | <span data-ttu-id="7d3eb-129">Valores</span><span class="sxs-lookup"><span data-stu-id="7d3eb-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7d3eb-130">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="7d3eb-131">N/D</span><span class="sxs-lookup"><span data-stu-id="7d3eb-131">N/A</span></span> | <span data-ttu-id="7d3eb-132">N/D</span><span class="sxs-lookup"><span data-stu-id="7d3eb-132">N/A</span></span> |
| <span data-ttu-id="7d3eb-133">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="7d3eb-134">*string-guid*</span><span class="sxs-lookup"><span data-stu-id="7d3eb-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="7d3eb-135">Localização do profiler</span><span class="sxs-lookup"><span data-stu-id="7d3eb-135">Profiler location</span></span>

- <span data-ttu-id="7d3eb-136">Especifica o caminho para o dLL do profiler para carregar no processo em execução atual (ou processo de 32 bits ou 64 bits).</span><span class="sxs-lookup"><span data-stu-id="7d3eb-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="7d3eb-137">Se mais de uma variável for definida, as variáveis específicas da bitness têm precedência.</span><span class="sxs-lookup"><span data-stu-id="7d3eb-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="7d3eb-138">Eles especificam qual bitness do profiler carregar.</span><span class="sxs-lookup"><span data-stu-id="7d3eb-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="7d3eb-139">Para obter mais informações, consulte [Encontrar a biblioteca profiler](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="7d3eb-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="7d3eb-140">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d3eb-140">Setting name</span></span> | <span data-ttu-id="7d3eb-141">Valores</span><span class="sxs-lookup"><span data-stu-id="7d3eb-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7d3eb-142">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="7d3eb-143">*string-path*</span><span class="sxs-lookup"><span data-stu-id="7d3eb-143">*string-path*</span></span> |
| <span data-ttu-id="7d3eb-144">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="7d3eb-145">*string-path*</span><span class="sxs-lookup"><span data-stu-id="7d3eb-145">*string-path*</span></span> |
| <span data-ttu-id="7d3eb-146">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="7d3eb-147">*string-path*</span><span class="sxs-lookup"><span data-stu-id="7d3eb-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="7d3eb-148">Escrever mapa perf</span><span class="sxs-lookup"><span data-stu-id="7d3eb-148">Write perf map</span></span>

- <span data-ttu-id="7d3eb-149">Ativa ou desativa a escrita */tmp/perf-$pid.map* nos sistemas Linux.</span><span class="sxs-lookup"><span data-stu-id="7d3eb-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="7d3eb-150">Padrão: Desabilitado ( ).`0`</span><span class="sxs-lookup"><span data-stu-id="7d3eb-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="7d3eb-151">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d3eb-151">Setting name</span></span> | <span data-ttu-id="7d3eb-152">Valores</span><span class="sxs-lookup"><span data-stu-id="7d3eb-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7d3eb-153">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="7d3eb-154">N/D</span><span class="sxs-lookup"><span data-stu-id="7d3eb-154">N/A</span></span> | <span data-ttu-id="7d3eb-155">N/D</span><span class="sxs-lookup"><span data-stu-id="7d3eb-155">N/A</span></span> |
| <span data-ttu-id="7d3eb-156">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="7d3eb-157">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="7d3eb-157">`0` - disabled</span></span><br/><span data-ttu-id="7d3eb-158">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="7d3eb-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="7d3eb-159">Marcadores de log perf</span><span class="sxs-lookup"><span data-stu-id="7d3eb-159">Perf log markers</span></span>

- <span data-ttu-id="7d3eb-160">Quando `COMPlus_PerfMapEnabled` estiver `1`definido para , habilita ou desativa o sinal especificado a ser aceito e ignorado como um marcador nos logs perf.</span><span class="sxs-lookup"><span data-stu-id="7d3eb-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="7d3eb-161">Padrão: Desabilitado ( ).`0`</span><span class="sxs-lookup"><span data-stu-id="7d3eb-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="7d3eb-162">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="7d3eb-162">Setting name</span></span> | <span data-ttu-id="7d3eb-163">Valores</span><span class="sxs-lookup"><span data-stu-id="7d3eb-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7d3eb-164">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="7d3eb-165">N/D</span><span class="sxs-lookup"><span data-stu-id="7d3eb-165">N/A</span></span> | <span data-ttu-id="7d3eb-166">N/D</span><span class="sxs-lookup"><span data-stu-id="7d3eb-166">N/A</span></span> |
| <span data-ttu-id="7d3eb-167">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="7d3eb-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="7d3eb-168">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="7d3eb-168">`0` - disabled</span></span><br/><span data-ttu-id="7d3eb-169">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="7d3eb-169">`1` - enabled</span></span> |
