---
title: Dependências de SDK do .NET Core e tempo de execução-.NET Core
description: Detalha o sistema operacional e os pré-requisitos de arquitetura de CPU para instalar o SDK do .NET Core e o tempo de execução no Windows, Linux e macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 4164ea5a04d80ab20109168a225b793b02ee616a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448887"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="08105-103">Dependências e requisitos do .NET Core</span><span class="sxs-lookup"><span data-stu-id="08105-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="08105-104">Este artigo detalha quais sistemas operacionais e arquitetura de CPU têm suporte no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="08105-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="08105-105">Sistemas operacionais compatíveis</span><span class="sxs-lookup"><span data-stu-id="08105-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="08105-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="08105-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="08105-107">As seguintes versões do Windows têm suporte com o .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="08105-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="08105-108">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="08105-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="08105-109">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="08105-109">OS</span></span>                            | <span data-ttu-id="08105-110">Versão</span><span class="sxs-lookup"><span data-stu-id="08105-110">Version</span></span>                        | <span data-ttu-id="08105-111">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="08105-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="08105-112">Windows Client</span><span class="sxs-lookup"><span data-stu-id="08105-112">Windows Client</span></span>                | <span data-ttu-id="08105-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="08105-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="08105-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-114">x64, x86</span></span>        |
| <span data-ttu-id="08105-115">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="08105-115">Windows 10 Client</span></span>             | <span data-ttu-id="08105-116">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="08105-116">Version 1607+</span></span>                  | <span data-ttu-id="08105-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-117">x64, x86</span></span>        |
| <span data-ttu-id="08105-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="08105-118">Windows Server</span></span>                | <span data-ttu-id="08105-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="08105-119">2012 R2+</span></span>                       | <span data-ttu-id="08105-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-120">x64, x86</span></span>        |
| <span data-ttu-id="08105-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="08105-121">Nano Server</span></span>                   | <span data-ttu-id="08105-122">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="08105-122">Version 1803+</span></span>                  | <span data-ttu-id="08105-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="08105-123">x64, ARM32</span></span>      |

