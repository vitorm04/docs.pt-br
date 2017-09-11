---
title: "Pré-requisitos para o .NET Core no Linux"
description: "Versões do Linux e dependências do .NET Core com suporte para desenvolver, implantar e executar aplicativos .NET Core em computadores Linux."
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/01/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: 7bbb8405f39a52d2798fd1dbc78f3116cb3bedbb
ms.openlocfilehash: 9864ffa31caa007cb649a9e6e8913863d9cb2c35
ms.contentlocale: pt-br
ms.lasthandoff: 09/05/2017

---

# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="d6f5e-104">Pré-requisitos para o .NET Core no Linux</span><span class="sxs-lookup"><span data-stu-id="d6f5e-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="d6f5e-105">Este artigo mostra as dependências necessárias para desenvolver aplicativos .NET Core no Linux.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="d6f5e-106">As versões/distribuições do Linux com suporte e as dependências a seguir são aplicáveis às duas maneiras de desenvolver aplicativos .NET Core no Linux:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="d6f5e-107">Linha de comando com seu editor favorito</span><span class="sxs-lookup"><span data-stu-id="d6f5e-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="d6f5e-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d6f5e-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="d6f5e-109">Versões do Linux com suporte</span><span class="sxs-lookup"><span data-stu-id="d6f5e-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d6f5e-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="d6f5e-111">O .NET Core 2.0 trata o Linux como um único sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="d6f5e-112">Há um único build do Linux (por arquitetura de chip) para distribuições Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="d6f5e-113">O .NET Core 2.x tem suporte nas seguintes distribuições/versões x64 do Linux:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-113">NET Core 2.x is supported on the following Linux x64 distributions/versions:</span></span>

 * <span data-ttu-id="d6f5e-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="d6f5e-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="d6f5e-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d6f5e-115">CentOS 7</span></span>
 * <span data-ttu-id="d6f5e-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="d6f5e-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="d6f5e-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="d6f5e-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="d6f5e-118">Debian 8.7 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d6f5e-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="d6f5e-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="d6f5e-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="d6f5e-120">Linux Mint 18, Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="d6f5e-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="d6f5e-121">openSUSE 42.2 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d6f5e-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="d6f5e-122">SUSE Enterprise Linux (SLES) 12 SP2 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d6f5e-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="d6f5e-123">Consulte [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 2.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 2.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d6f5e-124">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="d6f5e-125">O .NET Core 1.x é suportado nas seguintes distribuições/versões x64 do Linux:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-125">.NET Core 1.x is supported on the following Linux x64 distributions/versions:</span></span>

