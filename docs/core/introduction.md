---
title: .NET Core introdução e visão geral
description: .NET Core é uma implementação modular e de alto desempenho do .NET para criar aplicativos Windows, Linux e macOS. Saiba mais sobre o .NET Core para começar.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: a20cdda5cbd366d04e7ee9e8df3d1b15d10c1f4a
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391156"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="c99eb-104">Introdução ao .NET Core</span><span class="sxs-lookup"><span data-stu-id="c99eb-104">Introduction to .NET Core</span></span>

<span data-ttu-id="c99eb-105">[.NET Core](about.md) é uma plataforma de desenvolvimento [de código aberto](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)e de uso geral.</span><span class="sxs-lookup"><span data-stu-id="c99eb-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="c99eb-106">Você pode criar aplicativos .NET Core para Windows, macOS e Linux para processadores x64, x86, ARM32 e ARM64 usando várias linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="c99eb-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="c99eb-107">Estruturas e APIs são fornecidas para [nuvem,](/aspnet/core/) [IoT,](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0) [ui cliente](/dotnet/desktop-wpf/overview/index)e [machine learning](/dotnet/machine-learning/).</span><span class="sxs-lookup"><span data-stu-id="c99eb-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](/dotnet/desktop-wpf/overview/index), and [machine learning](/dotnet/machine-learning/).</span></span>

<span data-ttu-id="c99eb-108">[Baixe o .NET Core SDK](https://dotnet.microsoft.com/download) para experimentar o .NET Core na sua máquina.</span><span class="sxs-lookup"><span data-stu-id="c99eb-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="c99eb-109">A versão mais recente é [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="c99eb-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="c99eb-110">Baixe o .NET Core</span><span class="sxs-lookup"><span data-stu-id="c99eb-110">Download .NET Core</span></span>

<span data-ttu-id="c99eb-111">Você pode obter o .NET Core das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="c99eb-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="c99eb-112">Instaladores para Windows e macOS</span><span class="sxs-lookup"><span data-stu-id="c99eb-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="c99eb-113">Pacotes do Linux</span><span class="sxs-lookup"><span data-stu-id="c99eb-113">Linux packages</span></span>](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [<span data-ttu-id="c99eb-114">Contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="c99eb-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="c99eb-115">Zips e bolas de piche</span><span class="sxs-lookup"><span data-stu-id="c99eb-115">Zips and tar balls</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="c99eb-116">Instalar scripts</span><span class="sxs-lookup"><span data-stu-id="c99eb-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="c99eb-117">Notas de versão</span><span class="sxs-lookup"><span data-stu-id="c99eb-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="c99eb-118">Criar seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="c99eb-118">Create your first application</span></span>

<span data-ttu-id="c99eb-119">Após instalar o SDK do .NET Core, abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="c99eb-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="c99eb-120">Use os seguintes comandos para criar e executar um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="c99eb-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="c99eb-121">Você deve ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="c99eb-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="c99eb-122">Contribuir</span><span class="sxs-lookup"><span data-stu-id="c99eb-122">Contribute</span></span>

<span data-ttu-id="c99eb-123">.NET Core é uma plataforma aberta.</span><span class="sxs-lookup"><span data-stu-id="c99eb-123">.NET Core is an open platform.</span></span> <span data-ttu-id="c99eb-124">Todos podem participar.</span><span class="sxs-lookup"><span data-stu-id="c99eb-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="c99eb-125">Filie problemas e perguntas sobre produtos na [Comunidade de Desenvolvedores](https://developercommunity.visualstudio.com/spaces/61/index.html).</span><span class="sxs-lookup"><span data-stu-id="c99eb-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="c99eb-126">As contribuições dos produtos devem ser feitas em um dos repositórios do projeto, tais como [dotnet/runtime,](https://github.com/dotnet/runtime) [dotnet/sdk,](https://github.com/dotnet/sdk) [dotnet/rosyln](https://github.com/dotnet/roslyn)ou [aspnetcore](https://github.com/dotnet/aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="c99eb-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="c99eb-127">Para obter mais informações, consulte [os repos .NET Core](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span><span class="sxs-lookup"><span data-stu-id="c99eb-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="c99eb-128">Suporte</span><span class="sxs-lookup"><span data-stu-id="c99eb-128">Support</span></span>

<span data-ttu-id="c99eb-129">.NET Core é suportado pela Microsoft no Windows, macOS e Linux e pela Red Hat no Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="c99eb-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c99eb-130">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c99eb-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c99eb-131">Tutoriais do .NET Core</span><span class="sxs-lookup"><span data-stu-id="c99eb-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="c99eb-132">Experimente o .NET Core no seu navegador</span><span class="sxs-lookup"><span data-stu-id="c99eb-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
