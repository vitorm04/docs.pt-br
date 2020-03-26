---
title: Instale o .NET Core no Debian 9 - gerenciador de pacotes - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no Debian 9.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: cfe28d04edfac97938612537986498636c141be0
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134302"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="7fbd4-103">Debian 9 Package Manager - Instalar .NET Core</span><span class="sxs-lookup"><span data-stu-id="7fbd4-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="7fbd4-104">Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no Debian 9.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="7fbd4-105">Registrar a chave e o feed da Microsoft</span><span class="sxs-lookup"><span data-stu-id="7fbd4-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="7fbd4-106">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="7fbd4-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="7fbd4-107">Registre a chave da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="7fbd4-108">Registre o repositório do produto.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-108">Register the product repository.</span></span>
- <span data-ttu-id="7fbd4-109">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-109">Install required dependencies.</span></span>

<span data-ttu-id="7fbd4-110">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="7fbd4-111">Abra um terminal e execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="7fbd4-112">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="7fbd4-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="7fbd4-113">Atualize os produtos disponíveis para instalação e instale o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="7fbd4-114">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="7fbd4-115">Instale o tempo de execução do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7fbd4-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="7fbd4-116">Atualize os produtos disponíveis para instalação e instale o ASP.NET tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="7fbd4-117">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="7fbd4-118">Instale o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="7fbd4-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="7fbd4-119">Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="7fbd4-120">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="7fbd4-121">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="7fbd4-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="7fbd4-122">Solucionar problemas do gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="7fbd4-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="7fbd4-123">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7fbd4-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="7fbd4-124">Falhou em buscar</span><span class="sxs-lookup"><span data-stu-id="7fbd4-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
