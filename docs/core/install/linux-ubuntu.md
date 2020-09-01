---
title: Instalar o .NET Core no Ubuntu – .NET Core
description: Demonstra as várias maneiras de instalar o SDK do .NET Core e o tempo de execução do .NET Core no Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9694dac719024264edee849044f048970b63b7b7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132931"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a><span data-ttu-id="7377e-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7377e-103">Install .NET Core SDK or .NET Core Runtime on Ubuntu</span></span>

<span data-ttu-id="7377e-104">O .NET Core tem suporte no Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7377e-104">.NET Core is supported on Ubuntu.</span></span> <span data-ttu-id="7377e-105">Este artigo descreve como instalar o .NET Core no Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7377e-105">This article describes how to install .NET Core on Ubuntu.</span></span> <span data-ttu-id="7377e-106">Quando uma versão do Ubuntu ficar sem suporte, o .NET Core não terá mais suporte nessa versão.</span><span class="sxs-lookup"><span data-stu-id="7377e-106">When an Ubuntu version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="7377e-107">No entanto, essas instruções podem ajudá-lo a obter o .NET Core em execução nessas versões, mesmo que não haja suporte.</span><span class="sxs-lookup"><span data-stu-id="7377e-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="7377e-108">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="7377e-108">Supported distributions</span></span>

