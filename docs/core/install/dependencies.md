---
title: Dependências de SDK do .NET Core e tempo de execução-.NET Core
description: Detalha o sistema operacional e os pré-requisitos de arquitetura de CPU para instalar o SDK do .NET Core e o tempo de execução no Windows, Linux e macOS.
author: leecow
ms.author: leecow
ms.date: 06/01/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 81f6ab436428d71f71d9fd0f560bd2b0512a519b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590754"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="6d91c-103">Dependências e requisitos do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6d91c-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="6d91c-104">Este artigo detalha quais sistemas operacionais e arquitetura de CPU têm suporte no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d91c-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="6d91c-105">Sistemas operacionais compatíveis</span><span class="sxs-lookup"><span data-stu-id="6d91c-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="6d91c-106">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6d91c-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="6d91c-107">As seguintes versões do Windows têm suporte com o .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="6d91c-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="6d91c-108">Um `+` símbolo representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="6d91c-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6d91c-109">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="6d91c-109">OS</span></span>                            | <span data-ttu-id="6d91c-110">Versão</span><span class="sxs-lookup"><span data-stu-id="6d91c-110">Version</span></span>                        | <span data-ttu-id="6d91c-111">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="6d91c-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6d91c-112">Windows Client</span><span class="sxs-lookup"><span data-stu-id="6d91c-112">Windows Client</span></span>                | <span data-ttu-id="6d91c-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="6d91c-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6d91c-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-114">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-115">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="6d91c-115">Windows 10 Client</span></span>             | <span data-ttu-id="6d91c-116">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-116">Version 1607+</span></span>                  | <span data-ttu-id="6d91c-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-117">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6d91c-118">Windows Server</span></span>                | <span data-ttu-id="6d91c-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-119">2012 R2+</span></span>                       | <span data-ttu-id="6d91c-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-120">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6d91c-121">Nano Server</span></span>                   | <span data-ttu-id="6d91c-122">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-122">Version 1803+</span></span>                  | <span data-ttu-id="6d91c-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6d91c-123">x64, ARM32</span></span>      |

