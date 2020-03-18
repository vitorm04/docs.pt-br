---
title: Instale o .NET Core no gerenciador de pacotes Linux RHEL 7 - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 4f85ed3da8a434fcd5b6ee88491daf623c3c8b31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76980178"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="1854e-103">Gerenciador de pacotes RHEL 7 - Instalar .NET Core</span><span class="sxs-lookup"><span data-stu-id="1854e-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="1854e-104">Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="1854e-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="1854e-105">Registre sua assinatura do Red Hat</span><span class="sxs-lookup"><span data-stu-id="1854e-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="1854e-106">Para instalar o .NET Core do Red Hat no RHEL, primeiro você precisa se registrar usando o Red Hat Subscription Manager.</span><span class="sxs-lookup"><span data-stu-id="1854e-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="1854e-107">Se isso não foi feito em seu sistema, ou se você não tem certeza, consulte a [Documentação do Produto Red Hat para .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="1854e-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="1854e-108">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="1854e-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="1854e-109">Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="1854e-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="1854e-110">Em seu terminal, execute os seguintes comandos para ativar o canal rhel 7 dotnet e instalar.</span><span class="sxs-lookup"><span data-stu-id="1854e-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="1854e-111">Instale o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="1854e-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="1854e-112">Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o ASP.NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="1854e-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="1854e-113">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="1854e-113">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="1854e-114">Instale o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="1854e-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="1854e-115">Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o .NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="1854e-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="1854e-116">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="1854e-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a><span data-ttu-id="1854e-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="1854e-117">See also</span></span>

- [<span data-ttu-id="1854e-118">Usando o .NET Core 3.1 no Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="1854e-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
