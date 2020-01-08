---
title: Guia do .NET Core
description: O .NET Core é uma implementação modular de alto desempenho do .NET para a criação de aplicativos para Windows, Linux e macOS. Saiba mais sobre o .NET Core para começar.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 80a3b12972e24c3022ac2aa14406aa60635815a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341361"
---
# <a name="net-core-guide"></a><span data-ttu-id="fc3ec-104">Guia do .NET Core</span><span class="sxs-lookup"><span data-stu-id="fc3ec-104">.NET Core Guide</span></span>

<span data-ttu-id="fc3ec-105">O [.NET Core](about.md) é uma plataforma de desenvolvimento [de código aberto](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) de uso geral mantida pela Microsoft e pela comunidade .NET no [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="fc3ec-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="fc3ec-106">É uma plataforma cruzada (compatível com Windows, macOS e Linux) que pode ser usada no desenvolvimento de dispositivos, na nuvem e em aplicativos de IoT.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="fc3ec-107">Consulte [Sobre o .NET Core](about.md) para saber mais sobre o .NET Core, incluindo suas características, idiomas compatíveis, estruturas e APIs essenciais.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="fc3ec-108">Consulte os [Tutoriais do .NET Core](tutorials/index.md) para aprender a criar um aplicativo .NET Core simples.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="fc3ec-109">Bastam apenas alguns minutos para colocar seu primeiro aplicativo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="fc3ec-110">Consulte o tutorial online [Números em C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) caso deseje experimentar o .NET Core no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="fc3ec-111">Baixe o .NET Core</span><span class="sxs-lookup"><span data-stu-id="fc3ec-111">Download .NET Core</span></span>

<span data-ttu-id="fc3ec-112">Baixe o [SDK do .NET Core](https://www.microsoft.com/net/download) para experimentar o .NET Core em seu computador com Windows, MacOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="fc3ec-113">E se preferir usar contêineres do Docker, visite o [Hub do Docker do .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="fc3ec-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="fc3ec-114">Todas as versões do .NET Core estão disponíveis em [Downloads do .NET Core](https://dotnet.microsoft.com/download/dotnet-core) se você estiver procurando por outra versão.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="fc3ec-115">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="fc3ec-115">.NET Core 3.1</span></span>

<span data-ttu-id="fc3ec-116">A versão mais recente é o .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="fc3ec-117">3,1 inclui pequenas melhorias no .NET Core 3,0, no entanto, o .NET Core 3,1 é uma [versão com suporte a longo prazo](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="fc3ec-117">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="fc3ec-118">Para obter mais informações sobre a versão 3,1 do .NET Core, consulte [o que há de novo no .net core 3,1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="fc3ec-118">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="fc3ec-119">Criar seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="fc3ec-119">Create your first application</span></span>

<span data-ttu-id="fc3ec-120">Após instalar o SDK do .NET Core, abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="fc3ec-121">Insira os seguintes comandos de `dotnet` para criar e executar C# um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="fc3ec-121">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="fc3ec-122">Você deverá ver a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="fc3ec-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="fc3ec-123">Suporte do</span><span class="sxs-lookup"><span data-stu-id="fc3ec-123">Support</span></span>

<span data-ttu-id="fc3ec-124">O .NET Core tem [suporte da Microsoft](https://dotnet.microsoft.com/platform/support/policy), no Windows, no MacOS e no Linux.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="fc3ec-125">Ele é atualizado para segurança e qualidade várias vezes ao ano, normalmente mensalmente.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="fc3ec-126">As distribuições de binários do .NET Core são criadas e testadas em servidores mantidos pela Microsoft no Azure e têm suporte como qualquer produto da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="fc3ec-127">A [Red Hat oferece suporte ao .NET Core](http://redhatloves.net/) no Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="fc3ec-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="fc3ec-128">A Red Hat compila o .NET Core da origem e o disponibiliza nas [Coleções de Software do Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="fc3ec-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="fc3ec-129">Red Hat e Microsoft colaboram para garantir que o .NET Core funcione bem no RHEL.</span><span class="sxs-lookup"><span data-stu-id="fc3ec-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
