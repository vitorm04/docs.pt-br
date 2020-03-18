---
title: Instale o .NET Core no Gerenciador de pacotes Ubuntu 16.04 - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no Ubuntu 16.04.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 6038e64a2aa50d09923454e346f05c58a6c1e2fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920709"
---
# <a name="ubuntu-1604-package-manager---install-net-core"></a><span data-ttu-id="cf1ab-103">Ubuntu 16.04 Package Manager - Instalar .NET Core</span><span class="sxs-lookup"><span data-stu-id="cf1ab-103">Ubuntu 16.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="cf1ab-104">Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no Ubuntu 16.04.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-104">This article describes how to use a package manager to install .NET Core on Ubuntu 16.04.</span></span> <span data-ttu-id="cf1ab-105">Se você estiver instalando o tempo de execução, sugerimos que você instale o [tempo de execução do ASP.NET Core,](#install-the-aspnet-core-runtime)pois inclui os tempos de execução do .NET Core e do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="cf1ab-106">Registrar a chave e o feed da Microsoft</span><span class="sxs-lookup"><span data-stu-id="cf1ab-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="cf1ab-107">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="cf1ab-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="cf1ab-108">Registre a chave da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="cf1ab-109">Registre o repositório do produto.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-109">Register the product repository.</span></span>
- <span data-ttu-id="cf1ab-110">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-110">Install required dependencies.</span></span>

<span data-ttu-id="cf1ab-111">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="cf1ab-112">Abra um terminal e execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="cf1ab-113">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cf1ab-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="cf1ab-114">Atualize os produtos disponíveis para instalação e instale o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="cf1ab-115">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="cf1ab-116">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote dotnet-sdk-3.1,** consulte a [solucionar problemas na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="cf1ab-117">Instale o tempo de execução do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cf1ab-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="cf1ab-118">Atualize os produtos disponíveis para instalação e instale o tempo de execução do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="cf1ab-119">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-119">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="cf1ab-120">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote aspnetcore-runtime-3.1,** consulte a [solucionar problemas na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="cf1ab-121">Instale o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cf1ab-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="cf1ab-122">Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="cf1ab-123">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-123">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="cf1ab-124">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o tempo de execução do dotnet-3.1**do pacote, consulte a [seção 'Solucionar problemas' na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="cf1ab-125">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="cf1ab-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="cf1ab-126">Solucionar problemas do gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="cf1ab-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="cf1ab-127">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-127">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="cf1ab-128">Não é possível localizar</span><span class="sxs-lookup"><span data-stu-id="cf1ab-128">Unable to locate</span></span>

<span data-ttu-id="cf1ab-129">Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote {o pacote .NET Core},** execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-129">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="cf1ab-130">Se isso não funcionar, você pode executar uma instalação manual com os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="cf1ab-130">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/16.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="cf1ab-131">Falhou em buscar</span><span class="sxs-lookup"><span data-stu-id="cf1ab-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
