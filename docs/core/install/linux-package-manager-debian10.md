---
title: Instalar o .NET Core no Debian 10-Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no Debian 10.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 038f5579f99f700ce47dc67be2fd344f01cf800c
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595601"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="a3bc8-103">Gerenciador de pacotes do Debian 10 – instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="a3bc8-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="a3bc8-104">Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no Debian 10.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="a3bc8-105">Adicionar chave e feed do repositório da Microsoft</span><span class="sxs-lookup"><span data-stu-id="a3bc8-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="a3bc8-106">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="a3bc8-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="a3bc8-107">Adicione a chave de assinatura do pacote da Microsoft à lista de chaves confiáveis.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="a3bc8-108">Adicione o repositório ao Gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="a3bc8-109">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-109">Install required dependencies.</span></span>

<span data-ttu-id="a3bc8-110">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="a3bc8-111">Abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="a3bc8-112">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="a3bc8-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="a3bc8-113">Atualize os produtos disponíveis para instalação e, em seguida, instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="a3bc8-114">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="a3bc8-115">Instalar o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="a3bc8-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="a3bc8-116">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="a3bc8-117">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="a3bc8-118">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="a3bc8-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="a3bc8-119">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="a3bc8-120">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="a3bc8-121">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="a3bc8-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="a3bc8-122">Solucionar problemas do Gerenciador de pacotes</span><span class="sxs-lookup"><span data-stu-id="a3bc8-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="a3bc8-123">Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a3bc8-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="a3bc8-124">Falha ao buscar</span><span class="sxs-lookup"><span data-stu-id="a3bc8-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
