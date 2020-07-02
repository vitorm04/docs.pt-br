---
title: Instalar o .NET Core no SLES-.NET Core
description: Demonstra as várias maneiras de instalar o SDK do .NET Core e o tempo de execução do .NET Core no SLES.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 8f64efcc8206b47855871104e5b6914570c06da0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619410"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="47709-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no SLES</span><span class="sxs-lookup"><span data-stu-id="47709-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="47709-104">O .NET Core tem suporte no SLES.</span><span class="sxs-lookup"><span data-stu-id="47709-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="47709-105">Este artigo descreve como instalar o .NET Core no SLES.</span><span class="sxs-lookup"><span data-stu-id="47709-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="47709-106">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="47709-106">Supported distributions</span></span>

<span data-ttu-id="47709-107">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento no SLES 12 SP2 e no SLES 15.</span><span class="sxs-lookup"><span data-stu-id="47709-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="47709-108">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do SLES não seja mais suportada.</span><span class="sxs-lookup"><span data-stu-id="47709-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="47709-109">Um ✔️ indica que a versão do SLES ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="47709-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="47709-110">Um ❌ indica que a versão do SLES ou do .NET Core não tem suporte nessa versão do SLES.</span><span class="sxs-lookup"><span data-stu-id="47709-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="47709-111">Quando uma versão do SLES e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="47709-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="47709-112">SLES</span><span class="sxs-lookup"><span data-stu-id="47709-112">SLES</span></span>                   | <span data-ttu-id="47709-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="47709-113">.NET Core 2.1</span></span> | <span data-ttu-id="47709-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="47709-114">.NET Core 3.1</span></span> | <span data-ttu-id="47709-115">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="47709-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="47709-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="47709-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="47709-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="47709-117">✔️ 2.1</span></span>        | <span data-ttu-id="47709-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="47709-118">✔️ 3.1</span></span>        | <span data-ttu-id="47709-119">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="47709-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="47709-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="47709-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="47709-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="47709-121">✔️ 2.1</span></span>        | <span data-ttu-id="47709-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="47709-122">✔️ 3.1</span></span>        | <span data-ttu-id="47709-123">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="47709-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="47709-124">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="47709-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="47709-125">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="47709-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="47709-126">3.0</span><span class="sxs-lookup"><span data-stu-id="47709-126">3.0</span></span>
- <span data-ttu-id="47709-127">2.2</span><span class="sxs-lookup"><span data-stu-id="47709-127">2.2</span></span>
- <span data-ttu-id="47709-128">2,0</span><span class="sxs-lookup"><span data-stu-id="47709-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="47709-129">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="47709-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="47709-130">✔️ SLES 15</span><span class="sxs-lookup"><span data-stu-id="47709-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="47709-131">Atualmente, o pacote de instalação do repositório do SLES 15 da Microsoft instala o arquivo *Microsoft-prod.* Repository no diretório errado, impedindo que o Zypper Localize os pacotes do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="47709-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="47709-132">Para corrigir esse problema, crie um symlink no diretório correto.</span><span class="sxs-lookup"><span data-stu-id="47709-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="47709-133">✔️ SLES 12</span><span class="sxs-lookup"><span data-stu-id="47709-133">SLES 12 ✔️</span></span>

<span data-ttu-id="47709-134">O .NET Core requer o SP2 como um mínimo para a família SLES 12.</span><span class="sxs-lookup"><span data-stu-id="47709-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="47709-135">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="47709-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="47709-136">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="47709-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="47709-137">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="47709-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="47709-138">Dependências</span><span class="sxs-lookup"><span data-stu-id="47709-138">Dependencies</span></span>

<span data-ttu-id="47709-139">Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você.</span><span class="sxs-lookup"><span data-stu-id="47709-139">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="47709-140">Mas, se você instalar manualmente o .NET Core ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="47709-140">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="47709-141">krb5</span><span class="sxs-lookup"><span data-stu-id="47709-141">krb5</span></span>
- <span data-ttu-id="47709-142">libicu</span><span class="sxs-lookup"><span data-stu-id="47709-142">libicu</span></span>
- <span data-ttu-id="47709-143">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="47709-143">libopenssl1_1</span></span>

<span data-ttu-id="47709-144">Se a versão do OpenSSL do ambiente de tempo de execução de destino for 1,1 ou mais recente, você precisará instalar o **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="47709-144">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="47709-145">Para obter mais informações sobre as dependências, consulte [aplicativos do Linux autocontidos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="47709-145">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="47709-146">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="47709-146">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="47709-147">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="47709-147">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="47709-148">Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="47709-148">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="47709-149">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="47709-149">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="47709-150">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="47709-150">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="47709-151">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="47709-151">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="47709-152">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="47709-152">Next steps</span></span>

- [<span data-ttu-id="47709-153">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="47709-153">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
