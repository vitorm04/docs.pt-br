---
title: Instalar o .NET no Debian-.NET
description: Demonstra as várias maneiras de instalar o SDK do .NET e o tempo de execução do .NET no Debian.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 6dad4e1779600b22b8301e03ffb8fb2c16786ead
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506945"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-debian"></a><span data-ttu-id="599e0-103">Instalar o SDK do .NET ou o tempo de execução do .NET no Debian</span><span class="sxs-lookup"><span data-stu-id="599e0-103">Install the .NET SDK or the .NET Runtime on Debian</span></span>

<span data-ttu-id="599e0-104">Este artigo descreve como instalar o .NET no Debian.</span><span class="sxs-lookup"><span data-stu-id="599e0-104">This article describes how to install .NET on Debian.</span></span> <span data-ttu-id="599e0-105">Quando uma versão Debian fica sem suporte, o .NET não é mais compatível com essa versão.</span><span class="sxs-lookup"><span data-stu-id="599e0-105">When a Debian version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="599e0-106">No entanto, essas instruções podem ajudá-lo a obter o .NET em execução nessas versões, mesmo que não haja suporte.</span><span class="sxs-lookup"><span data-stu-id="599e0-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="599e0-107">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="599e0-107">Supported distributions</span></span>

<span data-ttu-id="599e0-108">A tabela a seguir é uma lista de versões do .NET com suporte no momento e as versões do Debian nas quais elas têm suporte.</span><span class="sxs-lookup"><span data-stu-id="599e0-108">The following table is a list of currently supported .NET releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="599e0-109">Essas versões permanecem com suporte até que a versão do [.net atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Debian atinja o fim da vida útil](https://wiki.debian.org/DebianReleases).</span><span class="sxs-lookup"><span data-stu-id="599e0-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="599e0-110">Um ✔️ indica que a versão do Debian ou do .NET ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="599e0-110">A ✔️ indicates that the version of Debian or .NET is still supported.</span></span>
- <span data-ttu-id="599e0-111">Um ❌ indica que a versão do Debian ou do .net não tem suporte nessa versão do Debian.</span><span class="sxs-lookup"><span data-stu-id="599e0-111">A ❌ indicates that the version of Debian or .NET isn't supported on that Debian release.</span></span>
- <span data-ttu-id="599e0-112">Quando uma versão do Debian e uma versão do .NET têm ✔️, essa combinação de so e .NET é suportada.</span><span class="sxs-lookup"><span data-stu-id="599e0-112">When both a version of Debian and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="599e0-113">Debian</span><span class="sxs-lookup"><span data-stu-id="599e0-113">Debian</span></span>                   | <span data-ttu-id="599e0-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="599e0-114">.NET Core 2.1</span></span> | <span data-ttu-id="599e0-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="599e0-115">.NET Core 3.1</span></span> | <span data-ttu-id="599e0-116">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="599e0-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="599e0-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="599e0-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="599e0-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="599e0-118">✔️ 2.1</span></span>        | <span data-ttu-id="599e0-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="599e0-119">✔️ 3.1</span></span>        | <span data-ttu-id="599e0-120">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="599e0-120">✔️ 5.0</span></span> |
| <span data-ttu-id="599e0-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="599e0-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="599e0-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="599e0-122">✔️ 2.1</span></span>        | <span data-ttu-id="599e0-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="599e0-123">✔️ 3.1</span></span>        | <span data-ttu-id="599e0-124">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="599e0-124">✔️ 5.0</span></span> |
| <span data-ttu-id="599e0-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="599e0-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="599e0-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="599e0-126">✔️ 2.1</span></span>        | <span data-ttu-id="599e0-127">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="599e0-127">❌ 3.1</span></span>        | <span data-ttu-id="599e0-128">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="599e0-128">❌ 5.0</span></span> |

<span data-ttu-id="599e0-129">Não há mais suporte para as seguintes versões do .NET.</span><span class="sxs-lookup"><span data-stu-id="599e0-129">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="599e0-130">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="599e0-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="599e0-131">3.0</span><span class="sxs-lookup"><span data-stu-id="599e0-131">3.0</span></span>
- <span data-ttu-id="599e0-132">2.2</span><span class="sxs-lookup"><span data-stu-id="599e0-132">2.2</span></span>
- <span data-ttu-id="599e0-133">2.0</span><span class="sxs-lookup"><span data-stu-id="599e0-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="599e0-134">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="599e0-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="599e0-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="599e0-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="599e0-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="599e0-136">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="599e0-137">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="599e0-137">Debian 8 ❌</span></span>

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

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="599e0-138">SDK de atualização de APT ou tempo de execução</span><span class="sxs-lookup"><span data-stu-id="599e0-138">APT update SDK or runtime</span></span>

<span data-ttu-id="599e0-139">Quando uma nova versão de patch estiver disponível para o .NET, você poderá simplesmente atualizá-la por meio de APT com os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="599e0-139">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="599e0-140">Solução de problemas da APT</span><span class="sxs-lookup"><span data-stu-id="599e0-140">APT troubleshooting</span></span>

<span data-ttu-id="599e0-141">Esta seção fornece informações sobre erros comuns que você pode obter ao usar a APT para instalar o .NET.</span><span class="sxs-lookup"><span data-stu-id="599e0-141">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="599e0-142">Não é possível localizar o pacote</span><span class="sxs-lookup"><span data-stu-id="599e0-142">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="599e0-143">Não foi possível \\ instalar alguns pacotes</span><span class="sxs-lookup"><span data-stu-id="599e0-143">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="599e0-144">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="599e0-144">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="599e0-145">Snap</span><span class="sxs-lookup"><span data-stu-id="599e0-145">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="599e0-146">Dependências</span><span class="sxs-lookup"><span data-stu-id="599e0-146">Dependencies</span></span>

<span data-ttu-id="599e0-147">Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você.</span><span class="sxs-lookup"><span data-stu-id="599e0-147">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="599e0-148">Mas, se você instalar manualmente o .NET Core ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="599e0-148">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="599e0-149">libc6</span><span class="sxs-lookup"><span data-stu-id="599e0-149">libc6</span></span>
- <span data-ttu-id="599e0-150">libgcc1</span><span class="sxs-lookup"><span data-stu-id="599e0-150">libgcc1</span></span>
- <span data-ttu-id="599e0-151">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="599e0-151">libgssapi-krb5-2</span></span>
- <span data-ttu-id="599e0-152">libicu52 (para 8. x)</span><span class="sxs-lookup"><span data-stu-id="599e0-152">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="599e0-153">libicu57 (para 9. x)</span><span class="sxs-lookup"><span data-stu-id="599e0-153">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="599e0-154">libicu63 (para 10. x)</span><span class="sxs-lookup"><span data-stu-id="599e0-154">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="599e0-155">libicu67 (para 11. x)</span><span class="sxs-lookup"><span data-stu-id="599e0-155">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="599e0-156">libssl 1.0.0 (para 8. x)</span><span class="sxs-lookup"><span data-stu-id="599e0-156">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="599e0-157">libssl 1.1 (para 9. x-11. x)</span><span class="sxs-lookup"><span data-stu-id="599e0-157">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="599e0-158">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="599e0-158">libstdc++6</span></span>
- <span data-ttu-id="599e0-159">zlib1g</span><span class="sxs-lookup"><span data-stu-id="599e0-159">zlib1g</span></span>

<span data-ttu-id="599e0-160">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="599e0-160">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="599e0-161">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="599e0-161">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="599e0-162">Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="599e0-162">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="599e0-163">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="599e0-163">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="599e0-164">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="599e0-164">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="599e0-165">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="599e0-165">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="599e0-166">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="599e0-166">Next steps</span></span>

- [<span data-ttu-id="599e0-167">Tutorial: criar um aplicativo de console com o SDK do .NET usando o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="599e0-167">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
