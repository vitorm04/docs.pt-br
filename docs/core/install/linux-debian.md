---
title: Instalar o .NET Core no Debian – .NET Core
description: Demonstra as várias maneiras de instalar o SDK do .NET Core e o tempo de execução do .NET Core no Debian.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c66d8e1daad4e59a766781b7117600352879b724
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603051"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="55bef-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no Debian</span><span class="sxs-lookup"><span data-stu-id="55bef-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="55bef-104">Este artigo descreve como instalar o .NET Core no Debian.</span><span class="sxs-lookup"><span data-stu-id="55bef-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="55bef-105">Quando uma versão Debian fica sem suporte, o .NET Core não é mais compatível com essa versão.</span><span class="sxs-lookup"><span data-stu-id="55bef-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="55bef-106">No entanto, essas instruções podem ajudá-lo a obter o .NET Core em execução nessas versões, mesmo que não haja suporte.</span><span class="sxs-lookup"><span data-stu-id="55bef-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="55bef-107">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="55bef-107">Supported distributions</span></span>

<span data-ttu-id="55bef-108">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento e as versões do Debian nas quais elas têm suporte.</span><span class="sxs-lookup"><span data-stu-id="55bef-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="55bef-109">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Debian atinja o fim da vida útil](https://wiki.debian.org/DebianReleases).</span><span class="sxs-lookup"><span data-stu-id="55bef-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="55bef-110">Um ✔️ indica que a versão do Debian ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="55bef-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="55bef-111">Um ❌ indica que a versão do Debian ou do .NET Core não tem suporte nessa versão do Debian.</span><span class="sxs-lookup"><span data-stu-id="55bef-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="55bef-112">Quando uma versão do Debian e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="55bef-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="55bef-113">Debian</span><span class="sxs-lookup"><span data-stu-id="55bef-113">Debian</span></span>                   | <span data-ttu-id="55bef-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="55bef-114">.NET Core 2.1</span></span> | <span data-ttu-id="55bef-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="55bef-115">.NET Core 3.1</span></span> | <span data-ttu-id="55bef-116">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="55bef-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="55bef-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="55bef-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="55bef-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="55bef-118">✔️ 2.1</span></span>        | <span data-ttu-id="55bef-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="55bef-119">✔️ 3.1</span></span>        | <span data-ttu-id="55bef-120">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="55bef-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="55bef-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="55bef-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="55bef-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="55bef-122">✔️ 2.1</span></span>        | <span data-ttu-id="55bef-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="55bef-123">✔️ 3.1</span></span>        | <span data-ttu-id="55bef-124">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="55bef-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="55bef-125">❌[8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="55bef-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="55bef-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="55bef-126">✔️ 2.1</span></span>        | <span data-ttu-id="55bef-127">❌3,1</span><span class="sxs-lookup"><span data-stu-id="55bef-127">❌ 3.1</span></span>        | <span data-ttu-id="55bef-128">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="55bef-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="55bef-129">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55bef-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="55bef-130">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="55bef-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="55bef-131">3.0</span><span class="sxs-lookup"><span data-stu-id="55bef-131">3.0</span></span>
- <span data-ttu-id="55bef-132">2.2</span><span class="sxs-lookup"><span data-stu-id="55bef-132">2.2</span></span>
- <span data-ttu-id="55bef-133">2,0</span><span class="sxs-lookup"><span data-stu-id="55bef-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="55bef-134">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="55bef-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="55bef-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="55bef-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="55bef-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="55bef-136">Debian 9 ✔️</span></span>

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

## <a name="debian-8-"></a><span data-ttu-id="55bef-137">Debian 8❌</span><span class="sxs-lookup"><span data-stu-id="55bef-137">Debian 8 ❌</span></span>

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

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="55bef-138">SDK de atualização de APT ou tempo de execução</span><span class="sxs-lookup"><span data-stu-id="55bef-138">APT update SDK or runtime</span></span>

<span data-ttu-id="55bef-139">Quando uma nova versão de patch está disponível para o .NET Core, você pode simplesmente atualizá-la por meio de APT com os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="55bef-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="55bef-140">Solução de problemas da APT</span><span class="sxs-lookup"><span data-stu-id="55bef-140">APT troubleshooting</span></span>

<span data-ttu-id="55bef-141">Esta seção fornece informações sobre erros comuns que você pode obter ao usar a APT para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55bef-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="55bef-142">Não é possível localizar</span><span class="sxs-lookup"><span data-stu-id="55bef-142">Unable to locate</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="55bef-143">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="55bef-143">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="55bef-144">Snap</span><span class="sxs-lookup"><span data-stu-id="55bef-144">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="55bef-145">Dependências</span><span class="sxs-lookup"><span data-stu-id="55bef-145">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="55bef-146">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="55bef-146">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="55bef-147">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="55bef-147">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="55bef-148">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="55bef-148">Next steps</span></span>

- [<span data-ttu-id="55bef-149">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="55bef-149">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