<span data-ttu-id="08105-124">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,1, consulte [versões do sistema operacional .net core 3,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="08105-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="08105-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="08105-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="08105-126">As seguintes versões do Windows têm suporte com o .NET Core 3,0:</span><span class="sxs-lookup"><span data-stu-id="08105-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="08105-127">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="08105-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="08105-128">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="08105-128">OS</span></span>                            | <span data-ttu-id="08105-129">Versão</span><span class="sxs-lookup"><span data-stu-id="08105-129">Version</span></span>                        | <span data-ttu-id="08105-130">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="08105-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="08105-131">Windows Client</span><span class="sxs-lookup"><span data-stu-id="08105-131">Windows Client</span></span>                | <span data-ttu-id="08105-132">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="08105-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="08105-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-133">x64, x86</span></span>        |
| <span data-ttu-id="08105-134">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="08105-134">Windows 10 Client</span></span>             | <span data-ttu-id="08105-135">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="08105-135">Version 1607+</span></span>                  | <span data-ttu-id="08105-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-136">x64, x86</span></span>        |
| <span data-ttu-id="08105-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="08105-137">Windows Server</span></span>                | <span data-ttu-id="08105-138">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="08105-138">2012 R2+</span></span>                       | <span data-ttu-id="08105-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-139">x64, x86</span></span>        |
| <span data-ttu-id="08105-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="08105-140">Nano Server</span></span>                   | <span data-ttu-id="08105-141">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="08105-141">Version 1803+</span></span>                  | <span data-ttu-id="08105-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="08105-142">x64, ARM32</span></span>      |

<span data-ttu-id="08105-143">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,0, consulte [versões do sistema operacional .net core 3,0 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="08105-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="08105-144">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="08105-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="08105-145">As seguintes versões do Windows têm suporte com o .NET Core 2,2:</span><span class="sxs-lookup"><span data-stu-id="08105-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="08105-146">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="08105-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="08105-147">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="08105-147">OS</span></span>                            | <span data-ttu-id="08105-148">Versão</span><span class="sxs-lookup"><span data-stu-id="08105-148">Version</span></span>                        | <span data-ttu-id="08105-149">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="08105-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="08105-150">Windows Client</span><span class="sxs-lookup"><span data-stu-id="08105-150">Windows Client</span></span>                | <span data-ttu-id="08105-151">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="08105-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="08105-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-152">x64, x86</span></span>        |
| <span data-ttu-id="08105-153">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="08105-153">Windows 10 Client</span></span>             | <span data-ttu-id="08105-154">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="08105-154">Version 1607+</span></span>                  | <span data-ttu-id="08105-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-155">x64, x86</span></span>        |
| <span data-ttu-id="08105-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="08105-156">Windows Server</span></span>                | <span data-ttu-id="08105-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="08105-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="08105-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-158">x64, x86</span></span>        |
| <span data-ttu-id="08105-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="08105-159">Nano Server</span></span>                   | <span data-ttu-id="08105-160">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="08105-160">Version 1803+</span></span>                   | <span data-ttu-id="08105-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="08105-161">x64, ARM32</span></span>      |

<span data-ttu-id="08105-162">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,2, consulte [versões do sistema operacional .net core 2,2 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="08105-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="08105-163">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="08105-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="08105-164">As seguintes versões do Windows têm suporte com o .NET Core 2,1:</span><span class="sxs-lookup"><span data-stu-id="08105-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="08105-165">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="08105-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="08105-166">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="08105-166">OS</span></span>                            | <span data-ttu-id="08105-167">Versão</span><span class="sxs-lookup"><span data-stu-id="08105-167">Version</span></span>                        | <span data-ttu-id="08105-168">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="08105-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="08105-169">Windows Client</span><span class="sxs-lookup"><span data-stu-id="08105-169">Windows Client</span></span>                | <span data-ttu-id="08105-170">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="08105-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="08105-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-171">x64, x86</span></span>        |
| <span data-ttu-id="08105-172">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="08105-172">Windows 10 Client</span></span>             | <span data-ttu-id="08105-173">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="08105-173">Version 1607+</span></span>                  | <span data-ttu-id="08105-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-174">x64, x86</span></span>        |
| <span data-ttu-id="08105-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="08105-175">Windows Server</span></span>                | <span data-ttu-id="08105-176">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="08105-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="08105-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="08105-177">x64, x86</span></span>        |
| <span data-ttu-id="08105-178">Nano Server</span><span class="sxs-lookup"><span data-stu-id="08105-178">Nano Server</span></span>                   | <span data-ttu-id="08105-179">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="08105-179">Version 1803+</span></span>                  | <span data-ttu-id="08105-180">x86</span><span class="sxs-lookup"><span data-stu-id="08105-180">x64,</span></span>            |

<span data-ttu-id="08105-181">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,1, consulte [versões do sistema operacional .net core 2,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="08105-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="08105-182">Windows 7/Vista/8,1/servidor 2008 R2</span><span class="sxs-lookup"><span data-stu-id="08105-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="08105-183">Dependências adicionais serão necessárias se você estiver instalando o SDK do .NET ou o tempo de execução nas seguintes versões do Windows:</span><span class="sxs-lookup"><span data-stu-id="08105-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="08105-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="08105-184">Windows 7 SP1</span></span>
- <span data-ttu-id="08105-185">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="08105-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="08105-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="08105-186">Windows 8.1</span></span>
- <span data-ttu-id="08105-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="08105-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="08105-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="08105-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="08105-189">Instale o seguinte:</span><span class="sxs-lookup"><span data-stu-id="08105-189">Install the following:</span></span>

- <span data-ttu-id="08105-190">[Atualização 3 C++ do Microsoft Visual 2015 redistribuível](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="08105-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="08105-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="08105-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="08105-192">Os requisitos acima também serão necessários se você vir entre um dos seguintes erros:</span><span class="sxs-lookup"><span data-stu-id="08105-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="08105-193">O programa não pode ser iniciado porque *API-MS-Win-CRT-Runtime-L1-1-0. dll* está ausente do seu computador.</span><span class="sxs-lookup"><span data-stu-id="08105-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="08105-194">Tente reinstalar o programa para corrigir esse problema.</span><span class="sxs-lookup"><span data-stu-id="08105-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="08105-195">\- ou –</span><span class="sxs-lookup"><span data-stu-id="08105-195">\- or -</span></span>
>
> <span data-ttu-id="08105-196">A biblioteca *hostfxr. dll* foi encontrada, mas está sendo carregada de *C:\\\<path_to_app >\\hostfxr. dll* falhou.</span><span class="sxs-lookup"><span data-stu-id="08105-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="08105-197">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="08105-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="08105-198">O .NET Core 3,1 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="08105-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="08105-199">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="08105-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="08105-200">O .NET Core 3,1 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="08105-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="08105-201">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="08105-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="08105-202">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="08105-202">OS</span></span>                             | <span data-ttu-id="08105-203">Versão</span><span class="sxs-lookup"><span data-stu-id="08105-203">Version</span></span>               | <span data-ttu-id="08105-204">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="08105-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="08105-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="08105-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="08105-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="08105-206">6, 7, 8</span></span>               | <span data-ttu-id="08105-207">x64</span><span class="sxs-lookup"><span data-stu-id="08105-207">x64</span></span> |
| <span data-ttu-id="08105-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="08105-208">CentOS</span></span>                         | <span data-ttu-id="08105-209">7+</span><span class="sxs-lookup"><span data-stu-id="08105-209">7+</span></span>                    | <span data-ttu-id="08105-210">x64</span><span class="sxs-lookup"><span data-stu-id="08105-210">x64</span></span> |
| <span data-ttu-id="08105-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="08105-211">Oracle Linux</span></span>                   | <span data-ttu-id="08105-212">7+</span><span class="sxs-lookup"><span data-stu-id="08105-212">7+</span></span>                    | <span data-ttu-id="08105-213">x64</span><span class="sxs-lookup"><span data-stu-id="08105-213">x64</span></span> |
| <span data-ttu-id="08105-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="08105-214">Fedora</span></span>                         | <span data-ttu-id="08105-215">29 +</span><span class="sxs-lookup"><span data-stu-id="08105-215">29+</span></span>                   | <span data-ttu-id="08105-216">x64</span><span class="sxs-lookup"><span data-stu-id="08105-216">x64</span></span> |
| <span data-ttu-id="08105-217">Debian</span><span class="sxs-lookup"><span data-stu-id="08105-217">Debian</span></span>                         | <span data-ttu-id="08105-218">9 e posterior</span><span class="sxs-lookup"><span data-stu-id="08105-218">9+</span></span>                    | <span data-ttu-id="08105-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="08105-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="08105-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="08105-220">Ubuntu</span></span>                         | <span data-ttu-id="08105-221">16.04+</span><span class="sxs-lookup"><span data-stu-id="08105-221">16.04+</span></span>                | <span data-ttu-id="08105-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="08105-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="08105-223">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="08105-223">Linux Mint</span></span>                     | <span data-ttu-id="08105-224">mais de 18 anos</span><span class="sxs-lookup"><span data-stu-id="08105-224">18+</span></span>                   | <span data-ttu-id="08105-225">x64</span><span class="sxs-lookup"><span data-stu-id="08105-225">x64</span></span> |
| <span data-ttu-id="08105-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="08105-226">openSUSE</span></span>                       | <span data-ttu-id="08105-227">15 +</span><span class="sxs-lookup"><span data-stu-id="08105-227">15+</span></span>                   | <span data-ttu-id="08105-228">x64</span><span class="sxs-lookup"><span data-stu-id="08105-228">x64</span></span> |
| <span data-ttu-id="08105-229">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="08105-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="08105-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="08105-230">12 SP2+</span></span>               | <span data-ttu-id="08105-231">x64</span><span class="sxs-lookup"><span data-stu-id="08105-231">x64</span></span> |
| <span data-ttu-id="08105-232">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="08105-232">Alpine Linux</span></span>                   | <span data-ttu-id="08105-233">3.10 +</span><span class="sxs-lookup"><span data-stu-id="08105-233">3.10+</span></span>                 | <span data-ttu-id="08105-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="08105-234">x64, ARM64</span></span> |

<span data-ttu-id="08105-235">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,1, consulte [versões do sistema operacional .net core 3,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="08105-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="08105-236">Para obter mais informações sobre como instalar o .NET Core 3,1 em ARM64 (kernel 4.14 +), consulte [instalando o .net core 3,0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="08105-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08105-237">O suporte a ARM64 requer o kernel do Linux 4,14 ou superior.</span><span class="sxs-lookup"><span data-stu-id="08105-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="08105-238">Algumas distribuições do Linux atendem a esse requisito, enquanto outras não.</span><span class="sxs-lookup"><span data-stu-id="08105-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="08105-239">Por exemplo, o Ubuntu 18, 4 tem suporte, mas o Ubuntu 16, 4 não.</span><span class="sxs-lookup"><span data-stu-id="08105-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="08105-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="08105-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="08105-241">O .NET Core 3,0 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="08105-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="08105-242">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="08105-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="08105-243">O .NET Core 3,0 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="08105-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="08105-244">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="08105-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="08105-245">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="08105-245">OS</span></span>                             | <span data-ttu-id="08105-246">Versão</span><span class="sxs-lookup"><span data-stu-id="08105-246">Version</span></span>               | <span data-ttu-id="08105-247">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="08105-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="08105-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="08105-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="08105-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="08105-249">6, 7, 8</span></span>               | <span data-ttu-id="08105-250">x64</span><span class="sxs-lookup"><span data-stu-id="08105-250">x64</span></span> |
| <span data-ttu-id="08105-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="08105-251">CentOS</span></span>                         | <span data-ttu-id="08105-252">7+</span><span class="sxs-lookup"><span data-stu-id="08105-252">7+</span></span>                    | <span data-ttu-id="08105-253">x64</span><span class="sxs-lookup"><span data-stu-id="08105-253">x64</span></span> |
| <span data-ttu-id="08105-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="08105-254">Oracle Linux</span></span>                   | <span data-ttu-id="08105-255">7+</span><span class="sxs-lookup"><span data-stu-id="08105-255">7+</span></span>                    | <span data-ttu-id="08105-256">x64</span><span class="sxs-lookup"><span data-stu-id="08105-256">x64</span></span> |
| <span data-ttu-id="08105-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="08105-257">Fedora</span></span>                         | <span data-ttu-id="08105-258">29 +</span><span class="sxs-lookup"><span data-stu-id="08105-258">29+</span></span>                   | <span data-ttu-id="08105-259">x64</span><span class="sxs-lookup"><span data-stu-id="08105-259">x64</span></span> |
| <span data-ttu-id="08105-260">Debian</span><span class="sxs-lookup"><span data-stu-id="08105-260">Debian</span></span>                         | <span data-ttu-id="08105-261">9 e posterior</span><span class="sxs-lookup"><span data-stu-id="08105-261">9+</span></span>                    | <span data-ttu-id="08105-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="08105-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="08105-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="08105-263">Ubuntu</span></span>                         | <span data-ttu-id="08105-264">16.04+</span><span class="sxs-lookup"><span data-stu-id="08105-264">16.04+</span></span>                | <span data-ttu-id="08105-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="08105-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="08105-266">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="08105-266">Linux Mint</span></span>                     | <span data-ttu-id="08105-267">mais de 18 anos</span><span class="sxs-lookup"><span data-stu-id="08105-267">18+</span></span>                   | <span data-ttu-id="08105-268">x64</span><span class="sxs-lookup"><span data-stu-id="08105-268">x64</span></span> |
| <span data-ttu-id="08105-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="08105-269">openSUSE</span></span>                       | <span data-ttu-id="08105-270">15 +</span><span class="sxs-lookup"><span data-stu-id="08105-270">15+</span></span>                   | <span data-ttu-id="08105-271">x64</span><span class="sxs-lookup"><span data-stu-id="08105-271">x64</span></span> |
| <span data-ttu-id="08105-272">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="08105-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="08105-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="08105-273">12 SP2+</span></span>               | <span data-ttu-id="08105-274">x64</span><span class="sxs-lookup"><span data-stu-id="08105-274">x64</span></span> |
| <span data-ttu-id="08105-275">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="08105-275">Alpine Linux</span></span>                   | <span data-ttu-id="08105-276">3.8+</span><span class="sxs-lookup"><span data-stu-id="08105-276">3.8+</span></span>                  | <span data-ttu-id="08105-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="08105-277">x64, ARM64</span></span> |

<span data-ttu-id="08105-278">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,0, consulte [versões do sistema operacional .net core 3,0 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="08105-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="08105-279">Para obter mais informações sobre como instalar o .NET Core 3.0 no ARM64, confira [Instalando o .NET Core 3.0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="08105-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="08105-280">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="08105-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="08105-281">O .NET Core 2,2 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="08105-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="08105-282">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="08105-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="08105-283">O .NET Core 2,2 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="08105-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="08105-284">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="08105-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="08105-285">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="08105-285">OS</span></span>                             |  <span data-ttu-id="08105-286">Versão</span><span class="sxs-lookup"><span data-stu-id="08105-286">Version</span></span>                |  <span data-ttu-id="08105-287">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="08105-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="08105-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="08105-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="08105-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="08105-289">6, 7</span></span>                   | <span data-ttu-id="08105-290">x64</span><span class="sxs-lookup"><span data-stu-id="08105-290">x64</span></span> |
| <span data-ttu-id="08105-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="08105-291">CentOS</span></span>                         |  <span data-ttu-id="08105-292">7</span><span class="sxs-lookup"><span data-stu-id="08105-292">7</span></span>                      | <span data-ttu-id="08105-293">x64</span><span class="sxs-lookup"><span data-stu-id="08105-293">x64</span></span> |
| <span data-ttu-id="08105-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="08105-294">Oracle Linux</span></span>                   |  <span data-ttu-id="08105-295">7</span><span class="sxs-lookup"><span data-stu-id="08105-295">7</span></span>                      | <span data-ttu-id="08105-296">x64</span><span class="sxs-lookup"><span data-stu-id="08105-296">x64</span></span> |
| <span data-ttu-id="08105-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="08105-297">Fedora</span></span>                         |  <span data-ttu-id="08105-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="08105-298">29, 30</span></span>                 | <span data-ttu-id="08105-299">x64</span><span class="sxs-lookup"><span data-stu-id="08105-299">x64</span></span> |
| <span data-ttu-id="08105-300">Debian</span><span class="sxs-lookup"><span data-stu-id="08105-300">Debian</span></span>                         |  <span data-ttu-id="08105-301">9</span><span class="sxs-lookup"><span data-stu-id="08105-301">9</span></span>                      | <span data-ttu-id="08105-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="08105-302">x64, ARM32</span></span> |
| <span data-ttu-id="08105-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="08105-303">Ubuntu</span></span>                         |  <span data-ttu-id="08105-304">16, 4, 18, 4, 18,10</span><span class="sxs-lookup"><span data-stu-id="08105-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="08105-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="08105-305">x64, ARM32</span></span> |
| <span data-ttu-id="08105-306">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="08105-306">Linux Mint</span></span>                     |  <span data-ttu-id="08105-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="08105-307">17, 18</span></span>                 | <span data-ttu-id="08105-308">x64</span><span class="sxs-lookup"><span data-stu-id="08105-308">x64</span></span> |
| <span data-ttu-id="08105-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="08105-309">openSUSE</span></span>                       |  <span data-ttu-id="08105-310">15 +</span><span class="sxs-lookup"><span data-stu-id="08105-310">15+</span></span>                    | <span data-ttu-id="08105-311">x64</span><span class="sxs-lookup"><span data-stu-id="08105-311">x64</span></span> |
| <span data-ttu-id="08105-312">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="08105-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="08105-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="08105-313">12 SP2+</span></span>                | <span data-ttu-id="08105-314">x64</span><span class="sxs-lookup"><span data-stu-id="08105-314">x64</span></span> |
| <span data-ttu-id="08105-315">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="08105-315">Alpine Linux</span></span>                   |  <span data-ttu-id="08105-316">3.8+</span><span class="sxs-lookup"><span data-stu-id="08105-316">3.8+</span></span>                   | <span data-ttu-id="08105-317">x64</span><span class="sxs-lookup"><span data-stu-id="08105-317">x64</span></span> |

<span data-ttu-id="08105-318">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,2, consulte [versões do sistema operacional .net core 2,2 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="08105-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="08105-319">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="08105-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="08105-320">O .NET Core 2,1 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="08105-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="08105-321">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="08105-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="08105-322">O .NET Core 2,1 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="08105-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="08105-323">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="08105-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="08105-324">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="08105-324">OS</span></span>                             |  <span data-ttu-id="08105-325">Versão</span><span class="sxs-lookup"><span data-stu-id="08105-325">Version</span></span>                |  <span data-ttu-id="08105-326">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="08105-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="08105-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="08105-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="08105-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="08105-328">6, 7, 8</span></span>                | <span data-ttu-id="08105-329">x64</span><span class="sxs-lookup"><span data-stu-id="08105-329">x64</span></span> |
| <span data-ttu-id="08105-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="08105-330">CentOS</span></span>                         |  <span data-ttu-id="08105-331">7+</span><span class="sxs-lookup"><span data-stu-id="08105-331">7+</span></span>                     | <span data-ttu-id="08105-332">x64</span><span class="sxs-lookup"><span data-stu-id="08105-332">x64</span></span> |
| <span data-ttu-id="08105-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="08105-333">Oracle Linux</span></span>                   |  <span data-ttu-id="08105-334">7+</span><span class="sxs-lookup"><span data-stu-id="08105-334">7+</span></span>                     | <span data-ttu-id="08105-335">x64</span><span class="sxs-lookup"><span data-stu-id="08105-335">x64</span></span> |
| <span data-ttu-id="08105-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="08105-336">Fedora</span></span>                         |  <span data-ttu-id="08105-337">29 +</span><span class="sxs-lookup"><span data-stu-id="08105-337">29+</span></span>                    | <span data-ttu-id="08105-338">x64</span><span class="sxs-lookup"><span data-stu-id="08105-338">x64</span></span> |
| <span data-ttu-id="08105-339">Debian</span><span class="sxs-lookup"><span data-stu-id="08105-339">Debian</span></span>                         |  <span data-ttu-id="08105-340">9</span><span class="sxs-lookup"><span data-stu-id="08105-340">9</span></span>                      | <span data-ttu-id="08105-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="08105-341">x64, ARM32</span></span> |
| <span data-ttu-id="08105-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="08105-342">Ubuntu</span></span>                         |  <span data-ttu-id="08105-343">16, 4, 18, 4, 19, 4, 19,10</span><span class="sxs-lookup"><span data-stu-id="08105-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="08105-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="08105-344">x64, ARM32</span></span> |
| <span data-ttu-id="08105-345">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="08105-345">Linux Mint</span></span>                     |  <span data-ttu-id="08105-346">17 +</span><span class="sxs-lookup"><span data-stu-id="08105-346">17+</span></span>                    | <span data-ttu-id="08105-347">x64</span><span class="sxs-lookup"><span data-stu-id="08105-347">x64</span></span> |
| <span data-ttu-id="08105-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="08105-348">openSUSE</span></span>                       |  <span data-ttu-id="08105-349">15 +</span><span class="sxs-lookup"><span data-stu-id="08105-349">15+</span></span>                    | <span data-ttu-id="08105-350">x64</span><span class="sxs-lookup"><span data-stu-id="08105-350">x64</span></span> |
| <span data-ttu-id="08105-351">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="08105-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="08105-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="08105-352">12 SP2+</span></span>                | <span data-ttu-id="08105-353">x64</span><span class="sxs-lookup"><span data-stu-id="08105-353">x64</span></span> |
| <span data-ttu-id="08105-354">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="08105-354">Alpine Linux</span></span>                   |  <span data-ttu-id="08105-355">3.8+</span><span class="sxs-lookup"><span data-stu-id="08105-355">3.8+</span></span>                   | <span data-ttu-id="08105-356">x64</span><span class="sxs-lookup"><span data-stu-id="08105-356">x64</span></span> |

<span data-ttu-id="08105-357">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,1, consulte [versões do sistema operacional .net core 2,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="08105-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="08105-358">Dependências de distribuição do Linux</span><span class="sxs-lookup"><span data-stu-id="08105-358">Linux distribution dependencies</span></span>

<span data-ttu-id="08105-359">Com base em sua distribuição do Linux, talvez seja necessário instalar dependências adicionais.</span><span class="sxs-lookup"><span data-stu-id="08105-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08105-360">Os nomes e as versões exatas podem variar ligeiramente na distribuição Linux de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="08105-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="08105-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="08105-361">Ubuntu</span></span>

<span data-ttu-id="08105-362">As distribuições do Ubuntu exigem que as seguintes bibliotecas sejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="08105-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="08105-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="08105-363">liblttng-ust0</span></span>
- <span data-ttu-id="08105-364">libcurl3 (para 14.x e 16.x)</span><span class="sxs-lookup"><span data-stu-id="08105-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="08105-365">libcurl4 (para 18.x)</span><span class="sxs-lookup"><span data-stu-id="08105-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="08105-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="08105-366">libssl1.0.0</span></span>
- <span data-ttu-id="08105-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="08105-367">libkrb5-3</span></span>
- <span data-ttu-id="08105-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="08105-368">zlib1g</span></span>
- <span data-ttu-id="08105-369">libicu52 (para 14.x)</span><span class="sxs-lookup"><span data-stu-id="08105-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="08105-370">libicu55 (para 16.x)</span><span class="sxs-lookup"><span data-stu-id="08105-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="08105-371">libicu57 (para 17.x)</span><span class="sxs-lookup"><span data-stu-id="08105-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="08105-372">libicu60 (para 18.x)</span><span class="sxs-lookup"><span data-stu-id="08105-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="08105-373">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="08105-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="08105-374">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="08105-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="08105-375">A maioria das versões do Ubuntu inclui uma versão anterior do libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="08105-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="08105-376">Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="08105-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="08105-377">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="08105-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="08105-378">CentOS e Fedora</span><span class="sxs-lookup"><span data-stu-id="08105-378">CentOS and Fedora</span></span>

<span data-ttu-id="08105-379">As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="08105-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="08105-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="08105-380">lttng-ust</span></span>
- <span data-ttu-id="08105-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="08105-381">libcurl</span></span>
- <span data-ttu-id="08105-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="08105-382">openssl-libs</span></span>
- <span data-ttu-id="08105-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="08105-383">krb5-libs</span></span>
- <span data-ttu-id="08105-384">libicu</span><span class="sxs-lookup"><span data-stu-id="08105-384">libicu</span></span>
- <span data-ttu-id="08105-385">zlib</span><span class="sxs-lookup"><span data-stu-id="08105-385">zlib</span></span>

<span data-ttu-id="08105-386">Usuários do Fedora: se a versão do OpenSSL > = 1,1, você precisará instalar o **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="08105-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="08105-387">Para o .NET Core 2,0, as seguintes dependências também são necessárias:</span><span class="sxs-lookup"><span data-stu-id="08105-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="08105-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="08105-388">libunwind</span></span>
- <span data-ttu-id="08105-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="08105-389">libuuid</span></span>

<span data-ttu-id="08105-390">Para obter mais informações sobre as dependências, consulte [aplicativos do Linux autocontidos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="08105-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="08105-391">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="08105-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="08105-392">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="08105-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="08105-393">A maioria das versões do CentOS e do Fedora inclui uma versão anterior do libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="08105-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="08105-394">Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="08105-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="08105-395">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="08105-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="08105-396">O .NET Core tem suporte nas seguintes versões do macOS:</span><span class="sxs-lookup"><span data-stu-id="08105-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="08105-397">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="08105-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="08105-398">Versão do .NET Core</span><span class="sxs-lookup"><span data-stu-id="08105-398">.NET Core Version</span></span> | <span data-ttu-id="08105-399">macOS</span><span class="sxs-lookup"><span data-stu-id="08105-399">macOS</span></span>                 | <span data-ttu-id="08105-400">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="08105-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="08105-401">3.1</span><span class="sxs-lookup"><span data-stu-id="08105-401">3.1</span></span>               | <span data-ttu-id="08105-402">Alta serra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="08105-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="08105-403">x64</span><span class="sxs-lookup"><span data-stu-id="08105-403">x64</span></span> | [<span data-ttu-id="08105-404">Mais informações</span><span class="sxs-lookup"><span data-stu-id="08105-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="08105-405">3.0</span><span class="sxs-lookup"><span data-stu-id="08105-405">3.0</span></span>               | <span data-ttu-id="08105-406">Alta serra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="08105-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="08105-407">x64</span><span class="sxs-lookup"><span data-stu-id="08105-407">x64</span></span> | [<span data-ttu-id="08105-408">Mais informações</span><span class="sxs-lookup"><span data-stu-id="08105-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="08105-409">2.2</span><span class="sxs-lookup"><span data-stu-id="08105-409">2.2</span></span>               | <span data-ttu-id="08105-410">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="08105-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="08105-411">x64</span><span class="sxs-lookup"><span data-stu-id="08105-411">x64</span></span> | [<span data-ttu-id="08105-412">Mais informações</span><span class="sxs-lookup"><span data-stu-id="08105-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="08105-413">2.1</span><span class="sxs-lookup"><span data-stu-id="08105-413">2.1</span></span>               | <span data-ttu-id="08105-414">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="08105-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="08105-415">x64</span><span class="sxs-lookup"><span data-stu-id="08105-415">x64</span></span> | [<span data-ttu-id="08105-416">Mais informações</span><span class="sxs-lookup"><span data-stu-id="08105-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="08105-417">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="08105-417">libgdiplus</span></span>

<span data-ttu-id="08105-418">Os aplicativos .NET Core que usam o assembly *System. sorteio. Common* exigem que o libgdiplus seja instalado.</span><span class="sxs-lookup"><span data-stu-id="08105-418">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="08105-419">Uma maneira fácil de obter o libgdiplus é usando o Gerenciador de pacotes [homebrew ("Brew")](https://brew.sh/) para MacOS.</span><span class="sxs-lookup"><span data-stu-id="08105-419">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="08105-420">Depois de instalar o *Brew*, instale o libgdiplus executando os seguintes comandos em um prompt de terminal (comando):</span><span class="sxs-lookup"><span data-stu-id="08105-420">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="08105-421">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="08105-421">Next steps</span></span>

- <span data-ttu-id="08105-422">Para desenvolver e executar aplicativos, instale o [SDK do .NET Core](sdk.md) (inclui o tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="08105-422">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="08105-423">Para executar aplicativos que outras pessoas criaram, instale o [tempo de execução do .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="08105-423">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
