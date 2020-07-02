---
title: Instalar o .NET Core no openSUSE-.NET Core
description: Demonstra as várias maneiras de instalar SDK do .NET Core e o tempo de execução do .NET Core no openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 24f0a5b5278d038c2f941b0984efcacd91dcbe31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619462"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="ea429-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no openSUSE</span><span class="sxs-lookup"><span data-stu-id="ea429-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="ea429-104">O .NET Core tem suporte no openSUSE.</span><span class="sxs-lookup"><span data-stu-id="ea429-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="ea429-105">Este artigo descreve como instalar o .NET Core no openSUSE.</span><span class="sxs-lookup"><span data-stu-id="ea429-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="ea429-106">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="ea429-106">Supported distributions</span></span>

<span data-ttu-id="ea429-107">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento no openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="ea429-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="ea429-108">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do openSUSE não seja mais suportada.</span><span class="sxs-lookup"><span data-stu-id="ea429-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="ea429-109">Um ✔️ indica que a versão do openSUSE ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="ea429-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="ea429-110">Um ❌ indica que a versão do openSUSE ou do .NET Core não tem suporte nessa versão do openSUSE.</span><span class="sxs-lookup"><span data-stu-id="ea429-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="ea429-111">Quando uma versão do openSUSE e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="ea429-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="ea429-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="ea429-112">openSUSE</span></span>                   | <span data-ttu-id="ea429-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ea429-113">.NET Core 2.1</span></span> | <span data-ttu-id="ea429-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ea429-114">.NET Core 3.1</span></span> | <span data-ttu-id="ea429-115">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="ea429-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="ea429-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="ea429-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="ea429-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="ea429-117">✔️ 2.1</span></span>        | <span data-ttu-id="ea429-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="ea429-118">✔️ 3.1</span></span>        | <span data-ttu-id="ea429-119">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="ea429-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="ea429-120">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea429-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="ea429-121">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="ea429-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="ea429-122">3.0</span><span class="sxs-lookup"><span data-stu-id="ea429-122">3.0</span></span>
- <span data-ttu-id="ea429-123">2.2</span><span class="sxs-lookup"><span data-stu-id="ea429-123">2.2</span></span>
- <span data-ttu-id="ea429-124">2,0</span><span class="sxs-lookup"><span data-stu-id="ea429-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ea429-125">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="ea429-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="ea429-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="ea429-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="ea429-127">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="ea429-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="ea429-128">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea429-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="ea429-129">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="ea429-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="ea429-130">Snap</span><span class="sxs-lookup"><span data-stu-id="ea429-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="ea429-131">Dependências</span><span class="sxs-lookup"><span data-stu-id="ea429-131">Dependencies</span></span>

<span data-ttu-id="ea429-132">Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você.</span><span class="sxs-lookup"><span data-stu-id="ea429-132">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="ea429-133">Mas, se você instalar manualmente o .NET Core ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="ea429-133">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="ea429-134">krb5</span><span class="sxs-lookup"><span data-stu-id="ea429-134">krb5</span></span>
- <span data-ttu-id="ea429-135">libicu</span><span class="sxs-lookup"><span data-stu-id="ea429-135">libicu</span></span>
- <span data-ttu-id="ea429-136">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="ea429-136">libopenssl1_0_0</span></span>

<span data-ttu-id="ea429-137">Se a versão do OpenSSL do ambiente de tempo de execução de destino for 1,1 ou mais recente, você precisará instalar o **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="ea429-137">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="ea429-138">Para obter mais informações sobre as dependências, consulte [aplicativos do Linux autocontidos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="ea429-138">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="ea429-139">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="ea429-139">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="ea429-140">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="ea429-140">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="ea429-141">Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="ea429-141">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="ea429-142">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="ea429-142">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="ea429-143">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="ea429-143">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="ea429-144">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="ea429-144">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="ea429-145">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ea429-145">Next steps</span></span>

- [<span data-ttu-id="ea429-146">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ea429-146">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
