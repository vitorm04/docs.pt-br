---
title: Instalar o .NET Core no CentOS 7-Gerenciador de pacotes-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 66e78aadf933d3e10b99e3d2c7258733e96164f6
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920862"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="b7e87-103">Gerenciador de pacotes do CentOS 7 – instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="b7e87-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="b7e87-104">Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no CentOS 7.</span><span class="sxs-lookup"><span data-stu-id="b7e87-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span> <span data-ttu-id="b7e87-105">Se você estiver instalando o tempo de execução, sugerimos que instale o [ASP.NET Core Runtime](#install-the-aspnet-core-runtime), pois ele inclui o .NET Core e ASP.NET Core Runtimes.</span><span class="sxs-lookup"><span data-stu-id="b7e87-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="b7e87-106">Registrar chave e feed da Microsoft</span><span class="sxs-lookup"><span data-stu-id="b7e87-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="b7e87-107">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="b7e87-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="b7e87-108">Registre a chave da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b7e87-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="b7e87-109">Registre o repositório do produto.</span><span class="sxs-lookup"><span data-stu-id="b7e87-109">Register the product repository.</span></span>
- <span data-ttu-id="b7e87-110">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="b7e87-110">Install required dependencies.</span></span>

<span data-ttu-id="b7e87-111">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="b7e87-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="b7e87-112">Abra um terminal e execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7e87-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="b7e87-113">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="b7e87-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="b7e87-114">Atualize os produtos disponíveis para instalação e, em seguida, instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b7e87-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="b7e87-115">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7e87-115">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="b7e87-116">Instalar o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="b7e87-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="b7e87-117">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b7e87-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="b7e87-118">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7e87-118">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="b7e87-119">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="b7e87-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="b7e87-120">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b7e87-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="b7e87-121">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7e87-121">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="b7e87-122">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="b7e87-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="b7e87-123">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="b7e87-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="b7e87-124">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b7e87-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="b7e87-125">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="b7e87-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
