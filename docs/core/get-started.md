---
title: Introdução ao .NET Core
description: Encontre recursos para aprender a criar aplicativos .NET Core no Windows, Linux e macOS.
author: thraka
ms.author: adegeo
ms.date: 06/27/2018
ms.openlocfilehash: b111d464b83f3bc6a4a0da86678c5364bf4a9537
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802293"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="ad691-103">Introdução ao .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad691-103">Get started with .NET Core</span></span>

<span data-ttu-id="ad691-104">Este artigo fornece informações de como começar a usar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad691-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="ad691-105">O .NET Core pode ser instalado no Windows, no Linux e no macOS.</span><span class="sxs-lookup"><span data-stu-id="ad691-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="ad691-106">Você pode codificar em seu editor de texto favorito e produzir aplicativos e bibliotecas multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="ad691-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="ad691-107">Se você não souber exatamente o que é o .NET Core ou como ele se relaciona com outras tecnologias do .NET, comece com a visão geral [O que é o .NET](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ad691-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="ad691-108">Resumindo, o .NET Core é uma implementação open-source e multiplataforma do .NET.</span><span class="sxs-lookup"><span data-stu-id="ad691-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="ad691-109">Criar um aplicativo</span><span class="sxs-lookup"><span data-stu-id="ad691-109">Create an application</span></span>

<span data-ttu-id="ad691-110">Primeiro, baixe e instale o [SDK do .NET Core](https://www.microsoft.com/net/download/) em seu computador.</span><span class="sxs-lookup"><span data-stu-id="ad691-110">First, download and install the [.NET Core SDK](https://www.microsoft.com/net/download/) on your computer.</span></span>

<span data-ttu-id="ad691-111">Em seguida, abra um terminal, como o **PowerShell**, um **prompt de comando** ou o **Bash**.</span><span class="sxs-lookup"><span data-stu-id="ad691-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="ad691-112">Digite os seguintes comandos `dotnet` para criar e executar um aplicativo C#.</span><span class="sxs-lookup"><span data-stu-id="ad691-112">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="ad691-113">Você deverá ver a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="ad691-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="ad691-114">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="ad691-114">Congratulations!</span></span> <span data-ttu-id="ad691-115">Você criou um aplicativo simples do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad691-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="ad691-116">Também é possível usar o [Visual Studio Code](tutorials/with-visual-studio-code.md), o [Visual Studio](tutorials/with-visual-studio.md) (somente Windows) ou o [Visual Studio para Mac](tutorials/using-on-mac-vs.md) (somente macOS), para criar um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad691-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="ad691-117">Tutoriais</span><span class="sxs-lookup"><span data-stu-id="ad691-117">Tutorials</span></span>

<span data-ttu-id="ad691-118">Você pode começar a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo.</span><span class="sxs-lookup"><span data-stu-id="ad691-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="ad691-119">Windows</span><span class="sxs-lookup"><span data-stu-id="ad691-119">Windows</span></span>](#tab/windows)

* [<span data-ttu-id="ad691-120">Compilar um aplicativo “Olá, Mundo” em C# com o .NET Core no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ad691-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)

* [<span data-ttu-id="ad691-121">Criar uma biblioteca de classes em C# e com o .NET Core no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ad691-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)

* [<span data-ttu-id="ad691-122">Criar um aplicativo “Olá, Mundo” em Visual Basic com o .NET Core no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ad691-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)

* [<span data-ttu-id="ad691-123">Criar uma biblioteca de classes com Visual Basic e o .NET Core no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ad691-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  

* <span data-ttu-id="ad691-124">Assista a um vídeo sobre [como instalar e usar o Visual Studio Code e o .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span><span class="sxs-lookup"><span data-stu-id="ad691-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>

* <span data-ttu-id="ad691-125">Assista a um vídeo sobre [como instalar e usar o Visual Studio 2017 e o .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span><span class="sxs-lookup"><span data-stu-id="ad691-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>

* [<span data-ttu-id="ad691-126">Introdução ao .NET Core usando a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ad691-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

<span data-ttu-id="ad691-127">Confira o artigo [Pré-requisitos do desenvolvimento para Windows](windows-prerequisites.md) para obter uma lista das versões do Windows com suporte.</span><span class="sxs-lookup"><span data-stu-id="ad691-127">See the [Prerequisites for Windows development](windows-prerequisites.md) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="ad691-128">Linux</span><span class="sxs-lookup"><span data-stu-id="ad691-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="ad691-129">Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo.</span><span class="sxs-lookup"><span data-stu-id="ad691-129">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* [<span data-ttu-id="ad691-130">Introdução ao .NET Core usando a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ad691-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* <span data-ttu-id="ad691-131">Assista a um vídeo sobre uma [introdução ao Visual Studio Code usando C# e o .NET Core no Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="ad691-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="ad691-132">Confira o artigo de [Pré-requisitos do desenvolvimento para Linux](linux-prerequisites.md) para ver uma lista das distribuições e versões do Linux com suporte.</span><span class="sxs-lookup"><span data-stu-id="ad691-132">See the [Prerequisites for Linux development](linux-prerequisites.md) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="ad691-133">macOS</span><span class="sxs-lookup"><span data-stu-id="ad691-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="ad691-134">Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo.</span><span class="sxs-lookup"><span data-stu-id="ad691-134">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* <span data-ttu-id="ad691-135">Assista a um vídeo sobre uma [introdução ao Visual Studio Code usando C# e o .NET Core no macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="ad691-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>

* [<span data-ttu-id="ad691-136">Introdução ao .NET Core no macOS usando o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ad691-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)

* [<span data-ttu-id="ad691-137">Introdução ao .NET Core usando a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ad691-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* [<span data-ttu-id="ad691-138">Introdução ao .NET Core no macOS usando o Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="ad691-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)

* [<span data-ttu-id="ad691-139">Compilar uma solução completa do .NET Core no macOS usando o Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="ad691-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="ad691-140">Confira o artigo [Pré-requisitos do desenvolvimento para macOS](macos-prerequisites.md) para obter uma lista das versões do OS X/macOS com suporte.</span><span class="sxs-lookup"><span data-stu-id="ad691-140">See the [Prerequisites for macOS development](macos-prerequisites.md) article for a list of the supported OS X / macOS versions.</span></span>

---
