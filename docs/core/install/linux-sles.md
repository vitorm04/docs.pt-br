---
title: Instalar o .NET Core no SLES-.NET Core
description: Demonstra as várias maneiras de instalar o SDK do .NET Core e o tempo de execução do .NET Core no SLES.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: b2eab6a0305d492e37e1b33d02be43ca41d42b6f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603030"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="81200-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no SLES</span><span class="sxs-lookup"><span data-stu-id="81200-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="81200-104">O .NET Core tem suporte no SLES.</span><span class="sxs-lookup"><span data-stu-id="81200-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="81200-105">Este artigo descreve como instalar o .NET Core no SLES.</span><span class="sxs-lookup"><span data-stu-id="81200-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="81200-106">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="81200-106">Supported distributions</span></span>

<span data-ttu-id="81200-107">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento no SLES 12 SP2 e no SLES 15.</span><span class="sxs-lookup"><span data-stu-id="81200-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="81200-108">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do SLES não seja mais suportada.</span><span class="sxs-lookup"><span data-stu-id="81200-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="81200-109">Um ✔️ indica que a versão do SLES ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="81200-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="81200-110">Um ❌ indica que a versão do SLES ou do .NET Core não tem suporte nessa versão do SLES.</span><span class="sxs-lookup"><span data-stu-id="81200-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="81200-111">Quando uma versão do SLES e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="81200-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="81200-112">SLES</span><span class="sxs-lookup"><span data-stu-id="81200-112">SLES</span></span>                   | <span data-ttu-id="81200-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="81200-113">.NET Core 2.1</span></span> | <span data-ttu-id="81200-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="81200-114">.NET Core 3.1</span></span> | <span data-ttu-id="81200-115">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="81200-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="81200-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="81200-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="81200-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="81200-117">✔️ 2.1</span></span>        | <span data-ttu-id="81200-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="81200-118">✔️ 3.1</span></span>        | <span data-ttu-id="81200-119">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="81200-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="81200-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="81200-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="81200-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="81200-121">✔️ 2.1</span></span>        | <span data-ttu-id="81200-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="81200-122">✔️ 3.1</span></span>        | <span data-ttu-id="81200-123">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="81200-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="81200-124">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="81200-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="81200-125">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="81200-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="81200-126">3.0</span><span class="sxs-lookup"><span data-stu-id="81200-126">3.0</span></span>
- <span data-ttu-id="81200-127">2.2</span><span class="sxs-lookup"><span data-stu-id="81200-127">2.2</span></span>
- <span data-ttu-id="81200-128">2,0</span><span class="sxs-lookup"><span data-stu-id="81200-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="81200-129">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="81200-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="81200-130">✔️ SLES 15</span><span class="sxs-lookup"><span data-stu-id="81200-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="81200-131">Atualmente, o pacote de instalação do repositório do SLES 15 da Microsoft instala o arquivo *Microsoft-prod.* Repository no diretório errado, impedindo que o Zypper Localize os pacotes do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="81200-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="81200-132">Para corrigir esse problema, crie um symlink no diretório correto.</span><span class="sxs-lookup"><span data-stu-id="81200-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="81200-133">✔️ SLES 12</span><span class="sxs-lookup"><span data-stu-id="81200-133">SLES 12 ✔️</span></span>

<span data-ttu-id="81200-134">O .NET Core requer o SP2 como um mínimo para a família SLES 12.</span><span class="sxs-lookup"><span data-stu-id="81200-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="81200-135">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="81200-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="81200-136">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="81200-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="81200-137">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="81200-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="81200-138">Snap</span><span class="sxs-lookup"><span data-stu-id="81200-138">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="81200-139">Dependências</span><span class="sxs-lookup"><span data-stu-id="81200-139">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="81200-140">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="81200-140">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="81200-141">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="81200-141">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="81200-142">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="81200-142">Next steps</span></span>

- [<span data-ttu-id="81200-143">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="81200-143">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
