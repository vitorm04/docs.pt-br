---
title: Instalar o .NET Core no Ubuntu – .NET Core
description: Demonstra as várias maneiras de instalar o SDK do .NET Core e o tempo de execução do .NET Core no Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: ed4f5b914d03cfb072ee4ba168c67262e0d40c08
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619423"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a><span data-ttu-id="351ae-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no Ubuntu</span><span class="sxs-lookup"><span data-stu-id="351ae-103">Install .NET Core SDK or .NET Core Runtime on Ubuntu</span></span>

<span data-ttu-id="351ae-104">O .NET Core tem suporte no Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="351ae-104">.NET Core is supported on Ubuntu.</span></span> <span data-ttu-id="351ae-105">Este artigo descreve como instalar o .NET Core no Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="351ae-105">This article describes how to install .NET Core on Ubuntu.</span></span> <span data-ttu-id="351ae-106">Quando uma versão do Ubuntu ficar sem suporte, o .NET Core não terá mais suporte nessa versão.</span><span class="sxs-lookup"><span data-stu-id="351ae-106">When an Ubuntu version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="351ae-107">No entanto, essas instruções podem ajudá-lo a obter o .NET Core em execução nessas versões, mesmo que não haja suporte.</span><span class="sxs-lookup"><span data-stu-id="351ae-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="351ae-108">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="351ae-108">Supported distributions</span></span>

