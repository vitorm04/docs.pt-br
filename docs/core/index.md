---
title: Guia do .NET Core
description: O .NET core é uma implementação modular de alto desempenho do .NET para a criação de aplicativos do Windows, Linux e Mac. Saiba mais sobre o .NET Core para começar.
author: richlander
ms.date: 09/23/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 95f18ca09852ce139a4b99ed7aef4802d4883e13
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216211"
---
# <a name="net-core-guide"></a><span data-ttu-id="204de-104">Guia do .NET Core</span><span class="sxs-lookup"><span data-stu-id="204de-104">.NET Core Guide</span></span>

<span data-ttu-id="204de-105">O [.NET Core](about.md) é uma plataforma de desenvolvimento [de código aberto](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) de uso geral mantida pela Microsoft e pela comunidade .NET no [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="204de-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="204de-106">É uma plataforma cruzada (compatível com Windows, macOS e Linux) que pode ser usada no desenvolvimento de dispositivos, na nuvem e em aplicativos de IoT.</span><span class="sxs-lookup"><span data-stu-id="204de-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="204de-107">Consulte [Sobre o .NET Core](about.md) para saber mais sobre o .NET Core, incluindo suas características, idiomas compatíveis, estruturas e APIs essenciais.</span><span class="sxs-lookup"><span data-stu-id="204de-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="204de-108">Consulte os [Tutoriais do .NET Core](tutorials/index.md) para aprender a criar um aplicativo .NET Core simples.</span><span class="sxs-lookup"><span data-stu-id="204de-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="204de-109">Bastam apenas alguns minutos para colocar seu primeiro aplicativo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="204de-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="204de-110">Consulte o tutorial online [Números em C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) caso deseje experimentar o .NET Core no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="204de-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="204de-111">Baixe o .NET Core</span><span class="sxs-lookup"><span data-stu-id="204de-111">Download .NET Core</span></span>

<span data-ttu-id="204de-112">Baixe o [SDK do .NET Core](https://www.microsoft.com/net/download) para experimentar o .NET Core em seu computador com Windows, MacOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="204de-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="204de-113">E se preferir usar contêineres do Docker, visite o [Hub do Docker do .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="204de-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="204de-114">Todas as versões do .NET Core estão disponíveis em [Downloads do .NET Core](https://dotnet.microsoft.com/download/dotnet-core) se você estiver procurando por outra versão.</span><span class="sxs-lookup"><span data-stu-id="204de-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-30"></a><span data-ttu-id="204de-115">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="204de-115">.NET Core 3.0</span></span>

<span data-ttu-id="204de-116">A versão mais recente é o .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="204de-116">The latest version is .NET Core 3.0.</span></span> <span data-ttu-id="204de-117">Os novos recursos incluem o suporte à área de trabalho do Windows com o Windows Presentation Foundation ( C# WPF) e o Windows Forms, o desenvolvimento da Web de pilha completo com mais de um novo C# C# e muito mais.</span><span class="sxs-lookup"><span data-stu-id="204de-117">New features include Windows Desktop support with Windows Presentation Foundation (WPF) and Windows Forms, full stack C# web development with Blazor, new enhancements to SignalR and Azure SignalR Service, new C# language features with C# 8, and much more.</span></span> <span data-ttu-id="204de-118">Para obter uma lista completa dos novos recursos do .NET Core 3,0, consulte [novidades do .net core 3,0](./whats-new/dotnet-core-3-0.md).</span><span class="sxs-lookup"><span data-stu-id="204de-118">For a full listing of the new features in .NET Core 3.0, see [What's new in .NET Core 3.0](./whats-new/dotnet-core-3-0.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="204de-119">Criar seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="204de-119">Create your first application</span></span>

<span data-ttu-id="204de-120">Após instalar o SDK do .NET Core, abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="204de-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="204de-121">Digite os seguintes `dotnet` comandos para criar e executar um C# aplicativo:</span><span class="sxs-lookup"><span data-stu-id="204de-121">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="204de-122">Você deverá ver a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="204de-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="204de-123">Suporte</span><span class="sxs-lookup"><span data-stu-id="204de-123">Support</span></span>

<span data-ttu-id="204de-124">O .NET Core tem [suporte da Microsoft](https://dotnet.microsoft.com/platform/support/policy), no Windows, no MacOS e no Linux.</span><span class="sxs-lookup"><span data-stu-id="204de-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="204de-125">Ele é atualizado para segurança e qualidade várias vezes ao ano, normalmente mensalmente.</span><span class="sxs-lookup"><span data-stu-id="204de-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="204de-126">As distribuições de binários do .NET Core são criadas e testadas em servidores mantidos pela Microsoft no Azure e têm suporte como qualquer produto da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="204de-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="204de-127">A [Red Hat oferece suporte ao .NET Core](http://redhatloves.net/) no Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="204de-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="204de-128">A Red Hat compila o .NET Core da origem e o disponibiliza nas [Coleções de Software do Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="204de-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="204de-129">Red Hat e Microsoft colaboram para garantir que o .NET Core funcione bem no RHEL.</span><span class="sxs-lookup"><span data-stu-id="204de-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