<span data-ttu-id="7377e-109">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento e as versões do Ubuntu nas quais elas têm suporte.</span><span class="sxs-lookup"><span data-stu-id="7377e-109">The following table is a list of currently supported .NET Core releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="7377e-110">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Ubuntu atinja o fim da vida útil](https://wiki.ubuntu.com/Releases).</span><span class="sxs-lookup"><span data-stu-id="7377e-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="7377e-111">Um ✔️ indica que a versão do Ubuntu ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="7377e-111">A ✔️ indicates that the version of Ubuntu or .NET Core is still supported.</span></span>
- <span data-ttu-id="7377e-112">Um ❌ indica que a versão do Ubuntu ou do .NET Core não tem suporte nessa versão do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7377e-112">A ❌ indicates that the version of Ubuntu or .NET Core isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="7377e-113">Quando uma versão do Ubuntu e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="7377e-113">When both a version of Ubuntu and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="7377e-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7377e-114">Ubuntu</span></span>                   | <span data-ttu-id="7377e-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7377e-115">.NET Core 2.1</span></span> | <span data-ttu-id="7377e-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7377e-116">.NET Core 3.1</span></span> | <span data-ttu-id="7377e-117">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="7377e-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="7377e-118">✔️ [20, 4 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="7377e-118">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="7377e-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="7377e-119">✔️ 2.1</span></span>        | <span data-ttu-id="7377e-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="7377e-120">✔️ 3.1</span></span>        | <span data-ttu-id="7377e-121">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="7377e-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="7377e-122">❌[19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="7377e-122">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="7377e-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="7377e-123">✔️ 2.1</span></span>        | <span data-ttu-id="7377e-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="7377e-124">✔️ 3.1</span></span>        | <span data-ttu-id="7377e-125">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="7377e-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="7377e-126">❌[19, 4](#1904-)</span><span class="sxs-lookup"><span data-stu-id="7377e-126">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="7377e-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="7377e-127">✔️ 2.1</span></span>        | <span data-ttu-id="7377e-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="7377e-128">✔️ 3.1</span></span>        | <span data-ttu-id="7377e-129">❌ visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="7377e-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="7377e-130">❌[18,10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="7377e-130">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="7377e-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="7377e-131">✔️ 2.1</span></span>        | <span data-ttu-id="7377e-132">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="7377e-132">❌ 3.1</span></span>        | <span data-ttu-id="7377e-133">❌ visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="7377e-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="7377e-134">✔️ [18, 4 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="7377e-134">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="7377e-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="7377e-135">✔️ 2.1</span></span>        | <span data-ttu-id="7377e-136">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="7377e-136">✔️ 3.1</span></span>        | <span data-ttu-id="7377e-137">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="7377e-137">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="7377e-138">❌[17,10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="7377e-138">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="7377e-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="7377e-139">✔️ 2.1</span></span>        | <span data-ttu-id="7377e-140">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="7377e-140">❌ 3.1</span></span>        | <span data-ttu-id="7377e-141">❌ visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="7377e-141">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="7377e-142">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="7377e-142">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="7377e-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="7377e-143">✔️ 2.1</span></span>        | <span data-ttu-id="7377e-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="7377e-144">❌ 3.1</span></span>        | <span data-ttu-id="7377e-145">❌ visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="7377e-145">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="7377e-146">❌ [16,10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="7377e-146">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="7377e-147">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="7377e-147">❌ 2.1</span></span>        | <span data-ttu-id="7377e-148">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="7377e-148">❌ 3.1</span></span>        | <span data-ttu-id="7377e-149">❌ visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="7377e-149">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="7377e-150">✔️ [16, 4 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="7377e-150">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="7377e-151">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="7377e-151">✔️ 2.1</span></span>        | <span data-ttu-id="7377e-152">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="7377e-152">✔️ 3.1</span></span>        | <span data-ttu-id="7377e-153">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="7377e-153">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="7377e-154">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7377e-154">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="7377e-155">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="7377e-155">The downloads for these still remain published:</span></span>

- <span data-ttu-id="7377e-156">3.0</span><span class="sxs-lookup"><span data-stu-id="7377e-156">3.0</span></span>
- <span data-ttu-id="7377e-157">2,2</span><span class="sxs-lookup"><span data-stu-id="7377e-157">2.2</span></span>
- <span data-ttu-id="7377e-158">2,0</span><span class="sxs-lookup"><span data-stu-id="7377e-158">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="7377e-159">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="7377e-159">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a><span data-ttu-id="7377e-160">20, 4 ✔️</span><span class="sxs-lookup"><span data-stu-id="7377e-160">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a><span data-ttu-id="7377e-161">19,10 ❌</span><span class="sxs-lookup"><span data-stu-id="7377e-161">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="7377e-162">19, 4 ❌</span><span class="sxs-lookup"><span data-stu-id="7377e-162">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="7377e-163">18,10 ❌</span><span class="sxs-lookup"><span data-stu-id="7377e-163">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="7377e-164">18, 4 ✔️</span><span class="sxs-lookup"><span data-stu-id="7377e-164">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a><span data-ttu-id="7377e-165">17,10 ❌</span><span class="sxs-lookup"><span data-stu-id="7377e-165">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="7377e-166">17, 4 ❌</span><span class="sxs-lookup"><span data-stu-id="7377e-166">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="7377e-167">16,10 ❌</span><span class="sxs-lookup"><span data-stu-id="7377e-167">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="7377e-168">16, 4 ✔️</span><span class="sxs-lookup"><span data-stu-id="7377e-168">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="7377e-169">SDK de atualização de APT ou tempo de execução</span><span class="sxs-lookup"><span data-stu-id="7377e-169">APT update SDK or runtime</span></span>

<span data-ttu-id="7377e-170">Quando uma nova versão de patch está disponível para o .NET Core, você pode simplesmente atualizá-la por meio de APT com os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="7377e-170">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="7377e-171">Solução de problemas da APT</span><span class="sxs-lookup"><span data-stu-id="7377e-171">APT troubleshooting</span></span>

<span data-ttu-id="7377e-172">Esta seção fornece informações sobre erros comuns que você pode obter ao usar a APT para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7377e-172">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="7377e-173">Não foi possível \\ instalar alguns pacotes</span><span class="sxs-lookup"><span data-stu-id="7377e-173">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="7377e-174">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="7377e-174">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="7377e-175">Snap</span><span class="sxs-lookup"><span data-stu-id="7377e-175">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="7377e-176">Dependências</span><span class="sxs-lookup"><span data-stu-id="7377e-176">Dependencies</span></span>

<span data-ttu-id="7377e-177">Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você.</span><span class="sxs-lookup"><span data-stu-id="7377e-177">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="7377e-178">Mas, se você instalar manualmente o .NET Core ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="7377e-178">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="7377e-179">libc6</span><span class="sxs-lookup"><span data-stu-id="7377e-179">libc6</span></span>
- <span data-ttu-id="7377e-180">libgcc1</span><span class="sxs-lookup"><span data-stu-id="7377e-180">libgcc1</span></span>
- <span data-ttu-id="7377e-181">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="7377e-181">libgssapi-krb5-2</span></span>
- <span data-ttu-id="7377e-182">libicu52 (para 14.x)</span><span class="sxs-lookup"><span data-stu-id="7377e-182">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="7377e-183">libicu55 (para 16.x)</span><span class="sxs-lookup"><span data-stu-id="7377e-183">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="7377e-184">libicu60 (para 18.x)</span><span class="sxs-lookup"><span data-stu-id="7377e-184">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="7377e-185">libicu66 (para 20. x)</span><span class="sxs-lookup"><span data-stu-id="7377e-185">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="7377e-186">libssl 1.0.0 (para 14. x, 16. x)</span><span class="sxs-lookup"><span data-stu-id="7377e-186">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="7377e-187">libssl 1.1 (para 18. x, 20. x)</span><span class="sxs-lookup"><span data-stu-id="7377e-187">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="7377e-188">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="7377e-188">libstdc++6</span></span>
- <span data-ttu-id="7377e-189">zlib1g</span><span class="sxs-lookup"><span data-stu-id="7377e-189">zlib1g</span></span>

<span data-ttu-id="7377e-190">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="7377e-190">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="7377e-191">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="7377e-191">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="7377e-192">Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="7377e-192">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="7377e-193">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="7377e-193">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="7377e-194">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="7377e-194">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="7377e-195">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="7377e-195">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="7377e-196">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7377e-196">Next steps</span></span>

- [<span data-ttu-id="7377e-197">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7377e-197">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
