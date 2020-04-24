---
title: Instale o .NET Core no Gerenciador de pacotes Ubuntu 19.04 - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no Ubuntu 19.04.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 3f338832185ed626289141f48cec88c1bf2e3a33
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645597"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a><span data-ttu-id="283d5-103">Ubuntu 19.04 Package Manager - Instalar .NET Core</span><span class="sxs-lookup"><span data-stu-id="283d5-103">Ubuntu 19.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="283d5-104">Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no Ubuntu 19.04.</span><span class="sxs-lookup"><span data-stu-id="283d5-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="283d5-105">Adicione a chave e o feed do repositório da Microsoft</span><span class="sxs-lookup"><span data-stu-id="283d5-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="283d5-106">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="283d5-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="283d5-107">Adicione a chave de assinatura do pacote da Microsoft à lista de chaves confiáveis.</span><span class="sxs-lookup"><span data-stu-id="283d5-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="283d5-108">Adicione o repositório ao gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="283d5-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="283d5-109">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="283d5-109">Install required dependencies.</span></span>

<span data-ttu-id="283d5-110">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="283d5-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="283d5-111">Abra um terminal e execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="283d5-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="283d5-112">Instale o .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="283d5-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="283d5-113">Atualize os produtos disponíveis para instalação e instale o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="283d5-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="283d5-114">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="283d5-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="283d5-115">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote dotnet-sdk-3.1,** consulte a [solucionar problemas na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.</span><span class="sxs-lookup"><span data-stu-id="283d5-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="283d5-116">Instale o tempo de execução do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="283d5-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="283d5-117">Atualize os produtos disponíveis para instalação e instale o tempo de execução do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="283d5-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="283d5-118">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="283d5-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="283d5-119">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote aspnetcore-runtime-3.1,** consulte a [solucionar problemas na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.</span><span class="sxs-lookup"><span data-stu-id="283d5-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="283d5-120">Instale o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="283d5-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="283d5-121">Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="283d5-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="283d5-122">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="283d5-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="283d5-123">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o tempo de execução do dotnet-3.1**do pacote, consulte a [seção 'Solucionar problemas' na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.</span><span class="sxs-lookup"><span data-stu-id="283d5-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="283d5-124">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="283d5-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="283d5-125">Solucionar problemas do gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="283d5-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="283d5-126">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="283d5-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="283d5-127">Não é possível localizar</span><span class="sxs-lookup"><span data-stu-id="283d5-127">Unable to locate</span></span>

<span data-ttu-id="283d5-128">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote {o pacote .NET Core},** execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="283d5-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="283d5-129">Se isso não funcionar, você pode executar uma instalação manual com os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="283d5-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="283d5-130">Falhou em buscar</span><span class="sxs-lookup"><span data-stu-id="283d5-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
