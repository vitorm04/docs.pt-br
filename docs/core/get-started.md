---
title: Introdução ao .NET Core
description: Encontre recursos para aprender a criar aplicativos .NET Core no Windows, Linux e macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bcf9ea0bb9a8346284c49060786afefa0f77745e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341383"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="dab03-103">Introdução ao .NET Core</span><span class="sxs-lookup"><span data-stu-id="dab03-103">Get started with .NET Core</span></span>

<span data-ttu-id="dab03-104">Este artigo fornece informações de como começar a usar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dab03-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="dab03-105">O .NET Core pode ser instalado no Windows, no Linux e no macOS.</span><span class="sxs-lookup"><span data-stu-id="dab03-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="dab03-106">Você pode codificar em seu editor de texto favorito e produzir aplicativos e bibliotecas multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="dab03-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="dab03-107">Se você não souber exatamente o que é o .NET Core ou como ele se relaciona com outras tecnologias do .NET, comece com a visão geral [O que é o .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet).</span><span class="sxs-lookup"><span data-stu-id="dab03-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="dab03-108">Resumindo, o .NET Core é uma implementação open-source e multiplataforma do .NET.</span><span class="sxs-lookup"><span data-stu-id="dab03-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="dab03-109">Criar um aplicativo</span><span class="sxs-lookup"><span data-stu-id="dab03-109">Create an application</span></span>

<span data-ttu-id="dab03-110">Primeiro, baixe e instale o [SDK do .NET Core](https://dotnet.microsoft.com/download) em seu computador.</span><span class="sxs-lookup"><span data-stu-id="dab03-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="dab03-111">Em seguida, abra um terminal, como o **PowerShell**, um **prompt de comando** ou o **Bash**.</span><span class="sxs-lookup"><span data-stu-id="dab03-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="dab03-112">Digite os seguintes comandos de `dotnet` para criar e executar um aplicativo C#:</span><span class="sxs-lookup"><span data-stu-id="dab03-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="dab03-113">Você deverá ver a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="dab03-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="dab03-114">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="dab03-114">Congratulations!</span></span> <span data-ttu-id="dab03-115">Você criou um aplicativo simples do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dab03-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="dab03-116">Também é possível usar o [Visual Studio Code](./tutorials/with-visual-studio-code.md), o [Visual Studio](./tutorials/with-visual-studio.md) (somente Windows) ou o [Visual Studio para Mac](./tutorials/using-on-mac-vs.md) (somente macOS), para criar um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dab03-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](./tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="dab03-117">Tutoriais</span><span class="sxs-lookup"><span data-stu-id="dab03-117">Tutorials</span></span>

<span data-ttu-id="dab03-118">Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:</span><span class="sxs-lookup"><span data-stu-id="dab03-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="dab03-119">Windows</span><span class="sxs-lookup"><span data-stu-id="dab03-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="dab03-120">Criar seu primeiro aplicativo de console do .NET Core no Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="dab03-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="dab03-121">Criar uma biblioteca de classes com .NET Standard no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dab03-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="dab03-122">Introdução ao .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="dab03-122">Get started with .NET Core using the .NET Core CLI</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="dab03-123">![ícone de câmera para vídeo](./media/video-icon.png "Assista a um vídeo")</span><span class="sxs-lookup"><span data-stu-id="dab03-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="dab03-124">Assista ao vídeo [como instalar e usar o Visual Studio Code e o .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) no Channel 9.</span><span class="sxs-lookup"><span data-stu-id="dab03-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="dab03-125">![ícone de câmera para vídeo](./media/video-icon.png "Assista a um vídeo")</span><span class="sxs-lookup"><span data-stu-id="dab03-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="dab03-126">Assista aos vídeos do [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) no YouTube.</span><span class="sxs-lookup"><span data-stu-id="dab03-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="dab03-127">Consulte o artigo [dependências e requisitos do .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-windows) para obter uma lista das versões do Windows com suporte.</span><span class="sxs-lookup"><span data-stu-id="dab03-127">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) article for a list of the supported Windows versions.</span></span>

<span data-ttu-id="dab03-128">Consulte o artigo [dependências de SDK do .NET Core e tempo de execução](install/dependencies.md?pivots=os-windows) para obter uma lista das versões do Windows com suporte.</span><span class="sxs-lookup"><span data-stu-id="dab03-128">See the [.NET Core SDK and runtime dependencies](install/dependencies.md?pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="dab03-129">Linux</span><span class="sxs-lookup"><span data-stu-id="dab03-129">Linux</span></span>](#tab/linux)

<span data-ttu-id="dab03-130">Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:</span><span class="sxs-lookup"><span data-stu-id="dab03-130">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="dab03-131">Introdução ao .NET Core usando a linha de comando</span><span class="sxs-lookup"><span data-stu-id="dab03-131">Get started with .NET Core using the command-line</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="dab03-132">![ícone de câmera para vídeo](./media/video-icon.png "Assista a um vídeo")</span><span class="sxs-lookup"><span data-stu-id="dab03-132">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="dab03-133">Assista a um vídeo sobre uma [introdução ao Visual Studio Code usando C# e o .NET Core no Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="dab03-133">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="dab03-134">Consulte o artigo [dependências de SDK do .NET Core e tempo de execução](install/dependencies.md?pivots=os-linux) para obter uma lista das versões e distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="dab03-134">See the [.NET Core SDK and runtime dependencies](install/dependencies.md?pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="dab03-135">macOS</span><span class="sxs-lookup"><span data-stu-id="dab03-135">macOS</span></span>](#tab/macos)

<span data-ttu-id="dab03-136">Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:</span><span class="sxs-lookup"><span data-stu-id="dab03-136">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="dab03-137">Introdução ao .NET Core no macOS usando o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dab03-137">Get started with .NET Core on macOS using Visual Studio Code</span></span>](./tutorials/using-on-macos.md)
- [<span data-ttu-id="dab03-138">Introdução ao .NET Core usando a linha de comando</span><span class="sxs-lookup"><span data-stu-id="dab03-138">Get started with .NET Core using the command-line</span></span>](./tutorials/cli-create-console-app.md)
- [<span data-ttu-id="dab03-139">Introdução ao .NET Core no macOS usando o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="dab03-139">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="dab03-140">Criar uma solução completa do .NET Core no macOS usando Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="dab03-140">Build a complete .NET Core solution on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| <span data-ttu-id="dab03-141">![ícone de câmera para vídeo](media/video-icon.png "Assista a um vídeo")</span><span class="sxs-lookup"><span data-stu-id="dab03-141">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="dab03-142">Assista a um vídeo sobre a [introdução ao Visual Studio Code C# usando o e o .NET Core no MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="dab03-142">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="dab03-143">Consulte o artigo [dependências de SDK do .NET Core e tempo de execução](install/dependencies.md?pivots=os-macos) para obter uma lista das versões do os X/MacOS com suporte.</span><span class="sxs-lookup"><span data-stu-id="dab03-143">See the [.NET Core SDK and runtime dependencies](install/dependencies.md?pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
