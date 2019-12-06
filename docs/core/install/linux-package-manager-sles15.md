---
title: Instalar o .NET Core no SLES 15-Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no SLES 15.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 5551ce8cffa92d4efb6bbe9db2a4887f4b26cd6e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836909"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="577cf-103">Gerenciador de pacotes SLES 15 – instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="577cf-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="577cf-104">Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no SLES 15.</span><span class="sxs-lookup"><span data-stu-id="577cf-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span> <span data-ttu-id="577cf-105">Se você estiver instalando o tempo de execução, sugerimos que instale o [ASP.NET Core Runtime](#install-the-aspnet-core-runtime), pois ele inclui o .NET Core e ASP.NET Core Runtimes.</span><span class="sxs-lookup"><span data-stu-id="577cf-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="577cf-106">Registrar a chave e o feed da Microsoft</span><span class="sxs-lookup"><span data-stu-id="577cf-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="577cf-107">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="577cf-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="577cf-108">Registrar a chave da Microsoft</span><span class="sxs-lookup"><span data-stu-id="577cf-108">Register the Microsoft key</span></span>
- <span data-ttu-id="577cf-109">registrar o repositório do produto</span><span class="sxs-lookup"><span data-stu-id="577cf-109">register the product repository</span></span>
- <span data-ttu-id="577cf-110">Instalar dependências necessárias</span><span class="sxs-lookup"><span data-stu-id="577cf-110">Install required dependencies</span></span>

<span data-ttu-id="577cf-111">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="577cf-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="577cf-112">Abra um terminal e execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="577cf-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="577cf-113">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="577cf-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="577cf-114">Atualize os produtos disponíveis para instalação e, em seguida, instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="577cf-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="577cf-115">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="577cf-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="577cf-116">Instalar o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="577cf-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="577cf-117">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="577cf-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="577cf-118">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="577cf-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="577cf-119">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="577cf-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="577cf-120">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="577cf-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="577cf-121">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="577cf-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="577cf-122">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="577cf-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
