---
title: Introdução ao .NET Core
description: Encontre recursos para aprender a criar aplicativos .NET Core no Windows, Linux e macOS.
author: adegeo
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 56eebc0fc5bad6f57d93358cbbef389d6355d66b
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656684"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="d1b50-103">Introdução ao .NET Core</span><span class="sxs-lookup"><span data-stu-id="d1b50-103">Get started with .NET Core</span></span>

<span data-ttu-id="d1b50-104">Este artigo fornece informações de como começar a usar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d1b50-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="d1b50-105">O .NET Core pode ser instalado no Windows, no Linux e no macOS.</span><span class="sxs-lookup"><span data-stu-id="d1b50-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="d1b50-106">Você pode codificar em seu editor de texto favorito e produzir aplicativos e bibliotecas multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="d1b50-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="d1b50-107">Se você não tiver certeza de qual é o .NET Core ou de como ele se relaciona com outras tecnologias .NET, comece com o [que é](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) a visão geral do .net.</span><span class="sxs-lookup"><span data-stu-id="d1b50-107">If you're unsure what .NET Core is or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="d1b50-108">Resumindo, o .NET Core é uma implementação open-source e multiplataforma do .NET.</span><span class="sxs-lookup"><span data-stu-id="d1b50-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="d1b50-109">Criar um aplicativo</span><span class="sxs-lookup"><span data-stu-id="d1b50-109">Create an application</span></span>

<span data-ttu-id="d1b50-110">Primeiro, baixe e instale o [SDK do .NET Core](https://dotnet.microsoft.com/download) em seu computador.</span><span class="sxs-lookup"><span data-stu-id="d1b50-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="d1b50-111">Em seguida, abra um terminal, como o **PowerShell**, um **prompt de comando** ou o **Bash**.</span><span class="sxs-lookup"><span data-stu-id="d1b50-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="d1b50-112">Insira os seguintes `dotnet` comandos para criar e executar um aplicativo C#:</span><span class="sxs-lookup"><span data-stu-id="d1b50-112">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="d1b50-113">A seguinte saída deve ser exibida:</span><span class="sxs-lookup"><span data-stu-id="d1b50-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="d1b50-114">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="d1b50-114">Congratulations!</span></span> <span data-ttu-id="d1b50-115">Você criou um aplicativo simples do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d1b50-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="d1b50-116">Também é possível usar o [Visual Studio Code](./tutorials/with-visual-studio-code.md), o [Visual Studio](./tutorials/with-visual-studio.md) (somente Windows) ou o [Visual Studio para Mac](tutorials/with-visual-studio-mac.md) (somente macOS), para criar um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d1b50-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/with-visual-studio-mac.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="d1b50-117">Tutoriais</span><span class="sxs-lookup"><span data-stu-id="d1b50-117">Tutorials</span></span>

<span data-ttu-id="d1b50-118">Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:</span><span class="sxs-lookup"><span data-stu-id="d1b50-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="d1b50-119">Windows</span><span class="sxs-lookup"><span data-stu-id="d1b50-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="d1b50-120">Criar seu primeiro aplicativo de console do .NET Core no Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="d1b50-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="d1b50-121">Criar uma biblioteca de classes com .NET Standard no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d1b50-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="d1b50-122">Tutorial: criar um aplicativo de console do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d1b50-122">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="d1b50-123">![ícone de câmera para vídeo](./media/video-icon.png "Assistir a um vídeo")</span><span class="sxs-lookup"><span data-stu-id="d1b50-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="d1b50-124">Assista ao vídeo [como instalar e usar o Visual Studio Code e o .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) no Channel 9.</span><span class="sxs-lookup"><span data-stu-id="d1b50-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="d1b50-125">![ícone de câmera para vídeo](./media/video-icon.png "Assistir a um vídeo")</span><span class="sxs-lookup"><span data-stu-id="d1b50-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="d1b50-126">Assista aos vídeos do [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) no YouTube.</span><span class="sxs-lookup"><span data-stu-id="d1b50-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="d1b50-127">Consulte o artigo [dependências e requisitos do .NET Core](install/dependencies.md?pivots=os-windows) para obter uma lista das versões do Windows com suporte.</span><span class="sxs-lookup"><span data-stu-id="d1b50-127">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linux"></a>[<span data-ttu-id="d1b50-128">Linux</span><span class="sxs-lookup"><span data-stu-id="d1b50-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="d1b50-129">Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:</span><span class="sxs-lookup"><span data-stu-id="d1b50-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="d1b50-130">Tutorial: criar um aplicativo de console do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d1b50-130">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="d1b50-131">![ícone de câmera para vídeo](./media/video-icon.png "Assistir a um vídeo")</span><span class="sxs-lookup"><span data-stu-id="d1b50-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="d1b50-132">Assista a um vídeo sobre uma [introdução ao Visual Studio Code usando C# e o .NET Core no Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="d1b50-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="d1b50-133">Consulte o artigo [dependências e requisitos do .NET Core](install/dependencies.md?pivots=os-linux) para obter uma lista das versões e distribuições do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="d1b50-133">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macos"></a>[<span data-ttu-id="d1b50-134">macOS</span><span class="sxs-lookup"><span data-stu-id="d1b50-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="d1b50-135">Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:</span><span class="sxs-lookup"><span data-stu-id="d1b50-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="d1b50-136">Tutorial: criar um aplicativo de console do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d1b50-136">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)
- [<span data-ttu-id="d1b50-137">Tutorial: criar um aplicativo de console do .NET Core usando Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="d1b50-137">Tutorial: Create a .NET Core console application using Visual Studio for Mac</span></span>](tutorials/with-visual-studio-mac.md)
- [<span data-ttu-id="d1b50-138">Criar uma biblioteca de .NET Standard no macOS usando Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="d1b50-138">Build a .NET Standard library on macOS using Visual Studio for Mac</span></span>](tutorials/library-with-visual-studio-mac.md)

|   |   |
|---|---|
| <span data-ttu-id="d1b50-139">![ícone de câmera para vídeo](media/video-icon.png "Assistir a um vídeo")</span><span class="sxs-lookup"><span data-stu-id="d1b50-139">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="d1b50-140">Assista a um vídeo sobre como [começar a usar o Visual Studio Code usando C# e .NET Core no MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="d1b50-140">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="d1b50-141">Consulte o artigo [dependências e requisitos do .NET Core](install/dependencies.md?pivots=os-macos) para obter uma lista das versões do os X/MacOS com suporte.</span><span class="sxs-lookup"><span data-stu-id="d1b50-141">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
