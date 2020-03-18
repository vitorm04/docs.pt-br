---
title: Instale o .NET Core no SLES 15 - gerenciador de pacotes - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no SLES 15.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: f48c131b4250bd04fffc0d815a3500732caacb7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76921041"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="9a2bc-103">SLES 15 Package Manager - Instalar .NET Core</span><span class="sxs-lookup"><span data-stu-id="9a2bc-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="9a2bc-104">Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no SLES 15.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span> <span data-ttu-id="9a2bc-105">Se você estiver instalando o tempo de execução, sugerimos que você instale o [tempo de execução do ASP.NET Core,](#install-the-aspnet-core-runtime)pois inclui os tempos de execução do .NET Core e do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="9a2bc-106">Registrar a chave e o feed da Microsoft</span><span class="sxs-lookup"><span data-stu-id="9a2bc-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="9a2bc-107">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="9a2bc-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="9a2bc-108">Registre a chave da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="9a2bc-109">Registre o repositório do produto.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-109">Register the product repository.</span></span>
- <span data-ttu-id="9a2bc-110">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-110">Install required dependencies.</span></span>

<span data-ttu-id="9a2bc-111">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="9a2bc-112">Abra um terminal e execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="9a2bc-113">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9a2bc-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="9a2bc-114">Atualize os produtos disponíveis para instalação e instale o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="9a2bc-115">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="9a2bc-116">Instale o tempo de execução do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9a2bc-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="9a2bc-117">Atualize os produtos disponíveis para instalação e instale o ASP.NET tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="9a2bc-118">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="9a2bc-119">Instale o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9a2bc-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="9a2bc-120">Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="9a2bc-121">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="9a2bc-122">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="9a2bc-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="9a2bc-123">Solucionar problemas do gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="9a2bc-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="9a2bc-124">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a2bc-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="9a2bc-125">Falhou em buscar</span><span class="sxs-lookup"><span data-stu-id="9a2bc-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-rpm.md)]
