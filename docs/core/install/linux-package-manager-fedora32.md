---
title: Instalar o .NET Core no Fedora 32-Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no Fedora 32.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624962"
---
# <a name="fedora-32-package-manager---install-net-core"></a><span data-ttu-id="0e9d0-103">Gerenciador de pacotes do Fedora 32 – instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="0e9d0-103">Fedora 32 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="0e9d0-104">Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="0e9d0-104">This article describes how to use a package manager to install .NET Core on Fedora 32.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

<span data-ttu-id="0e9d0-105">A partir do Fedora 32, o .NET Core 3,1 está disponível nos repositórios de pacote padrão no Fedora.</span><span class="sxs-lookup"><span data-stu-id="0e9d0-105">Starting with Fedora 32, .NET Core 3.1 is available in the default package repositories in Fedora.</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="0e9d0-106">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0e9d0-106">Install the .NET Core SDK</span></span>

<span data-ttu-id="0e9d0-107">Instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0e9d0-107">Install the .NET Core SDK.</span></span> <span data-ttu-id="0e9d0-108">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="0e9d0-108">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="0e9d0-109">Instalar o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="0e9d0-109">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="0e9d0-110">Instale o tempo de execução do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0e9d0-110">Install the ASP.NET runtime.</span></span> <span data-ttu-id="0e9d0-111">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="0e9d0-111">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="0e9d0-112">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0e9d0-112">Install the .NET Core runtime</span></span>

<span data-ttu-id="0e9d0-113">Instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0e9d0-113">Install the .NET Core runtime.</span></span> <span data-ttu-id="0e9d0-114">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="0e9d0-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="0e9d0-115">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="0e9d0-115">How to install other versions</span></span>

<span data-ttu-id="0e9d0-116">Para instalar outras versões do .NET Core, instale manualmente [o SDK do .NET Core](sdk.md?pivots=os-linux#download-and-manually-install) ou [o tempo de execução do .NET Core](runtime.md?pivots=os-linux#download-and-manually-install).</span><span class="sxs-lookup"><span data-stu-id="0e9d0-116">To install other versions of .NET Core, manually install [the .NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) or [the .NET Core Runtime](runtime.md?pivots=os-linux#download-and-manually-install).</span></span>
