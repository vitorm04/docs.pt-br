---
title: Instalar o .NET no Ubuntu – .NET
description: Demonstra as várias maneiras de instalar o SDK do .NET e o tempo de execução do .NET no Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 419bcf3ccd011cadba8f8c64e195d7dbdbf7e241
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507008"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="2226e-103">Instalar o SDK do .NET ou o tempo de execução do .NET no Ubuntu</span><span class="sxs-lookup"><span data-stu-id="2226e-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="2226e-104">O .NET tem suporte no Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="2226e-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="2226e-105">Este artigo descreve como instalar o .NET no Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="2226e-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="2226e-106">Quando uma versão do Ubuntu ficar sem suporte, o .NET não terá mais suporte com essa versão.</span><span class="sxs-lookup"><span data-stu-id="2226e-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="2226e-107">No entanto, essas instruções podem ajudá-lo a obter o .NET em execução nessas versões, mesmo que não haja suporte.</span><span class="sxs-lookup"><span data-stu-id="2226e-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="2226e-108">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="2226e-108">Supported distributions</span></span>

<span data-ttu-id="2226e-109">A tabela a seguir é uma lista de versões do .NET com suporte no momento e as versões do Ubuntu nas quais elas têm suporte.</span><span class="sxs-lookup"><span data-stu-id="2226e-109">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="2226e-110">Essas versões permanecem com suporte até que a versão do [.net atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Ubuntu atinja o fim da vida útil](https://wiki.ubuntu.com/Releases).</span><span class="sxs-lookup"><span data-stu-id="2226e-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="2226e-111">Um ✔️ indica que a versão do Ubuntu ou do .NET ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="2226e-111">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="2226e-112">Um ❌ indica que a versão do Ubuntu ou do .net não tem suporte nessa versão do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="2226e-112">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="2226e-113">Quando uma versão do Ubuntu e uma versão do .NET têm ✔️, essa combinação de so e .NET é suportada.</span><span class="sxs-lookup"><span data-stu-id="2226e-113">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="2226e-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="2226e-114">Ubuntu</span></span>                   | <span data-ttu-id="2226e-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2226e-115">.NET Core 2.1</span></span> | <span data-ttu-id="2226e-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="2226e-116">.NET Core 3.1</span></span> | <span data-ttu-id="2226e-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="2226e-117">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="2226e-118">✔️ [20,10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="2226e-118">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="2226e-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2226e-119">✔️ 2.1</span></span>        | <span data-ttu-id="2226e-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2226e-120">✔️ 3.1</span></span>        | <span data-ttu-id="2226e-121">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="2226e-121">✔️ 5.0</span></span> |
| <span data-ttu-id="2226e-122">✔️ [20, 4 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="2226e-122">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="2226e-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2226e-123">✔️ 2.1</span></span>        | <span data-ttu-id="2226e-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2226e-124">✔️ 3.1</span></span>        | <span data-ttu-id="2226e-125">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="2226e-125">✔️ 5.0</span></span> |
| <span data-ttu-id="2226e-126">❌[19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="2226e-126">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="2226e-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2226e-127">✔️ 2.1</span></span>        | <span data-ttu-id="2226e-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2226e-128">✔️ 3.1</span></span>        | <span data-ttu-id="2226e-129">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="2226e-129">✔️ 5.0</span></span> |
| <span data-ttu-id="2226e-130">❌[19, 4](#1904-)</span><span class="sxs-lookup"><span data-stu-id="2226e-130">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="2226e-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2226e-131">✔️ 2.1</span></span>        | <span data-ttu-id="2226e-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2226e-132">✔️ 3.1</span></span>        | <span data-ttu-id="2226e-133">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="2226e-133">❌ 5.0</span></span> |
| <span data-ttu-id="2226e-134">❌[18,10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="2226e-134">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="2226e-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2226e-135">✔️ 2.1</span></span>        | <span data-ttu-id="2226e-136">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="2226e-136">❌ 3.1</span></span>        | <span data-ttu-id="2226e-137">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="2226e-137">❌ 5.0</span></span> |
| <span data-ttu-id="2226e-138">✔️ [18, 4 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="2226e-138">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="2226e-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2226e-139">✔️ 2.1</span></span>        | <span data-ttu-id="2226e-140">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2226e-140">✔️ 3.1</span></span>        | <span data-ttu-id="2226e-141">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="2226e-141">✔️ 5.0</span></span> |
| <span data-ttu-id="2226e-142">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="2226e-142">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="2226e-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2226e-143">✔️ 2.1</span></span>        | <span data-ttu-id="2226e-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="2226e-144">❌ 3.1</span></span>        | <span data-ttu-id="2226e-145">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="2226e-145">❌ 5.0</span></span> |
| <span data-ttu-id="2226e-146">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="2226e-146">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="2226e-147">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2226e-147">✔️ 2.1</span></span>        | <span data-ttu-id="2226e-148">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="2226e-148">❌ 3.1</span></span>        | <span data-ttu-id="2226e-149">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="2226e-149">❌ 5.0</span></span> |
| <span data-ttu-id="2226e-150">❌[16,10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="2226e-150">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="2226e-151">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="2226e-151">❌ 2.1</span></span>        | <span data-ttu-id="2226e-152">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="2226e-152">❌ 3.1</span></span>        | <span data-ttu-id="2226e-153">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="2226e-153">❌ 5.0</span></span> |
| <span data-ttu-id="2226e-154">✔️ [16, 4 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="2226e-154">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="2226e-155">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2226e-155">✔️ 2.1</span></span>        | <span data-ttu-id="2226e-156">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2226e-156">✔️ 3.1</span></span>        | <span data-ttu-id="2226e-157">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="2226e-157">✔️ 5.0</span></span> |

<span data-ttu-id="2226e-158">Não há mais suporte para as seguintes versões do .NET.</span><span class="sxs-lookup"><span data-stu-id="2226e-158">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="2226e-159">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="2226e-159">The downloads for these still remain published:</span></span>

- <span data-ttu-id="2226e-160">3.0</span><span class="sxs-lookup"><span data-stu-id="2226e-160">3.0</span></span>
- <span data-ttu-id="2226e-161">2.2</span><span class="sxs-lookup"><span data-stu-id="2226e-161">2.2</span></span>
- <span data-ttu-id="2226e-162">2.0</span><span class="sxs-lookup"><span data-stu-id="2226e-162">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="2226e-163">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="2226e-163">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2010-"></a><span data-ttu-id="2226e-164">20,10 ✔️</span><span class="sxs-lookup"><span data-stu-id="2226e-164">20.10 ✔️</span></span>

<span data-ttu-id="2226e-165">Os feeds de pacote .NET 5 e .NET Core 3,1 para Ubuntu 20,10 atualmente têm um problema.</span><span class="sxs-lookup"><span data-stu-id="2226e-165">.NET 5 and .NET Core 3.1 package feeds for Ubuntu 20.10 currently have an issue.</span></span> <span data-ttu-id="2226e-166">Para obter mais informações sobre o problema, consulte o [problema do GitHub dotnet/Core # 5549](https://github.com/dotnet/core/issues/5549).</span><span class="sxs-lookup"><span data-stu-id="2226e-166">For more information about the issue, see [GitHub issue dotnet/core#5549](https://github.com/dotnet/core/issues/5549).</span></span> <span data-ttu-id="2226e-167">Este artigo será atualizado quando o problema for resolvido.</span><span class="sxs-lookup"><span data-stu-id="2226e-167">This article will be updated when the issue is resolved.</span></span>

<span data-ttu-id="2226e-168">Para instalar o .NET 5 ou o .NET Core 3,1 no Ubuntu 20,10, siga as instruções para [20, 4](#2004-).</span><span class="sxs-lookup"><span data-stu-id="2226e-168">To install .NET 5 or .NET Core 3.1 on Ubuntu 20.10, follow the instructions for [20.04](#2004-).</span></span>

## <a name="2004-"></a><span data-ttu-id="2226e-169">20, 4 ✔️</span><span class="sxs-lookup"><span data-stu-id="2226e-169">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="2226e-170">19,10 ❌</span><span class="sxs-lookup"><span data-stu-id="2226e-170">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="2226e-171">19, 4 ❌</span><span class="sxs-lookup"><span data-stu-id="2226e-171">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="2226e-172">18,10 ❌</span><span class="sxs-lookup"><span data-stu-id="2226e-172">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="2226e-173">18, 4 ✔️</span><span class="sxs-lookup"><span data-stu-id="2226e-173">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="2226e-174">17,10 ❌</span><span class="sxs-lookup"><span data-stu-id="2226e-174">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="2226e-175">17, 4 ❌</span><span class="sxs-lookup"><span data-stu-id="2226e-175">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="2226e-176">16,10 ❌</span><span class="sxs-lookup"><span data-stu-id="2226e-176">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="2226e-177">16, 4 ✔️</span><span class="sxs-lookup"><span data-stu-id="2226e-177">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="2226e-178">SDK de atualização de APT ou tempo de execução</span><span class="sxs-lookup"><span data-stu-id="2226e-178">APT update SDK or runtime</span></span>

<span data-ttu-id="2226e-179">Quando uma nova versão de patch estiver disponível para o .NET, você poderá simplesmente atualizá-la por meio de APT com os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="2226e-179">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="2226e-180">Solução de problemas da APT</span><span class="sxs-lookup"><span data-stu-id="2226e-180">APT troubleshooting</span></span>

<span data-ttu-id="2226e-181">Esta seção fornece informações sobre erros comuns que você pode obter ao usar a APT para instalar o .NET.</span><span class="sxs-lookup"><span data-stu-id="2226e-181">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="2226e-182">Não é possível localizar o pacote</span><span class="sxs-lookup"><span data-stu-id="2226e-182">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="2226e-183">Não foi possível \\ instalar alguns pacotes</span><span class="sxs-lookup"><span data-stu-id="2226e-183">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="2226e-184">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="2226e-184">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="2226e-185">Snap</span><span class="sxs-lookup"><span data-stu-id="2226e-185">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="2226e-186">Dependências</span><span class="sxs-lookup"><span data-stu-id="2226e-186">Dependencies</span></span>

<span data-ttu-id="2226e-187">Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você.</span><span class="sxs-lookup"><span data-stu-id="2226e-187">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="2226e-188">Mas, se você instalar o .NET manualmente ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="2226e-188">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="2226e-189">libc6</span><span class="sxs-lookup"><span data-stu-id="2226e-189">libc6</span></span>
- <span data-ttu-id="2226e-190">libgcc1</span><span class="sxs-lookup"><span data-stu-id="2226e-190">libgcc1</span></span>
- <span data-ttu-id="2226e-191">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="2226e-191">libgssapi-krb5-2</span></span>
- <span data-ttu-id="2226e-192">libicu52 (para 14.x)</span><span class="sxs-lookup"><span data-stu-id="2226e-192">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="2226e-193">libicu55 (para 16.x)</span><span class="sxs-lookup"><span data-stu-id="2226e-193">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="2226e-194">libicu60 (para 18.x)</span><span class="sxs-lookup"><span data-stu-id="2226e-194">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="2226e-195">libicu66 (para 20. x)</span><span class="sxs-lookup"><span data-stu-id="2226e-195">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="2226e-196">libssl 1.0.0 (para 14. x, 16. x)</span><span class="sxs-lookup"><span data-stu-id="2226e-196">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="2226e-197">libssl 1.1 (para 18. x, 20. x)</span><span class="sxs-lookup"><span data-stu-id="2226e-197">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="2226e-198">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="2226e-198">libstdc++6</span></span>
- <span data-ttu-id="2226e-199">zlib1g</span><span class="sxs-lookup"><span data-stu-id="2226e-199">zlib1g</span></span>

<span data-ttu-id="2226e-200">Para aplicativos .NET que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="2226e-200">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="2226e-201">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="2226e-201">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="2226e-202">Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="2226e-202">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="2226e-203">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="2226e-203">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="2226e-204">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="2226e-204">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="2226e-205">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="2226e-205">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="2226e-206">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2226e-206">Next steps</span></span>

- [<span data-ttu-id="2226e-207">Tutorial: criar um aplicativo de console com o SDK do .NET usando o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2226e-207">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
