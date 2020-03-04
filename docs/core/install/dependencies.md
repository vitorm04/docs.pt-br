---
title: Dependências de SDK do .NET Core e tempo de execução-.NET Core
description: Detalha o sistema operacional e os pré-requisitos de arquitetura de CPU para instalar o SDK do .NET Core e o tempo de execução no Windows, Linux e macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157798"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="9f98c-103">Dependências e requisitos do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9f98c-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="9f98c-104">Este artigo detalha quais sistemas operacionais e arquitetura de CPU têm suporte no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9f98c-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="9f98c-105">Sistemas operacionais compatíveis</span><span class="sxs-lookup"><span data-stu-id="9f98c-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="9f98c-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="9f98c-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="9f98c-107">As seguintes versões do Windows têm suporte com o .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="9f98c-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="9f98c-108">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="9f98c-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9f98c-109">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9f98c-109">OS</span></span>                            | <span data-ttu-id="9f98c-110">Versão</span><span class="sxs-lookup"><span data-stu-id="9f98c-110">Version</span></span>                        | <span data-ttu-id="9f98c-111">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="9f98c-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="9f98c-112">Windows Client</span><span class="sxs-lookup"><span data-stu-id="9f98c-112">Windows Client</span></span>                | <span data-ttu-id="9f98c-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="9f98c-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="9f98c-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-114">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-115">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="9f98c-115">Windows 10 Client</span></span>             | <span data-ttu-id="9f98c-116">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-116">Version 1607+</span></span>                  | <span data-ttu-id="9f98c-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-117">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="9f98c-118">Windows Server</span></span>                | <span data-ttu-id="9f98c-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-119">2012 R2+</span></span>                       | <span data-ttu-id="9f98c-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-120">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="9f98c-121">Nano Server</span></span>                   | <span data-ttu-id="9f98c-122">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-122">Version 1803+</span></span>                  | <span data-ttu-id="9f98c-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="9f98c-123">x64, ARM32</span></span>      |

