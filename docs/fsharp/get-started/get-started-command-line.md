---
title: Introdução ao F# com ferramentas de linha de comando
description: Saiba como criar uma solução simples de vários projetos sobre F# como usar o CLI do .NET Core em qualquer sistema operacional (Windows, MacOS ou Linux).
ms.date: 03/26/2018
ms.openlocfilehash: 1376b6b5384f380c06a96cdc568ad108de8a6e5f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855826"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="a74c2-103">Introdução ao F# com o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="a74c2-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="a74c2-104">Este artigo aborda como você pode começar a usar F# o em qualquer sistema operacional (Windows, MacOS ou Linux) com o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a74c2-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="a74c2-105">Ele passa pela criação de uma solução de vários projetos com uma biblioteca de classes chamada por um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="a74c2-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a74c2-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a74c2-106">Prerequisites</span></span>

<span data-ttu-id="a74c2-107">Para começar, você deve instalar a [SDK do .NET Core](https://dotnet.microsoft.com/download)mais recente.</span><span class="sxs-lookup"><span data-stu-id="a74c2-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="a74c2-108">Este artigo pressupõe que você saiba como usar uma linha de comando e ter um editor de texto preferido.</span><span class="sxs-lookup"><span data-stu-id="a74c2-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="a74c2-109">Se você ainda não o utiliza, [Visual Studio Code](get-started-vscode.md) é uma ótima opção como um editor de texto F#para o.</span><span class="sxs-lookup"><span data-stu-id="a74c2-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="a74c2-110">Criar uma solução simples de vários projetos</span><span class="sxs-lookup"><span data-stu-id="a74c2-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="a74c2-111">Abra um prompt de comando/terminal e use o comando [dotnet New](../../core/tools/dotnet-new.md) para criar um novo arquivo `FSNetCore`de solução chamado:</span><span class="sxs-lookup"><span data-stu-id="a74c2-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```console
dotnet new sln -o FSNetCore
```

<span data-ttu-id="a74c2-112">A seguinte estrutura de diretório é produzida após a execução do comando anterior:</span><span class="sxs-lookup"><span data-stu-id="a74c2-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="a74c2-113">Escrever uma biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="a74c2-113">Write a class library</span></span>

<span data-ttu-id="a74c2-114">Altere os diretórios para *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="a74c2-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="a74c2-115">Use o `dotnet new` comando, crie um projeto de biblioteca de classes na pasta **src** denominada library.</span><span class="sxs-lookup"><span data-stu-id="a74c2-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```console
dotnet new classlib -lang F# -o src/Library
```

<span data-ttu-id="a74c2-116">A seguinte estrutura de diretório é produzida após a execução do comando anterior:</span><span class="sxs-lookup"><span data-stu-id="a74c2-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="a74c2-117">Substitua o conteúdo de `Library.fs` pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a74c2-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="a74c2-118">Adicione o pacote NuGet Newtonsoft. JSON ao projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="a74c2-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="a74c2-119">Adicione o `Library` projeto `FSNetCore` à solução usando o comando [dotnet DPD Add](../../core/tools/dotnet-sln.md) :</span><span class="sxs-lookup"><span data-stu-id="a74c2-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```console
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="a74c2-120">Execute `dotnet build` para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="a74c2-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="a74c2-121">As dependências não resolvidas serão restauradas durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="a74c2-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="a74c2-122">Escrever um aplicativo de console que consome a biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="a74c2-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="a74c2-123">Use o `dotnet new` comando, crie um aplicativo de console na pasta **src** chamada app.</span><span class="sxs-lookup"><span data-stu-id="a74c2-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```console
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="a74c2-124">A seguinte estrutura de diretório é produzida após a execução do comando anterior:</span><span class="sxs-lookup"><span data-stu-id="a74c2-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="a74c2-125">Substitua o conteúdo do `Program.fs` arquivo pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a74c2-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="a74c2-126">Adicione uma referência ao `Library` projeto usando [dotnet Add Reference](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="a74c2-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="a74c2-127">Adicione o `App` projeto `FSNetCore` à solução usando o `dotnet sln add` comando:</span><span class="sxs-lookup"><span data-stu-id="a74c2-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```console
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="a74c2-128">Restaure as dependências `dotnet restore` do NuGet e `dotnet build` execute para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="a74c2-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="a74c2-129">Altere o diretório para `src/App` o projeto de console e execute o `Hello World` projeto passando como argumentos:</span><span class="sxs-lookup"><span data-stu-id="a74c2-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="a74c2-130">Você deverá ver os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="a74c2-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="a74c2-131">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a74c2-131">Next steps</span></span>

<span data-ttu-id="a74c2-132">Em seguida, confira o [Tour F# do](../tour.md) para saber mais sobre F# os diferentes recursos.</span><span class="sxs-lookup"><span data-stu-id="a74c2-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
