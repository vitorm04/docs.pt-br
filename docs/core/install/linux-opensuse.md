---
title: Instalar o .NET Core no openSUSE-.NET Core
description: Demonstra as várias maneiras de instalar SDK do .NET Core e o tempo de execução do .NET Core no openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 3a2ff1ca1519428f42c88048dde22aa11baaaa01
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324752"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="c1796-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no openSUSE</span><span class="sxs-lookup"><span data-stu-id="c1796-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="c1796-104">O .NET Core tem suporte no openSUSE.</span><span class="sxs-lookup"><span data-stu-id="c1796-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="c1796-105">Este artigo descreve como instalar o .NET Core no openSUSE.</span><span class="sxs-lookup"><span data-stu-id="c1796-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="c1796-106">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="c1796-106">Supported distributions</span></span>

<span data-ttu-id="c1796-107">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento no openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="c1796-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="c1796-108">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do openSUSE não seja mais suportada.</span><span class="sxs-lookup"><span data-stu-id="c1796-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="c1796-109">Um ✔️ indica que a versão do openSUSE ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="c1796-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="c1796-110">Um ❌ indica que a versão do openSUSE ou do .NET Core não tem suporte nessa versão do openSUSE.</span><span class="sxs-lookup"><span data-stu-id="c1796-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="c1796-111">Quando uma versão do openSUSE e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="c1796-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="c1796-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c1796-112">openSUSE</span></span>                   | <span data-ttu-id="c1796-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c1796-113">.NET Core 2.1</span></span> | <span data-ttu-id="c1796-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c1796-114">.NET Core 3.1</span></span> | <span data-ttu-id="c1796-115">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="c1796-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="c1796-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="c1796-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="c1796-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c1796-117">✔️ 2.1</span></span>        | <span data-ttu-id="c1796-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c1796-118">✔️ 3.1</span></span>        | <span data-ttu-id="c1796-119">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="c1796-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="c1796-120">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1796-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="c1796-121">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="c1796-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c1796-122">3.0</span><span class="sxs-lookup"><span data-stu-id="c1796-122">3.0</span></span>
- <span data-ttu-id="c1796-123">2.2</span><span class="sxs-lookup"><span data-stu-id="c1796-123">2.2</span></span>
- <span data-ttu-id="c1796-124">2,0</span><span class="sxs-lookup"><span data-stu-id="c1796-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c1796-125">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="c1796-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="c1796-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="c1796-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="c1796-127">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="c1796-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="c1796-128">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1796-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="c1796-129">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="c1796-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="c1796-130">Snap</span><span class="sxs-lookup"><span data-stu-id="c1796-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="c1796-131">Dependências</span><span class="sxs-lookup"><span data-stu-id="c1796-131">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="c1796-132">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="c1796-132">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="c1796-133">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="c1796-133">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="c1796-134">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c1796-134">Next steps</span></span>

- [<span data-ttu-id="c1796-135">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c1796-135">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
