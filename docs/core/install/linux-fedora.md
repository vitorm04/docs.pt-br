---
title: Instalar o .NET em Fedora-.NET
description: Demonstra as várias maneiras de instalar o SDK do .NET e o tempo de execução do .NET no Fedora.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: d5b5886f8b29e0f8e935850686cc84f78c55be02
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507036"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="cb860-103">Instalar o SDK do .NET ou o tempo de execução do .NET no Fedora</span><span class="sxs-lookup"><span data-stu-id="cb860-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="cb860-104">O .NET tem suporte no Fedora.</span><span class="sxs-lookup"><span data-stu-id="cb860-104">.NET is supported on Fedora.</span></span> <span data-ttu-id="cb860-105">Este artigo descreve como instalar o .NET no Fedora.</span><span class="sxs-lookup"><span data-stu-id="cb860-105">This article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="cb860-106">Quando uma versão do Fedora fica sem suporte, o .NET não é mais compatível com essa versão.</span><span class="sxs-lookup"><span data-stu-id="cb860-106">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="cb860-107">No entanto, essas instruções podem ajudá-lo a obter o .NET em execução nessas versões, mesmo que não haja suporte.</span><span class="sxs-lookup"><span data-stu-id="cb860-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="cb860-108">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="cb860-108">Supported distributions</span></span>