<span data-ttu-id="351ae-109">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento e as versões do Ubuntu nas quais elas têm suporte.</span><span class="sxs-lookup"><span data-stu-id="351ae-109">The following table is a list of currently supported .NET Core releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="351ae-110">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Ubuntu atinja o fim da vida útil](https://wiki.ubuntu.com/Releases).</span><span class="sxs-lookup"><span data-stu-id="351ae-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="351ae-111">Um ✔️ indica que a versão do Ubuntu ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="351ae-111">A ✔️ indicates that the version of Ubuntu or .NET Core is still supported.</span></span>
- <span data-ttu-id="351ae-112">Um ❌ indica que a versão do Ubuntu ou do .NET Core não tem suporte nessa versão do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="351ae-112">A ❌ indicates that the version of Ubuntu or .NET Core isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="351ae-113">Quando uma versão do Ubuntu e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="351ae-113">When both a version of Ubuntu and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="351ae-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="351ae-114">Ubuntu</span></span>                   | <span data-ttu-id="351ae-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="351ae-115">.NET Core 2.1</span></span> | <span data-ttu-id="351ae-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="351ae-116">.NET Core 3.1</span></span> | <span data-ttu-id="351ae-117">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="351ae-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="351ae-118">✔️ [20, 4 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="351ae-118">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="351ae-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="351ae-119">✔️ 2.1</span></span>        | <span data-ttu-id="351ae-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="351ae-120">✔️ 3.1</span></span>        | <span data-ttu-id="351ae-121">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="351ae-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="351ae-122">✔️ [19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="351ae-122">✔️ [19.10](#1910-)</span></span>       | <span data-ttu-id="351ae-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="351ae-123">✔️ 2.1</span></span>        | <span data-ttu-id="351ae-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="351ae-124">✔️ 3.1</span></span>        | <span data-ttu-id="351ae-125">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="351ae-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="351ae-126">❌[19, 4](#1904-)</span><span class="sxs-lookup"><span data-stu-id="351ae-126">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="351ae-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="351ae-127">✔️ 2.1</span></span>        | <span data-ttu-id="351ae-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="351ae-128">✔️ 3.1</span></span>        | <span data-ttu-id="351ae-129">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="351ae-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="351ae-130">❌[18,10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="351ae-130">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="351ae-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="351ae-131">✔️ 2.1</span></span>        | <span data-ttu-id="351ae-132">❌3,1</span><span class="sxs-lookup"><span data-stu-id="351ae-132">❌ 3.1</span></span>        | <span data-ttu-id="351ae-133">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="351ae-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="351ae-134">✔️ [18, 4 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="351ae-134">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="351ae-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="351ae-135">✔️ 2.1</span></span>        | <span data-ttu-id="351ae-136">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="351ae-136">✔️ 3.1</span></span>        | <span data-ttu-id="351ae-137">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="351ae-137">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="351ae-138">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="351ae-138">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="351ae-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="351ae-139">✔️ 2.1</span></span>        | <span data-ttu-id="351ae-140">❌3,1</span><span class="sxs-lookup"><span data-stu-id="351ae-140">❌ 3.1</span></span>        | <span data-ttu-id="351ae-141">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="351ae-141">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="351ae-142">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="351ae-142">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="351ae-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="351ae-143">✔️ 2.1</span></span>        | <span data-ttu-id="351ae-144">❌3,1</span><span class="sxs-lookup"><span data-stu-id="351ae-144">❌ 3.1</span></span>        | <span data-ttu-id="351ae-145">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="351ae-145">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="351ae-146">❌[16,10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="351ae-146">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="351ae-147">❌2,1</span><span class="sxs-lookup"><span data-stu-id="351ae-147">❌ 2.1</span></span>        | <span data-ttu-id="351ae-148">❌3,1</span><span class="sxs-lookup"><span data-stu-id="351ae-148">❌ 3.1</span></span>        | <span data-ttu-id="351ae-149">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="351ae-149">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="351ae-150">✔️ [16, 4 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="351ae-150">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="351ae-151">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="351ae-151">✔️ 2.1</span></span>        | <span data-ttu-id="351ae-152">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="351ae-152">✔️ 3.1</span></span>        | <span data-ttu-id="351ae-153">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="351ae-153">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="351ae-154">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="351ae-154">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="351ae-155">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="351ae-155">The downloads for these still remain published:</span></span>

- <span data-ttu-id="351ae-156">3.0</span><span class="sxs-lookup"><span data-stu-id="351ae-156">3.0</span></span>
- <span data-ttu-id="351ae-157">2.2</span><span class="sxs-lookup"><span data-stu-id="351ae-157">2.2</span></span>
- <span data-ttu-id="351ae-158">2,0</span><span class="sxs-lookup"><span data-stu-id="351ae-158">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="351ae-159">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="351ae-159">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a><span data-ttu-id="351ae-160">20, 4 ✔️</span><span class="sxs-lookup"><span data-stu-id="351ae-160">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a><span data-ttu-id="351ae-161">19,10 ✔️</span><span class="sxs-lookup"><span data-stu-id="351ae-161">19.10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="351ae-162">19, 4❌</span><span class="sxs-lookup"><span data-stu-id="351ae-162">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="351ae-163">18,10❌</span><span class="sxs-lookup"><span data-stu-id="351ae-163">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="351ae-164">18, 4 ✔️</span><span class="sxs-lookup"><span data-stu-id="351ae-164">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a><span data-ttu-id="351ae-165">17,10❌</span><span class="sxs-lookup"><span data-stu-id="351ae-165">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="351ae-166">17, 4❌</span><span class="sxs-lookup"><span data-stu-id="351ae-166">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="351ae-167">16,10❌</span><span class="sxs-lookup"><span data-stu-id="351ae-167">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="351ae-168">16, 4 ✔️</span><span class="sxs-lookup"><span data-stu-id="351ae-168">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="351ae-169">SDK de atualização de APT ou tempo de execução</span><span class="sxs-lookup"><span data-stu-id="351ae-169">APT update SDK or runtime</span></span>

<span data-ttu-id="351ae-170">Quando uma nova versão de patch está disponível para o .NET Core, você pode simplesmente atualizá-la por meio de APT com os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="351ae-170">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="351ae-171">Solução de problemas da APT</span><span class="sxs-lookup"><span data-stu-id="351ae-171">APT troubleshooting</span></span>

<span data-ttu-id="351ae-172">Esta seção fornece informações sobre erros comuns que você pode obter ao usar a APT para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="351ae-172">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="351ae-173">Não é possível localizar</span><span class="sxs-lookup"><span data-stu-id="351ae-173">Unable to locate</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="351ae-174">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="351ae-174">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="351ae-175">Snap</span><span class="sxs-lookup"><span data-stu-id="351ae-175">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="351ae-176">Dependências</span><span class="sxs-lookup"><span data-stu-id="351ae-176">Dependencies</span></span>

<span data-ttu-id="351ae-177">Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você.</span><span class="sxs-lookup"><span data-stu-id="351ae-177">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="351ae-178">Mas, se você instalar manualmente o .NET Core ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="351ae-178">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="351ae-179">libc6</span><span class="sxs-lookup"><span data-stu-id="351ae-179">libc6</span></span>
- <span data-ttu-id="351ae-180">libgcc1</span><span class="sxs-lookup"><span data-stu-id="351ae-180">libgcc1</span></span>
- <span data-ttu-id="351ae-181">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="351ae-181">libgssapi-krb5-2</span></span>
- <span data-ttu-id="351ae-182">libicu52 (para 14.x)</span><span class="sxs-lookup"><span data-stu-id="351ae-182">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="351ae-183">libicu55 (para 16.x)</span><span class="sxs-lookup"><span data-stu-id="351ae-183">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="351ae-184">libicu60 (para 18.x)</span><span class="sxs-lookup"><span data-stu-id="351ae-184">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="351ae-185">libicu66 (para 20. x)</span><span class="sxs-lookup"><span data-stu-id="351ae-185">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="351ae-186">libssl 1.0.0 (para 14. x, 16. x)</span><span class="sxs-lookup"><span data-stu-id="351ae-186">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="351ae-187">libssl 1.1 (para 18. x, 20. x)</span><span class="sxs-lookup"><span data-stu-id="351ae-187">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="351ae-188">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="351ae-188">libstdc++6</span></span>
- <span data-ttu-id="351ae-189">zlib1g</span><span class="sxs-lookup"><span data-stu-id="351ae-189">zlib1g</span></span>

<span data-ttu-id="351ae-190">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="351ae-190">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="351ae-191">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="351ae-191">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="351ae-192">Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="351ae-192">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="351ae-193">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="351ae-193">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="351ae-194">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="351ae-194">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="351ae-195">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="351ae-195">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="351ae-196">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="351ae-196">Next steps</span></span>

- [<span data-ttu-id="351ae-197">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="351ae-197">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
