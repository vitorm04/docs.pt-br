---
title: Pré-requisitos para .NET Core no Mac
description: Suporte para versões do macOS e dependências do .NET Core para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS.
author: guardrex
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: e895306164b93cb94dab2161971f99eae3138be9
ms.sourcegitcommit: 90775b20343b6ad831af6f5380f8ab7553abb16b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54186170"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="20c3d-103">Pré-requisitos para o .NET Core no macOS</span><span class="sxs-lookup"><span data-stu-id="20c3d-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="20c3d-104">Este artigo mostra as versões para macOS e dependências do .NET Core com o suporte que você precisa para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS.</span><span class="sxs-lookup"><span data-stu-id="20c3d-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="20c3d-105">As dependências e versões de sistemas operacionais com suporte a seguir se aplicam às três maneiras de desenvolver aplicativos do .NET Core no Mac: por meio da [linha de comando com o editor favorito](tutorials/using-with-xplat-cli.md), do [Visual Studio Code](https://code.visualstudio.com/) e do [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="20c3d-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="20c3d-106">Versões para macOS com suporte</span><span class="sxs-lookup"><span data-stu-id="20c3d-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="20c3d-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="20c3d-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="20c3d-108">Há suporte para o .NET Core 2.x nas seguintes versões do macOS:</span><span class="sxs-lookup"><span data-stu-id="20c3d-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="20c3d-109">macOS 10.12 “Sierra” e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="20c3d-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="20c3d-110">Confira [Versões de sistema operacional compatíveis com o .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) e [Versões de sistema operacional compatíveis com o .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o .NET Core 2.1 e o .NET Core 2.2, versões de sistema operacional sem suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="20c3d-110">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="20c3d-111">Para acessar os links de download e saber mais, confira [Downloads do .NET Core 2.2](https://www.microsoft.com/net/download/dotnet-core/2.2) ou [Downloads do .NET Core 2.1](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="20c3d-111">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>


# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="20c3d-112">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="20c3d-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="20c3d-113">Há suporte para o .NET Core 1.x nas seguintes versões do macOS:</span><span class="sxs-lookup"><span data-stu-id="20c3d-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="20c3d-114">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="20c3d-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="20c3d-115">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="20c3d-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="20c3d-116">Confira [Versões de sistema operacional compatíveis com o .NET Core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) e [Versões de sistema operacional compatíveis com o .NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o .NET Core 1.1 e o .NET Core 1.0, versões de sistema operacional sem suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="20c3d-116">See [.NET Core 1.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) and [.NET Core 1.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.1 and .NET Core 1.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="20c3d-117">Para acessar os links de download e saber mais, confira [Downloads do .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) ou [Downloads do .NET Core 1.0](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="20c3d-117">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="20c3d-118">.NET Core 3.0 Versão Prévia 1</span><span class="sxs-lookup"><span data-stu-id="20c3d-118">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="20c3d-119">Há suporte para o .NET Core 3.0 Versão Prévia 1 nas seguintes versões do macOS:</span><span class="sxs-lookup"><span data-stu-id="20c3d-119">.NET Core 3.0 Preview 1 is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="20c3d-120">macOS 10.12 “Sierra” e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="20c3d-120">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="20c3d-121">Confira [Versões de sistema operacional compatíveis com o .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o.NET Core 3.0, versões de sistema operacional sem suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="20c3d-121">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="20c3d-122">Para obter links de download e mais informações, confira [Downloads do .NET Core 3.0](https://www.microsoft.com/net/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="20c3d-122">For download links and more information, see [.NET Core 3.0 downloads](https://www.microsoft.com/net/download/dotnet-core/3.0).</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="20c3d-123">Dependências do .NET Core</span><span class="sxs-lookup"><span data-stu-id="20c3d-123">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="20c3d-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="20c3d-124">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="20c3d-125">Faça download e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core).</span><span class="sxs-lookup"><span data-stu-id="20c3d-125">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="20c3d-126">Se você tiver problemas com a instalação no macOS, veja o tópico [Problemas conhecidos](https://github.com/dotnet/core/tree/master/release-notes/2.1) para a versão instalada.</span><span class="sxs-lookup"><span data-stu-id="20c3d-126">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="20c3d-127">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="20c3d-127">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="20c3d-128">O .NET Core 1.x exige OpenSSL para execução em macOS.</span><span class="sxs-lookup"><span data-stu-id="20c3d-128">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="20c3d-129">Uma maneira fácil de obter o OpenSSL é usando o gerenciador de pacotes [Homebrew ("brew")](https://brew.sh/) para macOS.</span><span class="sxs-lookup"><span data-stu-id="20c3d-129">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="20c3d-130">Depois de instalar o *brew*, instale o OpenSSL executando os seguintes comandos em um prompt (de comando) do Terminal:</span><span class="sxs-lookup"><span data-stu-id="20c3d-130">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="20c3d-131">Faça download e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core).</span><span class="sxs-lookup"><span data-stu-id="20c3d-131">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="20c3d-132">Se você tiver problemas com a instalação no macOS, veja os tópicos [Problemas conhecidos do 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) e [Problemas conhecidos do 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="20c3d-132">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="20c3d-133">.NET Core 3.0 Versão Prévia 1</span><span class="sxs-lookup"><span data-stu-id="20c3d-133">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="20c3d-134">Faça download e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core).</span><span class="sxs-lookup"><span data-stu-id="20c3d-134">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="20c3d-135">Caso tenha problemas com a instalação no macOS, consulte o tópico [Notas sobre a versão](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) da versão instalada.</span><span class="sxs-lookup"><span data-stu-id="20c3d-135">If you have problems with the installation on macOS, consult the [Release notes](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) topic for the version you have installed.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="20c3d-136">Aumentar o limite máximo de arquivos abertos (versões do .NET Core anteriores ao SDK do .NET Core 2.0.2)</span><span class="sxs-lookup"><span data-stu-id="20c3d-136">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span> 