* <span data-ttu-id="d6f5e-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="d6f5e-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="d6f5e-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d6f5e-127">CentOS 7</span></span>
* <span data-ttu-id="d6f5e-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="d6f5e-128">Oracle Linux 7</span></span>
* <span data-ttu-id="d6f5e-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="d6f5e-129">Fedora 24</span></span>
* <span data-ttu-id="d6f5e-130">Debian 8.2 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d6f5e-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="d6f5e-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="d6f5e-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="d6f5e-132">O Ubuntu 16.10 é suportado pela versão de patch mais recente do .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="d6f5e-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="d6f5e-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="d6f5e-133">Linux Mint 17</span></span>
* <span data-ttu-id="d6f5e-134">openSUSE 42.1 ou versões posteriores (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="d6f5e-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="d6f5e-135">Consulte [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 1.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 1.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="d6f5e-136">Dependências de distribuição do Linux</span><span class="sxs-lookup"><span data-stu-id="d6f5e-136">Linux distribution dependencies</span></span>

### <a name="ubuntu"></a><span data-ttu-id="d6f5e-137">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d6f5e-137">Ubuntu</span></span>

<span data-ttu-id="d6f5e-138">As distribuições do Ubuntu requerem que as seguintes bibliotecas estejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-138">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="d6f5e-139">libunwind8</span><span class="sxs-lookup"><span data-stu-id="d6f5e-139">libunwind8</span></span>
* <span data-ttu-id="d6f5e-140">libunwind8-dev</span><span class="sxs-lookup"><span data-stu-id="d6f5e-140">libunwind8-dev</span></span>
* <span data-ttu-id="d6f5e-141">gettext</span><span class="sxs-lookup"><span data-stu-id="d6f5e-141">gettext</span></span>
* <span data-ttu-id="d6f5e-142">libicu-dev</span><span class="sxs-lookup"><span data-stu-id="d6f5e-142">libicu-dev</span></span>
* <span data-ttu-id="d6f5e-143">liblttng-ust-dev</span><span class="sxs-lookup"><span data-stu-id="d6f5e-143">liblttng-ust-dev</span></span>
* <span data-ttu-id="d6f5e-144">libcurl4-openssl-dev</span><span class="sxs-lookup"><span data-stu-id="d6f5e-144">libcurl4-openssl-dev</span></span>
* <span data-ttu-id="d6f5e-145">libssl-dev</span><span class="sxs-lookup"><span data-stu-id="d6f5e-145">libssl-dev</span></span>
* <span data-ttu-id="d6f5e-146">uuid-dev</span><span class="sxs-lookup"><span data-stu-id="d6f5e-146">uuid-dev</span></span>
* <span data-ttu-id="d6f5e-147">unzip</span><span class="sxs-lookup"><span data-stu-id="d6f5e-147">unzip</span></span>

### <a name="centos"></a><span data-ttu-id="d6f5e-148">CentOS</span><span class="sxs-lookup"><span data-stu-id="d6f5e-148">CentOS</span></span>

<span data-ttu-id="d6f5e-149">As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-149">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="d6f5e-150">deltarpm</span><span class="sxs-lookup"><span data-stu-id="d6f5e-150">deltarpm</span></span>
* <span data-ttu-id="d6f5e-151">epel-release</span><span class="sxs-lookup"><span data-stu-id="d6f5e-151">epel-release</span></span>
* <span data-ttu-id="d6f5e-152">unzip</span><span class="sxs-lookup"><span data-stu-id="d6f5e-152">unzip</span></span>
* <span data-ttu-id="d6f5e-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="d6f5e-153">libunwind</span></span>
* <span data-ttu-id="d6f5e-154">gettext</span><span class="sxs-lookup"><span data-stu-id="d6f5e-154">gettext</span></span>
* <span data-ttu-id="d6f5e-155">libcurl-devel</span><span class="sxs-lookup"><span data-stu-id="d6f5e-155">libcurl-devel</span></span>
* <span data-ttu-id="d6f5e-156">openssl-devel</span><span class="sxs-lookup"><span data-stu-id="d6f5e-156">openssl-devel</span></span>
* <span data-ttu-id="d6f5e-157">zlib</span><span class="sxs-lookup"><span data-stu-id="d6f5e-157">zlib</span></span>
* <span data-ttu-id="d6f5e-158">libicu-devel</span><span class="sxs-lookup"><span data-stu-id="d6f5e-158">libicu-devel</span></span>

<span data-ttu-id="d6f5e-159">Para obter mais informações sobre as dependências, confira [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (Aplicativos Linux autossuficientes).</span><span class="sxs-lookup"><span data-stu-id="d6f5e-159">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="d6f5e-160">Instalando as dependências do .NET Core com os instaladores nativos</span><span class="sxs-lookup"><span data-stu-id="d6f5e-160">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="d6f5e-161">Os instaladores nativos do .NET Core estão disponíveis para versões/distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-161">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="d6f5e-162">Os instaladores nativos exigem acesso de administrador (sudo) ao servidor.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-162">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="d6f5e-163">A vantagem de usar um instalador nativo é que todas as dependências nativas do .NET Core são instaladas.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-163">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="d6f5e-164">Os instaladores nativos também instalam o SDK do .NET Core em todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-164">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="d6f5e-165">No Linux, há duas opções de pacote de instalador:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-165">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="d6f5e-166">Usando um gerenciador de pacotes baseado em feed, como apt-get para Ubuntu ou yum para CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-166">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="d6f5e-167">Usando os próprios pacotes, DEB ou RPM.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-167">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="d6f5e-168">Instalações de script com o script do instalador do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6f5e-168">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="d6f5e-169">Os scripts `dotnet-install` são usados para executar uma instalação de não administrador da cadeia de ferramentas da CLI e o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-169">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="d6f5e-170">Baixe os scripts no [repositório GitHub da CLI](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain).</span><span class="sxs-lookup"><span data-stu-id="d6f5e-170">You can download the scripts from the [CLI GitHub repo](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain).</span></span>

<span data-ttu-id="d6f5e-171">O script bash do instalador é usado em cenários de automação e em instalações não realizadas por administrador.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-171">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="d6f5e-172">Esse script também lê as opções do PowerShell para que elas possam ser usadas com o script em sistemas Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-172">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6f5e-173">Antes de executar o script, instale as [dependências](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) necessárias.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-173">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d6f5e-174">Instalar o .NET Core para RHEL (Red Hat Enterprise Linux) 7</span><span class="sxs-lookup"><span data-stu-id="d6f5e-174">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="d6f5e-175">Para instalar o .NET Core no RHEL 7:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-175">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="d6f5e-176">Habilite o canal do .NET no Red Hat, disponível em sua assinatura do RHEL 7 Server.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-176">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="d6f5e-177">Para o Red Hat Enterprise 7 Server, use:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-177">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="d6f5e-178">Para a estação de trabalho do Red Hat Enterprise 7, use:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-178">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="d6f5e-179">Para o nó de computação do Red Hat Enterprise 7 HPC, use:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-179">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="d6f5e-180">Instale a ferramenta scl.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-180">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="d6f5e-181">Instale o .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6f5e-181">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d6f5e-182">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-182">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="d6f5e-183">Instale o SDK e o tempo de execução do .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-183">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="d6f5e-184">Habilite o SDK/tempo de execução do .NET Core 2.0 para o seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-184">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d6f5e-185">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-185">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="d6f5e-186">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-186">**.NET Core 1.1**</span></span>

<span data-ttu-id="d6f5e-187">Instale o SDK e o tempo de execução do .NET Core 1.1:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-187">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="d6f5e-188">Habilite o SDK e o tempo de execução do .NET Core 1.1 para o seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-188">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="d6f5e-189">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-189">**.NET Core 1.0**</span></span>

<span data-ttu-id="d6f5e-190">Instale o SDK e o tempo de execução do .NET Core 1.0:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-190">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="d6f5e-191">Habilite o SDK e o tempo de execução do .NET Core 1.0 para o seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-191">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="d6f5e-192">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-192">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="d6f5e-193">Para que o canal do .NET do Red Hat acesse a ajuda de registro, consulte o [Capítulo 1 do Guia de Introdução do .NET Core 1.1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) no Red Hat.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-193">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="d6f5e-194">Instalar o .NET Core para Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 e Linux Mint 17, Linux Mint 18 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="d6f5e-194">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="d6f5e-195">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-195">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d6f5e-196">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-196">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="d6f5e-197">Registre a chave do Produto da Microsoft como confiável.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-197">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="d6f5e-198">Configure o feed do pacote de host de versão desejado.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-198">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="d6f5e-199">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-199">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="d6f5e-200">**Ubuntu 16.04/Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-200">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="d6f5e-201">**Ubuntu 14.04/Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-201">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="d6f5e-202">Instale o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-202">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="d6f5e-203">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-203">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d6f5e-204">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-204">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="d6f5e-205">Configure o feed do pacote de host de versão desejado.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-205">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="d6f5e-206">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-206">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="d6f5e-207">**Ubuntu 16.04/Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-207">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="d6f5e-208">**Ubuntu 14.04/Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-208">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="d6f5e-209">Instalar o .NET Core 1.x no Ubuntu ou Linux Mint:</span><span class="sxs-lookup"><span data-stu-id="d6f5e-209">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="d6f5e-210">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-210">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="d6f5e-211">Instalar o .NET Core para Debian 8 ou Debian 9 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="d6f5e-211">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="d6f5e-212">Para instalar o .NET Core no Debian 8 ou Debian 9 (64 bits):</span><span class="sxs-lookup"><span data-stu-id="d6f5e-212">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="d6f5e-213">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-213">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="d6f5e-214">Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-214">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d6f5e-215">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-215">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="d6f5e-216">Instale os componentes do sistema.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-216">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="d6f5e-217">Registre a chave do Produto da Microsoft como confiável.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-217">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="d6f5e-218">Registre o feed do Produto da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-218">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="d6f5e-219">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-219">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="d6f5e-220">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-220">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="d6f5e-221">Extraia os binários do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-221">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="d6f5e-222">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-222">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d6f5e-223">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-223">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="d6f5e-224">Obtenha os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-224">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="d6f5e-225">Baixe os binários do SDK do .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="d6f5e-225">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="d6f5e-226">Extraia os binários do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-226">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="d6f5e-227">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-227">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="d6f5e-228">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-228">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="d6f5e-229">Instalar o .NET Core para Fedora 24, Fedora 25 ou Fedora 26 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="d6f5e-229">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="d6f5e-230">Para instalar o .NET Core para Fedora 26, Fedora 25 (.NET Core 2.x) ou Fedora 24 (.NET Core 1.x):</span><span class="sxs-lookup"><span data-stu-id="d6f5e-230">To Install .NET Core for Fedora 26, Fedora 25 (.NET Core 2.x) or Fedora 24 (.NET Core 1.x):</span></span>

1. <span data-ttu-id="d6f5e-231">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-231">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="d6f5e-232">Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-232">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d6f5e-233">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-233">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="d6f5e-234">**Fedora 26 ou Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-234">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="d6f5e-235">Registre a chave de assinatura da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-235">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="d6f5e-236">Adicione o feed do produto dotnet.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-236">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="d6f5e-237">Instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-237">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="d6f5e-238">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-238">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d6f5e-239">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-239">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="d6f5e-240">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="d6f5e-240">**Fedora 24**</span></span>

2. <span data-ttu-id="d6f5e-241">Obtenha os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-241">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="d6f5e-242">Baixe o binário do SDK do .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="d6f5e-242">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="d6f5e-243">Extraia os binários do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-243">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="d6f5e-244">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-244">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="d6f5e-245">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-245">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="d6f5e-246">Instalar o .NET Core para CentOS 7.1 (64 bits) e Oracle Linux 7.1 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="d6f5e-246">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="d6f5e-247">Para instalar o .NET Core para CentOS 7.1 (64 bits) e Oracle Linux 7.1 (64 bits):</span><span class="sxs-lookup"><span data-stu-id="d6f5e-247">To Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="d6f5e-248">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-248">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="d6f5e-249">Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-249">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d6f5e-250">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-250">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="d6f5e-251">Registre a chave de assinatura da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-251">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="d6f5e-252">Adicione o feed do Produto da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-252">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="d6f5e-253">Instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-253">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="d6f5e-254">Adicione dotnet ao seu PATH</span><span class="sxs-lookup"><span data-stu-id="d6f5e-254">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d6f5e-255">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-255">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="d6f5e-256">Obtenha os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-256">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="d6f5e-257">Baixe o binário do SDK do .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="d6f5e-257">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="d6f5e-258">Extraia os binários do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-258">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="d6f5e-259">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-259">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="d6f5e-260">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-260">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="d6f5e-261">Instalar o .NET Core para SUSE Linux Enterprise Server (64 bits)</span><span class="sxs-lookup"><span data-stu-id="d6f5e-261">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="d6f5e-262">Para instalar o .NET Core 2.x para SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bits):</span><span class="sxs-lookup"><span data-stu-id="d6f5e-262">To Install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="d6f5e-263">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-263">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="d6f5e-264">Adicione o feed do produto dotnet.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-264">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="d6f5e-265">Instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-265">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="d6f5e-266">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-266">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="d6f5e-267">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-267">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="d6f5e-268">Instalar o .NET Core para openSUSE (64 bits)</span><span class="sxs-lookup"><span data-stu-id="d6f5e-268">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="d6f5e-269">Para instalar o .NET Core 2.x para openSUSE ou .NET Core 1.x para openSUSE (64 bits):</span><span class="sxs-lookup"><span data-stu-id="d6f5e-269">To Install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="d6f5e-270">Remova todas as versões **prévias anteriores** do .NET Core do sistema.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-270">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="d6f5e-271">Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-271">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d6f5e-272">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-272">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="d6f5e-273">Registre a chave de assinatura da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-273">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="d6f5e-274">Adicione o feed do produto dotnet.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-274">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="d6f5e-275">Instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-275">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="d6f5e-276">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-276">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d6f5e-277">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d6f5e-277">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="d6f5e-278">Obtenha os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-278">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="d6f5e-279">Baixe o binário do SDK do .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="d6f5e-279">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="d6f5e-280">Extraia os binários do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-280">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="d6f5e-281">Adicione dotnet ao seu CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-281">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="d6f5e-282">Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-282">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="d6f5e-283">Se você tiver problemas com a instalação do .NET Core 2.x em uma versão/distribuição do Linux com suporte, consulte o tópico [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) (Problemas conhecidos do 2.0) de suas versões/distribuições instaladas.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-283">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="d6f5e-284">Se você tiver problemas com a instalação do .NET Core 1.x em uma versão/distribuição do Linux com suporte, consulte o tópico [1.0.0 Known issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) (Problemas conhecidos do 1.0.0) e [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) (Problemas conhecidos do 1.0.1) de suas versões/distribuições instaladas.</span><span class="sxs-lookup"><span data-stu-id="d6f5e-284">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>

