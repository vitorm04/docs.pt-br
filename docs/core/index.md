---
title: Guia do .NET Core
description: O .NET core é uma implementação modular de alto desempenho do .NET para a criação de aplicativos do Windows, Linux e Mac. Saiba mais sobre o .NET Core para começar.
author: richlander
ms.author: mairaw
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: b302b6fc7e097a811c718d2244f603246cb5c259
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121032"
---
# <a name="net-core-guide"></a><span data-ttu-id="231f0-104">Guia do .NET Core</span><span class="sxs-lookup"><span data-stu-id="231f0-104">.NET Core Guide</span></span>

<span data-ttu-id="231f0-105">O [.NET Core](about.md) é uma plataforma de desenvolvimento [aberta](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) de uso geral mantida pela Microsoft e pela comunidade .NET no [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="231f0-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="231f0-106">Ele é multiplataforma e oferece suporte a Windows, macOS e Linux, e pode ser usado em dispositivos, na nuvem e em aplicativos de IoT.</span><span class="sxs-lookup"><span data-stu-id="231f0-106">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and IoT applications.</span></span>

<span data-ttu-id="231f0-107">Consulte [Sobre o .NET Core](about.md) para saber mais sobre o .NET Core, incluindo suas características, idiomas compatíveis, estruturas e APIs essenciais.</span><span class="sxs-lookup"><span data-stu-id="231f0-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="231f0-108">Consulte os [Tutoriais do .NET Core](tutorials/index.md) para aprender a criar um aplicativo .NET Core simples.</span><span class="sxs-lookup"><span data-stu-id="231f0-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="231f0-109">Bastam apenas alguns minutos para colocar seu primeiro aplicativo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="231f0-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="231f0-110">Se quiser experimentar o .NET Core no seu navegador, consulte [Números em C#](https://docs.microsoft.com/dotnet/csharp/quick-starts/numbers-in-csharp) no guia de início rápido.</span><span class="sxs-lookup"><span data-stu-id="231f0-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](https://docs.microsoft.com/dotnet/csharp/quick-starts/numbers-in-csharp) quickstart.</span></span>

## <a name="download-net-core-21"></a><span data-ttu-id="231f0-111">Faça o download do .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="231f0-111">Download .NET Core 2.1</span></span>

<span data-ttu-id="231f0-112">Faça o download do [SDK do .NET Core 2.1](https://www.microsoft.com/net/download) para experimentar o .NET Core em seu computador Windows, macOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="231f0-112">Download the [.NET Core  2.1 SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="231f0-113">Visite [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) se preferir usar contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="231f0-113">Visit [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="231f0-114">Todas as versões do .NET Core estão disponíveis em [Downloads do .NET Core](https://www.microsoft.com/net/download/archives) se você estiver procurando por outra versão.</span><span class="sxs-lookup"><span data-stu-id="231f0-114">All .NET Core versions are available at [.NET Core Downloads](https://www.microsoft.com/net/download/archives) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="231f0-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="231f0-115">.NET Core 2.1</span></span>

<span data-ttu-id="231f0-116">O [.NET Core 2.1](whats-new/dotnet-core-2-1.md) é a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="231f0-116">The latest version is [.NET Core 2.1](whats-new/dotnet-core-2-1.md).</span></span> <span data-ttu-id="231f0-117">Os novos recursos incluem: ferramentas globais, APIs de alto desempenho (como <xref:System.Span%601?displayProperty=nameWithType>), compilação JIT em camadas, [build](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) e [melhorias de desempenho no tempo de execução](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/), e suporte para Alpine e ARM32.</span><span class="sxs-lookup"><span data-stu-id="231f0-117">New features include: global tools, high-performance APIs (such as <xref:System.Span%601?displayProperty=nameWithType>), tiered JIT compilation, [build](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) and [runtime performance improvements](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/), and support for Alpine and ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="231f0-118">Criar seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="231f0-118">Create your first application</span></span>

<span data-ttu-id="231f0-119">Após instalar o SDK do .NET Core, abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="231f0-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="231f0-120">Digite os seguintes comandos `dotnet` para criar e executar um aplicativo C#.</span><span class="sxs-lookup"><span data-stu-id="231f0-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="231f0-121">Você deverá ver a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="231f0-121">You should see the following output:</span></span>

```console
Hello World!
```

## <a name="support"></a><span data-ttu-id="231f0-122">Suporte</span><span class="sxs-lookup"><span data-stu-id="231f0-122">Support</span></span>

<span data-ttu-id="231f0-123">A [Microsoft disponibiliza](https://www.microsoft.com/net/support/policy) o .NET Core para Windows, no macOS e no Linux.</span><span class="sxs-lookup"><span data-stu-id="231f0-123">.NET Core is [supported by Microsoft](https://www.microsoft.com/net/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="231f0-124">Ele é atualizado para segurança e qualidade várias vezes ao ano, normalmente mensalmente.</span><span class="sxs-lookup"><span data-stu-id="231f0-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="231f0-125">As distribuições de binários do .NET Core são criadas e testadas em servidores mantidos pela Microsoft no Azure e têm suporte como qualquer produto da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="231f0-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="231f0-126">A [Red Hat oferece suporte ao .NET Core](http://redhatloves.net/) no Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="231f0-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="231f0-127">A Red Hat compila o .NET Core da origem e o disponibiliza nas [Coleções de Software do Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="231f0-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="231f0-128">Red Hat e Microsoft colaboram para garantir que o .NET Core funcione bem no RHEL.</span><span class="sxs-lookup"><span data-stu-id="231f0-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
