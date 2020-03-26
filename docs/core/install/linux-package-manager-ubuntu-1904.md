---
title: Instale o .NET Core no Gerenciador de pacotes Ubuntu 19.04 - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no Ubuntu 19.04.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: a0a6cedb6dbf572750fcc238aff59b7f66edf44f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134140"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a><span data-ttu-id="316ea-103">Ubuntu 19.04 Package Manager - Instalar .NET Core</span><span class="sxs-lookup"><span data-stu-id="316ea-103">Ubuntu 19.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="316ea-104">Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no Ubuntu 19.04.</span><span class="sxs-lookup"><span data-stu-id="316ea-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="316ea-105">Registrar a chave e o feed da Microsoft</span><span class="sxs-lookup"><span data-stu-id="316ea-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="316ea-106">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="316ea-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="316ea-107">Registre a chave da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="316ea-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="316ea-108">Registre o repositório do produto.</span><span class="sxs-lookup"><span data-stu-id="316ea-108">Register the product repository.</span></span>
- <span data-ttu-id="316ea-109">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="316ea-109">Install required dependencies.</span></span>

<span data-ttu-id="316ea-110">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="316ea-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="316ea-111">Abra um terminal e execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="316ea-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="316ea-112">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="316ea-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="316ea-113">Atualize os produtos disponíveis para instalação e instale o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="316ea-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="316ea-114">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="316ea-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="316ea-115">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote dotnet-sdk-3.1,** consulte a [solucionar problemas na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.</span><span class="sxs-lookup"><span data-stu-id="316ea-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="316ea-116">Instale o tempo de execução do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="316ea-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="316ea-117">Atualize os produtos disponíveis para instalação e instale o tempo de execução do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="316ea-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="316ea-118">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="316ea-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="316ea-119">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote aspnetcore-runtime-3.1,** consulte a [solucionar problemas na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.</span><span class="sxs-lookup"><span data-stu-id="316ea-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="316ea-120">Instale o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="316ea-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="316ea-121">Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="316ea-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="316ea-122">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="316ea-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="316ea-123">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o tempo de execução do dotnet-3.1**do pacote, consulte a [seção 'Solucionar problemas' na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.</span><span class="sxs-lookup"><span data-stu-id="316ea-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="316ea-124">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="316ea-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="316ea-125">Solucionar problemas do gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="316ea-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="316ea-126">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="316ea-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="316ea-127">Não é possível localizar</span><span class="sxs-lookup"><span data-stu-id="316ea-127">Unable to locate</span></span>

<span data-ttu-id="316ea-128">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote {o pacote .NET Core},** execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="316ea-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="316ea-129">Se isso não funcionar, você pode executar uma instalação manual com os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="316ea-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="316ea-130">Falhou em buscar</span><span class="sxs-lookup"><span data-stu-id="316ea-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
