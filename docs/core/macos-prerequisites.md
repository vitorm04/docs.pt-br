---
title: "Pré-requisitos para .NET Core no Mac"
description: "Suporte para versões do macOS e dependências do .NET Core para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS."
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 07/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8feaee2cbfa55e23bd49c0ab76d995f15be343b4
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="prerequisites-for-net-core-on-mac"></a><span data-ttu-id="976e0-104">Pré-requisitos para .NET Core no Mac</span><span class="sxs-lookup"><span data-stu-id="976e0-104">Prerequisites for .NET Core on Mac</span></span>

<span data-ttu-id="976e0-105">Este artigo mostra as versões para macOS e dependências do .NET Core com o suporte que você precisa para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS.</span><span class="sxs-lookup"><span data-stu-id="976e0-105">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="976e0-106">As dependências e versões de sistemas operacionais com suporte a seguir se aplicam às três maneiras de desenvolver aplicativos do .NET Core no Mac: por meio da [linha de comando com o editor favorito](tutorials/using-with-xplat-cli.md), do [Visual Studio Code](https://code.visualstudio.com/) e do [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="976e0-106">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="976e0-107">Versões para macOS com suporte</span><span class="sxs-lookup"><span data-stu-id="976e0-107">Supported macOS versions</span></span>

<span data-ttu-id="976e0-108">O .NET Core é compatível com as seguintes versões do macOS:</span><span class="sxs-lookup"><span data-stu-id="976e0-108">.NET Core is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="976e0-109">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="976e0-109">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="976e0-110">macOS 10.11 "El Capitan" (somente .NET Core 1.x)</span><span class="sxs-lookup"><span data-stu-id="976e0-110">macOS 10.11 "El Capitan" (.NET Core 1.x only)</span></span>

<span data-ttu-id="976e0-111">Confira as [Versões de sistema operacional com suporte](https://github.com/dotnet/core/blob/master/roadmap.md#supported-os-versions) para obter a lista completa de sistemas operacionais com suporte.</span><span class="sxs-lookup"><span data-stu-id="976e0-111">See [Supported OS Versions](https://github.com/dotnet/core/blob/master/roadmap.md#supported-os-versions) for the complete list of supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="976e0-112">Dependências do .NET Core</span><span class="sxs-lookup"><span data-stu-id="976e0-112">.NET Core dependencies</span></span>

<span data-ttu-id="976e0-113">**.NET Core 1.x**</span><span class="sxs-lookup"><span data-stu-id="976e0-113">**.NET Core 1.x**</span></span>

<span data-ttu-id="976e0-114">O .NET Core 1.x exige OpenSSL para execução em macOS.</span><span class="sxs-lookup"><span data-stu-id="976e0-114">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="976e0-115">Uma maneira fácil de obter o OpenSSL é usando o gerenciador de pacotes [Homebrew ("brew")](https://brew.sh/) para macOS.</span><span class="sxs-lookup"><span data-stu-id="976e0-115">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="976e0-116">Depois de instalar o *brew*, instale o OpenSSL executando os seguintes comandos em um prompt (de comando) do Terminal:</span><span class="sxs-lookup"><span data-stu-id="976e0-116">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="976e0-117">Baixe e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core).</span><span class="sxs-lookup"><span data-stu-id="976e0-117">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="976e0-118">Se você tiver problemas com a instalação no macOS, veja os tópicos [Problemas conhecidos do 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) e [Problemas conhecidos do 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="976e0-118">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

<span data-ttu-id="976e0-119">**.NET Core 2.x**</span><span class="sxs-lookup"><span data-stu-id="976e0-119">**.NET Core 2.x**</span></span>

<span data-ttu-id="976e0-120">Baixe e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core).</span><span class="sxs-lookup"><span data-stu-id="976e0-120">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="976e0-121">Se você tiver problemas com a instalação no macOS, veja o tópico [Problemas conhecidos](https://github.com/dotnet/core/tree/master/release-notes/2.0) para a versão instalada.</span><span class="sxs-lookup"><span data-stu-id="976e0-121">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="976e0-122">Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="976e0-122">Visual Studio for Mac</span></span>

<span data-ttu-id="976e0-123">Você pode usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="976e0-123">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="976e0-124">No entanto, se você quiser desenvolver aplicativos .NET Core no Mac em um ambiente de desenvolvimento integrado, use o [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="976e0-124">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="976e0-125">O desenvolvimento em .NET Core no macOS com Visual Studio para Mac exige:</span><span class="sxs-lookup"><span data-stu-id="976e0-125">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="976e0-126">Uma versão com suporte do sistema operacional macOS</span><span class="sxs-lookup"><span data-stu-id="976e0-126">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="976e0-127">OpenSSL (apenas .NET Core 1.x; o .NET Core 2.x usa os serviços de segurança disponíveis nativamente no macOS)</span><span class="sxs-lookup"><span data-stu-id="976e0-127">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="976e0-128">SDK do .NET Core para Mac</span><span class="sxs-lookup"><span data-stu-id="976e0-128">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="976e0-129">Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="976e0-129">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