<span data-ttu-id="9f98c-124">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,1, consulte [versões do sistema operacional .net core 3,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="9f98c-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="9f98c-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9f98c-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="9f98c-126">As seguintes versões do Windows têm suporte com o .NET Core 3,0:</span><span class="sxs-lookup"><span data-stu-id="9f98c-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="9f98c-127">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="9f98c-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9f98c-128">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9f98c-128">OS</span></span>                            | <span data-ttu-id="9f98c-129">Versão</span><span class="sxs-lookup"><span data-stu-id="9f98c-129">Version</span></span>                        | <span data-ttu-id="9f98c-130">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="9f98c-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="9f98c-131">Windows Client</span><span class="sxs-lookup"><span data-stu-id="9f98c-131">Windows Client</span></span>                | <span data-ttu-id="9f98c-132">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="9f98c-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="9f98c-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-133">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-134">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="9f98c-134">Windows 10 Client</span></span>             | <span data-ttu-id="9f98c-135">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-135">Version 1607+</span></span>                  | <span data-ttu-id="9f98c-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-136">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="9f98c-137">Windows Server</span></span>                | <span data-ttu-id="9f98c-138">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-138">2012 R2+</span></span>                       | <span data-ttu-id="9f98c-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-139">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="9f98c-140">Nano Server</span></span>                   | <span data-ttu-id="9f98c-141">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-141">Version 1803+</span></span>                  | <span data-ttu-id="9f98c-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="9f98c-142">x64, ARM32</span></span>      |

<span data-ttu-id="9f98c-143">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,0, consulte [versões do sistema operacional .net core 3,0 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="9f98c-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="9f98c-144">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="9f98c-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="9f98c-145">As seguintes versões do Windows têm suporte com o .NET Core 2,2:</span><span class="sxs-lookup"><span data-stu-id="9f98c-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="9f98c-146">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="9f98c-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9f98c-147">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9f98c-147">OS</span></span>                            | <span data-ttu-id="9f98c-148">Versão</span><span class="sxs-lookup"><span data-stu-id="9f98c-148">Version</span></span>                        | <span data-ttu-id="9f98c-149">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="9f98c-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="9f98c-150">Windows Client</span><span class="sxs-lookup"><span data-stu-id="9f98c-150">Windows Client</span></span>                | <span data-ttu-id="9f98c-151">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="9f98c-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="9f98c-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-152">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-153">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="9f98c-153">Windows 10 Client</span></span>             | <span data-ttu-id="9f98c-154">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-154">Version 1607+</span></span>                  | <span data-ttu-id="9f98c-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-155">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="9f98c-156">Windows Server</span></span>                | <span data-ttu-id="9f98c-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="9f98c-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-158">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="9f98c-159">Nano Server</span></span>                   | <span data-ttu-id="9f98c-160">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-160">Version 1803+</span></span>                   | <span data-ttu-id="9f98c-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="9f98c-161">x64, ARM32</span></span>      |

<span data-ttu-id="9f98c-162">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,2, consulte [versões do sistema operacional .net core 2,2 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="9f98c-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="9f98c-163">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9f98c-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="9f98c-164">As seguintes versões do Windows têm suporte com o .NET Core 2,1:</span><span class="sxs-lookup"><span data-stu-id="9f98c-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="9f98c-165">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="9f98c-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9f98c-166">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9f98c-166">OS</span></span>                            | <span data-ttu-id="9f98c-167">Versão</span><span class="sxs-lookup"><span data-stu-id="9f98c-167">Version</span></span>                        | <span data-ttu-id="9f98c-168">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="9f98c-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="9f98c-169">Windows Client</span><span class="sxs-lookup"><span data-stu-id="9f98c-169">Windows Client</span></span>                | <span data-ttu-id="9f98c-170">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="9f98c-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="9f98c-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-171">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-172">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="9f98c-172">Windows 10 Client</span></span>             | <span data-ttu-id="9f98c-173">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-173">Version 1607+</span></span>                  | <span data-ttu-id="9f98c-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-174">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="9f98c-175">Windows Server</span></span>                | <span data-ttu-id="9f98c-176">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="9f98c-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-177">x64, x86</span></span>        |
| <span data-ttu-id="9f98c-178">Nano Server</span><span class="sxs-lookup"><span data-stu-id="9f98c-178">Nano Server</span></span>                   | <span data-ttu-id="9f98c-179">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-179">Version 1803+</span></span>                  | <span data-ttu-id="9f98c-180">x86</span><span class="sxs-lookup"><span data-stu-id="9f98c-180">x64,</span></span>            |

<span data-ttu-id="9f98c-181">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,1, consulte [versões do sistema operacional .net core 2,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="9f98c-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="9f98c-182">Windows 7/Vista/8,1/servidor 2008 R2</span><span class="sxs-lookup"><span data-stu-id="9f98c-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="9f98c-183">Dependências adicionais serão necessárias se você estiver instalando o SDK do .NET ou o tempo de execução nas seguintes versões do Windows:</span><span class="sxs-lookup"><span data-stu-id="9f98c-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="9f98c-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="9f98c-184">Windows 7 SP1</span></span>
- <span data-ttu-id="9f98c-185">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="9f98c-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="9f98c-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="9f98c-186">Windows 8.1</span></span>
- <span data-ttu-id="9f98c-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="9f98c-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="9f98c-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9f98c-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="9f98c-189">Instale o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9f98c-189">Install the following:</span></span>

- <span data-ttu-id="9f98c-190">[Atualização 3 C++ do Microsoft Visual 2015 redistribuível](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="9f98c-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="9f98c-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="9f98c-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="9f98c-192">Os requisitos acima também serão necessários se você vir entre um dos seguintes erros:</span><span class="sxs-lookup"><span data-stu-id="9f98c-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="9f98c-193">O programa não pode ser iniciado porque *API-MS-Win-CRT-Runtime-L1-1-0. dll* está ausente do seu computador.</span><span class="sxs-lookup"><span data-stu-id="9f98c-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="9f98c-194">Tente reinstalar o programa para corrigir esse problema.</span><span class="sxs-lookup"><span data-stu-id="9f98c-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="9f98c-195">\- ou –</span><span class="sxs-lookup"><span data-stu-id="9f98c-195">\- or -</span></span>
>
> <span data-ttu-id="9f98c-196">A biblioteca *hostfxr. dll* foi encontrada, mas está sendo carregada de *C:\\\<path_to_app >\\hostfxr. dll* falhou.</span><span class="sxs-lookup"><span data-stu-id="9f98c-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="9f98c-197">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="9f98c-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="9f98c-198">O .NET Core 3,1 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="9f98c-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="9f98c-199">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="9f98c-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="9f98c-200">O .NET Core 3,1 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="9f98c-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="9f98c-201">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="9f98c-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9f98c-202">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9f98c-202">OS</span></span>                             | <span data-ttu-id="9f98c-203">Versão</span><span class="sxs-lookup"><span data-stu-id="9f98c-203">Version</span></span>               | <span data-ttu-id="9f98c-204">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="9f98c-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="9f98c-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="9f98c-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="9f98c-206">6, 7, 8</span></span>               | <span data-ttu-id="9f98c-207">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-207">x64</span></span> |
| <span data-ttu-id="9f98c-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="9f98c-208">CentOS</span></span>                         | <span data-ttu-id="9f98c-209">7+</span><span class="sxs-lookup"><span data-stu-id="9f98c-209">7+</span></span>                    | <span data-ttu-id="9f98c-210">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-210">x64</span></span> |
| <span data-ttu-id="9f98c-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-211">Oracle Linux</span></span>                   | <span data-ttu-id="9f98c-212">7+</span><span class="sxs-lookup"><span data-stu-id="9f98c-212">7+</span></span>                    | <span data-ttu-id="9f98c-213">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-213">x64</span></span> |
| <span data-ttu-id="9f98c-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="9f98c-214">Fedora</span></span>                         | <span data-ttu-id="9f98c-215">29 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-215">29+</span></span>                   | <span data-ttu-id="9f98c-216">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-216">x64</span></span> |
| <span data-ttu-id="9f98c-217">Debian</span><span class="sxs-lookup"><span data-stu-id="9f98c-217">Debian</span></span>                         | <span data-ttu-id="9f98c-218">9 e posterior</span><span class="sxs-lookup"><span data-stu-id="9f98c-218">9+</span></span>                    | <span data-ttu-id="9f98c-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="9f98c-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="9f98c-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9f98c-220">Ubuntu</span></span>                         | <span data-ttu-id="9f98c-221">16.04+</span><span class="sxs-lookup"><span data-stu-id="9f98c-221">16.04+</span></span>                | <span data-ttu-id="9f98c-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="9f98c-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="9f98c-223">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="9f98c-223">Linux Mint</span></span>                     | <span data-ttu-id="9f98c-224">mais de 18 anos</span><span class="sxs-lookup"><span data-stu-id="9f98c-224">18+</span></span>                   | <span data-ttu-id="9f98c-225">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-225">x64</span></span> |
| <span data-ttu-id="9f98c-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="9f98c-226">openSUSE</span></span>                       | <span data-ttu-id="9f98c-227">15 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-227">15+</span></span>                   | <span data-ttu-id="9f98c-228">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-228">x64</span></span> |
| <span data-ttu-id="9f98c-229">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="9f98c-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="9f98c-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="9f98c-230">12 SP2+</span></span>               | <span data-ttu-id="9f98c-231">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-231">x64</span></span> |
| <span data-ttu-id="9f98c-232">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-232">Alpine Linux</span></span>                   | <span data-ttu-id="9f98c-233">3.10 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-233">3.10+</span></span>                 | <span data-ttu-id="9f98c-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="9f98c-234">x64, ARM64</span></span> |

<span data-ttu-id="9f98c-235">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,1, consulte [versões do sistema operacional .net core 3,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="9f98c-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="9f98c-236">Para obter mais informações sobre como instalar o .NET Core 3,1 em ARM64 (kernel 4.14 +), consulte [instalando o .net core 3,0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="9f98c-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f98c-237">O suporte a ARM64 requer o kernel do Linux 4,14 ou superior.</span><span class="sxs-lookup"><span data-stu-id="9f98c-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="9f98c-238">Algumas distribuições do Linux atendem a esse requisito, enquanto outras não.</span><span class="sxs-lookup"><span data-stu-id="9f98c-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="9f98c-239">Por exemplo, o Ubuntu 18, 4 tem suporte, mas o Ubuntu 16, 4 não.</span><span class="sxs-lookup"><span data-stu-id="9f98c-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="9f98c-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9f98c-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="9f98c-241">O .NET Core 3,0 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="9f98c-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="9f98c-242">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="9f98c-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="9f98c-243">O .NET Core 3,0 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="9f98c-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="9f98c-244">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="9f98c-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9f98c-245">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9f98c-245">OS</span></span>                             | <span data-ttu-id="9f98c-246">Versão</span><span class="sxs-lookup"><span data-stu-id="9f98c-246">Version</span></span>               | <span data-ttu-id="9f98c-247">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="9f98c-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="9f98c-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="9f98c-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="9f98c-249">6, 7, 8</span></span>               | <span data-ttu-id="9f98c-250">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-250">x64</span></span> |
| <span data-ttu-id="9f98c-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="9f98c-251">CentOS</span></span>                         | <span data-ttu-id="9f98c-252">7+</span><span class="sxs-lookup"><span data-stu-id="9f98c-252">7+</span></span>                    | <span data-ttu-id="9f98c-253">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-253">x64</span></span> |
| <span data-ttu-id="9f98c-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-254">Oracle Linux</span></span>                   | <span data-ttu-id="9f98c-255">7+</span><span class="sxs-lookup"><span data-stu-id="9f98c-255">7+</span></span>                    | <span data-ttu-id="9f98c-256">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-256">x64</span></span> |
| <span data-ttu-id="9f98c-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="9f98c-257">Fedora</span></span>                         | <span data-ttu-id="9f98c-258">29 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-258">29+</span></span>                   | <span data-ttu-id="9f98c-259">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-259">x64</span></span> |
| <span data-ttu-id="9f98c-260">Debian</span><span class="sxs-lookup"><span data-stu-id="9f98c-260">Debian</span></span>                         | <span data-ttu-id="9f98c-261">9 e posterior</span><span class="sxs-lookup"><span data-stu-id="9f98c-261">9+</span></span>                    | <span data-ttu-id="9f98c-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="9f98c-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="9f98c-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9f98c-263">Ubuntu</span></span>                         | <span data-ttu-id="9f98c-264">16.04+</span><span class="sxs-lookup"><span data-stu-id="9f98c-264">16.04+</span></span>                | <span data-ttu-id="9f98c-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="9f98c-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="9f98c-266">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="9f98c-266">Linux Mint</span></span>                     | <span data-ttu-id="9f98c-267">mais de 18 anos</span><span class="sxs-lookup"><span data-stu-id="9f98c-267">18+</span></span>                   | <span data-ttu-id="9f98c-268">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-268">x64</span></span> |
| <span data-ttu-id="9f98c-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="9f98c-269">openSUSE</span></span>                       | <span data-ttu-id="9f98c-270">15 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-270">15+</span></span>                   | <span data-ttu-id="9f98c-271">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-271">x64</span></span> |
| <span data-ttu-id="9f98c-272">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="9f98c-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="9f98c-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="9f98c-273">12 SP2+</span></span>               | <span data-ttu-id="9f98c-274">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-274">x64</span></span> |
| <span data-ttu-id="9f98c-275">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-275">Alpine Linux</span></span>                   | <span data-ttu-id="9f98c-276">3.8+</span><span class="sxs-lookup"><span data-stu-id="9f98c-276">3.8+</span></span>                  | <span data-ttu-id="9f98c-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="9f98c-277">x64, ARM64</span></span> |

<span data-ttu-id="9f98c-278">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,0, consulte [versões do sistema operacional .net core 3,0 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="9f98c-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="9f98c-279">Para obter mais informações sobre como instalar o .NET Core 3.0 no ARM64, confira [Instalando o .NET Core 3.0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="9f98c-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="9f98c-280">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="9f98c-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="9f98c-281">O .NET Core 2,2 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="9f98c-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="9f98c-282">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="9f98c-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="9f98c-283">O .NET Core 2,2 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="9f98c-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="9f98c-284">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="9f98c-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9f98c-285">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9f98c-285">OS</span></span>                             |  <span data-ttu-id="9f98c-286">Versão</span><span class="sxs-lookup"><span data-stu-id="9f98c-286">Version</span></span>                |  <span data-ttu-id="9f98c-287">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="9f98c-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="9f98c-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="9f98c-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="9f98c-289">6, 7</span></span>                   | <span data-ttu-id="9f98c-290">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-290">x64</span></span> |
| <span data-ttu-id="9f98c-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="9f98c-291">CentOS</span></span>                         |  <span data-ttu-id="9f98c-292">7</span><span class="sxs-lookup"><span data-stu-id="9f98c-292">7</span></span>                      | <span data-ttu-id="9f98c-293">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-293">x64</span></span> |
| <span data-ttu-id="9f98c-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-294">Oracle Linux</span></span>                   |  <span data-ttu-id="9f98c-295">7</span><span class="sxs-lookup"><span data-stu-id="9f98c-295">7</span></span>                      | <span data-ttu-id="9f98c-296">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-296">x64</span></span> |
| <span data-ttu-id="9f98c-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="9f98c-297">Fedora</span></span>                         |  <span data-ttu-id="9f98c-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="9f98c-298">29, 30</span></span>                 | <span data-ttu-id="9f98c-299">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-299">x64</span></span> |
| <span data-ttu-id="9f98c-300">Debian</span><span class="sxs-lookup"><span data-stu-id="9f98c-300">Debian</span></span>                         |  <span data-ttu-id="9f98c-301">9</span><span class="sxs-lookup"><span data-stu-id="9f98c-301">9</span></span>                      | <span data-ttu-id="9f98c-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="9f98c-302">x64, ARM32</span></span> |
| <span data-ttu-id="9f98c-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9f98c-303">Ubuntu</span></span>                         |  <span data-ttu-id="9f98c-304">16, 4, 18, 4, 18,10</span><span class="sxs-lookup"><span data-stu-id="9f98c-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="9f98c-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="9f98c-305">x64, ARM32</span></span> |
| <span data-ttu-id="9f98c-306">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="9f98c-306">Linux Mint</span></span>                     |  <span data-ttu-id="9f98c-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="9f98c-307">17, 18</span></span>                 | <span data-ttu-id="9f98c-308">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-308">x64</span></span> |
| <span data-ttu-id="9f98c-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="9f98c-309">openSUSE</span></span>                       |  <span data-ttu-id="9f98c-310">15 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-310">15+</span></span>                    | <span data-ttu-id="9f98c-311">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-311">x64</span></span> |
| <span data-ttu-id="9f98c-312">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="9f98c-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="9f98c-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="9f98c-313">12 SP2+</span></span>                | <span data-ttu-id="9f98c-314">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-314">x64</span></span> |
| <span data-ttu-id="9f98c-315">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-315">Alpine Linux</span></span>                   |  <span data-ttu-id="9f98c-316">3.8+</span><span class="sxs-lookup"><span data-stu-id="9f98c-316">3.8+</span></span>                   | <span data-ttu-id="9f98c-317">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-317">x64</span></span> |

<span data-ttu-id="9f98c-318">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,2, consulte [versões do sistema operacional .net core 2,2 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="9f98c-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="9f98c-319">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9f98c-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="9f98c-320">O .NET Core 2,1 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="9f98c-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="9f98c-321">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="9f98c-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="9f98c-322">O .NET Core 2,1 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="9f98c-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="9f98c-323">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="9f98c-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9f98c-324">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="9f98c-324">OS</span></span>                             |  <span data-ttu-id="9f98c-325">Versão</span><span class="sxs-lookup"><span data-stu-id="9f98c-325">Version</span></span>                |  <span data-ttu-id="9f98c-326">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="9f98c-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="9f98c-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="9f98c-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="9f98c-328">6, 7, 8</span></span>                | <span data-ttu-id="9f98c-329">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-329">x64</span></span> |
| <span data-ttu-id="9f98c-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="9f98c-330">CentOS</span></span>                         |  <span data-ttu-id="9f98c-331">7+</span><span class="sxs-lookup"><span data-stu-id="9f98c-331">7+</span></span>                     | <span data-ttu-id="9f98c-332">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-332">x64</span></span> |
| <span data-ttu-id="9f98c-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-333">Oracle Linux</span></span>                   |  <span data-ttu-id="9f98c-334">7+</span><span class="sxs-lookup"><span data-stu-id="9f98c-334">7+</span></span>                     | <span data-ttu-id="9f98c-335">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-335">x64</span></span> |
| <span data-ttu-id="9f98c-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="9f98c-336">Fedora</span></span>                         |  <span data-ttu-id="9f98c-337">29 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-337">29+</span></span>                    | <span data-ttu-id="9f98c-338">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-338">x64</span></span> |
| <span data-ttu-id="9f98c-339">Debian</span><span class="sxs-lookup"><span data-stu-id="9f98c-339">Debian</span></span>                         |  <span data-ttu-id="9f98c-340">9</span><span class="sxs-lookup"><span data-stu-id="9f98c-340">9</span></span>                      | <span data-ttu-id="9f98c-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="9f98c-341">x64, ARM32</span></span> |
| <span data-ttu-id="9f98c-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9f98c-342">Ubuntu</span></span>                         |  <span data-ttu-id="9f98c-343">16, 4, 18, 4, 19, 4, 19,10</span><span class="sxs-lookup"><span data-stu-id="9f98c-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="9f98c-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="9f98c-344">x64, ARM32</span></span> |
| <span data-ttu-id="9f98c-345">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="9f98c-345">Linux Mint</span></span>                     |  <span data-ttu-id="9f98c-346">17+</span><span class="sxs-lookup"><span data-stu-id="9f98c-346">17+</span></span>                    | <span data-ttu-id="9f98c-347">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-347">x64</span></span> |
| <span data-ttu-id="9f98c-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="9f98c-348">openSUSE</span></span>                       |  <span data-ttu-id="9f98c-349">15 +</span><span class="sxs-lookup"><span data-stu-id="9f98c-349">15+</span></span>                    | <span data-ttu-id="9f98c-350">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-350">x64</span></span> |
| <span data-ttu-id="9f98c-351">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="9f98c-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="9f98c-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="9f98c-352">12 SP2+</span></span>                | <span data-ttu-id="9f98c-353">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-353">x64</span></span> |
| <span data-ttu-id="9f98c-354">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-354">Alpine Linux</span></span>                   |  <span data-ttu-id="9f98c-355">3.8+</span><span class="sxs-lookup"><span data-stu-id="9f98c-355">3.8+</span></span>                   | <span data-ttu-id="9f98c-356">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-356">x64</span></span> |

<span data-ttu-id="9f98c-357">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,1, consulte [versões do sistema operacional .net core 2,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="9f98c-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="9f98c-358">Dependências de distribuição do Linux</span><span class="sxs-lookup"><span data-stu-id="9f98c-358">Linux distribution dependencies</span></span>

<span data-ttu-id="9f98c-359">Com base em sua distribuição do Linux, talvez seja necessário instalar dependências adicionais.</span><span class="sxs-lookup"><span data-stu-id="9f98c-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f98c-360">Os nomes e as versões exatas podem variar ligeiramente na distribuição Linux de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="9f98c-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="9f98c-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9f98c-361">Ubuntu</span></span>

<span data-ttu-id="9f98c-362">As distribuições do Ubuntu exigem que as seguintes bibliotecas sejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="9f98c-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="9f98c-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="9f98c-363">liblttng-ust0</span></span>
- <span data-ttu-id="9f98c-364">libcurl3 (para 14.x e 16.x)</span><span class="sxs-lookup"><span data-stu-id="9f98c-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="9f98c-365">libcurl4 (para 18.x)</span><span class="sxs-lookup"><span data-stu-id="9f98c-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="9f98c-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="9f98c-366">libssl1.0.0</span></span>
- <span data-ttu-id="9f98c-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="9f98c-367">libkrb5-3</span></span>
- <span data-ttu-id="9f98c-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="9f98c-368">zlib1g</span></span>
- <span data-ttu-id="9f98c-369">libicu52 (para 14.x)</span><span class="sxs-lookup"><span data-stu-id="9f98c-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="9f98c-370">libicu55 (para 16.x)</span><span class="sxs-lookup"><span data-stu-id="9f98c-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="9f98c-371">libicu57 (para 17.x)</span><span class="sxs-lookup"><span data-stu-id="9f98c-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="9f98c-372">libicu60 (para 18.x)</span><span class="sxs-lookup"><span data-stu-id="9f98c-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="9f98c-373">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="9f98c-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="9f98c-374">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="9f98c-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="9f98c-375">A maioria das versões do Ubuntu inclui uma versão anterior do libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="9f98c-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="9f98c-376">Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="9f98c-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="9f98c-377">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="9f98c-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="9f98c-378">CentOS e Fedora</span><span class="sxs-lookup"><span data-stu-id="9f98c-378">CentOS and Fedora</span></span>

<span data-ttu-id="9f98c-379">As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="9f98c-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="9f98c-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="9f98c-380">lttng-ust</span></span>
- <span data-ttu-id="9f98c-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="9f98c-381">libcurl</span></span>
- <span data-ttu-id="9f98c-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="9f98c-382">openssl-libs</span></span>
- <span data-ttu-id="9f98c-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="9f98c-383">krb5-libs</span></span>
- <span data-ttu-id="9f98c-384">libicu</span><span class="sxs-lookup"><span data-stu-id="9f98c-384">libicu</span></span>
- <span data-ttu-id="9f98c-385">zlib</span><span class="sxs-lookup"><span data-stu-id="9f98c-385">zlib</span></span>

<span data-ttu-id="9f98c-386">Usuários do Fedora: se a versão do OpenSSL > = 1,1, você precisará instalar o **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="9f98c-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="9f98c-387">Para o .NET Core 2,0, as seguintes dependências também são necessárias:</span><span class="sxs-lookup"><span data-stu-id="9f98c-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="9f98c-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="9f98c-388">libunwind</span></span>
- <span data-ttu-id="9f98c-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="9f98c-389">libuuid</span></span>

<span data-ttu-id="9f98c-390">Para obter mais informações sobre as dependências, consulte [aplicativos do Linux autocontidos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="9f98c-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="9f98c-391">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="9f98c-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="9f98c-392">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="9f98c-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="9f98c-393">A maioria das versões do CentOS e do Fedora inclui uma versão anterior do libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="9f98c-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="9f98c-394">Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="9f98c-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="9f98c-395">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="9f98c-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="9f98c-396">O .NET Core tem suporte nas seguintes versões do macOS:</span><span class="sxs-lookup"><span data-stu-id="9f98c-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="9f98c-397">Um símbolo de `+` representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="9f98c-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9f98c-398">Versão do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9f98c-398">.NET Core Version</span></span> | <span data-ttu-id="9f98c-399">macOS</span><span class="sxs-lookup"><span data-stu-id="9f98c-399">macOS</span></span>                 | <span data-ttu-id="9f98c-400">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="9f98c-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="9f98c-401">3.1</span><span class="sxs-lookup"><span data-stu-id="9f98c-401">3.1</span></span>               | <span data-ttu-id="9f98c-402">Alta serra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="9f98c-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="9f98c-403">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-403">x64</span></span> | [<span data-ttu-id="9f98c-404">Mais informações</span><span class="sxs-lookup"><span data-stu-id="9f98c-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="9f98c-405">3.0</span><span class="sxs-lookup"><span data-stu-id="9f98c-405">3.0</span></span>               | <span data-ttu-id="9f98c-406">Alta serra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="9f98c-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="9f98c-407">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-407">x64</span></span> | [<span data-ttu-id="9f98c-408">Mais informações</span><span class="sxs-lookup"><span data-stu-id="9f98c-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="9f98c-409">2.2</span><span class="sxs-lookup"><span data-stu-id="9f98c-409">2.2</span></span>               | <span data-ttu-id="9f98c-410">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="9f98c-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="9f98c-411">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-411">x64</span></span> | [<span data-ttu-id="9f98c-412">Mais informações</span><span class="sxs-lookup"><span data-stu-id="9f98c-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="9f98c-413">2.1</span><span class="sxs-lookup"><span data-stu-id="9f98c-413">2.1</span></span>               | <span data-ttu-id="9f98c-414">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="9f98c-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="9f98c-415">x64</span><span class="sxs-lookup"><span data-stu-id="9f98c-415">x64</span></span> | [<span data-ttu-id="9f98c-416">Mais informações</span><span class="sxs-lookup"><span data-stu-id="9f98c-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="9f98c-417">A partir do macOS Catalina (versão 10,15), todo software criado após 1º de junho de 2019 que é distribuído com a ID do desenvolvedor deve ser notarized.</span><span class="sxs-lookup"><span data-stu-id="9f98c-417">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="9f98c-418">Esse requisito se aplica ao tempo de execução do .NET Core, SDK do .NET Core e software criado com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9f98c-418">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="9f98c-419">Os instaladores do .NET Core (Runtime e SDK) versões 3,1, 3,0 e 2,1, foram notarizeddos desde 18 de fevereiro de 2020.</span><span class="sxs-lookup"><span data-stu-id="9f98c-419">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="9f98c-420">Versões anteriores liberadas não são notarized.</span><span class="sxs-lookup"><span data-stu-id="9f98c-420">Prior released versions aren't notarized.</span></span> <span data-ttu-id="9f98c-421">Se você executar um aplicativo não notarized, verá um erro semelhante à imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="9f98c-421">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![alerta de notarization Catalina do macOS](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="9f98c-423">Para obter mais informações sobre como o imforced-notarization afeta o .NET Core (e seus aplicativos .NET Core), consulte [trabalhando com o MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="9f98c-423">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="9f98c-424">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="9f98c-424">libgdiplus</span></span>

<span data-ttu-id="9f98c-425">Os aplicativos .NET Core que usam o assembly *System. sorteio. Common* exigem que o libgdiplus seja instalado.</span><span class="sxs-lookup"><span data-stu-id="9f98c-425">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="9f98c-426">Uma maneira fácil de obter o libgdiplus é usando o Gerenciador de pacotes [homebrew ("Brew")](https://brew.sh/) para MacOS.</span><span class="sxs-lookup"><span data-stu-id="9f98c-426">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="9f98c-427">Depois de instalar o *Brew*, instale o libgdiplus executando os seguintes comandos em um prompt de terminal (comando):</span><span class="sxs-lookup"><span data-stu-id="9f98c-427">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="9f98c-428">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="9f98c-428">Next steps</span></span>

- <span data-ttu-id="9f98c-429">Para desenvolver e executar aplicativos, instale o [SDK do .NET Core](sdk.md) (inclui o tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="9f98c-429">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="9f98c-430">Para executar aplicativos que outras pessoas criaram, instale o [tempo de execução do .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="9f98c-430">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
