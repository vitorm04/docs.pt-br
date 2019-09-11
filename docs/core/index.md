---
title: Guia do .NET Core
description: O .NET core é uma implementação modular de alto desempenho do .NET para a criação de aplicativos do Windows, Linux e Mac. Saiba mais sobre o .NET Core para começar.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 0007c1c6a9939c46f123535f9053ac1d4ced7266
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848938"
---
# <a name="net-core-guide"></a><span data-ttu-id="68ec5-104">Guia do .NET Core</span><span class="sxs-lookup"><span data-stu-id="68ec5-104">.NET Core Guide</span></span>

<span data-ttu-id="68ec5-105">O [.NET Core](about.md) é uma plataforma de desenvolvimento [de código aberto](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) de uso geral mantida pela Microsoft e pela comunidade .NET no [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="68ec5-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="68ec5-106">É uma plataforma cruzada (compatível com Windows, macOS e Linux) que pode ser usada no desenvolvimento de dispositivos, na nuvem e em aplicativos de IoT.</span><span class="sxs-lookup"><span data-stu-id="68ec5-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="68ec5-107">Consulte [Sobre o .NET Core](about.md) para saber mais sobre o .NET Core, incluindo suas características, idiomas compatíveis, estruturas e APIs essenciais.</span><span class="sxs-lookup"><span data-stu-id="68ec5-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="68ec5-108">Consulte os [Tutoriais do .NET Core](tutorials/index.md) para aprender a criar um aplicativo .NET Core simples.</span><span class="sxs-lookup"><span data-stu-id="68ec5-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="68ec5-109">Bastam apenas alguns minutos para colocar seu primeiro aplicativo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="68ec5-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="68ec5-110">Consulte o tutorial online [Números em C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) caso deseje experimentar o .NET Core no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="68ec5-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core-22"></a><span data-ttu-id="68ec5-111">Baixe o .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="68ec5-111">Download .NET Core 2.2</span></span>

<span data-ttu-id="68ec5-112">Baixe o [SDK do .NET Core 2.2](https://dotnet.microsoft.com/download) para experimentar o .NET Core em seu computador Windows, macOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="68ec5-112">Download the [.NET Core  2.2 SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="68ec5-113">Acesse [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) se preferir usar contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="68ec5-113">Visit [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="68ec5-114">Todas as versões do .NET Core estão disponíveis em [Downloads do .NET Core](https://dotnet.microsoft.com/download/dotnet-core) se você estiver procurando por outra versão.</span><span class="sxs-lookup"><span data-stu-id="68ec5-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-22"></a><span data-ttu-id="68ec5-115">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="68ec5-115">.NET Core 2.2</span></span>

<span data-ttu-id="68ec5-116">O [.NET Core 2.2](whats-new/dotnet-core-2-2.md) é a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="68ec5-116">The latest version is [.NET Core 2.2](whats-new/dotnet-core-2-2.md).</span></span> <span data-ttu-id="68ec5-117">Os novos recursos incluem: implantações dependentes de estrutura, ganchos de inicialização, autenticação do AAD com o Azure SQL e suporte para Windows para ARM32.</span><span class="sxs-lookup"><span data-stu-id="68ec5-117">New features include: framework-dependent deployments, startup hooks, AAD authentication with Azure SQL, and support for Windows ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="68ec5-118">Criar seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="68ec5-118">Create your first application</span></span>

<span data-ttu-id="68ec5-119">Após instalar o SDK do .NET Core, abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="68ec5-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="68ec5-120">Digite os seguintes comandos `dotnet` para criar e executar um aplicativo C#.</span><span class="sxs-lookup"><span data-stu-id="68ec5-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="68ec5-121">Você deverá ver a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="68ec5-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="68ec5-122">Suporte</span><span class="sxs-lookup"><span data-stu-id="68ec5-122">Support</span></span>

<span data-ttu-id="68ec5-123">A [Microsoft disponibiliza](https://dotnet.microsoft.com/platform/support/policy) o .NET Core para Windows, no macOS e no Linux.</span><span class="sxs-lookup"><span data-stu-id="68ec5-123">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="68ec5-124">Ele é atualizado para segurança e qualidade várias vezes ao ano, normalmente mensalmente.</span><span class="sxs-lookup"><span data-stu-id="68ec5-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="68ec5-125">As distribuições de binários do .NET Core são criadas e testadas em servidores mantidos pela Microsoft no Azure e têm suporte como qualquer produto da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="68ec5-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="68ec5-126">A [Red Hat oferece suporte ao .NET Core](http://redhatloves.net/) no Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="68ec5-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="68ec5-127">A Red Hat compila o .NET Core da origem e o disponibiliza nas [Coleções de Software do Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="68ec5-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="68ec5-128">Red Hat e Microsoft colaboram para garantir que o .NET Core funcione bem no RHEL.</span><span class="sxs-lookup"><span data-stu-id="68ec5-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
