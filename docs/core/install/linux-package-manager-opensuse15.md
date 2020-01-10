---
title: Instalar o .NET Core no openSUSE 15-Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no openSUSE 15.
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: cba07bafc32cc71a1cdaec08902284e105af4776
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740677"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="4fa46-103">Gerenciador de pacotes do openSUSE 15 – instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="4fa46-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="4fa46-104">Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="4fa46-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span> <span data-ttu-id="4fa46-105">Se você estiver instalando o tempo de execução, sugerimos que instale o [ASP.NET Core Runtime](#install-the-aspnet-core-runtime), pois ele inclui o .NET Core e ASP.NET Core Runtimes.</span><span class="sxs-lookup"><span data-stu-id="4fa46-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="4fa46-106">Registrar a chave e o feed da Microsoft</span><span class="sxs-lookup"><span data-stu-id="4fa46-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="4fa46-107">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="4fa46-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="4fa46-108">Registre a chave da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4fa46-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="4fa46-109">Registre o repositório do produto.</span><span class="sxs-lookup"><span data-stu-id="4fa46-109">Register the product repository.</span></span>
- <span data-ttu-id="4fa46-110">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="4fa46-110">Install required dependencies.</span></span>

<span data-ttu-id="4fa46-111">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="4fa46-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="4fa46-112">Abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="4fa46-112">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="dependency-error-with-net-core-31"></a><span data-ttu-id="4fa46-113">Erro de dependência com o .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="4fa46-113">Dependency error with .NET Core 3.1</span></span>

<span data-ttu-id="4fa46-114">O feed de pacote do .NET Core 3,1 para openSUSE tem um problema com a dependência **krb5** .</span><span class="sxs-lookup"><span data-stu-id="4fa46-114">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="4fa46-115">Use o comando a seguir para instalar as dependências corretas antes de instalar o .NET Core 3,1 ou o ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4fa46-115">Use the following command to install the correct dependencies prior to installing .NET Core 3.1 or ASP.NET Core 3.1.</span></span>

```bash
sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="4fa46-116">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4fa46-116">Install the .NET Core SDK</span></span>

<span data-ttu-id="4fa46-117">Atualize os produtos disponíveis para instalação e, em seguida, instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fa46-117">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="4fa46-118">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="4fa46-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="4fa46-119">O feed de pacote do .NET Core 3,1 para openSUSE tem um problema com a dependência **krb5** .</span><span class="sxs-lookup"><span data-stu-id="4fa46-119">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="4fa46-120">Use o comando a seguir para instalar as dependências corretas e, em seguida, instale o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4fa46-120">Use the following command to install the correct dependencies, then install the .NET Core 3.1 SDK.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="4fa46-121">Instalar o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="4fa46-121">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="4fa46-122">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4fa46-122">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="4fa46-123">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="4fa46-123">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="4fa46-124">O feed de pacote do .NET Core 3,1 para openSUSE tem um problema com a dependência **krb5** .</span><span class="sxs-lookup"><span data-stu-id="4fa46-124">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="4fa46-125">Use o comando a seguir para instalar as dependências corretas e, em seguida, instale o tempo de execução do ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4fa46-125">Use the following command to install the correct dependencies, then install the ASP.NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="4fa46-126">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4fa46-126">Install the .NET Core runtime</span></span>

<span data-ttu-id="4fa46-127">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fa46-127">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="4fa46-128">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="4fa46-128">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="4fa46-129">O feed de pacote do .NET Core 3,1 para openSUSE tem um problema com a dependência **krb5** .</span><span class="sxs-lookup"><span data-stu-id="4fa46-129">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="4fa46-130">Use o comando a seguir para instalar as dependências corretas e, em seguida, instale o tempo de execução do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4fa46-130">Use the following command to install the correct dependencies, then install the .NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="4fa46-131">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="4fa46-131">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
