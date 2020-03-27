---
title: .NET Core introdução e visão geral
description: .NET Core é uma implementação modular e de alto desempenho do .NET para criar aplicativos Windows, Linux e macOS. Saiba mais sobre o .NET Core para começar.
author: richlander
ms.date: 03/25/2020
ms.custom: updateeachrelease
ms.openlocfilehash: edd3864d3c3c5c0e9fd8c26ee806ffc9e100423d
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80351697"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="e3389-104">Introdução ao .NET Core</span><span class="sxs-lookup"><span data-stu-id="e3389-104">Introduction to .NET Core</span></span>

<span data-ttu-id="e3389-105">O [.NET Core](about.md) é uma plataforma de desenvolvimento [de código aberto](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT) de uso geral mantida pela Microsoft e pela comunidade .NET no [GitHub](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="e3389-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="e3389-106">É uma plataforma cruzada (compatível com Windows, macOS e Linux) que pode ser usada no desenvolvimento de dispositivos, na nuvem e em aplicativos de IoT.</span><span class="sxs-lookup"><span data-stu-id="e3389-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="e3389-107">Baixe o .NET Core</span><span class="sxs-lookup"><span data-stu-id="e3389-107">Download .NET Core</span></span>

<span data-ttu-id="e3389-108">Baixe o [.NET Core SDK](https://dotnet.microsoft.com/download) para experimentar o .NET Core em sua máquina Windows, macOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="e3389-108">Download the [.NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="e3389-109">Se preferir usar contêineres Docker, visite o [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="e3389-109">If you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

## <a name="net-core-31"></a><span data-ttu-id="e3389-110">.NET Núcleo 3.1</span><span class="sxs-lookup"><span data-stu-id="e3389-110">.NET Core 3.1</span></span>

<span data-ttu-id="e3389-111">A versão mais recente é .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="e3389-111">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="e3389-112">3.1 inclui pequenas melhorias sobre o .NET Core 3.0, no entanto, .NET Core 3.1 é uma [versão suportada a longo prazo](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="e3389-112">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="e3389-113">Para obter mais informações sobre a versão .NET Core 3.1, consulte [as novidades do .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="e3389-113">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

<span data-ttu-id="e3389-114">Se você está procurando por outra versão do .NET Core, todas as versões estão disponíveis em [downloads .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="e3389-114">If you're looking for another version of .NET Core, all the versions are available at [.NET Core downloads](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="e3389-115">Criar seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="e3389-115">Create your first application</span></span>

<span data-ttu-id="e3389-116">Após instalar o SDK do .NET Core, abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e3389-116">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="e3389-117">Digite `dotnet` os seguintes comandos para criar e executar um aplicativo C#:</span><span class="sxs-lookup"><span data-stu-id="e3389-117">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="e3389-118">Você deve ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="e3389-118">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="e3389-119">Suporte</span><span class="sxs-lookup"><span data-stu-id="e3389-119">Support</span></span>

<span data-ttu-id="e3389-120">O .NET Core é [suportado pela Microsoft](https://dotnet.microsoft.com/platform/support/policy) no Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="e3389-120">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy) on Windows, macOS, and Linux.</span></span> <span data-ttu-id="e3389-121">Ele é atualizado para segurança e qualidade várias vezes ao ano, normalmente mensalmente.</span><span class="sxs-lookup"><span data-stu-id="e3389-121">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="e3389-122">As distribuições de binários do .NET Core são criadas e testadas em servidores mantidos pela Microsoft no Azure e têm suporte como qualquer produto da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e3389-122">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="e3389-123">A [Red Hat oferece suporte ao .NET Core](http://redhatloves.net/) no Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="e3389-123">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="e3389-124">A Red Hat compila o .NET Core da origem e o disponibiliza nas [Coleções de Software do Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="e3389-124">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="e3389-125">Red Hat e Microsoft colaboram para garantir que o .NET Core funcione bem no RHEL.</span><span class="sxs-lookup"><span data-stu-id="e3389-125">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e3389-126">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e3389-126">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e3389-127">Tutoriais do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e3389-127">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="e3389-128">Experimente o .NET Core no seu navegador</span><span class="sxs-lookup"><span data-stu-id="e3389-128">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
