---
title: "Pré-requisitos para .NET Core no Mac"
description: "Suporte para versões do macOS e dependências do .NET Core para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS."
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: 5aac7566f532312c890bad07c901929ae826ece3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="ef80e-104">Pré-requisitos para o .NET Core no macOS</span><span class="sxs-lookup"><span data-stu-id="ef80e-104">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="ef80e-105">Este artigo mostra as versões para macOS e dependências do .NET Core com o suporte que você precisa para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS.</span><span class="sxs-lookup"><span data-stu-id="ef80e-105">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="ef80e-106">As dependências e versões de sistemas operacionais com suporte a seguir se aplicam às três maneiras de desenvolver aplicativos do .NET Core no Mac: por meio da [linha de comando com o editor favorito](tutorials/using-with-xplat-cli.md), do [Visual Studio Code](https://code.visualstudio.com/) e do [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="ef80e-106">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="ef80e-107">Versões para macOS com suporte</span><span class="sxs-lookup"><span data-stu-id="ef80e-107">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ef80e-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ef80e-108">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ef80e-109">Há suporte para o .NET Core 2.x nas seguintes versões do macOS:</span><span class="sxs-lookup"><span data-stu-id="ef80e-109">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="ef80e-110">macOS 10.12 “Sierra” e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="ef80e-110">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="ef80e-111">Consulte [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 2.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 2.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="ef80e-111">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ef80e-112">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ef80e-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ef80e-113">Há suporte para o .NET Core 1.x nas seguintes versões do macOS:</span><span class="sxs-lookup"><span data-stu-id="ef80e-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="ef80e-114">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="ef80e-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="ef80e-115">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="ef80e-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="ef80e-116">Consulte [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 1.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 1.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="ef80e-116">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="ef80e-117">Dependências do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef80e-117">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ef80e-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ef80e-118">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ef80e-119">Baixe e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core).</span><span class="sxs-lookup"><span data-stu-id="ef80e-119">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="ef80e-120">Se você tiver problemas com a instalação no macOS, veja o tópico [Problemas conhecidos](https://github.com/dotnet/core/tree/master/release-notes/2.0) para a versão instalada.</span><span class="sxs-lookup"><span data-stu-id="ef80e-120">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ef80e-121">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ef80e-121">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ef80e-122">**.NET Core 1.x**</span><span class="sxs-lookup"><span data-stu-id="ef80e-122">**.NET Core 1.x**</span></span>

<span data-ttu-id="ef80e-123">O .NET Core 1.x exige OpenSSL para execução em macOS.</span><span class="sxs-lookup"><span data-stu-id="ef80e-123">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="ef80e-124">Uma maneira fácil de obter o OpenSSL é usando o gerenciador de pacotes [Homebrew ("brew")](https://brew.sh/) para macOS.</span><span class="sxs-lookup"><span data-stu-id="ef80e-124">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="ef80e-125">Depois de instalar o *brew*, instale o OpenSSL executando os seguintes comandos em um prompt (de comando) do Terminal:</span><span class="sxs-lookup"><span data-stu-id="ef80e-125">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="ef80e-126">Baixe e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core).</span><span class="sxs-lookup"><span data-stu-id="ef80e-126">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="ef80e-127">Se você tiver problemas com a instalação no macOS, veja os tópicos [Problemas conhecidos do 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) e [Problemas conhecidos do 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="ef80e-127">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit"></a><span data-ttu-id="ef80e-128">Aumentar o limite máximo de arquivos abertos</span><span class="sxs-lookup"><span data-stu-id="ef80e-128">Increase the maximum open file limit</span></span>

<span data-ttu-id="ef80e-129">O limite padrão de arquivos abertos no macOS pode não ser suficiente para algumas cargas de trabalho do .NET Core, como restauração de projetos ou execução de testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="ef80e-129">The default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="ef80e-130">Aumente esse limite seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="ef80e-130">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="ef80e-131">Usando um editor de texto, crie um novo arquivo _/Library/LaunchDaemons/limit.maxfiles.plist_ e salve o arquivo com este conteúdo:</span><span class="sxs-lookup"><span data-stu-id="ef80e-131">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
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

2. <span data-ttu-id="ef80e-132">Em uma janela do terminal, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="ef80e-132">In a terminal window, run the following command:</span></span>

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. <span data-ttu-id="ef80e-133">Reinicialize o Mac para aplicar essas configurações.</span><span class="sxs-lookup"><span data-stu-id="ef80e-133">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="ef80e-134">Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="ef80e-134">Visual Studio for Mac</span></span>

<span data-ttu-id="ef80e-135">Você pode usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef80e-135">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="ef80e-136">No entanto, se você quiser desenvolver aplicativos .NET Core no Mac em um ambiente de desenvolvimento integrado, use o [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="ef80e-136">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="ef80e-137">O desenvolvimento em .NET Core no macOS com Visual Studio para Mac exige:</span><span class="sxs-lookup"><span data-stu-id="ef80e-137">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="ef80e-138">Uma versão com suporte do sistema operacional macOS</span><span class="sxs-lookup"><span data-stu-id="ef80e-138">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="ef80e-139">OpenSSL (apenas .NET Core 1.x; o .NET Core 2.x usa os serviços de segurança disponíveis nativamente no macOS)</span><span class="sxs-lookup"><span data-stu-id="ef80e-139">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="ef80e-140">SDK do .NET Core para Mac</span><span class="sxs-lookup"><span data-stu-id="ef80e-140">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="ef80e-141">Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="ef80e-141">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)
