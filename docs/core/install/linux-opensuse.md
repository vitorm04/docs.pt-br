---
title: Instalar o .NET Core no openSUSE-.NET Core
description: Demonstra as várias maneiras de instalar SDK do .NET Core e o tempo de execução do .NET Core no openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: ccdb23ca1838d2c15c9a95b45c8505efe7a6df0e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539224"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="c635c-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no openSUSE</span><span class="sxs-lookup"><span data-stu-id="c635c-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="c635c-104">O .NET Core tem suporte no openSUSE.</span><span class="sxs-lookup"><span data-stu-id="c635c-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="c635c-105">Este artigo descreve como instalar o .NET Core no openSUSE.</span><span class="sxs-lookup"><span data-stu-id="c635c-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="c635c-106">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="c635c-106">Supported distributions</span></span>

<span data-ttu-id="c635c-107">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento no openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="c635c-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="c635c-108">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do openSUSE não seja mais suportada.</span><span class="sxs-lookup"><span data-stu-id="c635c-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="c635c-109">Um ✔️ indica que a versão do openSUSE ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="c635c-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="c635c-110">Um ❌ indica que a versão do openSUSE ou do .NET Core não tem suporte nessa versão do openSUSE.</span><span class="sxs-lookup"><span data-stu-id="c635c-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="c635c-111">Quando uma versão do openSUSE e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="c635c-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="c635c-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c635c-112">openSUSE</span></span>                   | <span data-ttu-id="c635c-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c635c-113">.NET Core 2.1</span></span> | <span data-ttu-id="c635c-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c635c-114">.NET Core 3.1</span></span> | <span data-ttu-id="c635c-115">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="c635c-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="c635c-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="c635c-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="c635c-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c635c-117">✔️ 2.1</span></span>        | <span data-ttu-id="c635c-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c635c-118">✔️ 3.1</span></span>        | <span data-ttu-id="c635c-119">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="c635c-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="c635c-120">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c635c-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="c635c-121">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="c635c-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c635c-122">3.0</span><span class="sxs-lookup"><span data-stu-id="c635c-122">3.0</span></span>
- <span data-ttu-id="c635c-123">2.2</span><span class="sxs-lookup"><span data-stu-id="c635c-123">2.2</span></span>
- <span data-ttu-id="c635c-124">2.0</span><span class="sxs-lookup"><span data-stu-id="c635c-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c635c-125">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="c635c-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="c635c-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="c635c-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="c635c-127">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="c635c-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="c635c-128">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c635c-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="c635c-129">Não é possível localizar o pacote</span><span class="sxs-lookup"><span data-stu-id="c635c-129">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="c635c-130">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="c635c-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="c635c-131">Snap</span><span class="sxs-lookup"><span data-stu-id="c635c-131">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="c635c-132">Dependências</span><span class="sxs-lookup"><span data-stu-id="c635c-132">Dependencies</span></span>

<span data-ttu-id="c635c-133">Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você.</span><span class="sxs-lookup"><span data-stu-id="c635c-133">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="c635c-134">Mas, se você instalar manualmente o .NET Core ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="c635c-134">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="c635c-135">krb5</span><span class="sxs-lookup"><span data-stu-id="c635c-135">krb5</span></span>
- <span data-ttu-id="c635c-136">libicu</span><span class="sxs-lookup"><span data-stu-id="c635c-136">libicu</span></span>
- <span data-ttu-id="c635c-137">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="c635c-137">libopenssl1_0_0</span></span>

<span data-ttu-id="c635c-138">Se a versão do OpenSSL do ambiente de tempo de execução de destino for 1,1 ou mais recente, você precisará instalar o **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="c635c-138">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="c635c-139">Para obter mais informações sobre as dependências, consulte [aplicativos do Linux autocontidos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="c635c-139">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="c635c-140">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="c635c-140">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="c635c-141">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="c635c-141">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="c635c-142">Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="c635c-142">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="c635c-143">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="c635c-143">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="c635c-144">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="c635c-144">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="c635c-145">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="c635c-145">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="c635c-146">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c635c-146">Next steps</span></span>

- [<span data-ttu-id="c635c-147">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c635c-147">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
