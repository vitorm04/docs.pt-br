---
title: Instalar o .NET no CentOS-.NET
description: Demonstra as várias maneiras de instalar o SDK do .NET e o tempo de execução do .NET no CentOS.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: d0f5d38de0f505d62f2a35c5d1c3f7161c91a96b
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507085"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-centos"></a><span data-ttu-id="91873-103">Instalar o SDK do .NET ou o tempo de execução do .NET no CentOS</span><span class="sxs-lookup"><span data-stu-id="91873-103">Install the .NET SDK or the .NET Runtime on CentOS</span></span>

<span data-ttu-id="91873-104">O .NET tem suporte no CentOS.</span><span class="sxs-lookup"><span data-stu-id="91873-104">.NET is supported on CentOS.</span></span> <span data-ttu-id="91873-105">Este artigo descreve como instalar o .NET no CentOS.</span><span class="sxs-lookup"><span data-stu-id="91873-105">This article describes how to install .NET on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="91873-106">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="91873-106">Supported distributions</span></span>

<span data-ttu-id="91873-107">A tabela a seguir é uma lista de versões do .NET com suporte no momento no CentOS 7 e no CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="91873-107">The following table is a list of currently supported .NET releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="91873-108">Essas versões permanecem com suporte até que a versão do [.net atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do CentOS não seja mais suportada.</span><span class="sxs-lookup"><span data-stu-id="91873-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="91873-109">Um ✔️ indica que a versão do CentOS ou do .NET ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="91873-109">A ✔️ indicates that the version of CentOS or .NET is still supported.</span></span>
- <span data-ttu-id="91873-110">Um ❌ indica que a versão do CentOS ou do .net não tem suporte nessa versão do CentOS.</span><span class="sxs-lookup"><span data-stu-id="91873-110">A ❌ indicates that the version of CentOS or .NET isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="91873-111">Quando uma versão do CentOS e uma versão do .NET têm ✔️, essa combinação de so e .NET é suportada.</span><span class="sxs-lookup"><span data-stu-id="91873-111">When both a version of CentOS and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="91873-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="91873-112">CentOS</span></span>                   | <span data-ttu-id="91873-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="91873-113">.NET Core 2.1</span></span> | <span data-ttu-id="91873-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="91873-114">.NET Core 3.1</span></span> | <span data-ttu-id="91873-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="91873-115">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="91873-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="91873-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="91873-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="91873-117">✔️ 2.1</span></span>        | <span data-ttu-id="91873-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="91873-118">✔️ 3.1</span></span>        | <span data-ttu-id="91873-119">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="91873-119">✔️ 5.0</span></span> |
| <span data-ttu-id="91873-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="91873-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="91873-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="91873-121">✔️ 2.1</span></span>        | <span data-ttu-id="91873-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="91873-122">✔️ 3.1</span></span>        | <span data-ttu-id="91873-123">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="91873-123">✔️ 5.0</span></span> |

<span data-ttu-id="91873-124">Não há mais suporte para as seguintes versões do .NET.</span><span class="sxs-lookup"><span data-stu-id="91873-124">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="91873-125">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="91873-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="91873-126">3.0</span><span class="sxs-lookup"><span data-stu-id="91873-126">3.0</span></span>
- <span data-ttu-id="91873-127">2.2</span><span class="sxs-lookup"><span data-stu-id="91873-127">2.2</span></span>
- <span data-ttu-id="91873-128">2.0</span><span class="sxs-lookup"><span data-stu-id="91873-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="91873-129">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="91873-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="91873-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="91873-130">CentOS 8 ✔️</span></span>

<span data-ttu-id="91873-131">O .NET 5,0 está disponível nos repositórios de pacotes padrão do CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="91873-131">.NET 5.0 is available in the default package repositories for CentOS 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="91873-132">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="91873-132">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-50](includes/linux-install-50-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="91873-133">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="91873-133">Troubleshoot the package manager</span></span>

<span data-ttu-id="91873-134">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET.</span><span class="sxs-lookup"><span data-stu-id="91873-134">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="91873-135">Não é possível localizar o pacote</span><span class="sxs-lookup"><span data-stu-id="91873-135">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="91873-136">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="91873-136">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="91873-137">Snap</span><span class="sxs-lookup"><span data-stu-id="91873-137">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="91873-138">Dependências</span><span class="sxs-lookup"><span data-stu-id="91873-138">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="91873-139">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="91873-139">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="91873-140">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="91873-140">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="91873-141">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="91873-141">Next steps</span></span>

- [<span data-ttu-id="91873-142">Tutorial: criar um aplicativo de console com o SDK do .NET usando o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="91873-142">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
