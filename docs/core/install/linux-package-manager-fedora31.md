---
title: Instale o .NET Core no Fedora 31 - gerenciador de pacotes - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no Fedora 31.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 56e5789132af2aa1171ea51698ae55d1eea5d457
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645308"
---
# <a name="fedora-31-package-manager---install-net-core"></a><span data-ttu-id="85177-103">Fedora 31 Package Manager - Instalar .NET Core</span><span class="sxs-lookup"><span data-stu-id="85177-103">Fedora 31 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="85177-104">Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no Fedora 31.</span><span class="sxs-lookup"><span data-stu-id="85177-104">This article describes how to use a package manager to install .NET Core on Fedora 31.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="85177-105">Adicione a chave e o feed do repositório da Microsoft</span><span class="sxs-lookup"><span data-stu-id="85177-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="85177-106">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="85177-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="85177-107">Adicione a chave de assinatura do pacote da Microsoft à lista de chaves confiáveis.</span><span class="sxs-lookup"><span data-stu-id="85177-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="85177-108">Adicione o repositório ao gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="85177-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="85177-109">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="85177-109">Install required dependencies.</span></span>

<span data-ttu-id="85177-110">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="85177-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="85177-111">Abra um terminal e execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="85177-111">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="85177-112">Instale o .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="85177-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="85177-113">Atualize os produtos disponíveis para instalação e instale o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="85177-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="85177-114">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="85177-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="85177-115">Instale o tempo de execução do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="85177-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="85177-116">Atualize os produtos disponíveis para instalação e instale o ASP.NET tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="85177-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="85177-117">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="85177-117">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="85177-118">Instale o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="85177-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="85177-119">Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85177-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="85177-120">Em seu terminal, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="85177-120">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="85177-121">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="85177-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="85177-122">Solucionar problemas do gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="85177-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="85177-123">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85177-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="85177-124">Falhou em buscar</span><span class="sxs-lookup"><span data-stu-id="85177-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
