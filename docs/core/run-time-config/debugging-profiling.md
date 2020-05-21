---
title: Depurando configurações de configuração de criação de perfil
description: Saiba mais sobre as configurações de tempo de execução que configuram a depuração e a criação de perfil para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761987"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="6268f-103">Opções de configuração de tempo de execução para depuração e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6268f-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="6268f-104">Habilitar diagnósticos</span><span class="sxs-lookup"><span data-stu-id="6268f-104">Enable diagnostics</span></span>

- <span data-ttu-id="6268f-105">Configura se o depurador, o criador de perfil e o diagnóstico EventPipe estão habilitados ou desabilitados.</span><span class="sxs-lookup"><span data-stu-id="6268f-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="6268f-106">Se você omitir essa configuração, os diagnósticos serão habilitados.</span><span class="sxs-lookup"><span data-stu-id="6268f-106">If you omit this setting, diagnostics are enabled.</span></span> <span data-ttu-id="6268f-107">Isso é equivalente a definir o valor como `1` .</span><span class="sxs-lookup"><span data-stu-id="6268f-107">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="6268f-108">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="6268f-108">Setting name</span></span> | <span data-ttu-id="6268f-109">Valores</span><span class="sxs-lookup"><span data-stu-id="6268f-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6268f-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6268f-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="6268f-111">N/D</span><span class="sxs-lookup"><span data-stu-id="6268f-111">N/A</span></span> | <span data-ttu-id="6268f-112">N/D</span><span class="sxs-lookup"><span data-stu-id="6268f-112">N/A</span></span> |
| <span data-ttu-id="6268f-113">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="6268f-113">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="6268f-114">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="6268f-114">`1` - enabled</span></span><br/><span data-ttu-id="6268f-115">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="6268f-115">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="6268f-116">Habilitar criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6268f-116">Enable profiling</span></span>

- <span data-ttu-id="6268f-117">Configura se a criação de perfil está habilitada para o processo em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="6268f-117">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="6268f-118">Se você omitir essa configuração, a criação de perfil será desabilitada.</span><span class="sxs-lookup"><span data-stu-id="6268f-118">If you omit this setting, profiling is disabled.</span></span> <span data-ttu-id="6268f-119">Isso é equivalente a definir o valor como `0` .</span><span class="sxs-lookup"><span data-stu-id="6268f-119">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="6268f-120">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="6268f-120">Setting name</span></span> | <span data-ttu-id="6268f-121">Valores</span><span class="sxs-lookup"><span data-stu-id="6268f-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6268f-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6268f-122">**runtimeconfig.json**</span></span> | <span data-ttu-id="6268f-123">N/D</span><span class="sxs-lookup"><span data-stu-id="6268f-123">N/A</span></span> | <span data-ttu-id="6268f-124">N/D</span><span class="sxs-lookup"><span data-stu-id="6268f-124">N/A</span></span> |
| <span data-ttu-id="6268f-125">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="6268f-125">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="6268f-126">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="6268f-126">`0` - disabled</span></span><br/><span data-ttu-id="6268f-127">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="6268f-127">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="6268f-128">GUID do criador de perfil</span><span class="sxs-lookup"><span data-stu-id="6268f-128">Profiler GUID</span></span>

- <span data-ttu-id="6268f-129">Especifica o GUID do criador de perfil a ser carregado no processo em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="6268f-129">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="6268f-130">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="6268f-130">Setting name</span></span> | <span data-ttu-id="6268f-131">Valores</span><span class="sxs-lookup"><span data-stu-id="6268f-131">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6268f-132">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6268f-132">**runtimeconfig.json**</span></span> | <span data-ttu-id="6268f-133">N/D</span><span class="sxs-lookup"><span data-stu-id="6268f-133">N/A</span></span> | <span data-ttu-id="6268f-134">N/D</span><span class="sxs-lookup"><span data-stu-id="6268f-134">N/A</span></span> |
| <span data-ttu-id="6268f-135">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="6268f-135">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="6268f-136">*GUID de cadeia de caracteres*</span><span class="sxs-lookup"><span data-stu-id="6268f-136">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="6268f-137">Local do criador de perfil</span><span class="sxs-lookup"><span data-stu-id="6268f-137">Profiler location</span></span>

