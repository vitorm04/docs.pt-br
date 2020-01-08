---
title: Instalar o .NET Core no Linux RHEL 8,1 Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no RHEL 8,1.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 8674b5d9d0f0ee384ca6798a7ea699bad67c5e5e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341175"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="4b1e2-103">Gerenciador de pacotes RHEL 8,1 – instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b1e2-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="4b1e2-104">Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="4b1e2-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span> <span data-ttu-id="4b1e2-105">O .NET Core 3,1 ainda não está disponível para o RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="4b1e2-105">.NET Core 3.1 is not yet available for RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="4b1e2-106">O RHEL 8,0 não inclui o .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="4b1e2-106">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="4b1e2-107">Use o comando `yum upgrade` para atualizar para RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="4b1e2-107">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="4b1e2-108">Registrar sua assinatura do Red Hat</span><span class="sxs-lookup"><span data-stu-id="4b1e2-108">Register your Red Hat subscription</span></span>

<span data-ttu-id="4b1e2-109">Para instalar o .NET Core do Red Hat no RHEL, primeiro você precisa se registrar usando o Gerenciador de assinaturas do Red Hat.</span><span class="sxs-lookup"><span data-stu-id="4b1e2-109">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="4b1e2-110">Se isso não tiver sido feito em seu sistema ou se você não tiver certeza, consulte a [documentação do produto Red Hat para .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="4b1e2-110">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="4b1e2-111">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b1e2-111">Install the .NET Core SDK</span></span>

<span data-ttu-id="4b1e2-112">Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b1e2-112">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="4b1e2-113">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="4b1e2-113">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="4b1e2-114">Instalar o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="4b1e2-114">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="4b1e2-115">Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o tempo de execução de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b1e2-115">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="4b1e2-116">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="4b1e2-116">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="4b1e2-117">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b1e2-117">Install the .NET Core Runtime</span></span>

<span data-ttu-id="4b1e2-118">Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b1e2-118">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="4b1e2-119">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="4b1e2-119">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a><span data-ttu-id="4b1e2-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="4b1e2-120">See also</span></span>

- [<span data-ttu-id="4b1e2-121">Usando o .NET Core 3,0 no Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="4b1e2-121">Using .NET Core 3.0 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
