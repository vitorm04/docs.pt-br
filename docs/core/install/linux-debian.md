---
title: Instalar o .NET Core no Debian – .NET Core
description: Demonstra as várias maneiras de instalar o SDK do .NET Core e o tempo de execução do .NET Core no Debian.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: d0f7d4092ec420d031d0874a56b9e2148afdb865
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538534"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="9ffa9-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no Debian</span><span class="sxs-lookup"><span data-stu-id="9ffa9-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="9ffa9-104">Este artigo descreve como instalar o .NET Core no Debian.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="9ffa9-105">Quando uma versão Debian fica sem suporte, o .NET Core não é mais compatível com essa versão.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="9ffa9-106">No entanto, essas instruções podem ajudá-lo a obter o .NET Core em execução nessas versões, mesmo que não haja suporte.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="9ffa9-107">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="9ffa9-107">Supported distributions</span></span>

<span data-ttu-id="9ffa9-108">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento e as versões do Debian nas quais elas têm suporte.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="9ffa9-109">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Debian atinja o fim da vida útil](https://wiki.debian.org/DebianReleases).</span><span class="sxs-lookup"><span data-stu-id="9ffa9-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="9ffa9-110">Um ✔️ indica que a versão do Debian ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="9ffa9-111">Um ❌ indica que a versão do Debian ou do .NET Core não tem suporte nessa versão do Debian.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="9ffa9-112">Quando uma versão do Debian e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="9ffa9-113">Debian</span><span class="sxs-lookup"><span data-stu-id="9ffa9-113">Debian</span></span>                   | <span data-ttu-id="9ffa9-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9ffa9-114">.NET Core 2.1</span></span> | <span data-ttu-id="9ffa9-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="9ffa9-115">.NET Core 3.1</span></span> | <span data-ttu-id="9ffa9-116">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="9ffa9-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="9ffa9-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="9ffa9-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="9ffa9-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="9ffa9-118">✔️ 2.1</span></span>        | <span data-ttu-id="9ffa9-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="9ffa9-119">✔️ 3.1</span></span>        | <span data-ttu-id="9ffa9-120">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="9ffa9-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="9ffa9-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="9ffa9-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="9ffa9-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="9ffa9-122">✔️ 2.1</span></span>        | <span data-ttu-id="9ffa9-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="9ffa9-123">✔️ 3.1</span></span>        | <span data-ttu-id="9ffa9-124">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="9ffa9-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="9ffa9-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="9ffa9-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="9ffa9-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="9ffa9-126">✔️ 2.1</span></span>        | <span data-ttu-id="9ffa9-127">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="9ffa9-127">❌ 3.1</span></span>        | <span data-ttu-id="9ffa9-128">❌ visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="9ffa9-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="9ffa9-129">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="9ffa9-130">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="9ffa9-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="9ffa9-131">3.0</span><span class="sxs-lookup"><span data-stu-id="9ffa9-131">3.0</span></span>
- <span data-ttu-id="9ffa9-132">2.2</span><span class="sxs-lookup"><span data-stu-id="9ffa9-132">2.2</span></span>
- <span data-ttu-id="9ffa9-133">2.0</span><span class="sxs-lookup"><span data-stu-id="9ffa9-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="9ffa9-134">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="9ffa9-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="9ffa9-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="9ffa9-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="9ffa9-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="9ffa9-136">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="9ffa9-137">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="9ffa9-137">Debian 8 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-debian.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/8/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="9ffa9-138">SDK de atualização de APT ou tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9ffa9-138">APT update SDK or runtime</span></span>

<span data-ttu-id="9ffa9-139">Quando uma nova versão de patch está disponível para o .NET Core, você pode simplesmente atualizá-la por meio de APT com os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="9ffa9-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="9ffa9-140">Solução de problemas da APT</span><span class="sxs-lookup"><span data-stu-id="9ffa9-140">APT troubleshooting</span></span>

<span data-ttu-id="9ffa9-141">Esta seção fornece informações sobre erros comuns que você pode obter ao usar a APT para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="9ffa9-142">Não é possível localizar o pacote</span><span class="sxs-lookup"><span data-stu-id="9ffa9-142">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="9ffa9-143">Não foi possível \\ instalar alguns pacotes</span><span class="sxs-lookup"><span data-stu-id="9ffa9-143">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="9ffa9-144">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="9ffa9-144">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="9ffa9-145">Snap</span><span class="sxs-lookup"><span data-stu-id="9ffa9-145">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="9ffa9-146">Dependências</span><span class="sxs-lookup"><span data-stu-id="9ffa9-146">Dependencies</span></span>

<span data-ttu-id="9ffa9-147">Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-147">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="9ffa9-148">Mas, se você instalar manualmente o .NET Core ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="9ffa9-148">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="9ffa9-149">libc6</span><span class="sxs-lookup"><span data-stu-id="9ffa9-149">libc6</span></span>
- <span data-ttu-id="9ffa9-150">libgcc1</span><span class="sxs-lookup"><span data-stu-id="9ffa9-150">libgcc1</span></span>
- <span data-ttu-id="9ffa9-151">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="9ffa9-151">libgssapi-krb5-2</span></span>
- <span data-ttu-id="9ffa9-152">libicu52 (para 8. x)</span><span class="sxs-lookup"><span data-stu-id="9ffa9-152">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="9ffa9-153">libicu57 (para 9. x)</span><span class="sxs-lookup"><span data-stu-id="9ffa9-153">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="9ffa9-154">libicu63 (para 10. x)</span><span class="sxs-lookup"><span data-stu-id="9ffa9-154">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="9ffa9-155">libicu67 (para 11. x)</span><span class="sxs-lookup"><span data-stu-id="9ffa9-155">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="9ffa9-156">libssl 1.0.0 (para 8. x)</span><span class="sxs-lookup"><span data-stu-id="9ffa9-156">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="9ffa9-157">libssl 1.1 (para 9. x-11. x)</span><span class="sxs-lookup"><span data-stu-id="9ffa9-157">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="9ffa9-158">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="9ffa9-158">libstdc++6</span></span>
- <span data-ttu-id="9ffa9-159">zlib1g</span><span class="sxs-lookup"><span data-stu-id="9ffa9-159">zlib1g</span></span>

<span data-ttu-id="9ffa9-160">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="9ffa9-160">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="9ffa9-161">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="9ffa9-161">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="9ffa9-162">Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-162">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="9ffa9-163">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="9ffa9-163">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="9ffa9-164">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="9ffa9-164">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="9ffa9-165">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="9ffa9-165">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="9ffa9-166">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="9ffa9-166">Next steps</span></span>

- [<span data-ttu-id="9ffa9-167">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9ffa9-167">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
