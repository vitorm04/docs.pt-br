---
title: Instalar o .NET Core no Fedora-.NET Core
description: Demonstra as várias maneiras de instalar SDK do .NET Core e o tempo de execução do .NET Core no Fedora.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 52aa9409ec876e0d1eaef22fb739046941fda897
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603086"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-fedora"></a><span data-ttu-id="07c1e-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no Fedora</span><span class="sxs-lookup"><span data-stu-id="07c1e-103">Install .NET Core SDK or .NET Core Runtime on Fedora</span></span>

<span data-ttu-id="07c1e-104">O .NET Core tem suporte no Fedora.</span><span class="sxs-lookup"><span data-stu-id="07c1e-104">.NET Core is supported on Fedora.</span></span> <span data-ttu-id="07c1e-105">Este artigo descreve como instalar o .NET Core no Fedora.</span><span class="sxs-lookup"><span data-stu-id="07c1e-105">This article describes how to install .NET Core on Fedora.</span></span> <span data-ttu-id="07c1e-106">Quando uma versão do Fedora fica sem suporte, o .NET Core não é mais compatível com essa versão.</span><span class="sxs-lookup"><span data-stu-id="07c1e-106">When a Fedora version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="07c1e-107">No entanto, essas instruções podem ajudá-lo a obter o .NET Core em execução nessas versões, mesmo que não haja suporte.</span><span class="sxs-lookup"><span data-stu-id="07c1e-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="07c1e-108">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="07c1e-108">Supported distributions</span></span>

<span data-ttu-id="07c1e-109">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento e as versões do Fedora em que têm suporte.</span><span class="sxs-lookup"><span data-stu-id="07c1e-109">The following table is a list of currently supported .NET Core releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="07c1e-110">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Fedora atinja o fim da vida útil](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="07c1e-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="07c1e-111">Um ✔️ indica que a versão do Fedora ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="07c1e-111">A ✔️ indicates that the version of Fedora or .NET Core is still supported.</span></span>
- <span data-ttu-id="07c1e-112">Um ❌ indica que a versão do Fedora ou do .NET Core não tem suporte nessa versão do Fedora.</span><span class="sxs-lookup"><span data-stu-id="07c1e-112">A ❌ indicates that the version of Fedora or .NET Core isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="07c1e-113">Quando uma versão do Fedora e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="07c1e-113">When both a version of Fedora and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="07c1e-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="07c1e-114">Fedora</span></span>                   | <span data-ttu-id="07c1e-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="07c1e-115">.NET Core 2.1</span></span> | <span data-ttu-id="07c1e-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="07c1e-116">.NET Core 3.1</span></span> | <span data-ttu-id="07c1e-117">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="07c1e-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="07c1e-118">✔️ [32](linux-fedora.md#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="07c1e-118">✔️ [32](linux-fedora.md#fedora-32-)</span></span> | <span data-ttu-id="07c1e-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-119">✔️ 2.1</span></span>        | <span data-ttu-id="07c1e-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-120">✔️ 3.1</span></span>        | <span data-ttu-id="07c1e-121">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="07c1e-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="07c1e-122">✔️ [31](linux-fedora.md#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="07c1e-122">✔️ [31](linux-fedora.md#fedora-31-)</span></span> | <span data-ttu-id="07c1e-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-123">✔️ 2.1</span></span>        | <span data-ttu-id="07c1e-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-124">✔️ 3.1</span></span>        | <span data-ttu-id="07c1e-125">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="07c1e-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="07c1e-126">❌ [30](linux-fedora.md#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="07c1e-126">❌ [30](linux-fedora.md#fedora-30-)</span></span> | <span data-ttu-id="07c1e-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-127">✔️ 2.1</span></span>        | <span data-ttu-id="07c1e-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-128">✔️ 3.1</span></span>        | <span data-ttu-id="07c1e-129">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="07c1e-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="07c1e-130">❌[29](linux-fedora.md#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="07c1e-130">❌ [29](linux-fedora.md#fedora-29-)</span></span> | <span data-ttu-id="07c1e-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-131">✔️ 2.1</span></span>        | <span data-ttu-id="07c1e-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-132">✔️ 3.1</span></span>        | <span data-ttu-id="07c1e-133">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="07c1e-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="07c1e-134">❌[28](linux-fedora.md#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="07c1e-134">❌ [28](linux-fedora.md#fedora-28-)</span></span> | <span data-ttu-id="07c1e-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-135">✔️ 2.1</span></span>        | <span data-ttu-id="07c1e-136">❌3,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-136">❌ 3.1</span></span>        | <span data-ttu-id="07c1e-137">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="07c1e-137">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="07c1e-138">❌[27](linux-fedora.md#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="07c1e-138">❌ [27](linux-fedora.md#fedora-27-)</span></span> | <span data-ttu-id="07c1e-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-139">✔️ 2.1</span></span>        | <span data-ttu-id="07c1e-140">❌3,1</span><span class="sxs-lookup"><span data-stu-id="07c1e-140">❌ 3.1</span></span>        | <span data-ttu-id="07c1e-141">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="07c1e-141">❌ 5.0 Preview</span></span> |

<span data-ttu-id="07c1e-142">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07c1e-142">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="07c1e-143">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="07c1e-143">The downloads for these still remain published:</span></span>

- <span data-ttu-id="07c1e-144">3.0</span><span class="sxs-lookup"><span data-stu-id="07c1e-144">3.0</span></span>
- <span data-ttu-id="07c1e-145">2.2</span><span class="sxs-lookup"><span data-stu-id="07c1e-145">2.2</span></span>
- <span data-ttu-id="07c1e-146">2,0</span><span class="sxs-lookup"><span data-stu-id="07c1e-146">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="07c1e-147">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="07c1e-147">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-32-"></a><span data-ttu-id="07c1e-148">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="07c1e-148">Fedora 32 ✔️</span></span>

<span data-ttu-id="07c1e-149">O .NET Core 3,1 está disponível nos repositórios de pacote padrão para Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="07c1e-149">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="07c1e-150">Fedora 31 ✔️</span><span class="sxs-lookup"><span data-stu-id="07c1e-150">Fedora 31 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="07c1e-151">Fedora 30❌</span><span class="sxs-lookup"><span data-stu-id="07c1e-151">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="07c1e-152">Fedora 29❌</span><span class="sxs-lookup"><span data-stu-id="07c1e-152">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="07c1e-153">Fedora 28❌</span><span class="sxs-lookup"><span data-stu-id="07c1e-153">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="07c1e-154">Fedora 27❌</span><span class="sxs-lookup"><span data-stu-id="07c1e-154">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="07c1e-155">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="07c1e-155">Troubleshoot the package manager</span></span>

<span data-ttu-id="07c1e-156">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07c1e-156">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="07c1e-157">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="07c1e-157">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="07c1e-158">Snap</span><span class="sxs-lookup"><span data-stu-id="07c1e-158">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="07c1e-159">Dependências</span><span class="sxs-lookup"><span data-stu-id="07c1e-159">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="07c1e-160">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="07c1e-160">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="07c1e-161">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="07c1e-161">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="07c1e-162">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="07c1e-162">Next steps</span></span>

- [<span data-ttu-id="07c1e-163">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="07c1e-163">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
