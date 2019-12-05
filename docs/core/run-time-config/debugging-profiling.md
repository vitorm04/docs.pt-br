---
title: Depurando configurações de configuração de criação de perfil
description: Saiba mais sobre as configurações de tempo de execução que configuram a depuração e a criação de perfil para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802795"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="fb664-103">Opções de configuração de tempo de execução para depuração e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="fb664-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="fb664-104">Habilitar diagnósticos</span><span class="sxs-lookup"><span data-stu-id="fb664-104">Enable diagnostics</span></span>

- <span data-ttu-id="fb664-105">Configura se o depurador, o criador de perfil e o diagnóstico EventPipe estão habilitados ou desabilitados.</span><span class="sxs-lookup"><span data-stu-id="fb664-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="fb664-106">Padrão: habilitado (`1`).</span><span class="sxs-lookup"><span data-stu-id="fb664-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="fb664-107">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="fb664-107">Setting name</span></span> | <span data-ttu-id="fb664-108">Valores</span><span class="sxs-lookup"><span data-stu-id="fb664-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fb664-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fb664-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="fb664-110">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb664-110">N/A</span></span> | <span data-ttu-id="fb664-111">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb664-111">N/A</span></span> |
| <span data-ttu-id="fb664-112">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fb664-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="fb664-113">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="fb664-113">`1` - enabled</span></span><br/><span data-ttu-id="fb664-114">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="fb664-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="fb664-115">Habilitar criação de perfil</span><span class="sxs-lookup"><span data-stu-id="fb664-115">Enable profiling</span></span>

- <span data-ttu-id="fb664-116">Configura se a criação de perfil está habilitada para o processo em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="fb664-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="fb664-117">Padrão: desabilitado (`0`).</span><span class="sxs-lookup"><span data-stu-id="fb664-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="fb664-118">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="fb664-118">Setting name</span></span> | <span data-ttu-id="fb664-119">Valores</span><span class="sxs-lookup"><span data-stu-id="fb664-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fb664-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fb664-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="fb664-121">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb664-121">N/A</span></span> | <span data-ttu-id="fb664-122">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb664-122">N/A</span></span> |
| <span data-ttu-id="fb664-123">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fb664-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="fb664-124">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="fb664-124">`0` - disabled</span></span><br/><span data-ttu-id="fb664-125">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="fb664-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="fb664-126">GUID do criador de perfil</span><span class="sxs-lookup"><span data-stu-id="fb664-126">Profiler GUID</span></span>

- <span data-ttu-id="fb664-127">Especifica o GUID do criador de perfil a ser carregado no processo em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="fb664-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="fb664-128">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="fb664-128">Setting name</span></span> | <span data-ttu-id="fb664-129">Valores</span><span class="sxs-lookup"><span data-stu-id="fb664-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fb664-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fb664-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="fb664-131">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb664-131">N/A</span></span> | <span data-ttu-id="fb664-132">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb664-132">N/A</span></span> |
| <span data-ttu-id="fb664-133">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fb664-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="fb664-134">*GUID de cadeia de caracteres*</span><span class="sxs-lookup"><span data-stu-id="fb664-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="fb664-135">Local do criador de perfil</span><span class="sxs-lookup"><span data-stu-id="fb664-135">Profiler location</span></span>

- <span data-ttu-id="fb664-136">Especifica o caminho para a DLL do criador de perfil a ser carregada no processo em execução no momento (ou no processo de 32 bits ou 64 bits).</span><span class="sxs-lookup"><span data-stu-id="fb664-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="fb664-137">Se mais de uma variável for definida, as variáveis específicas de bit de bits têm precedência.</span><span class="sxs-lookup"><span data-stu-id="fb664-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="fb664-138">Eles especificam qual bit de Profiler carregar.</span><span class="sxs-lookup"><span data-stu-id="fb664-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="fb664-139">Para obter mais informações, consulte [localizando a biblioteca do profiler](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="fb664-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="fb664-140">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="fb664-140">Setting name</span></span> | <span data-ttu-id="fb664-141">Valores</span><span class="sxs-lookup"><span data-stu-id="fb664-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fb664-142">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fb664-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="fb664-143">*Cadeia de caracteres-caminho*</span><span class="sxs-lookup"><span data-stu-id="fb664-143">*string-path*</span></span> |
| <span data-ttu-id="fb664-144">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fb664-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="fb664-145">*Cadeia de caracteres-caminho*</span><span class="sxs-lookup"><span data-stu-id="fb664-145">*string-path*</span></span> |
| <span data-ttu-id="fb664-146">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fb664-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="fb664-147">*Cadeia de caracteres-caminho*</span><span class="sxs-lookup"><span data-stu-id="fb664-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="fb664-148">Gravar mapa de desempenho</span><span class="sxs-lookup"><span data-stu-id="fb664-148">Write perf map</span></span>

- <span data-ttu-id="fb664-149">Habilita ou desabilita a gravação de */tmp/perf-$PID. map* em sistemas Linux.</span><span class="sxs-lookup"><span data-stu-id="fb664-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="fb664-150">Padrão: desabilitado (`0`).</span><span class="sxs-lookup"><span data-stu-id="fb664-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="fb664-151">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="fb664-151">Setting name</span></span> | <span data-ttu-id="fb664-152">Valores</span><span class="sxs-lookup"><span data-stu-id="fb664-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fb664-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fb664-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="fb664-154">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb664-154">N/A</span></span> | <span data-ttu-id="fb664-155">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb664-155">N/A</span></span> |
| <span data-ttu-id="fb664-156">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fb664-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="fb664-157">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="fb664-157">`0` - disabled</span></span><br/><span data-ttu-id="fb664-158">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="fb664-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="fb664-159">Marcadores de log de desempenho</span><span class="sxs-lookup"><span data-stu-id="fb664-159">Perf log markers</span></span>

- <span data-ttu-id="fb664-160">Quando `COMPlus_PerfMapEnabled` é definido como `1`, habilita ou desabilita o sinal especificado a ser aceito e ignorado como um marcador nos logs de desempenho.</span><span class="sxs-lookup"><span data-stu-id="fb664-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="fb664-161">Padrão: desabilitado (`0`).</span><span class="sxs-lookup"><span data-stu-id="fb664-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="fb664-162">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="fb664-162">Setting name</span></span> | <span data-ttu-id="fb664-163">Valores</span><span class="sxs-lookup"><span data-stu-id="fb664-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fb664-164">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fb664-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="fb664-165">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb664-165">N/A</span></span> | <span data-ttu-id="fb664-166">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb664-166">N/A</span></span> |
| <span data-ttu-id="fb664-167">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fb664-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="fb664-168">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="fb664-168">`0` - disabled</span></span><br/><span data-ttu-id="fb664-169">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="fb664-169">`1` - enabled</span></span> |
