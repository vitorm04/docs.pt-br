---
title: 'Introdução ao F # com as ferramentas de linha de comando'
description: 'Saiba como criar uma solução multiprojeto simples em F # usando a CLI do .NET Core em qualquer sistema operacional (Windows, macOs ou Linux).'
author: cartermp
ms.author: phcart
ms.date: 03/26/2018
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 767385be605d863644db563a2e86a41ca80527c4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="0b387-103">Introdução à linguagem F # com o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="0b387-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="0b387-104">Este artigo aborda como você pode começar com F # em qualquer sistema operacional (Windows, macOS ou Linux) com o .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="0b387-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="0b387-105">Ele passa pelo criando uma solução multiprojeto com uma biblioteca de classe que é chamada por um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="0b387-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0b387-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0b387-106">Prerequisites</span></span>

<span data-ttu-id="0b387-107">Para começar, você deve instalar o [.NET Core SDK 1.0 ou posterior](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="0b387-107">To begin, you must install the [.NET Core SDK 1.0 or later](https://www.microsoft.com/net/download/).</span></span> <span data-ttu-id="0b387-108">Não é necessário desinstalar uma versão anterior do SDK .NET Core, pois ele oferece suporte a instalações lado a lado.</span><span class="sxs-lookup"><span data-stu-id="0b387-108">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="0b387-109">Este artigo pressupõe que você sabe como usar uma linha de comando e tem um texto preferencial editor.</span><span class="sxs-lookup"><span data-stu-id="0b387-109">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="0b387-110">Se você já não usá-lo, [código do Visual Studio](https://code.visualstudio.com) é uma ótima opção como um editor de texto para F #.</span><span class="sxs-lookup"><span data-stu-id="0b387-110">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="0b387-111">Para obter o incríveis recursos como IntelliSense, melhor realce de sintaxe e muito mais, você pode baixar o [Ionide extensão](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="0b387-111">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="0b387-112">Criar uma solução multiprojeto simple</span><span class="sxs-lookup"><span data-stu-id="0b387-112">Build a simple multi-project solution</span></span>

<span data-ttu-id="0b387-113">Abra um prompt de comando/terminal e use o [dotnet novo](../../core/tools/dotnet-new.md) comando para criar um novo arquivo de solução chamado `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="0b387-113">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="0b387-114">A seguinte estrutura de diretório é gerada depois de executar o comando anterior:</span><span class="sxs-lookup"><span data-stu-id="0b387-114">The following directory structure is produced after running the previous command:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="0b387-115">Gravar uma biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="0b387-115">Write a class library</span></span>

<span data-ttu-id="0b387-116">Altere os diretórios para *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="0b387-116">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="0b387-117">Use o `dotnet new` de comando, crie um projeto de biblioteca de classe no **src** pasta denominada biblioteca.</span><span class="sxs-lookup"><span data-stu-id="0b387-117">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```
dotnet new lib -lang F# -o src/Library
```

<span data-ttu-id="0b387-118">A seguinte estrutura de diretório é gerada depois de executar o comando anterior:</span><span class="sxs-lookup"><span data-stu-id="0b387-118">The following directory structure is produced after running the previous command:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="0b387-119">Substitua o conteúdo do `Library.fs` com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="0b387-119">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="0b387-120">Adicione o pacote NuGet newtonsoft. JSON para o projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="0b387-120">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="0b387-121">Adicionar o `Library` de projeto para o `FSNetCore` solução usando o [dotnet sln adicionar](../../core/tools/dotnet-sln.md) comando:</span><span class="sxs-lookup"><span data-stu-id="0b387-121">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="0b387-122">Restaure as dependências do NuGet usando o `dotnet restore` comando ([consulte a Observação](#dotnet-restore-note)) e execute `dotnet build` para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="0b387-122">Restore the NuGet dependencies using the `dotnet restore` command ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="0b387-123">Escrever um aplicativo de console que consome a biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="0b387-123">Write a console application that consumes the class library</span></span>

<span data-ttu-id="0b387-124">Use o `dotnet new` de comando, crie um aplicativo de console no **src** pasta denominada de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b387-124">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="0b387-125">A seguinte estrutura de diretório é gerada depois de executar o comando anterior:</span><span class="sxs-lookup"><span data-stu-id="0b387-125">The following directory structure is produced after running the previous command:</span></span>

```
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

<span data-ttu-id="0b387-126">Substitua o conteúdo do `Program.fs` arquivo com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="0b387-126">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="0b387-127">Adicione uma referência para o `Library` projeto usando [dotnet adicionar referência](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="0b387-127">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="0b387-128">Adicionar o `App` de projeto para o `FSNetCore` solução usando o `dotnet sln add` comando:</span><span class="sxs-lookup"><span data-stu-id="0b387-128">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="0b387-129">Restaure as dependências do NuGet, `dotnet restore` ([consulte a Observação](#dotnet-restore-note)) e execute `dotnet build` para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="0b387-129">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="0b387-130">Altere o diretório para o `src/App` projeto de console e executar o projeto passando `Hello World` como argumentos:</span><span class="sxs-lookup"><span data-stu-id="0b387-130">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```
cd src/App
dotnet run Hello World
```

<span data-ttu-id="0b387-131">Você verá os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="0b387-131">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]