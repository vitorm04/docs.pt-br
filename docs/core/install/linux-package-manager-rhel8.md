---
title: Instalar o .NET Core no Linux RHEL 8 Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: 8829e842e920e6abd4184b5140f80bb016acace2
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728236"
---
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="ccf45-103">Gerenciador de pacotes RHEL 8 – instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="ccf45-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="ccf45-104">Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core em Red Hat Enterprise Linux (RHEL) 8.</span><span class="sxs-lookup"><span data-stu-id="ccf45-104">This article describes how to use a package manager to install .NET Core on Red Hat Enterprise Linux (RHEL) 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="ccf45-105">Registrar sua assinatura do Red Hat</span><span class="sxs-lookup"><span data-stu-id="ccf45-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="ccf45-106">Para instalar o .NET Core do Red Hat no RHEL, primeiro você precisa se registrar usando o Gerenciador de assinaturas do Red Hat.</span><span class="sxs-lookup"><span data-stu-id="ccf45-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="ccf45-107">Se isso não tiver sido feito em seu sistema ou se você não tiver certeza, consulte a [documentação do produto Red Hat para .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="ccf45-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="ccf45-108">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ccf45-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="ccf45-109">Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ccf45-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="ccf45-110">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="ccf45-110">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="ccf45-111">Instalar o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="ccf45-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="ccf45-112">Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o tempo de execução de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ccf45-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="ccf45-113">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="ccf45-113">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="ccf45-114">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ccf45-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="ccf45-115">Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ccf45-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="ccf45-116">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="ccf45-116">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ccf45-117">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="ccf45-117">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="see-also"></a><span data-ttu-id="ccf45-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="ccf45-118">See also</span></span>

- [<span data-ttu-id="ccf45-119">Usando o .NET Core 3,1 no Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="ccf45-119">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
