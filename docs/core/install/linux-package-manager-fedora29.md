---
title: Instalar o .NET Core no Fedora 29-Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no Fedora 29.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 1cd761e323467ef34fdad58de7385c1ca7b2c14a
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836958"
---
# <a name="fedora-29-package-manager---install-net-core"></a><span data-ttu-id="fa9b9-103">Fedora 29 Package Manager – instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="fa9b9-103">Fedora 29 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="fa9b9-104">Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no Fedora 29.</span><span class="sxs-lookup"><span data-stu-id="fa9b9-104">This article describes how to use a package manager to install .NET Core on Fedora 29.</span></span> <span data-ttu-id="fa9b9-105">Se você estiver instalando o tempo de execução, sugerimos que instale o [ASP.NET Core Runtime](#install-the-aspnet-core-runtime), pois ele inclui o .NET Core e ASP.NET Core Runtimes.</span><span class="sxs-lookup"><span data-stu-id="fa9b9-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="fa9b9-106">Registrar a chave e o feed da Microsoft</span><span class="sxs-lookup"><span data-stu-id="fa9b9-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="fa9b9-107">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="fa9b9-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="fa9b9-108">Registrar a chave da Microsoft</span><span class="sxs-lookup"><span data-stu-id="fa9b9-108">Register the Microsoft key</span></span>
- <span data-ttu-id="fa9b9-109">registrar o repositório do produto</span><span class="sxs-lookup"><span data-stu-id="fa9b9-109">register the product repository</span></span>
- <span data-ttu-id="fa9b9-110">Instalar dependências necessárias</span><span class="sxs-lookup"><span data-stu-id="fa9b9-110">Install required dependencies</span></span>

<span data-ttu-id="fa9b9-111">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="fa9b9-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="fa9b9-112">Abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa9b9-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="fa9b9-113">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="fa9b9-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="fa9b9-114">Atualize os produtos disponíveis para instalação e, em seguida, instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fa9b9-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="fa9b9-115">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa9b9-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="fa9b9-116">Instalar o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="fa9b9-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="fa9b9-117">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fa9b9-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="fa9b9-118">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa9b9-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="fa9b9-119">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="fa9b9-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="fa9b9-120">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fa9b9-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="fa9b9-121">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa9b9-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="fa9b9-122">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="fa9b9-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
