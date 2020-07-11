---
title: Visão geral e introdução ao .NET Core
description: O .NET Core é uma implementação modular de alto desempenho do .NET para a criação de aplicativos para Windows, Linux e macOS. Saiba mais sobre o .NET Core para começar.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: b28ad965e54680e2e1134c389266741ade28084f
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226576"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="e1fd0-104">Introdução ao .NET Core</span><span class="sxs-lookup"><span data-stu-id="e1fd0-104">Introduction to .NET Core</span></span>

<span data-ttu-id="e1fd0-105">O [.NET Core](about.md) é uma plataforma de desenvolvimento de software livre [, de uso](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)geral.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="e1fd0-106">Você pode criar aplicativos .NET Core para Windows, macOS e Linux para processadores x64, x86, ARM32 e ARM64 usando várias linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="e1fd0-107">Estruturas e APIs são fornecidas para a [nuvem](/aspnet/core/), a [IOT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), a [interface do usuário do cliente](../desktop-wpf/overview/index.md)e o [Machine Learning](/dotnet/machine-learning/).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](../desktop-wpf/overview/index.md), and [machine learning](/dotnet/machine-learning/).</span></span>

<span data-ttu-id="e1fd0-108">[Baixe o SDK do .NET Core](https://dotnet.microsoft.com/download) para experimentar o .NET Core em seu computador.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="e1fd0-109">A versão mais recente é o [.NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="e1fd0-110">Baixe o .NET Core</span><span class="sxs-lookup"><span data-stu-id="e1fd0-110">Download .NET Core</span></span>

<span data-ttu-id="e1fd0-111">Você pode obter o .NET Core das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="e1fd0-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="e1fd0-112">Instaladores para Windows e macOS</span><span class="sxs-lookup"><span data-stu-id="e1fd0-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="e1fd0-113">Pacotes do Linux</span><span class="sxs-lookup"><span data-stu-id="e1fd0-113">Linux packages</span></span>](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [<span data-ttu-id="e1fd0-114">Contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="e1fd0-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="e1fd0-115">Zips e tarballs</span><span class="sxs-lookup"><span data-stu-id="e1fd0-115">Zips and tarballs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="e1fd0-116">Scripts de instalação</span><span class="sxs-lookup"><span data-stu-id="e1fd0-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="e1fd0-117">Notas de versão</span><span class="sxs-lookup"><span data-stu-id="e1fd0-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="e1fd0-118">Criar seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="e1fd0-118">Create your first application</span></span>

<span data-ttu-id="e1fd0-119">Após instalar o SDK do .NET Core, abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="e1fd0-120">Use os comandos a seguir para criar e executar um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="e1fd0-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="e1fd0-121">A seguinte saída deve ser exibida:</span><span class="sxs-lookup"><span data-stu-id="e1fd0-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="e1fd0-122">Contribuir</span><span class="sxs-lookup"><span data-stu-id="e1fd0-122">Contribute</span></span>

<span data-ttu-id="e1fd0-123">O .NET Core é uma plataforma aberta.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-123">.NET Core is an open platform.</span></span> <span data-ttu-id="e1fd0-124">Todos são bem-vindos a participar.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="e1fd0-125">Arquivar questões e problemas do produto na [comunidade de desenvolvedores](https://developercommunity.visualstudio.com/spaces/61/index.html).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="e1fd0-126">As contribuições de produto devem ser feitas em um dos repositórios do projeto, como [dotnet/tempo de execução](https://github.com/dotnet/runtime), [dotnet/SDK](https://github.com/dotnet/sdk), [dotnet/Rosyln](https://github.com/dotnet/roslyn)ou [aspnetcore](https://github.com/dotnet/aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="e1fd0-127">Para obter mais informações, consulte [.NET Core repositórios](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span><span class="sxs-lookup"><span data-stu-id="e1fd0-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="e1fd0-128">Suporte</span><span class="sxs-lookup"><span data-stu-id="e1fd0-128">Support</span></span>

<span data-ttu-id="e1fd0-129">O .NET Core tem suporte da Microsoft no Windows, macOS e Linux e pelo Red Hat em Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="e1fd0-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e1fd0-130">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e1fd0-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e1fd0-131">Tutoriais do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e1fd0-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="e1fd0-132">Experimente o .NET Core em seu navegador</span><span class="sxs-lookup"><span data-stu-id="e1fd0-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
