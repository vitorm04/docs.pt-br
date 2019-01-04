---
title: Pré-requisitos para o .NET Core no Linux
description: Versões do Linux e dependências do .NET Core com suporte para desenvolver, implantar e executar aplicativos .NET Core em computadores Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 7a2b0b3af97500ab0988e5de7a44713a8c05ccb9
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656044"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="37031-103">Pré-requisitos para o .NET Core no Linux</span><span class="sxs-lookup"><span data-stu-id="37031-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="37031-104">Este artigo mostra as dependências necessárias para desenvolver aplicativos .NET Core no Linux.</span><span class="sxs-lookup"><span data-stu-id="37031-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="37031-105">As versões/distribuições do Linux com suporte e as dependências a seguir são aplicáveis às duas maneiras de desenvolver aplicativos .NET Core no Linux:</span><span class="sxs-lookup"><span data-stu-id="37031-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="37031-106">Linha de comando com seu editor favorito</span><span class="sxs-lookup"><span data-stu-id="37031-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="37031-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="37031-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="37031-108">O pacote do SDK do .NET Core não é necessário para servidores/ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="37031-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="37031-109">Apenas o pacote de tempo de execução do .NET Core é necessário para aplicativos implantados em ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="37031-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="37031-110">O tempo de execução do .NET Core é implantado com aplicativos como parte de uma implantação independente. No entanto, ele deve ser implantado para aplicativos implantados dependentes da estrutura separadamente.</span><span class="sxs-lookup"><span data-stu-id="37031-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="37031-111">Para obter mais informações sobre os tipos de implantação independentes e dependentes da estrutura, consulte [Implantação de aplicativos .NET Core](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="37031-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="37031-112">Consulte também [Aplicativos Linux independentes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) para obter diretrizes específicas.</span><span class="sxs-lookup"><span data-stu-id="37031-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="37031-113">Versões do Linux com suporte</span><span class="sxs-lookup"><span data-stu-id="37031-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="37031-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="37031-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="37031-115">O .NET Core 2.x trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="37031-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="37031-116">Há um único build do Linux (por arquitetura de chip) para distribuições Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="37031-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="37031-117">Para acessar os links de download e saber mais, confira [Downloads do .NET Core 2.2](https://www.microsoft.com/net/download/dotnet-core/2.2) ou [Downloads do .NET Core 2.1](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="37031-117">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="37031-118">Há suporte para o .NET Core 2.x nas seguintes versões/distribuições do Linux:</span><span class="sxs-lookup"><span data-stu-id="37031-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="37031-119">Red Hat Enterprise Linux 7, 6 – 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="37031-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="37031-120">CentOS 7 – 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="37031-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="37031-121">Oracle Linux 7 – 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="37031-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="37031-122">Fedora 28, 27 – 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="37031-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="37031-123">Debian 9 (64 bits, `arm32`), 8.7 ou versões posteriores – 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="37031-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="37031-124">Ubuntu 18.04 (64 bits `arm32`), 16.04, 14.04 - 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="37031-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="37031-125">Linux Mint 18, 17 – 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="37031-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="37031-126">openSUSE 42.3 ou versões posteriores – 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="37031-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="37031-127">SLES (SUSE Linux Enterprise Server) 12 Service Pack 2 ou posterior – 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="37031-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="37031-128">Alpine Linux 3.7 ou versões posteriores – 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="37031-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="37031-129">Confira [Versões de sistema operacional compatíveis com o .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) e [Versões de sistema operacional compatíveis com o .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o .NET Core 2.1 e o .NET Core 2.2, versões de sistema operacional sem suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="37031-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="37031-130">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="37031-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="37031-131">Para acessar os links de download e saber mais, confira [Downloads do .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) ou [Downloads do .NET Core 1.0](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="37031-131">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="37031-132">O .NET Core 1.x é suportado nas seguintes distribuições/versões de 64 bits do Linux (`x86_64` ou `amd64`):</span><span class="sxs-lookup"><span data-stu-id="37031-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="37031-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="37031-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="37031-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="37031-134">CentOS 7</span></span>
* <span data-ttu-id="37031-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="37031-135">Oracle Linux 7</span></span>
* <span data-ttu-id="37031-136">Fedora 28 (.NET Core 1.1), 27</span><span class="sxs-lookup"><span data-stu-id="37031-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="37031-137">Debian 8.2 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="37031-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="37031-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="37031-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="37031-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="37031-139">Linux Mint 17</span></span>
* <span data-ttu-id="37031-140">openSUSE 42.3 ou versões posteriores (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="37031-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="37031-141">Consulte [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 1.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 1.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="37031-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="37031-142">.NET Core 3.0 Versão Prévia 1</span><span class="sxs-lookup"><span data-stu-id="37031-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="37031-143">O .NET Core 3.0 Versão Prévia 1 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="37031-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="37031-144">Há um único build do Linux (por arquitetura de chip) para distribuições Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="37031-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="37031-145">Para obter links de download e mais informações, confira [Downloads do .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="37031-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="37031-146">Há suporte para o .NET Core 3.0 Versão Prévia 1 nas versões/distribuições do Linux a seguir.</span><span class="sxs-lookup"><span data-stu-id="37031-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="37031-147">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="37031-147">OS</span></span>                            | <span data-ttu-id="37031-148">Versão</span><span class="sxs-lookup"><span data-stu-id="37031-148">Version</span></span>               | <span data-ttu-id="37031-149">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="37031-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="37031-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="37031-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="37031-151">6</span><span class="sxs-lookup"><span data-stu-id="37031-151">6</span></span>                     | <span data-ttu-id="37031-152">X64</span><span class="sxs-lookup"><span data-stu-id="37031-152">x64</span></span>
<span data-ttu-id="37031-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="37031-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="37031-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="37031-154">CentOS</span></span><br><span data-ttu-id="37031-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="37031-155">Oracle Linux</span></span>  | <span data-ttu-id="37031-156">7</span><span class="sxs-lookup"><span data-stu-id="37031-156">7</span></span>                     | <span data-ttu-id="37031-157">X64</span><span class="sxs-lookup"><span data-stu-id="37031-157">x64</span></span>
<span data-ttu-id="37031-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="37031-158">Fedora</span></span>                        | <span data-ttu-id="37031-159">28</span><span class="sxs-lookup"><span data-stu-id="37031-159">28</span></span>                    | <span data-ttu-id="37031-160">X64</span><span class="sxs-lookup"><span data-stu-id="37031-160">x64</span></span>
<span data-ttu-id="37031-161">Debian</span><span class="sxs-lookup"><span data-stu-id="37031-161">Debian</span></span>                        | <span data-ttu-id="37031-162">9</span><span class="sxs-lookup"><span data-stu-id="37031-162">9</span></span>                     | <span data-ttu-id="37031-163">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="37031-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="37031-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="37031-164">Ubuntu</span></span>                        | <span data-ttu-id="37031-165">16.04+, 18.04+</span><span class="sxs-lookup"><span data-stu-id="37031-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="37031-166">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="37031-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="37031-167">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="37031-167">Linux Mint</span></span>                    | <span data-ttu-id="37031-168">18</span><span class="sxs-lookup"><span data-stu-id="37031-168">18</span></span>                    | <span data-ttu-id="37031-169">X64</span><span class="sxs-lookup"><span data-stu-id="37031-169">x64</span></span>
<span data-ttu-id="37031-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="37031-170">openSUSE</span></span>                      | <span data-ttu-id="37031-171">42.3+</span><span class="sxs-lookup"><span data-stu-id="37031-171">42.3+</span></span>                 | <span data-ttu-id="37031-172">X64</span><span class="sxs-lookup"><span data-stu-id="37031-172">x64</span></span>
<span data-ttu-id="37031-173">SLES (SUSE Linux Enterprise Server)</span><span class="sxs-lookup"><span data-stu-id="37031-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="37031-174">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="37031-174">12 SP2+</span></span>               | <span data-ttu-id="37031-175">X64</span><span class="sxs-lookup"><span data-stu-id="37031-175">x64</span></span>
<span data-ttu-id="37031-176">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="37031-176">Alpine Linux</span></span>                  | <span data-ttu-id="37031-177">3.8+</span><span class="sxs-lookup"><span data-stu-id="37031-177">3.8+</span></span>                  | <span data-ttu-id="37031-178">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="37031-178">x64, ARM64</span></span>

<span data-ttu-id="37031-179">\* O suporte ao ARM32 e ARM64 começa no Debian 9 e no Ubuntu 16.04.</span><span class="sxs-lookup"><span data-stu-id="37031-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="37031-180">Não há suporte para versões anteriores dessas distribuições em chips ARM.</span><span class="sxs-lookup"><span data-stu-id="37031-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="37031-181">Confira [Versões de sistema operacional compatíveis com o .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o.NET Core 3.0, versões de sistema operacional sem suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="37031-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="37031-182">Para obter mais informações sobre como instalar o .NET Core 3.0 no ARM64, confira [Instalando o .NET Core 3.0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="37031-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>



---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="37031-183">Dependências de distribuição do Linux</span><span class="sxs-lookup"><span data-stu-id="37031-183">Linux distribution dependencies</span></span>

<span data-ttu-id="37031-184">Veja a seguir alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="37031-184">The following are intended to be examples.</span></span> <span data-ttu-id="37031-185">Os nomes e as versões exatas podem variar ligeiramente na distribuição Linux de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="37031-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="37031-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="37031-186">Ubuntu</span></span>

<span data-ttu-id="37031-187">As distribuições do Ubuntu requerem que as seguintes bibliotecas estejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="37031-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="37031-188">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="37031-188">liblttng-ust0</span></span>
* <span data-ttu-id="37031-189">libcurl3</span><span class="sxs-lookup"><span data-stu-id="37031-189">libcurl3</span></span>
* <span data-ttu-id="37031-190">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="37031-190">libssl1.0.0</span></span>
* <span data-ttu-id="37031-191">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="37031-191">libkrb5-3</span></span>
* <span data-ttu-id="37031-192">zlib1g</span><span class="sxs-lookup"><span data-stu-id="37031-192">zlib1g</span></span>
* <span data-ttu-id="37031-193">libicu52 (para 14.x)</span><span class="sxs-lookup"><span data-stu-id="37031-193">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="37031-194">libicu55 (para 16.x)</span><span class="sxs-lookup"><span data-stu-id="37031-194">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="37031-195">libicu57 (para 17.x)</span><span class="sxs-lookup"><span data-stu-id="37031-195">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="37031-196">libicu60 (para 18.x)</span><span class="sxs-lookup"><span data-stu-id="37031-196">libicu60 (for 18.x)</span></span>

<span data-ttu-id="37031-197">Para versões anteriores ao .NET Core 2.1, as seguintes dependências também são necessárias:</span><span class="sxs-lookup"><span data-stu-id="37031-197">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="37031-198">libunwind8</span><span class="sxs-lookup"><span data-stu-id="37031-198">libunwind8</span></span>
* <span data-ttu-id="37031-199">libuuid1</span><span class="sxs-lookup"><span data-stu-id="37031-199">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="37031-200">CentOS e Fedora</span><span class="sxs-lookup"><span data-stu-id="37031-200">CentOS and Fedora</span></span>

<span data-ttu-id="37031-201">As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="37031-201">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="37031-202">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="37031-202">lttng-ust</span></span>
* <span data-ttu-id="37031-203">libcurl</span><span class="sxs-lookup"><span data-stu-id="37031-203">libcurl</span></span>
* <span data-ttu-id="37031-204">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="37031-204">openssl-libs</span></span>
* <span data-ttu-id="37031-205">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="37031-205">krb5-libs</span></span>
* <span data-ttu-id="37031-206">libicu</span><span class="sxs-lookup"><span data-stu-id="37031-206">libicu</span></span>
* <span data-ttu-id="37031-207">zlib</span><span class="sxs-lookup"><span data-stu-id="37031-207">zlib</span></span>

<span data-ttu-id="37031-208">Usuários do Fedora: Se a versão do OpenSSL for >= 1.1, será necessário instalar compat-openssl10.</span><span class="sxs-lookup"><span data-stu-id="37031-208">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="37031-209">Para versões anteriores ao .NET Core 2.1, as seguintes dependências também são necessárias:</span><span class="sxs-lookup"><span data-stu-id="37031-209">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="37031-210">libunwind</span><span class="sxs-lookup"><span data-stu-id="37031-210">libunwind</span></span>
* <span data-ttu-id="37031-211">libuuid</span><span class="sxs-lookup"><span data-stu-id="37031-211">libuuid</span></span>

<span data-ttu-id="37031-212">Para obter mais informações sobre as dependências, confira [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (Aplicativos Linux autossuficientes).</span><span class="sxs-lookup"><span data-stu-id="37031-212">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="37031-213">Instalando as dependências do .NET Core com os instaladores nativos</span><span class="sxs-lookup"><span data-stu-id="37031-213">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="37031-214">Os instaladores nativos do .NET Core estão disponíveis para versões/distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="37031-214">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="37031-215">Os instaladores nativos exigem acesso de administrador (sudo) ao servidor.</span><span class="sxs-lookup"><span data-stu-id="37031-215">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="37031-216">A vantagem de usar um instalador nativo é que todas as dependências nativas do .NET Core são instaladas.</span><span class="sxs-lookup"><span data-stu-id="37031-216">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="37031-217">Os instaladores nativos também instalam o SDK do .NET Core em todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="37031-217">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="37031-218">No Linux, há duas opções de pacote de instalador:</span><span class="sxs-lookup"><span data-stu-id="37031-218">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="37031-219">Usando um gerenciador de pacotes baseado em feed, como apt-get para Ubuntu ou yum para CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="37031-219">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="37031-220">Usando os próprios pacotes, DEB ou RPM.</span><span class="sxs-lookup"><span data-stu-id="37031-220">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="37031-221">Instalações de script com o script do instalador do .NET Core</span><span class="sxs-lookup"><span data-stu-id="37031-221">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="37031-222">Os [scripts dotnet-install](./tools/dotnet-install-script.md) são usados para executar uma instalação que não é de administrador da cadeia de ferramentas da CLI e o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="37031-222">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="37031-223">É possível baixar o script em [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span><span class="sxs-lookup"><span data-stu-id="37031-223">You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span></span>

<span data-ttu-id="37031-224">O padrão do script é instalar a versão "LTS" mais recente, que é .NET Core 1.1 no momento.</span><span class="sxs-lookup"><span data-stu-id="37031-224">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="37031-225">Para instalar o .NET Core 2.1, execute o script com a seguinte opção:</span><span class="sxs-lookup"><span data-stu-id="37031-225">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="37031-226">O script bash do instalador é usado em cenários de automação e em instalações não realizadas por administrador.</span><span class="sxs-lookup"><span data-stu-id="37031-226">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="37031-227">Esse script também lê as opções do PowerShell para que elas possam ser usadas com o script em sistemas Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="37031-227">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="37031-228">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="37031-228">Troubleshoot</span></span>

<span data-ttu-id="37031-229">Se você tiver problemas com a instalação do .NET Core em uma versão/distribuição do Linux compatível, consulte os tópicos a seguir relacionadas a suas versões/distribuições instaladas:</span><span class="sxs-lookup"><span data-stu-id="37031-229">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="37031-230">Problemas conhecidos do .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="37031-230">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="37031-231">Problemas conhecidos do .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="37031-231">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="37031-232">Problemas conhecidos do .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="37031-232">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="37031-233">Problemas conhecidos do .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="37031-233">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="37031-234">Problemas conhecidos do .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="37031-234">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
