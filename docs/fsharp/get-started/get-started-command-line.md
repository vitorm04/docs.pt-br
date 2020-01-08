---
title: Introdução ao F# com ferramentas de linha de comando
description: Saiba como criar uma solução simples de vários projetos sobre F# como usar o CLI do .NET Core em qualquer sistema operacional (Windows, MacOS ou Linux).
ms.date: 03/26/2018
ms.openlocfilehash: aa3ed84660a951eeafc11a00ea3831f587b6d876
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559481"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="4d06d-103">Introdução ao F# com o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4d06d-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="4d06d-104">Este artigo aborda como você pode começar a usar F# o em qualquer sistema operacional (Windows, MacOS ou Linux) com o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4d06d-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="4d06d-105">Ele passa pela criação de uma solução de vários projetos com uma biblioteca de classes chamada por um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="4d06d-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d06d-106">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4d06d-106">Prerequisites</span></span>

<span data-ttu-id="4d06d-107">Para começar, você deve instalar a [SDK do .NET Core](https://dotnet.microsoft.com/download)mais recente.</span><span class="sxs-lookup"><span data-stu-id="4d06d-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="4d06d-108">Este artigo pressupõe que você saiba como usar uma linha de comando e ter um editor de texto preferido.</span><span class="sxs-lookup"><span data-stu-id="4d06d-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="4d06d-109">Se você ainda não o utiliza, [Visual Studio Code](get-started-vscode.md) é uma ótima opção como um editor de texto F#para o.</span><span class="sxs-lookup"><span data-stu-id="4d06d-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="4d06d-110">Criar uma solução simples de vários projetos</span><span class="sxs-lookup"><span data-stu-id="4d06d-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="4d06d-111">Abra um prompt de comando/terminal e use o comando [dotnet New](../../core/tools/dotnet-new.md) para criar um novo arquivo de solução chamado `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="4d06d-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```dotnetcli
dotnet new sln -o FSNetCore
```

<span data-ttu-id="4d06d-112">A seguinte estrutura de diretório é produzida após a execução do comando anterior:</span><span class="sxs-lookup"><span data-stu-id="4d06d-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="4d06d-113">Escrever uma biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="4d06d-113">Write a class library</span></span>

<span data-ttu-id="4d06d-114">Altere os diretórios para *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="4d06d-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="4d06d-115">Use o comando `dotnet new`, crie um projeto de biblioteca de classes na pasta **src** denominada library.</span><span class="sxs-lookup"><span data-stu-id="4d06d-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

<span data-ttu-id="4d06d-116">A seguinte estrutura de diretório é produzida após a execução do comando anterior:</span><span class="sxs-lookup"><span data-stu-id="4d06d-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="4d06d-117">Substitua o conteúdo de `Library.fs` pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="4d06d-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="4d06d-118">Adicione o pacote NuGet Newtonsoft. JSON ao projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="4d06d-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="4d06d-119">Adicione o projeto `Library` à solução `FSNetCore` usando o comando [dotnet sln Add](../../core/tools/dotnet-sln.md) :</span><span class="sxs-lookup"><span data-stu-id="4d06d-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="4d06d-120">Execute `dotnet build` para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="4d06d-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="4d06d-121">As dependências não resolvidas serão restauradas durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="4d06d-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="4d06d-122">Escrever um aplicativo de console que consome a biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="4d06d-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="4d06d-123">Use o comando `dotnet new`, crie um aplicativo de console na pasta **src** chamada app.</span><span class="sxs-lookup"><span data-stu-id="4d06d-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

<span data-ttu-id="4d06d-124">A seguinte estrutura de diretório é produzida após a execução do comando anterior:</span><span class="sxs-lookup"><span data-stu-id="4d06d-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="4d06d-125">Substitua o conteúdo do arquivo `Program.fs` pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="4d06d-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="4d06d-126">Adicione uma referência ao projeto `Library` usando [dotnet Adicionar referência](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="4d06d-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="4d06d-127">Adicione o projeto `App` à solução `FSNetCore` usando o comando `dotnet sln add`:</span><span class="sxs-lookup"><span data-stu-id="4d06d-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```dotnetcli
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="4d06d-128">Restaure as dependências do NuGet, `dotnet restore` e execute `dotnet build` para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="4d06d-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="4d06d-129">Altere o diretório para o projeto de console `src/App` e execute o projeto passando `Hello World` como argumentos:</span><span class="sxs-lookup"><span data-stu-id="4d06d-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="4d06d-130">Você deve ver o seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="4d06d-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="4d06d-131">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4d06d-131">Next steps</span></span>

<span data-ttu-id="4d06d-132">Em seguida, confira o [Tour F# do](../tour.md) para saber mais sobre F# os diferentes recursos.</span><span class="sxs-lookup"><span data-stu-id="4d06d-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
