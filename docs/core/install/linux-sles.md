---
title: Instalar o .NET no SLES-.NET
description: Demonstra as várias maneiras de instalar o SDK do .NET e o tempo de execução do .NET no SLES.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 558574116aac2a3c755481069641e81a435a2a43
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506841"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-sles"></a><span data-ttu-id="0209d-103">Instalar o SDK do .NET ou o tempo de execução do .NET no SLES</span><span class="sxs-lookup"><span data-stu-id="0209d-103">Install the .NET SDK or the .NET Runtime on SLES</span></span>

<span data-ttu-id="0209d-104">O .NET tem suporte no SLES.</span><span class="sxs-lookup"><span data-stu-id="0209d-104">.NET is supported on SLES.</span></span> <span data-ttu-id="0209d-105">Este artigo descreve como instalar o .NET no SLES.</span><span class="sxs-lookup"><span data-stu-id="0209d-105">This article describes how to install .NET on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="0209d-106">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="0209d-106">Supported distributions</span></span>

<span data-ttu-id="0209d-107">A tabela a seguir é uma lista de versões do .NET com suporte no momento no SLES 12 SP2 e no SLES 15.</span><span class="sxs-lookup"><span data-stu-id="0209d-107">The following table is a list of currently supported .NET releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="0209d-108">Essas versões permanecem com suporte até que a versão do [.net atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do SLES não seja mais suportada.</span><span class="sxs-lookup"><span data-stu-id="0209d-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="0209d-109">Um ✔️ indica que a versão do SLES ou do .NET ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="0209d-109">A ✔️ indicates that the version of SLES or .NET is still supported.</span></span>
- <span data-ttu-id="0209d-110">Um ❌ indica que a versão do SLES ou do .net não tem suporte nessa versão do SLES.</span><span class="sxs-lookup"><span data-stu-id="0209d-110">A ❌ indicates that the version of SLES or .NET isn't supported on that SLES release.</span></span>
- <span data-ttu-id="0209d-111">Quando uma versão do SLES e uma versão do .NET têm ✔️, essa combinação de so e .NET é suportada.</span><span class="sxs-lookup"><span data-stu-id="0209d-111">When both a version of SLES and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="0209d-112">SLES</span><span class="sxs-lookup"><span data-stu-id="0209d-112">SLES</span></span>                   | <span data-ttu-id="0209d-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0209d-113">.NET Core 2.1</span></span> | <span data-ttu-id="0209d-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="0209d-114">.NET Core 3.1</span></span> | <span data-ttu-id="0209d-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="0209d-115">.NET 5.0</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="0209d-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="0209d-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="0209d-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0209d-117">✔️ 2.1</span></span>        | <span data-ttu-id="0209d-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0209d-118">✔️ 3.1</span></span>        | <span data-ttu-id="0209d-119">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="0209d-119">✔️ 5.0</span></span> |
| <span data-ttu-id="0209d-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="0209d-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="0209d-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0209d-121">✔️ 2.1</span></span>        | <span data-ttu-id="0209d-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0209d-122">✔️ 3.1</span></span>        | <span data-ttu-id="0209d-123">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="0209d-123">✔️ 5.0</span></span> |

<span data-ttu-id="0209d-124">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0209d-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="0209d-125">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="0209d-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="0209d-126">3.0</span><span class="sxs-lookup"><span data-stu-id="0209d-126">3.0</span></span>
- <span data-ttu-id="0209d-127">2.2</span><span class="sxs-lookup"><span data-stu-id="0209d-127">2.2</span></span>
- <span data-ttu-id="0209d-128">2.0</span><span class="sxs-lookup"><span data-stu-id="0209d-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="0209d-129">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="0209d-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="0209d-130">✔️ SLES 15</span><span class="sxs-lookup"><span data-stu-id="0209d-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="0209d-131">Atualmente, o pacote de instalação do repositório do SLES 15 da Microsoft instala o arquivo *Microsoft-prod. repositório* no diretório errado, impedindo que o Zypper Localize os pacotes .net.</span><span class="sxs-lookup"><span data-stu-id="0209d-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET packages.</span></span> <span data-ttu-id="0209d-132">Para corrigir esse problema, crie um symlink no diretório correto.</span><span class="sxs-lookup"><span data-stu-id="0209d-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="0209d-133">✔️ SLES 12</span><span class="sxs-lookup"><span data-stu-id="0209d-133">SLES 12 ✔️</span></span>

<span data-ttu-id="0209d-134">O .NET requer o SP2 como um mínimo para a família SLES 12.</span><span class="sxs-lookup"><span data-stu-id="0209d-134">.NET requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="0209d-135">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="0209d-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="0209d-136">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET.</span><span class="sxs-lookup"><span data-stu-id="0209d-136">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="0209d-137">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="0209d-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="0209d-138">Dependências</span><span class="sxs-lookup"><span data-stu-id="0209d-138">Dependencies</span></span>

<span data-ttu-id="0209d-139">Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você.</span><span class="sxs-lookup"><span data-stu-id="0209d-139">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="0209d-140">Mas, se você instalar o .NET manualmente ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="0209d-140">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="0209d-141">krb5</span><span class="sxs-lookup"><span data-stu-id="0209d-141">krb5</span></span>
- <span data-ttu-id="0209d-142">libicu</span><span class="sxs-lookup"><span data-stu-id="0209d-142">libicu</span></span>
- <span data-ttu-id="0209d-143">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="0209d-143">libopenssl1_1</span></span>

<span data-ttu-id="0209d-144">Se a versão do OpenSSL do ambiente de tempo de execução de destino for 1,1 ou mais recente, você precisará instalar o **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="0209d-144">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="0209d-145">Para obter mais informações sobre as dependências, consulte [aplicativos do Linux autocontidos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="0209d-145">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="0209d-146">Para aplicativos .NET que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="0209d-146">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="0209d-147">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="0209d-147">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="0209d-148">Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="0209d-148">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="0209d-149">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="0209d-149">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="0209d-150">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="0209d-150">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="0209d-151">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="0209d-151">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="0209d-152">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="0209d-152">Next steps</span></span>

- [<span data-ttu-id="0209d-153">Tutorial: criar um aplicativo de console com o SDK do .NET usando o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0209d-153">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