<span data-ttu-id="20c3d-137">Em versões anteriores do .NET Core (anteriores ao SDK do .NET Core 2.0.2), o limite padrão de arquivos abertos no macOS pode não ser suficiente para algumas cargas de trabalho do .NET Core, como restauração de projetos ou execução de testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="20c3d-137">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="20c3d-138">Aumente esse limite seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="20c3d-138">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="20c3d-139">Usando um editor de texto, crie um novo arquivo _/Library/LaunchDaemons/limit.maxfiles.plist_ e salve o arquivo com este conteúdo:</span><span class="sxs-lookup"><span data-stu-id="20c3d-139">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>limit.maxfiles</string>
    <key>ProgramArguments</key>
    <array>
      <string>launchctl</string>
      <string>limit</string>
      <string>maxfiles</string>
      <string>2048</string>
      <string>4096</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>ServiceIPC</key>
    <false/>
  </dict>
</plist>
```

2. <span data-ttu-id="20c3d-140">Em uma janela do terminal, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="20c3d-140">In a terminal window, run the following command:</span></span>

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. <span data-ttu-id="20c3d-141">Reinicialize o Mac para aplicar essas configurações.</span><span class="sxs-lookup"><span data-stu-id="20c3d-141">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="20c3d-142">Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="20c3d-142">Visual Studio for Mac</span></span>

<span data-ttu-id="20c3d-143">Você pode usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="20c3d-143">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="20c3d-144">No entanto, se você quiser desenvolver aplicativos .NET Core no Mac em um ambiente de desenvolvimento integrado, use o [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="20c3d-144">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="20c3d-145">O desenvolvimento em .NET Core no macOS com Visual Studio para Mac exige:</span><span class="sxs-lookup"><span data-stu-id="20c3d-145">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="20c3d-146">Uma versão com suporte do sistema operacional macOS</span><span class="sxs-lookup"><span data-stu-id="20c3d-146">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="20c3d-147">OpenSSL (apenas .NET Core 1.x; o .NET Core 2.x usa os serviços de segurança disponíveis nativamente no macOS)</span><span class="sxs-lookup"><span data-stu-id="20c3d-147">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="20c3d-148">SDK do .NET Core para Mac</span><span class="sxs-lookup"><span data-stu-id="20c3d-148">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="20c3d-149">Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="20c3d-149">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
