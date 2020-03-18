---
title: Instale o .NET Core no CentOS 7 - gerenciador de pacotes - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 66e78aadf933d3e10b99e3d2c7258733e96164f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920862"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="7701d-103">Gerenciador de pacotes CentOS 7 - Instalar .NET Core</span><span class="sxs-lookup"><span data-stu-id="7701d-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="7701d-104">Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no CentOS 7.</span><span class="sxs-lookup"><span data-stu-id="7701d-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span> <span data-ttu-id="7701d-105">Se você estiver instalando o tempo de execução, sugerimos que você instale o [tempo de execução do ASP.NET Core,](#install-the-aspnet-core-runtime)pois inclui os tempos de execução do .NET Core e do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7701d-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="7701d-106">Registrar a chave e o feed da Microsoft</span><span class="sxs-lookup"><span data-stu-id="7701d-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="7701d-107">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="7701d-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="7701d-108">Registre a chave da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7701d-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="7701d-109">Registre o repositório do produto.</span><span class="sxs-lookup"><span data-stu-id="7701d-109">Register the product repository.</span></span>
- <span data-ttu-id="7701d-110">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="7701d-110">Install required dependencies.</span></span>

<span data-ttu-id="7701d-111">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="7701d-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="7701d-112">Abra um terminal e execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="7701d-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="7701d-113">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="7701d-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="7701d-114">Atualize os produtos disponíveis para instalação e instale o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="7701d-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="7701d-115">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="7701d-115">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="7701d-116">Instale o tempo de execução do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7701d-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="7701d-117">Atualize os produtos disponíveis para instalação e instale o ASP.NET tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7701d-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="7701d-118">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="7701d-118">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="7701d-119">Instale o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="7701d-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="7701d-120">Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7701d-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="7701d-121">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="7701d-121">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="7701d-122">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="7701d-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="7701d-123">Solucionar problemas do gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="7701d-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="7701d-124">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7701d-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="7701d-125">Falhou em buscar</span><span class="sxs-lookup"><span data-stu-id="7701d-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
