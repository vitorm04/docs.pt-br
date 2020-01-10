---
title: Instalar o .NET Core no Linux RHEL 7 Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: bcc41bfcd7c6d03038952e3faaf07952c3deb69d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715530"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="43397-103">Gerenciador de pacotes RHEL 7-instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="43397-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="43397-104">Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="43397-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span> <span data-ttu-id="43397-105">O .NET Core 3,1 ainda não está disponível para o RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="43397-105">.NET Core 3.1 is not yet available for RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="43397-106">Registrar sua assinatura do Red Hat</span><span class="sxs-lookup"><span data-stu-id="43397-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="43397-107">Para instalar o .NET Core do Red Hat no RHEL, primeiro você precisa se registrar usando o Gerenciador de assinaturas do Red Hat.</span><span class="sxs-lookup"><span data-stu-id="43397-107">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="43397-108">Se isso não tiver sido feito em seu sistema ou se você não tiver certeza, consulte a [documentação do produto Red Hat para .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="43397-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="43397-109">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="43397-109">Install the .NET Core SDK</span></span>

<span data-ttu-id="43397-110">Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43397-110">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="43397-111">Em seu terminal, execute os seguintes comandos para habilitar o canal do RHEL 7 dotnet e instalar.</span><span class="sxs-lookup"><span data-stu-id="43397-111">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="43397-112">Instalar o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="43397-112">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="43397-113">Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o tempo de execução de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="43397-113">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="43397-114">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="43397-114">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="43397-115">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="43397-115">Install the .NET Core Runtime</span></span>

<span data-ttu-id="43397-116">Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43397-116">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="43397-117">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="43397-117">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a><span data-ttu-id="43397-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="43397-118">See also</span></span>

- [<span data-ttu-id="43397-119">Usando o .NET Core 3,0 no Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="43397-119">Using .NET Core 3.0 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)