<span data-ttu-id="cb860-109">A tabela a seguir é uma lista de versões do .NET com suporte no momento e as versões do Fedora em que têm suporte.</span><span class="sxs-lookup"><span data-stu-id="cb860-109">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="cb860-110">Essas versões permanecem com suporte até que a versão do [.net atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Fedora atinja o fim da vida útil](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="cb860-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="cb860-111">Um ✔️ indica que a versão do Fedora ou do .NET ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="cb860-111">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="cb860-112">Um ❌ indica que a versão do Fedora ou do .net não tem suporte nessa versão do Fedora.</span><span class="sxs-lookup"><span data-stu-id="cb860-112">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="cb860-113">Quando uma versão do Fedora e uma versão do .NET têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="cb860-113">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="cb860-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="cb860-114">Fedora</span></span>               | <span data-ttu-id="cb860-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cb860-115">.NET Core 2.1</span></span> | <span data-ttu-id="cb860-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="cb860-116">.NET Core 3.1</span></span> | <span data-ttu-id="cb860-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="cb860-117">.NET 5.0</span></span> |
|----------------------|---------------|---------------|----------|
| <span data-ttu-id="cb860-118">✔️ [33](#fedora-33-)</span><span class="sxs-lookup"><span data-stu-id="cb860-118">✔️ [33](#fedora-33-)</span></span> | <span data-ttu-id="cb860-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb860-119">✔️ 2.1</span></span>        | <span data-ttu-id="cb860-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb860-120">✔️ 3.1</span></span>        | <span data-ttu-id="cb860-121">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb860-121">✔️ 5.0</span></span> |
| <span data-ttu-id="cb860-122">✔️ [32](#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="cb860-122">✔️ [32](#fedora-32-)</span></span> | <span data-ttu-id="cb860-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb860-123">✔️ 2.1</span></span>        | <span data-ttu-id="cb860-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb860-124">✔️ 3.1</span></span>        | <span data-ttu-id="cb860-125">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb860-125">✔️ 5.0</span></span> |
| <span data-ttu-id="cb860-126">❌[31](#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="cb860-126">❌ [31](#fedora-31-)</span></span> | <span data-ttu-id="cb860-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb860-127">✔️ 2.1</span></span>        | <span data-ttu-id="cb860-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb860-128">✔️ 3.1</span></span>        | <span data-ttu-id="cb860-129">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb860-129">❌ 5.0</span></span> |
| <span data-ttu-id="cb860-130">❌[30](#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="cb860-130">❌ [30](#fedora-30-)</span></span> | <span data-ttu-id="cb860-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb860-131">✔️ 2.1</span></span>        | <span data-ttu-id="cb860-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb860-132">✔️ 3.1</span></span>        | <span data-ttu-id="cb860-133">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb860-133">❌ 5.0</span></span> |
| <span data-ttu-id="cb860-134">❌[29](#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="cb860-134">❌ [29](#fedora-29-)</span></span> | <span data-ttu-id="cb860-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb860-135">✔️ 2.1</span></span>        | <span data-ttu-id="cb860-136">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb860-136">✔️ 3.1</span></span>        | <span data-ttu-id="cb860-137">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb860-137">❌ 5.0</span></span> |
| <span data-ttu-id="cb860-138">❌[28](#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="cb860-138">❌ [28](#fedora-28-)</span></span> | <span data-ttu-id="cb860-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb860-139">✔️ 2.1</span></span>        | <span data-ttu-id="cb860-140">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb860-140">❌ 3.1</span></span>        | <span data-ttu-id="cb860-141">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb860-141">❌ 5.0</span></span> |
| <span data-ttu-id="cb860-142">❌[27](#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="cb860-142">❌ [27](#fedora-27-)</span></span> | <span data-ttu-id="cb860-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb860-143">✔️ 2.1</span></span>        | <span data-ttu-id="cb860-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb860-144">❌ 3.1</span></span>        | <span data-ttu-id="cb860-145">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb860-145">❌ 5.0</span></span> |

<span data-ttu-id="cb860-146">Não há mais suporte para as seguintes versões do .NET.</span><span class="sxs-lookup"><span data-stu-id="cb860-146">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="cb860-147">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="cb860-147">The downloads for these still remain published:</span></span>

- <span data-ttu-id="cb860-148">3.0</span><span class="sxs-lookup"><span data-stu-id="cb860-148">3.0</span></span>
- <span data-ttu-id="cb860-149">2.2</span><span class="sxs-lookup"><span data-stu-id="cb860-149">2.2</span></span>
- <span data-ttu-id="cb860-150">2.0</span><span class="sxs-lookup"><span data-stu-id="cb860-150">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="cb860-151">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="cb860-151">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a><span data-ttu-id="cb860-152">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="cb860-152">Fedora 33 ✔️</span></span>

<span data-ttu-id="cb860-153">O .NET 5 e o .NET Core 3,1 estão disponíveis nos repositórios de pacote padrão para Fedora 33.</span><span class="sxs-lookup"><span data-stu-id="cb860-153">.NET 5 and .NET Core 3.1 are available in the default package repositories for Fedora 33.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a><span data-ttu-id="cb860-154">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="cb860-154">Fedora 32 ✔️</span></span>

<span data-ttu-id="cb860-155">O .NET Core 3,1 está disponível nos repositórios de pacote padrão para Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="cb860-155">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="cb860-156">Fedora 31 ❌</span><span class="sxs-lookup"><span data-stu-id="cb860-156">Fedora 31 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="cb860-157">Fedora 30 ❌</span><span class="sxs-lookup"><span data-stu-id="cb860-157">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="cb860-158">Fedora 29 ❌</span><span class="sxs-lookup"><span data-stu-id="cb860-158">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="cb860-159">Fedora 28 ❌</span><span class="sxs-lookup"><span data-stu-id="cb860-159">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="cb860-160">Fedora 27 ❌</span><span class="sxs-lookup"><span data-stu-id="cb860-160">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="cb860-161">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="cb860-161">Troubleshoot the package manager</span></span>

<span data-ttu-id="cb860-162">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb860-162">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="cb860-163">Não é possível localizar o pacote</span><span class="sxs-lookup"><span data-stu-id="cb860-163">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="cb860-164">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="cb860-164">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="cb860-165">Snap</span><span class="sxs-lookup"><span data-stu-id="cb860-165">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="cb860-166">Dependências</span><span class="sxs-lookup"><span data-stu-id="cb860-166">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="cb860-167">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="cb860-167">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="cb860-168">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="cb860-168">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="cb860-169">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="cb860-169">Next steps</span></span>

- [<span data-ttu-id="cb860-170">Tutorial: criar um aplicativo de console com o SDK do .NET usando o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cb860-170">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