<span data-ttu-id="6d91c-124">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,1, consulte [versões do sistema operacional .net core 3,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6d91c-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="6d91c-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6d91c-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="6d91c-126">*O .NET Core 3,0 está atualmente sem suporte. Para obter mais informações, consulte a [política de suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="6d91c-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="6d91c-127">As seguintes versões do Windows têm suporte com o .NET Core 3,0:</span><span class="sxs-lookup"><span data-stu-id="6d91c-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="6d91c-128">Um `+` símbolo representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="6d91c-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6d91c-129">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="6d91c-129">OS</span></span>                            | <span data-ttu-id="6d91c-130">Versão</span><span class="sxs-lookup"><span data-stu-id="6d91c-130">Version</span></span>                        | <span data-ttu-id="6d91c-131">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="6d91c-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6d91c-132">Windows Client</span><span class="sxs-lookup"><span data-stu-id="6d91c-132">Windows Client</span></span>                | <span data-ttu-id="6d91c-133">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="6d91c-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6d91c-134">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-134">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-135">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="6d91c-135">Windows 10 Client</span></span>             | <span data-ttu-id="6d91c-136">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-136">Version 1607+</span></span>                  | <span data-ttu-id="6d91c-137">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-137">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6d91c-138">Windows Server</span></span>                | <span data-ttu-id="6d91c-139">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-139">2012 R2+</span></span>                       | <span data-ttu-id="6d91c-140">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-140">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-141">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6d91c-141">Nano Server</span></span>                   | <span data-ttu-id="6d91c-142">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-142">Version 1803+</span></span>                  | <span data-ttu-id="6d91c-143">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6d91c-143">x64, ARM32</span></span>      |

<span data-ttu-id="6d91c-144">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,0, consulte [versões do sistema operacional .net core 3,0 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6d91c-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="6d91c-145">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="6d91c-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="6d91c-146">*O .NET Core 2,2 está atualmente sem suporte. Para obter mais informações, consulte a [política de suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="6d91c-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="6d91c-147">As seguintes versões do Windows têm suporte com o .NET Core 2,2:</span><span class="sxs-lookup"><span data-stu-id="6d91c-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="6d91c-148">Um `+` símbolo representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="6d91c-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6d91c-149">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="6d91c-149">OS</span></span>                            | <span data-ttu-id="6d91c-150">Versão</span><span class="sxs-lookup"><span data-stu-id="6d91c-150">Version</span></span>                        | <span data-ttu-id="6d91c-151">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="6d91c-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6d91c-152">Windows Client</span><span class="sxs-lookup"><span data-stu-id="6d91c-152">Windows Client</span></span>                | <span data-ttu-id="6d91c-153">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="6d91c-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6d91c-154">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-154">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-155">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="6d91c-155">Windows 10 Client</span></span>             | <span data-ttu-id="6d91c-156">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-156">Version 1607+</span></span>                  | <span data-ttu-id="6d91c-157">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-157">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6d91c-158">Windows Server</span></span>                | <span data-ttu-id="6d91c-159">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="6d91c-160">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-160">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-161">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6d91c-161">Nano Server</span></span>                   | <span data-ttu-id="6d91c-162">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-162">Version 1803+</span></span>                   | <span data-ttu-id="6d91c-163">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6d91c-163">x64, ARM32</span></span>      |

<span data-ttu-id="6d91c-164">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,2, consulte [versões do sistema operacional .net core 2,2 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6d91c-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="6d91c-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6d91c-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6d91c-166">As seguintes versões do Windows têm suporte com o .NET Core 2,1:</span><span class="sxs-lookup"><span data-stu-id="6d91c-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="6d91c-167">Um `+` símbolo representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="6d91c-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6d91c-168">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="6d91c-168">OS</span></span>                            | <span data-ttu-id="6d91c-169">Versão</span><span class="sxs-lookup"><span data-stu-id="6d91c-169">Version</span></span>                        | <span data-ttu-id="6d91c-170">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="6d91c-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6d91c-171">Windows Client</span><span class="sxs-lookup"><span data-stu-id="6d91c-171">Windows Client</span></span>                | <span data-ttu-id="6d91c-172">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="6d91c-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6d91c-173">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-173">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-174">Cliente do Windows 10</span><span class="sxs-lookup"><span data-stu-id="6d91c-174">Windows 10 Client</span></span>             | <span data-ttu-id="6d91c-175">Versão 1607 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-175">Version 1607+</span></span>                  | <span data-ttu-id="6d91c-176">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-176">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6d91c-177">Windows Server</span></span>                | <span data-ttu-id="6d91c-178">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="6d91c-179">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-179">x64, x86</span></span>        |
| <span data-ttu-id="6d91c-180">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6d91c-180">Nano Server</span></span>                   | <span data-ttu-id="6d91c-181">Versão 1803 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-181">Version 1803+</span></span>                  | <span data-ttu-id="6d91c-182">x86</span><span class="sxs-lookup"><span data-stu-id="6d91c-182">x64,</span></span>            |

<span data-ttu-id="6d91c-183">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,1, consulte [versões do sistema operacional .net core 2,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6d91c-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="6d91c-184">Windows 7/Vista/8,1/servidor 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6d91c-184">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="6d91c-185">Dependências adicionais serão necessárias se você estiver instalando o SDK do .NET ou o tempo de execução nas seguintes versões do Windows:</span><span class="sxs-lookup"><span data-stu-id="6d91c-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="6d91c-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="6d91c-186">Windows 7 SP1</span></span>
- <span data-ttu-id="6d91c-187">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="6d91c-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="6d91c-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="6d91c-188">Windows 8.1</span></span>
- <span data-ttu-id="6d91c-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="6d91c-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="6d91c-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6d91c-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="6d91c-191">Instale o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6d91c-191">Install the following:</span></span>

- <span data-ttu-id="6d91c-192">[Microsoft Visual C++ 2015 redistribuível atualização 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="6d91c-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="6d91c-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="6d91c-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="6d91c-194">Os requisitos acima também serão necessários se você vir entre um dos seguintes erros:</span><span class="sxs-lookup"><span data-stu-id="6d91c-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="6d91c-195">O programa não pode ser iniciado porque *API-MS-Win-CRT-Runtime-L1-1-0. dll* está ausente do seu computador.</span><span class="sxs-lookup"><span data-stu-id="6d91c-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="6d91c-196">Tente reinstalar o programa para corrigir esse problema.</span><span class="sxs-lookup"><span data-stu-id="6d91c-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="6d91c-197">\- ou –</span><span class="sxs-lookup"><span data-stu-id="6d91c-197">\- or -</span></span>
>
> <span data-ttu-id="6d91c-198">O programa não pode ser iniciado porque *API-MS-Win-cor-TimeZone-L1-1-0. dll* está ausente do seu computador.</span><span class="sxs-lookup"><span data-stu-id="6d91c-198">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="6d91c-199">Tente reinstalar o programa para corrigir esse problema.</span><span class="sxs-lookup"><span data-stu-id="6d91c-199">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="6d91c-200">\- ou –</span><span class="sxs-lookup"><span data-stu-id="6d91c-200">\- or -</span></span>
>
> <span data-ttu-id="6d91c-201">A biblioteca *hostfxr. dll* foi encontrada, mas o carregamento de *C: \\ \<path_to_app> \\ hostfxr. dll* falhou.</span><span class="sxs-lookup"><span data-stu-id="6d91c-201">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="6d91c-202">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6d91c-202">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="6d91c-203">O .NET Core 3,1 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="6d91c-203">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="6d91c-204">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="6d91c-204">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="6d91c-205">O .NET Core 3,1 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="6d91c-205">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="6d91c-206">Um `+` símbolo representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="6d91c-206">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6d91c-207">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="6d91c-207">OS</span></span>                             | <span data-ttu-id="6d91c-208">Versão</span><span class="sxs-lookup"><span data-stu-id="6d91c-208">Version</span></span>               | <span data-ttu-id="6d91c-209">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="6d91c-209">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="6d91c-210">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-210">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="6d91c-211">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="6d91c-211">6, 7, 8</span></span>               | <span data-ttu-id="6d91c-212">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-212">x64</span></span> |
| <span data-ttu-id="6d91c-213">CentOS</span><span class="sxs-lookup"><span data-stu-id="6d91c-213">CentOS</span></span>                         | <span data-ttu-id="6d91c-214">7+</span><span class="sxs-lookup"><span data-stu-id="6d91c-214">7+</span></span>                    | <span data-ttu-id="6d91c-215">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-215">x64</span></span> |
| <span data-ttu-id="6d91c-216">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-216">Oracle Linux</span></span>                   | <span data-ttu-id="6d91c-217">7+</span><span class="sxs-lookup"><span data-stu-id="6d91c-217">7+</span></span>                    | <span data-ttu-id="6d91c-218">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-218">x64</span></span> |
| <span data-ttu-id="6d91c-219">Fedora</span><span class="sxs-lookup"><span data-stu-id="6d91c-219">Fedora</span></span>                         | <span data-ttu-id="6d91c-220">mais de 30</span><span class="sxs-lookup"><span data-stu-id="6d91c-220">30+</span></span>                   | <span data-ttu-id="6d91c-221">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-221">x64</span></span> |
| <span data-ttu-id="6d91c-222">Debian</span><span class="sxs-lookup"><span data-stu-id="6d91c-222">Debian</span></span>                         | <span data-ttu-id="6d91c-223">9 e posterior</span><span class="sxs-lookup"><span data-stu-id="6d91c-223">9+</span></span>                    | <span data-ttu-id="6d91c-224">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="6d91c-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="6d91c-225">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6d91c-225">Ubuntu</span></span>                         | <span data-ttu-id="6d91c-226">16.04+</span><span class="sxs-lookup"><span data-stu-id="6d91c-226">16.04+</span></span>                | <span data-ttu-id="6d91c-227">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="6d91c-227">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="6d91c-228">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="6d91c-228">Linux Mint</span></span>                     | <span data-ttu-id="6d91c-229">mais de 18 anos</span><span class="sxs-lookup"><span data-stu-id="6d91c-229">18+</span></span>                   | <span data-ttu-id="6d91c-230">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-230">x64</span></span> |
| <span data-ttu-id="6d91c-231">openSUSE</span><span class="sxs-lookup"><span data-stu-id="6d91c-231">openSUSE</span></span>                       | <span data-ttu-id="6d91c-232">15 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-232">15+</span></span>                   | <span data-ttu-id="6d91c-233">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-233">x64</span></span> |
| <span data-ttu-id="6d91c-234">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="6d91c-234">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="6d91c-235">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="6d91c-235">12 SP2+</span></span>               | <span data-ttu-id="6d91c-236">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-236">x64</span></span> |
| <span data-ttu-id="6d91c-237">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-237">Alpine Linux</span></span>                   | <span data-ttu-id="6d91c-238">3.10 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-238">3.10+</span></span>                 | <span data-ttu-id="6d91c-239">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="6d91c-239">x64, ARM64</span></span> |

<span data-ttu-id="6d91c-240">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,1, consulte [versões do sistema operacional .net core 3,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6d91c-240">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="6d91c-241">Para obter mais informações sobre como instalar o .NET Core 3,1 em ARM64 (kernel 4.14 +), consulte [instalando o .net core 3,0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="6d91c-241">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d91c-242">O suporte a ARM64 requer o kernel do Linux 4,14 ou superior.</span><span class="sxs-lookup"><span data-stu-id="6d91c-242">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="6d91c-243">Algumas distribuições do Linux atendem a esse requisito, enquanto outras não.</span><span class="sxs-lookup"><span data-stu-id="6d91c-243">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="6d91c-244">Por exemplo, o Ubuntu 18, 4 tem suporte, mas o Ubuntu 16, 4 não.</span><span class="sxs-lookup"><span data-stu-id="6d91c-244">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="6d91c-245">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6d91c-245">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="6d91c-246">*O .NET Core 3,0 está atualmente sem suporte. Para obter mais informações, consulte a [política de suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="6d91c-246">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="6d91c-247">O .NET Core 3,0 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="6d91c-247">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="6d91c-248">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="6d91c-248">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="6d91c-249">O .NET Core 3,0 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="6d91c-249">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="6d91c-250">Um `+` símbolo representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="6d91c-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6d91c-251">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="6d91c-251">OS</span></span>                             | <span data-ttu-id="6d91c-252">Versão</span><span class="sxs-lookup"><span data-stu-id="6d91c-252">Version</span></span>               | <span data-ttu-id="6d91c-253">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="6d91c-253">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="6d91c-254">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-254">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="6d91c-255">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="6d91c-255">6, 7, 8</span></span>               | <span data-ttu-id="6d91c-256">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-256">x64</span></span> |
| <span data-ttu-id="6d91c-257">CentOS</span><span class="sxs-lookup"><span data-stu-id="6d91c-257">CentOS</span></span>                         | <span data-ttu-id="6d91c-258">7+</span><span class="sxs-lookup"><span data-stu-id="6d91c-258">7+</span></span>                    | <span data-ttu-id="6d91c-259">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-259">x64</span></span> |
| <span data-ttu-id="6d91c-260">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-260">Oracle Linux</span></span>                   | <span data-ttu-id="6d91c-261">7+</span><span class="sxs-lookup"><span data-stu-id="6d91c-261">7+</span></span>                    | <span data-ttu-id="6d91c-262">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-262">x64</span></span> |
| <span data-ttu-id="6d91c-263">Fedora</span><span class="sxs-lookup"><span data-stu-id="6d91c-263">Fedora</span></span>                         | <span data-ttu-id="6d91c-264">29 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-264">29+</span></span>                   | <span data-ttu-id="6d91c-265">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-265">x64</span></span> |
| <span data-ttu-id="6d91c-266">Debian</span><span class="sxs-lookup"><span data-stu-id="6d91c-266">Debian</span></span>                         | <span data-ttu-id="6d91c-267">9 e posterior</span><span class="sxs-lookup"><span data-stu-id="6d91c-267">9+</span></span>                    | <span data-ttu-id="6d91c-268">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="6d91c-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="6d91c-269">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6d91c-269">Ubuntu</span></span>                         | <span data-ttu-id="6d91c-270">16.04+</span><span class="sxs-lookup"><span data-stu-id="6d91c-270">16.04+</span></span>                | <span data-ttu-id="6d91c-271">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="6d91c-271">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="6d91c-272">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="6d91c-272">Linux Mint</span></span>                     | <span data-ttu-id="6d91c-273">mais de 18 anos</span><span class="sxs-lookup"><span data-stu-id="6d91c-273">18+</span></span>                   | <span data-ttu-id="6d91c-274">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-274">x64</span></span> |
| <span data-ttu-id="6d91c-275">openSUSE</span><span class="sxs-lookup"><span data-stu-id="6d91c-275">openSUSE</span></span>                       | <span data-ttu-id="6d91c-276">15 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-276">15+</span></span>                   | <span data-ttu-id="6d91c-277">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-277">x64</span></span> |
| <span data-ttu-id="6d91c-278">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="6d91c-278">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="6d91c-279">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="6d91c-279">12 SP2+</span></span>               | <span data-ttu-id="6d91c-280">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-280">x64</span></span> |
| <span data-ttu-id="6d91c-281">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-281">Alpine Linux</span></span>                   | <span data-ttu-id="6d91c-282">3.8+</span><span class="sxs-lookup"><span data-stu-id="6d91c-282">3.8+</span></span>                  | <span data-ttu-id="6d91c-283">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="6d91c-283">x64, ARM64</span></span> |

<span data-ttu-id="6d91c-284">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,0, consulte [versões do sistema operacional .net core 3,0 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6d91c-284">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="6d91c-285">Para obter mais informações sobre como instalar o .NET Core 3.0 no ARM64, confira [Instalando o .NET Core 3.0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="6d91c-285">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="6d91c-286">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="6d91c-286">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="6d91c-287">*O .NET Core 2,2 está atualmente sem suporte. Para obter mais informações, consulte a [política de suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="6d91c-287">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="6d91c-288">O .NET Core 2,2 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="6d91c-288">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="6d91c-289">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="6d91c-289">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="6d91c-290">O .NET Core 2,2 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="6d91c-290">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="6d91c-291">Um `+` símbolo representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="6d91c-291">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6d91c-292">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="6d91c-292">OS</span></span>                             |  <span data-ttu-id="6d91c-293">Versão</span><span class="sxs-lookup"><span data-stu-id="6d91c-293">Version</span></span>                |  <span data-ttu-id="6d91c-294">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="6d91c-294">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="6d91c-295">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-295">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="6d91c-296">6, 7</span><span class="sxs-lookup"><span data-stu-id="6d91c-296">6, 7</span></span>                   | <span data-ttu-id="6d91c-297">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-297">x64</span></span> |
| <span data-ttu-id="6d91c-298">CentOS</span><span class="sxs-lookup"><span data-stu-id="6d91c-298">CentOS</span></span>                         |  <span data-ttu-id="6d91c-299">7</span><span class="sxs-lookup"><span data-stu-id="6d91c-299">7</span></span>                      | <span data-ttu-id="6d91c-300">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-300">x64</span></span> |
| <span data-ttu-id="6d91c-301">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-301">Oracle Linux</span></span>                   |  <span data-ttu-id="6d91c-302">7</span><span class="sxs-lookup"><span data-stu-id="6d91c-302">7</span></span>                      | <span data-ttu-id="6d91c-303">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-303">x64</span></span> |
| <span data-ttu-id="6d91c-304">Fedora</span><span class="sxs-lookup"><span data-stu-id="6d91c-304">Fedora</span></span>                         |  <span data-ttu-id="6d91c-305">29, 30</span><span class="sxs-lookup"><span data-stu-id="6d91c-305">29, 30</span></span>                 | <span data-ttu-id="6d91c-306">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-306">x64</span></span> |
| <span data-ttu-id="6d91c-307">Debian</span><span class="sxs-lookup"><span data-stu-id="6d91c-307">Debian</span></span>                         |  <span data-ttu-id="6d91c-308">9</span><span class="sxs-lookup"><span data-stu-id="6d91c-308">9</span></span>                      | <span data-ttu-id="6d91c-309">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6d91c-309">x64, ARM32</span></span> |
| <span data-ttu-id="6d91c-310">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6d91c-310">Ubuntu</span></span>                         |  <span data-ttu-id="6d91c-311">16, 4, 18, 4, 18,10</span><span class="sxs-lookup"><span data-stu-id="6d91c-311">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="6d91c-312">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6d91c-312">x64, ARM32</span></span> |
| <span data-ttu-id="6d91c-313">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="6d91c-313">Linux Mint</span></span>                     |  <span data-ttu-id="6d91c-314">17, 18</span><span class="sxs-lookup"><span data-stu-id="6d91c-314">17, 18</span></span>                 | <span data-ttu-id="6d91c-315">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-315">x64</span></span> |
| <span data-ttu-id="6d91c-316">openSUSE</span><span class="sxs-lookup"><span data-stu-id="6d91c-316">openSUSE</span></span>                       |  <span data-ttu-id="6d91c-317">15 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-317">15+</span></span>                    | <span data-ttu-id="6d91c-318">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-318">x64</span></span> |
| <span data-ttu-id="6d91c-319">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="6d91c-319">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="6d91c-320">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="6d91c-320">12 SP2+</span></span>                | <span data-ttu-id="6d91c-321">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-321">x64</span></span> |
| <span data-ttu-id="6d91c-322">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-322">Alpine Linux</span></span>                   |  <span data-ttu-id="6d91c-323">3.8+</span><span class="sxs-lookup"><span data-stu-id="6d91c-323">3.8+</span></span>                   | <span data-ttu-id="6d91c-324">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-324">x64</span></span> |

<span data-ttu-id="6d91c-325">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,2, consulte [versões do sistema operacional .net core 2,2 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6d91c-325">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="6d91c-326">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6d91c-326">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6d91c-327">O .NET Core 2,1 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="6d91c-327">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="6d91c-328">Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="6d91c-328">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="6d91c-329">O .NET Core 2,1 tem suporte nas seguintes distribuições/versões do Linux:</span><span class="sxs-lookup"><span data-stu-id="6d91c-329">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="6d91c-330">Um `+` símbolo representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="6d91c-330">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6d91c-331">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="6d91c-331">OS</span></span>                             |  <span data-ttu-id="6d91c-332">Versão</span><span class="sxs-lookup"><span data-stu-id="6d91c-332">Version</span></span>                |  <span data-ttu-id="6d91c-333">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="6d91c-333">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="6d91c-334">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-334">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="6d91c-335">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="6d91c-335">6, 7, 8</span></span>                | <span data-ttu-id="6d91c-336">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-336">x64</span></span> |
| <span data-ttu-id="6d91c-337">CentOS</span><span class="sxs-lookup"><span data-stu-id="6d91c-337">CentOS</span></span>                         |  <span data-ttu-id="6d91c-338">7+</span><span class="sxs-lookup"><span data-stu-id="6d91c-338">7+</span></span>                     | <span data-ttu-id="6d91c-339">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-339">x64</span></span> |
| <span data-ttu-id="6d91c-340">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-340">Oracle Linux</span></span>                   |  <span data-ttu-id="6d91c-341">7+</span><span class="sxs-lookup"><span data-stu-id="6d91c-341">7+</span></span>                     | <span data-ttu-id="6d91c-342">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-342">x64</span></span> |
| <span data-ttu-id="6d91c-343">Fedora</span><span class="sxs-lookup"><span data-stu-id="6d91c-343">Fedora</span></span>                         |  <span data-ttu-id="6d91c-344">mais de 30</span><span class="sxs-lookup"><span data-stu-id="6d91c-344">30+</span></span>                    | <span data-ttu-id="6d91c-345">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-345">x64</span></span> |
| <span data-ttu-id="6d91c-346">Debian</span><span class="sxs-lookup"><span data-stu-id="6d91c-346">Debian</span></span>                         |  <span data-ttu-id="6d91c-347">9</span><span class="sxs-lookup"><span data-stu-id="6d91c-347">9</span></span>                      | <span data-ttu-id="6d91c-348">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6d91c-348">x64, ARM32</span></span> |
| <span data-ttu-id="6d91c-349">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6d91c-349">Ubuntu</span></span>                         |  <span data-ttu-id="6d91c-350">16, 4, 18, 4, 19, 4, 19,10</span><span class="sxs-lookup"><span data-stu-id="6d91c-350">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="6d91c-351">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6d91c-351">x64, ARM32</span></span> |
| <span data-ttu-id="6d91c-352">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="6d91c-352">Linux Mint</span></span>                     |  <span data-ttu-id="6d91c-353">17+</span><span class="sxs-lookup"><span data-stu-id="6d91c-353">17+</span></span>                    | <span data-ttu-id="6d91c-354">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-354">x64</span></span> |
| <span data-ttu-id="6d91c-355">openSUSE</span><span class="sxs-lookup"><span data-stu-id="6d91c-355">openSUSE</span></span>                       |  <span data-ttu-id="6d91c-356">15 +</span><span class="sxs-lookup"><span data-stu-id="6d91c-356">15+</span></span>                    | <span data-ttu-id="6d91c-357">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-357">x64</span></span> |
| <span data-ttu-id="6d91c-358">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="6d91c-358">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="6d91c-359">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="6d91c-359">12 SP2+</span></span>                | <span data-ttu-id="6d91c-360">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-360">x64</span></span> |
| <span data-ttu-id="6d91c-361">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-361">Alpine Linux</span></span>                   |  <span data-ttu-id="6d91c-362">3.8+</span><span class="sxs-lookup"><span data-stu-id="6d91c-362">3.8+</span></span>                   | <span data-ttu-id="6d91c-363">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-363">x64</span></span> |

<span data-ttu-id="6d91c-364">Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,1, consulte [versões do sistema operacional .net core 2,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6d91c-364">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="6d91c-365">Dependências de distribuição do Linux</span><span class="sxs-lookup"><span data-stu-id="6d91c-365">Linux distribution dependencies</span></span>

<span data-ttu-id="6d91c-366">Com base em sua distribuição do Linux, talvez seja necessário instalar dependências adicionais.</span><span class="sxs-lookup"><span data-stu-id="6d91c-366">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d91c-367">Os nomes e as versões exatas podem variar ligeiramente na distribuição Linux de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="6d91c-367">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="6d91c-368">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6d91c-368">Ubuntu</span></span>

<span data-ttu-id="6d91c-369">As distribuições do Ubuntu exigem que as seguintes bibliotecas sejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="6d91c-369">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="6d91c-370">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="6d91c-370">liblttng-ust0</span></span>
- <span data-ttu-id="6d91c-371">libcurl3 (para 14.x e 16.x)</span><span class="sxs-lookup"><span data-stu-id="6d91c-371">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="6d91c-372">libcurl4 (para 18.x)</span><span class="sxs-lookup"><span data-stu-id="6d91c-372">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="6d91c-373">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="6d91c-373">libssl1.0.0</span></span>
- <span data-ttu-id="6d91c-374">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="6d91c-374">libkrb5-3</span></span>
- <span data-ttu-id="6d91c-375">zlib1g</span><span class="sxs-lookup"><span data-stu-id="6d91c-375">zlib1g</span></span>
- <span data-ttu-id="6d91c-376">libicu52 (para 14.x)</span><span class="sxs-lookup"><span data-stu-id="6d91c-376">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="6d91c-377">libicu55 (para 16.x)</span><span class="sxs-lookup"><span data-stu-id="6d91c-377">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="6d91c-378">libicu57 (para 17.x)</span><span class="sxs-lookup"><span data-stu-id="6d91c-378">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="6d91c-379">libicu60 (para 18.x)</span><span class="sxs-lookup"><span data-stu-id="6d91c-379">libicu60 (for 18.x)</span></span>

<span data-ttu-id="6d91c-380">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="6d91c-380">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="6d91c-381">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="6d91c-381">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="6d91c-382">A maioria das versões do Ubuntu inclui uma versão anterior do libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="6d91c-382">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="6d91c-383">Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="6d91c-383">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="6d91c-384">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="6d91c-384">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="6d91c-385">CentOS e Fedora</span><span class="sxs-lookup"><span data-stu-id="6d91c-385">CentOS and Fedora</span></span>

<span data-ttu-id="6d91c-386">As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="6d91c-386">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="6d91c-387">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="6d91c-387">lttng-ust</span></span>
- <span data-ttu-id="6d91c-388">libcurl</span><span class="sxs-lookup"><span data-stu-id="6d91c-388">libcurl</span></span>
- <span data-ttu-id="6d91c-389">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="6d91c-389">openssl-libs</span></span>
- <span data-ttu-id="6d91c-390">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="6d91c-390">krb5-libs</span></span>
- <span data-ttu-id="6d91c-391">libicu</span><span class="sxs-lookup"><span data-stu-id="6d91c-391">libicu</span></span>
- <span data-ttu-id="6d91c-392">zlib</span><span class="sxs-lookup"><span data-stu-id="6d91c-392">zlib</span></span>

<span data-ttu-id="6d91c-393">Usuários do Fedora: se a versão do OpenSSL >= 1,1, você precisará instalar o **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="6d91c-393">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="6d91c-394">Para o .NET Core 2,0, as seguintes dependências também são necessárias:</span><span class="sxs-lookup"><span data-stu-id="6d91c-394">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="6d91c-395">libunwind</span><span class="sxs-lookup"><span data-stu-id="6d91c-395">libunwind</span></span>
- <span data-ttu-id="6d91c-396">libuuid</span><span class="sxs-lookup"><span data-stu-id="6d91c-396">libuuid</span></span>

<span data-ttu-id="6d91c-397">Para obter mais informações sobre as dependências, consulte [aplicativos do Linux autocontidos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="6d91c-397">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="6d91c-398">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="6d91c-398">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="6d91c-399">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="6d91c-399">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="6d91c-400">A maioria das versões do CentOS e do Fedora inclui uma versão anterior do libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="6d91c-400">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="6d91c-401">Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="6d91c-401">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="6d91c-402">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="6d91c-402">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="alpine"></a><span data-ttu-id="6d91c-403">Alpine</span><span class="sxs-lookup"><span data-stu-id="6d91c-403">Alpine</span></span>

<span data-ttu-id="6d91c-404">As distribuições alpineáveis exigem que as seguintes bibliotecas sejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="6d91c-404">Alpine distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="6d91c-405">ICU-bibliotecas (isso não é necessário se a globalização estiver desabilitada)</span><span class="sxs-lookup"><span data-stu-id="6d91c-405">icu-libs (this is not needed if globalization is disabled)</span></span>
- <span data-ttu-id="6d91c-406">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="6d91c-406">krb5-libs</span></span>
- <span data-ttu-id="6d91c-407">libcurl</span><span class="sxs-lookup"><span data-stu-id="6d91c-407">libcurl</span></span>
- <span data-ttu-id="6d91c-408">libintl</span><span class="sxs-lookup"><span data-stu-id="6d91c-408">libintl</span></span>
- <span data-ttu-id="6d91c-409">libssl 1.1 (para Alpine 3,9 ou posterior) ou libssl 1.0 (para aqueles mais antigos)</span><span class="sxs-lookup"><span data-stu-id="6d91c-409">libssl1.1 (for Alpine 3.9 or later) or libssl1.0 (for older ones)</span></span>
- <span data-ttu-id="6d91c-410">libstdc++</span><span class="sxs-lookup"><span data-stu-id="6d91c-410">libstdc++</span></span>
- <span data-ttu-id="6d91c-411">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="6d91c-411">lttng-ust</span></span>
- <span data-ttu-id="6d91c-412">numactl (opcional, útil somente para dispositivos com NUMA habilitado)</span><span class="sxs-lookup"><span data-stu-id="6d91c-412">numactl (optional, useful only for devices with NUMA enabled)</span></span>
- <span data-ttu-id="6d91c-413">zlib</span><span class="sxs-lookup"><span data-stu-id="6d91c-413">zlib</span></span>

<span data-ttu-id="6d91c-414">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="6d91c-414">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="6d91c-415">libgdiplus (está disponível somente no repositório de borda/teste)</span><span class="sxs-lookup"><span data-stu-id="6d91c-415">libgdiplus (it is available only in the edge/testing repository)</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="6d91c-416">O .NET Core tem suporte nas seguintes versões do macOS:</span><span class="sxs-lookup"><span data-stu-id="6d91c-416">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="6d91c-417">Um `+` símbolo representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="6d91c-417">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6d91c-418">Versão do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6d91c-418">.NET Core Version</span></span> | <span data-ttu-id="6d91c-419">macOS</span><span class="sxs-lookup"><span data-stu-id="6d91c-419">macOS</span></span>                 | <span data-ttu-id="6d91c-420">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="6d91c-420">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="6d91c-421">3.1</span><span class="sxs-lookup"><span data-stu-id="6d91c-421">3.1</span></span>               | <span data-ttu-id="6d91c-422">Alta serra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="6d91c-422">High Sierra (10.13+)</span></span>  | <span data-ttu-id="6d91c-423">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-423">x64</span></span> | [<span data-ttu-id="6d91c-424">Mais informações</span><span class="sxs-lookup"><span data-stu-id="6d91c-424">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="6d91c-425">3.0</span><span class="sxs-lookup"><span data-stu-id="6d91c-425">3.0</span></span>               | <span data-ttu-id="6d91c-426">Alta serra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="6d91c-426">High Sierra (10.13+)</span></span>  | <span data-ttu-id="6d91c-427">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-427">x64</span></span> | [<span data-ttu-id="6d91c-428">Mais informações</span><span class="sxs-lookup"><span data-stu-id="6d91c-428">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="6d91c-429">2.2</span><span class="sxs-lookup"><span data-stu-id="6d91c-429">2.2</span></span>               | <span data-ttu-id="6d91c-430">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="6d91c-430">Sierra (10.12+)</span></span>       | <span data-ttu-id="6d91c-431">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-431">x64</span></span> | [<span data-ttu-id="6d91c-432">Mais informações</span><span class="sxs-lookup"><span data-stu-id="6d91c-432">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="6d91c-433">2.1</span><span class="sxs-lookup"><span data-stu-id="6d91c-433">2.1</span></span>               | <span data-ttu-id="6d91c-434">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="6d91c-434">Sierra (10.12+)</span></span>       | <span data-ttu-id="6d91c-435">x64</span><span class="sxs-lookup"><span data-stu-id="6d91c-435">x64</span></span> | [<span data-ttu-id="6d91c-436">Mais informações</span><span class="sxs-lookup"><span data-stu-id="6d91c-436">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="6d91c-437">A partir do macOS Catalina (versão 10,15), todo software criado após 1º de junho de 2019 que é distribuído com a ID do desenvolvedor deve ser notarized.</span><span class="sxs-lookup"><span data-stu-id="6d91c-437">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="6d91c-438">Esse requisito se aplica ao tempo de execução do .NET Core, SDK do .NET Core e software criado com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d91c-438">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="6d91c-439">Os instaladores do .NET Core (Runtime e SDK) versões 3,1, 3,0 e 2,1, foram notarizeddos desde 18 de fevereiro de 2020.</span><span class="sxs-lookup"><span data-stu-id="6d91c-439">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="6d91c-440">Versões anteriores liberadas não são notarized.</span><span class="sxs-lookup"><span data-stu-id="6d91c-440">Prior released versions aren't notarized.</span></span> <span data-ttu-id="6d91c-441">Se você executar um aplicativo não notarized, verá um erro semelhante à imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="6d91c-441">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![alerta de notarization Catalina do macOS](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="6d91c-443">Para obter mais informações sobre como o imforced-notarization afeta o .NET Core (e seus aplicativos .NET Core), consulte [trabalhando com o MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="6d91c-443">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="6d91c-444">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="6d91c-444">libgdiplus</span></span>

<span data-ttu-id="6d91c-445">Os aplicativos .NET Core que usam o assembly *System. sorteio. Common* exigem que o libgdiplus seja instalado.</span><span class="sxs-lookup"><span data-stu-id="6d91c-445">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="6d91c-446">Uma maneira fácil de obter o libgdiplus é usando o Gerenciador de pacotes [homebrew ("Brew")](https://brew.sh/) para MacOS.</span><span class="sxs-lookup"><span data-stu-id="6d91c-446">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="6d91c-447">Depois de instalar o *Brew*, instale o libgdiplus executando os seguintes comandos em um prompt de terminal (comando):</span><span class="sxs-lookup"><span data-stu-id="6d91c-447">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="6d91c-448">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6d91c-448">Next steps</span></span>

- <span data-ttu-id="6d91c-449">Para desenvolver e executar aplicativos, instale o [SDK do .NET Core](sdk.md) (inclui o tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="6d91c-449">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="6d91c-450">Para executar aplicativos que outras pessoas criaram, instale o [tempo de execução do .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="6d91c-450">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
