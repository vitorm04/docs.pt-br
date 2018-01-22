---
title: "Pré-requisitos para o .NET Core no Linux"
description: "Versões do Linux e dependências do .NET Core com suporte para desenvolver, implantar e executar aplicativos .NET Core em computadores Linux."
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 12/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: d3c5dde443f848831f7c0585633339c35213357b
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="11613-104">Pré-requisitos para o .NET Core no Linux</span><span class="sxs-lookup"><span data-stu-id="11613-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="11613-105">Este artigo mostra as dependências necessárias para desenvolver aplicativos .NET Core no Linux.</span><span class="sxs-lookup"><span data-stu-id="11613-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="11613-106">As versões/distribuições do Linux com suporte e as dependências a seguir são aplicáveis às duas maneiras de desenvolver aplicativos .NET Core no Linux:</span><span class="sxs-lookup"><span data-stu-id="11613-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="11613-107">Linha de comando com seu editor favorito</span><span class="sxs-lookup"><span data-stu-id="11613-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="11613-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="11613-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="11613-109">Versões do Linux com suporte</span><span class="sxs-lookup"><span data-stu-id="11613-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="11613-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="11613-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="11613-111">O .NET Core 2.0 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="11613-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="11613-112">Há um único build do Linux (por arquitetura de chip) para distribuições Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="11613-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="11613-113">O .NET Core 2.x é suportado nas seguintes distribuições/versões de 64 bits do Linux (`x86_64` ou `amd64`):</span><span class="sxs-lookup"><span data-stu-id="11613-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="11613-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="11613-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="11613-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11613-115">CentOS 7</span></span>
 * <span data-ttu-id="11613-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="11613-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="11613-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="11613-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="11613-118">Debian 8.7 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="11613-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="11613-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="11613-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="11613-120">Linux Mint 18, Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="11613-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="11613-121">openSUSE 42.2 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="11613-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="11613-122">SUSE Enterprise Linux (SLES) 12 SP2 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="11613-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="11613-123">Consulte [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 2.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 2.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="11613-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="11613-124">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="11613-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="11613-125">O .NET Core 1.x é suportado nas seguintes distribuições/versões de 64 bits do Linux (`x86_64` ou `amd64`):</span><span class="sxs-lookup"><span data-stu-id="11613-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="11613-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="11613-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="11613-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11613-127">CentOS 7</span></span>
* <span data-ttu-id="11613-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="11613-128">Oracle Linux 7</span></span>
* <span data-ttu-id="11613-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="11613-129">Fedora 24</span></span>
* <span data-ttu-id="11613-130">Debian 8.2 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="11613-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="11613-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="11613-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="11613-132">O Ubuntu 16.10 é suportado pela versão de patch mais recente do .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="11613-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="11613-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="11613-133">Linux Mint 17</span></span>
* <span data-ttu-id="11613-134">openSUSE 42.1 ou versões posteriores (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="11613-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="11613-135">Consulte [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 1.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 1.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="11613-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="11613-136">Dependências de distribuição do Linux</span><span class="sxs-lookup"><span data-stu-id="11613-136">Linux distribution dependencies</span></span>

<span data-ttu-id="11613-137">Veja a seguir alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="11613-137">The following are intended to be examples.</span></span> <span data-ttu-id="11613-138">Os nomes e as versões exatas podem variar ligeiramente na distribuição Linux de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="11613-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="11613-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="11613-139">Ubuntu</span></span>

<span data-ttu-id="11613-140">As distribuições do Ubuntu requerem que as seguintes bibliotecas estejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="11613-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="11613-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="11613-141">libunwind8</span></span>
* <span data-ttu-id="11613-142">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="11613-142">liblttng-ust0</span></span>
* <span data-ttu-id="11613-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="11613-143">libcurl3</span></span>
* <span data-ttu-id="11613-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="11613-144">libssl1.0.0</span></span>
* <span data-ttu-id="11613-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="11613-145">libuuid1</span></span>
* <span data-ttu-id="11613-146">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="11613-146">libkrb5-3</span></span>
* <span data-ttu-id="11613-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="11613-147">zlib1g</span></span>
* <span data-ttu-id="11613-148">libicu52 (para 14.X)</span><span class="sxs-lookup"><span data-stu-id="11613-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="11613-149">libicu55 (para 16.X)</span><span class="sxs-lookup"><span data-stu-id="11613-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="11613-150">libicu57 (para 17.X)</span><span class="sxs-lookup"><span data-stu-id="11613-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="11613-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="11613-151">CentOS</span></span>

<span data-ttu-id="11613-152">As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="11613-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="11613-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="11613-153">libunwind</span></span>
* <span data-ttu-id="11613-154">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="11613-154">lttng-ust</span></span>
* <span data-ttu-id="11613-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="11613-155">libcurl</span></span>
* <span data-ttu-id="11613-156">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="11613-156">openssl-libs</span></span>
* <span data-ttu-id="11613-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="11613-157">libuuid</span></span>
* <span data-ttu-id="11613-158">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="11613-158">krb5-libs</span></span>
* <span data-ttu-id="11613-159">libicu</span><span class="sxs-lookup"><span data-stu-id="11613-159">libicu</span></span>
* <span data-ttu-id="11613-160">zlib</span><span class="sxs-lookup"><span data-stu-id="11613-160">zlib</span></span>

<span data-ttu-id="11613-161">Para obter mais informações sobre as dependências, confira [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (Aplicativos Linux autossuficientes).</span><span class="sxs-lookup"><span data-stu-id="11613-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="11613-162">Instalando as dependências do .NET Core com os instaladores nativos</span><span class="sxs-lookup"><span data-stu-id="11613-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="11613-163">Os instaladores nativos do .NET Core estão disponíveis para versões/distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="11613-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="11613-164">Os instaladores nativos exigem acesso de administrador (sudo) ao servidor.</span><span class="sxs-lookup"><span data-stu-id="11613-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="11613-165">A vantagem de usar um instalador nativo é que todas as dependências nativas do .NET Core são instaladas.</span><span class="sxs-lookup"><span data-stu-id="11613-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="11613-166">Os instaladores nativos também instalam o SDK do .NET Core em todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="11613-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="11613-167">No Linux, há duas opções de pacote de instalador:</span><span class="sxs-lookup"><span data-stu-id="11613-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="11613-168">Usando um gerenciador de pacotes baseado em feed, como apt-get para Ubuntu ou yum para CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="11613-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="11613-169">Usando os próprios pacotes, DEB ou RPM.</span><span class="sxs-lookup"><span data-stu-id="11613-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="11613-170">Instalações de script com o script do instalador do .NET Core</span><span class="sxs-lookup"><span data-stu-id="11613-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="11613-171">Os scripts `dotnet-install` são usados para executar uma instalação de não administrador da cadeia de ferramentas da CLI e o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="11613-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="11613-172">Baixe o script em https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="11613-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="11613-173">O script bash do instalador é usado em cenários de automação e em instalações não realizadas por administrador.</span><span class="sxs-lookup"><span data-stu-id="11613-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="11613-174">Esse script também lê as opções do PowerShell para que elas possam ser usadas com o script em sistemas Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="11613-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11613-175">Antes de executar o script, instale as [dependências](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) necessárias.</span><span class="sxs-lookup"><span data-stu-id="11613-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="11613-176">Instalar o .NET Core para RHEL (Red Hat Enterprise Linux) 7</span><span class="sxs-lookup"><span data-stu-id="11613-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="11613-177">Para instalar o .NET Core no RHEL 7:</span><span class="sxs-lookup"><span data-stu-id="11613-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="11613-178">Habilite o canal do .NET no Red Hat, disponível em sua assinatura do RHEL 7 Server.</span><span class="sxs-lookup"><span data-stu-id="11613-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="11613-179">Para o Red Hat Enterprise 7 Server, use:</span><span class="sxs-lookup"><span data-stu-id="11613-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="11613-180">Para a estação de trabalho do Red Hat Enterprise 7, use:</span><span class="sxs-lookup"><span data-stu-id="11613-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="11613-181">Para o nó de computação do Red Hat Enterprise 7 HPC, use:</span><span class="sxs-lookup"><span data-stu-id="11613-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="11613-182">Instale a ferramenta scl.</span><span class="sxs-lookup"><span data-stu-id="11613-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="11613-183">Instale o .NET Core</span><span class="sxs-lookup"><span data-stu-id="11613-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="11613-184">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="11613-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="11613-185">Instale o SDK e o tempo de execução do .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="11613-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="11613-186">Habilite o SDK/tempo de execução do .NET Core 2.0 para o seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="11613-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="11613-187">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="11613-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="11613-188">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="11613-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="11613-189">Instale o SDK e o tempo de execução do .NET Core 1.1:</span><span class="sxs-lookup"><span data-stu-id="11613-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="11613-190">Habilite o SDK e o tempo de execução do .NET Core 1.1 para o seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="11613-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="11613-191">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="11613-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="11613-192">Instale o SDK e o tempo de execução do .NET Core 1.0:</span><span class="sxs-lookup"><span data-stu-id="11613-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="11613-193">Habilite o SDK e o tempo de execução do .NET Core 1.0 para o seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="11613-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="11613-194">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="11613-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="11613-195">Para que o canal do .NET do Red Hat acesse a ajuda de registro, consulte o [Capítulo 1 do Guia de Introdução do .NET Core 1.1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) no Red Hat.</span><span class="sxs-lookup"><span data-stu-id="11613-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="11613-196">Instalar o .NET Core para Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 e Linux Mint 17, Linux Mint 18 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="11613-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="11613-197">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="11613-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="11613-198">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="11613-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="11613-199">Registre a chave do Produto da Microsoft como confiável.</span><span class="sxs-lookup"><span data-stu-id="11613-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="11613-200">Configure o feed do pacote de host de versão desejado.</span><span class="sxs-lookup"><span data-stu-id="11613-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="11613-201">**Ubuntu 17.10**</span><span class="sxs-lookup"><span data-stu-id="11613-201">**Ubuntu 17.10**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-artful-prod artful main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```
   <span data-ttu-id="11613-202">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="11613-202">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="11613-203">**Ubuntu 16.04/Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="11613-203">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="11613-204">**Ubuntu 14.04/Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="11613-204">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="11613-205">Instale o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11613-205">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.1.3
   ```

4. <span data-ttu-id="11613-206">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="11613-206">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="11613-207">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="11613-207">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="11613-208">Configure o feed do pacote de host de versão desejado.</span><span class="sxs-lookup"><span data-stu-id="11613-208">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="11613-209">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="11613-209">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="11613-210">**Ubuntu 16.04/Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="11613-210">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="11613-211">**Ubuntu 14.04/Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="11613-211">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="11613-212">Instalar o .NET Core 1.x no Ubuntu ou Linux Mint:</span><span class="sxs-lookup"><span data-stu-id="11613-212">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="11613-213">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="11613-213">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="11613-214">Instalar o .NET Core para Debian 8 ou Debian 9 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="11613-214">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="11613-215">Para instalar o .NET Core no Debian 8 ou Debian 9 (64 bits):</span><span class="sxs-lookup"><span data-stu-id="11613-215">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="11613-216">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="11613-216">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="11613-217">Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.</span><span class="sxs-lookup"><span data-stu-id="11613-217">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="11613-218">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="11613-218">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="11613-219">Instale os componentes do sistema.</span><span class="sxs-lookup"><span data-stu-id="11613-219">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="11613-220">Registre a chave do Produto da Microsoft como confiável.</span><span class="sxs-lookup"><span data-stu-id="11613-220">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="11613-221">Registre o feed do Produto da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="11613-221">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="11613-222">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="11613-222">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="11613-223">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="11613-223">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="11613-224">Instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11613-224">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="11613-225">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="11613-225">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="11613-226">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="11613-226">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="11613-227">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="11613-227">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="11613-228">Obtenha os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="11613-228">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="11613-229">Baixe os binários do SDK do .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="11613-229">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="11613-230">Extraia os binários do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11613-230">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="11613-231">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="11613-231">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="11613-232">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="11613-232">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="11613-233">Instalar o .NET Core para Fedora 24, Fedora 25 ou Fedora 26 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="11613-233">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="11613-234">Para instalar o .NET Core 2.x no Fedora 26 ou Fedora 25, ou o .NET Core 1.x no Fedora 24:</span><span class="sxs-lookup"><span data-stu-id="11613-234">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="11613-235">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="11613-235">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="11613-236">Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.</span><span class="sxs-lookup"><span data-stu-id="11613-236">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="11613-237">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="11613-237">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="11613-238">**Fedora 26 ou Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="11613-238">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="11613-239">Registre a chave de assinatura da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="11613-239">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="11613-240">Adicione o feed do produto dotnet.</span><span class="sxs-lookup"><span data-stu-id="11613-240">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="11613-241">Instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11613-241">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="11613-242">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="11613-242">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="11613-243">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="11613-243">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="11613-244">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="11613-244">**Fedora 24**</span></span>

2. <span data-ttu-id="11613-245">Obtenha os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="11613-245">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="11613-246">Baixe o binário do SDK do .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="11613-246">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="11613-247">Extraia os binários do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11613-247">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="11613-248">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="11613-248">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="11613-249">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="11613-249">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="11613-250">Instalar o .NET Core para CentOS 7.1 (64 bits) e Oracle Linux 7.1 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="11613-250">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="11613-251">Para instalar o .NET Core para CentOS 7.1 (64 bits) e Oracle Linux 7.1 (64 bits):</span><span class="sxs-lookup"><span data-stu-id="11613-251">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="11613-252">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="11613-252">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="11613-253">Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.</span><span class="sxs-lookup"><span data-stu-id="11613-253">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="11613-254">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="11613-254">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="11613-255">Registre a chave de assinatura da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="11613-255">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="11613-256">Adicione o feed do Produto da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="11613-256">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="11613-257">Instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11613-257">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="11613-258">Adicione dotnet ao seu PATH</span><span class="sxs-lookup"><span data-stu-id="11613-258">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="11613-259">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="11613-259">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="11613-260">Obtenha os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="11613-260">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="11613-261">Baixe o binário do SDK do .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="11613-261">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="11613-262">Extraia os binários do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11613-262">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="11613-263">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="11613-263">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="11613-264">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="11613-264">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="11613-265">Instalar o .NET Core para SUSE Linux Enterprise Server (64 bits)</span><span class="sxs-lookup"><span data-stu-id="11613-265">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="11613-266">Para instalar o .NET Core 2.x para SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bits):</span><span class="sxs-lookup"><span data-stu-id="11613-266">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="11613-267">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="11613-267">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="11613-268">Adicione o feed do produto dotnet.</span><span class="sxs-lookup"><span data-stu-id="11613-268">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="11613-269">Instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11613-269">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="11613-270">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="11613-270">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="11613-271">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="11613-271">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="11613-272">Instalar o .NET Core para openSUSE (64 bits)</span><span class="sxs-lookup"><span data-stu-id="11613-272">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="11613-273">Para instalar o .NET Core 2.x para openSUSE ou .NET Core 1.x para openSUSE (64 bits):</span><span class="sxs-lookup"><span data-stu-id="11613-273">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="11613-274">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="11613-274">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="11613-275">Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.</span><span class="sxs-lookup"><span data-stu-id="11613-275">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="11613-276">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="11613-276">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="11613-277">Registre a chave de assinatura da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="11613-277">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="11613-278">Adicione o feed do produto dotnet.</span><span class="sxs-lookup"><span data-stu-id="11613-278">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="11613-279">Instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11613-279">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="11613-280">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="11613-280">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="11613-281">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="11613-281">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="11613-282">Obtenha os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="11613-282">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="11613-283">Baixe o binário do SDK do .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="11613-283">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="11613-284">Extraia os binários do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11613-284">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="11613-285">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="11613-285">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="11613-286">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="11613-286">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="11613-287">Se você tiver problemas com a instalação do .NET Core 2.x em uma versão/distribuição do Linux com suporte, consulte o tópico [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) (Problemas conhecidos do 2.0) de suas versões/distribuições instaladas.</span><span class="sxs-lookup"><span data-stu-id="11613-287">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="11613-288">Se você tiver problemas com a instalação do .NET Core 1.x em uma versão/distribuição do Linux com suporte, consulte o tópico [1.0.0 Known issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) (Problemas conhecidos do 1.0.0) e [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) (Problemas conhecidos do 1.0.1) de suas versões/distribuições instaladas.</span><span class="sxs-lookup"><span data-stu-id="11613-288">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
