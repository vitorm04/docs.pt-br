---
title: Instalar o .NET Core no SLES-.NET Core
description: Demonstra as várias maneiras de instalar o SDK do .NET Core e o tempo de execução do .NET Core no SLES.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: e1a2490c1d653eb07aebdd51e34e1bf462906482
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324704"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="15a6a-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no SLES</span><span class="sxs-lookup"><span data-stu-id="15a6a-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="15a6a-104">O .NET Core tem suporte no SLES.</span><span class="sxs-lookup"><span data-stu-id="15a6a-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="15a6a-105">Este artigo descreve como instalar o .NET Core no SLES.</span><span class="sxs-lookup"><span data-stu-id="15a6a-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="15a6a-106">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="15a6a-106">Supported distributions</span></span>

<span data-ttu-id="15a6a-107">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento no SLES 12 SP2 e no SLES 15.</span><span class="sxs-lookup"><span data-stu-id="15a6a-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="15a6a-108">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do SLES não seja mais suportada.</span><span class="sxs-lookup"><span data-stu-id="15a6a-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="15a6a-109">Um ✔️ indica que a versão do SLES ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="15a6a-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="15a6a-110">Um ❌ indica que a versão do SLES ou do .NET Core não tem suporte nessa versão do SLES.</span><span class="sxs-lookup"><span data-stu-id="15a6a-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="15a6a-111">Quando uma versão do SLES e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="15a6a-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="15a6a-112">SLES</span><span class="sxs-lookup"><span data-stu-id="15a6a-112">SLES</span></span>                   | <span data-ttu-id="15a6a-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="15a6a-113">.NET Core 2.1</span></span> | <span data-ttu-id="15a6a-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="15a6a-114">.NET Core 3.1</span></span> | <span data-ttu-id="15a6a-115">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="15a6a-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="15a6a-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="15a6a-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="15a6a-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="15a6a-117">✔️ 2.1</span></span>        | <span data-ttu-id="15a6a-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="15a6a-118">✔️ 3.1</span></span>        | <span data-ttu-id="15a6a-119">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="15a6a-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="15a6a-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="15a6a-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="15a6a-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="15a6a-121">✔️ 2.1</span></span>        | <span data-ttu-id="15a6a-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="15a6a-122">✔️ 3.1</span></span>        | <span data-ttu-id="15a6a-123">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="15a6a-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="15a6a-124">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="15a6a-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="15a6a-125">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="15a6a-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="15a6a-126">3.0</span><span class="sxs-lookup"><span data-stu-id="15a6a-126">3.0</span></span>
- <span data-ttu-id="15a6a-127">2.2</span><span class="sxs-lookup"><span data-stu-id="15a6a-127">2.2</span></span>
- <span data-ttu-id="15a6a-128">2,0</span><span class="sxs-lookup"><span data-stu-id="15a6a-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="15a6a-129">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="15a6a-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="15a6a-130">✔️ SLES 15</span><span class="sxs-lookup"><span data-stu-id="15a6a-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="15a6a-131">Atualmente, o pacote de instalação do repositório do SLES 15 da Microsoft instala o arquivo *Microsoft-prod.* Repository no diretório errado, impedindo que o Zypper Localize os pacotes do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="15a6a-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="15a6a-132">Para corrigir esse problema, crie um symlink no diretório correto.</span><span class="sxs-lookup"><span data-stu-id="15a6a-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="15a6a-133">✔️ SLES 12</span><span class="sxs-lookup"><span data-stu-id="15a6a-133">SLES 12 ✔️</span></span>

<span data-ttu-id="15a6a-134">O .NET Core requer o SP2 como um mínimo para a família SLES 12.</span><span class="sxs-lookup"><span data-stu-id="15a6a-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="15a6a-135">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="15a6a-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="15a6a-136">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="15a6a-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="15a6a-137">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="15a6a-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="15a6a-138">Dependências</span><span class="sxs-lookup"><span data-stu-id="15a6a-138">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="15a6a-139">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="15a6a-139">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="15a6a-140">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="15a6a-140">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="15a6a-141">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="15a6a-141">Next steps</span></span>

- [<span data-ttu-id="15a6a-142">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="15a6a-142">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
