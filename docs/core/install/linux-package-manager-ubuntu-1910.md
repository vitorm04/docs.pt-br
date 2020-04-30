---
title: Instalar o .NET Core no Ubuntu 19,10 Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no Ubuntu 19,10.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 9e77628d557e52c61ee75d6d6affe21f627ec40a
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595592"
---
# <a name="ubuntu-1910-package-manager---install-net-core"></a><span data-ttu-id="5f589-103">Gerenciador de pacotes do Ubuntu 19,10 – instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f589-103">Ubuntu 19.10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="5f589-104">Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no Ubuntu 19,10.</span><span class="sxs-lookup"><span data-stu-id="5f589-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.10.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="5f589-105">Adicionar chave e feed do repositório da Microsoft</span><span class="sxs-lookup"><span data-stu-id="5f589-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="5f589-106">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="5f589-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="5f589-107">Adicione a chave de assinatura do pacote da Microsoft à lista de chaves confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5f589-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="5f589-108">Adicione o repositório ao Gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="5f589-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="5f589-109">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="5f589-109">Install required dependencies.</span></span>

<span data-ttu-id="5f589-110">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="5f589-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="5f589-111">Abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f589-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="5f589-112">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f589-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="5f589-113">Atualize os produtos disponíveis para instalação e, em seguida, instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f589-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="5f589-114">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f589-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="5f589-115">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote dotnet-SDK-3,1**, consulte a seção [solucionar problemas do Gerenciador de pacotes](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="5f589-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="5f589-116">Instalar o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="5f589-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="5f589-117">Atualize os produtos disponíveis para instalação e instale o ASP.NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="5f589-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="5f589-118">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f589-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="5f589-119">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote aspnetcore-Runtime-3,1**, consulte a seção [solucionar problemas do Gerenciador de pacotes](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="5f589-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="5f589-120">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f589-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="5f589-121">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f589-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="5f589-122">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f589-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="5f589-123">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote dotnet-Runtime-3,1**, consulte a seção [solucionar problemas do Gerenciador de pacotes](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="5f589-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="5f589-124">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="5f589-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="5f589-125">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="5f589-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="5f589-126">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f589-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="5f589-127">Não é possível localizar</span><span class="sxs-lookup"><span data-stu-id="5f589-127">Unable to locate</span></span>

<span data-ttu-id="5f589-128">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote {The .NET Core Package}**, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f589-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="5f589-129">Se isso não funcionar, você poderá executar uma instalação manual com os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f589-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/19.10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="5f589-130">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="5f589-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
