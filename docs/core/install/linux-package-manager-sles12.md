---
title: Instale o .NET Core no SLES 12 - gerenciador de pacotes - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no SLES 12.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 8358107c682274fc2b75bf72689eaa4b168a86c5
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134214"
---
# <a name="sles-12-package-manager---install-net-core"></a><span data-ttu-id="73c2c-103">SLES 12 Package Manager - Instalar .NET Core</span><span class="sxs-lookup"><span data-stu-id="73c2c-103">SLES 12 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="73c2c-104">Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no SLES 12.</span><span class="sxs-lookup"><span data-stu-id="73c2c-104">This article describes how to use a package manager to install .NET Core on SLES 12.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="73c2c-105">Registrar a chave e o feed da Microsoft</span><span class="sxs-lookup"><span data-stu-id="73c2c-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="73c2c-106">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="73c2c-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="73c2c-107">Registre a chave da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="73c2c-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="73c2c-108">Registre o repositório do produto.</span><span class="sxs-lookup"><span data-stu-id="73c2c-108">Register the product repository.</span></span>
- <span data-ttu-id="73c2c-109">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="73c2c-109">Install required dependencies.</span></span>

<span data-ttu-id="73c2c-110">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="73c2c-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="73c2c-111">Abra um terminal e execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="73c2c-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="73c2c-112">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="73c2c-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="73c2c-113">Atualize os produtos disponíveis para instalação e instale o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="73c2c-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="73c2c-114">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="73c2c-114">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="73c2c-115">Instale o tempo de execução do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="73c2c-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="73c2c-116">Atualize os produtos disponíveis para instalação e instale o ASP.NET tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="73c2c-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="73c2c-117">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="73c2c-117">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="73c2c-118">Instale o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="73c2c-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="73c2c-119">Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="73c2c-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="73c2c-120">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="73c2c-120">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="73c2c-121">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="73c2c-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="73c2c-122">Solucionar problemas do gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="73c2c-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="73c2c-123">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="73c2c-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="73c2c-124">Falhou em buscar</span><span class="sxs-lookup"><span data-stu-id="73c2c-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