- <span data-ttu-id="6268f-138">Especifica o caminho para a DLL do criador de perfil a ser carregada no processo em execução no momento (ou no processo de 32 bits ou 64 bits).</span><span class="sxs-lookup"><span data-stu-id="6268f-138">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="6268f-139">Se mais de uma variável for definida, as variáveis específicas de bit de bits têm precedência.</span><span class="sxs-lookup"><span data-stu-id="6268f-139">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="6268f-140">Eles especificam qual bit de Profiler carregar.</span><span class="sxs-lookup"><span data-stu-id="6268f-140">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="6268f-141">Para obter mais informações, consulte [localizando a biblioteca do profiler](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="6268f-141">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="6268f-142">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="6268f-142">Setting name</span></span> | <span data-ttu-id="6268f-143">Valores</span><span class="sxs-lookup"><span data-stu-id="6268f-143">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6268f-144">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="6268f-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="6268f-145">*Cadeia de caracteres-caminho*</span><span class="sxs-lookup"><span data-stu-id="6268f-145">*string-path*</span></span> |
| <span data-ttu-id="6268f-146">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="6268f-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="6268f-147">*Cadeia de caracteres-caminho*</span><span class="sxs-lookup"><span data-stu-id="6268f-147">*string-path*</span></span> |
| <span data-ttu-id="6268f-148">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="6268f-148">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="6268f-149">*Cadeia de caracteres-caminho*</span><span class="sxs-lookup"><span data-stu-id="6268f-149">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="6268f-150">Gravar mapa de desempenho</span><span class="sxs-lookup"><span data-stu-id="6268f-150">Write perf map</span></span>

- <span data-ttu-id="6268f-151">Habilita ou desabilita a gravação de */tmp/perf-$PID. map* em sistemas Linux.</span><span class="sxs-lookup"><span data-stu-id="6268f-151">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="6268f-152">Se você omitir essa configuração, a gravação do mapa de desempenho será desabilitada.</span><span class="sxs-lookup"><span data-stu-id="6268f-152">If you omit this setting, writing the perf map is disabled.</span></span> <span data-ttu-id="6268f-153">Isso é equivalente a definir o valor como `0` .</span><span class="sxs-lookup"><span data-stu-id="6268f-153">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="6268f-154">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="6268f-154">Setting name</span></span> | <span data-ttu-id="6268f-155">Valores</span><span class="sxs-lookup"><span data-stu-id="6268f-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6268f-156">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6268f-156">**runtimeconfig.json**</span></span> | <span data-ttu-id="6268f-157">N/D</span><span class="sxs-lookup"><span data-stu-id="6268f-157">N/A</span></span> | <span data-ttu-id="6268f-158">N/D</span><span class="sxs-lookup"><span data-stu-id="6268f-158">N/A</span></span> |
| <span data-ttu-id="6268f-159">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="6268f-159">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="6268f-160">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="6268f-160">`0` - disabled</span></span><br/><span data-ttu-id="6268f-161">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="6268f-161">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="6268f-162">Marcadores de log de desempenho</span><span class="sxs-lookup"><span data-stu-id="6268f-162">Perf log markers</span></span>

- <span data-ttu-id="6268f-163">Habilita ou desabilita o sinal especificado a ser aceito e ignorado como um marcador nos logs de desempenho.</span><span class="sxs-lookup"><span data-stu-id="6268f-163">Enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="6268f-164">Se você omitir essa configuração, o sinal especificado não será ignorado.</span><span class="sxs-lookup"><span data-stu-id="6268f-164">If you omit this setting, the specified signal is not ignored.</span></span> <span data-ttu-id="6268f-165">Isso é equivalente a definir o valor como `0` .</span><span class="sxs-lookup"><span data-stu-id="6268f-165">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="6268f-166">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="6268f-166">Setting name</span></span> | <span data-ttu-id="6268f-167">Valores</span><span class="sxs-lookup"><span data-stu-id="6268f-167">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6268f-168">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6268f-168">**runtimeconfig.json**</span></span> | <span data-ttu-id="6268f-169">N/D</span><span class="sxs-lookup"><span data-stu-id="6268f-169">N/A</span></span> | <span data-ttu-id="6268f-170">N/D</span><span class="sxs-lookup"><span data-stu-id="6268f-170">N/A</span></span> |
| <span data-ttu-id="6268f-171">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="6268f-171">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="6268f-172">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="6268f-172">`0` - disabled</span></span><br/><span data-ttu-id="6268f-173">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="6268f-173">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="6268f-174">Essa configuração será ignorada se [COMPlus_PerfMapEnabled](#write-perf-map) for omitida ou definida como `0` (ou seja, desabilitada).</span><span class="sxs-lookup"><span data-stu-id="6268f-174">This setting is ignored if [COMPlus_PerfMapEnabled](#write-perf-map) is omitted or set to `0` (that is, disabled).</span></span>
