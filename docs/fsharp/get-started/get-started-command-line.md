---
title: Introdução ao F# com as ferramentas de linha de comando
description: Saiba como criar uma solução multiprojeto simple no F# usando a CLI do .NET Core em qualquer sistema operacional (Windows, macOs ou Linux).
ms.date: 03/26/2018
ms.openlocfilehash: bc9b223fcf133ffe8b19d5284dcbd3c14a426235
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152093"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="a6e92-103">Introdução ao F# com a CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="a6e92-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="a6e92-104">Este artigo aborda como você pode começar com F# em qualquer sistema operacional (Windows, macOS ou Linux) com a CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a6e92-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="a6e92-105">Ele percorre a criação de uma solução multiprojeto com uma biblioteca de classes que é chamada por um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="a6e92-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a6e92-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a6e92-106">Prerequisites</span></span>

<span data-ttu-id="a6e92-107">Para começar, você deve instalar a versão mais recente [SDK do .NET Core](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="a6e92-107">To begin, you must install the latest [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

<span data-ttu-id="a6e92-108">Este artigo pressupõe que você sabe como usar uma linha de comando e tiver um texto preferido de editor.</span><span class="sxs-lookup"><span data-stu-id="a6e92-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="a6e92-109">Se você não usá-lo, já [Visual Studio Code](get-started-vscode.md) é uma ótima opção como um editor de texto para F#.</span><span class="sxs-lookup"><span data-stu-id="a6e92-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="a6e92-110">Crie uma solução multiprojeto simples</span><span class="sxs-lookup"><span data-stu-id="a6e92-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="a6e92-111">Abra um prompt de comando/terminal e use o [dotnet new](../../core/tools/dotnet-new.md) comando para criar um novo arquivo de solução chamado `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="a6e92-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```console
dotnet new sln -o FSNetCore
```

<span data-ttu-id="a6e92-112">A seguinte estrutura de diretório é produzida depois de executar o comando anterior:</span><span class="sxs-lookup"><span data-stu-id="a6e92-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="a6e92-113">Escrever uma biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="a6e92-113">Write a class library</span></span>

<span data-ttu-id="a6e92-114">Altere os diretórios para *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="a6e92-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="a6e92-115">Use o `dotnet new` de comando, crie um projeto de biblioteca de classes na **src** pasta denominada biblioteca.</span><span class="sxs-lookup"><span data-stu-id="a6e92-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```console
dotnet new classlib -lang F# -o src/Library
```

<span data-ttu-id="a6e92-116">A seguinte estrutura de diretório é produzida depois de executar o comando anterior:</span><span class="sxs-lookup"><span data-stu-id="a6e92-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="a6e92-117">Substitua o conteúdo do `Library.fs` com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a6e92-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="a6e92-118">Adicione o pacote do NuGet newtonsoft. JSON ao projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="a6e92-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="a6e92-119">Adicione a `Library` do projeto para o `FSNetCore` solução usando o [dotnet sln adicionar](../../core/tools/dotnet-sln.md) comando:</span><span class="sxs-lookup"><span data-stu-id="a6e92-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```console
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="a6e92-120">Executar `dotnet build` para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="a6e92-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="a6e92-121">Dependências não resolvidas serão restauradas ao compilar.</span><span class="sxs-lookup"><span data-stu-id="a6e92-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="a6e92-122">Escrever um aplicativo de console que consome a biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="a6e92-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="a6e92-123">Use o `dotnet new` de comando, crie um aplicativo de console na **src** pasta aplicativo de chamada.</span><span class="sxs-lookup"><span data-stu-id="a6e92-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```console
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="a6e92-124">A seguinte estrutura de diretório é produzida depois de executar o comando anterior:</span><span class="sxs-lookup"><span data-stu-id="a6e92-124">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="a6e92-125">Substitua o conteúdo do `Program.fs` arquivo pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a6e92-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    argv
    |> Array.map getJsonNetJson
    |> Array.iter (printfn "%s")

    0 // return an integer exit code
```

<span data-ttu-id="a6e92-126">Adicione uma referência para o `Library` projeto usando o [dotnet adicionar referência](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="a6e92-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="a6e92-127">Adicione a `App` do projeto para o `FSNetCore` solução usando o `dotnet sln add` comando:</span><span class="sxs-lookup"><span data-stu-id="a6e92-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```console
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="a6e92-128">Restaure as dependências do NuGet `dotnet restore` e execute `dotnet build` para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="a6e92-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="a6e92-129">Altere o diretório para o `src/App` projeto de console e executar o projeto passando `Hello World` como argumentos:</span><span class="sxs-lookup"><span data-stu-id="a6e92-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="a6e92-130">Você verá os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="a6e92-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="a6e92-131">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a6e92-131">Next steps</span></span>

<span data-ttu-id="a6e92-132">Em seguida, confira a [Tour do F# ](../tour.md) para saber mais sobre diferentes F# recursos.</span><span class="sxs-lookup"><span data-stu-id="a6e92-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
