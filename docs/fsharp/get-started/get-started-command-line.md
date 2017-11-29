---
title: "Introdução ao F # com as ferramentas de linha de comando"
description: "Saiba como usar F # com várias plataformas .NET Core CLI."
keywords: "visual f#, f#, programação funcional, .NET, .NET Core"
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: a23d4861ce599f20f37ecd0564a0187e7b9b739f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="41036-104">Introdução à linguagem F # com o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="41036-104">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="41036-105">Este artigo aborda como você pode começar a usar a F # no núcleo do .NET.</span><span class="sxs-lookup"><span data-stu-id="41036-105">This article covers how you can get started with using F# on .NET Core.</span></span> <span data-ttu-id="41036-106">Ele percorrerá criando uma solução multiprojeto com uma biblioteca de classe que é chamado por um aplicativo de Console.</span><span class="sxs-lookup"><span data-stu-id="41036-106">It will go through building a multi-project solution with a Class Library that is called by a Console Application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="41036-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="41036-107">Prerequisites</span></span>

<span data-ttu-id="41036-108">Para começar, você deve instalar o [.NET Core SDK 1.0 ou posterior](https://dot.net/core).</span><span class="sxs-lookup"><span data-stu-id="41036-108">To begin, you must install the [.NET Core SDK 1.0 or later](https://dot.net/core).</span></span> <span data-ttu-id="41036-109">Não é necessário desinstalar uma versão anterior do SDK .NET Core, pois ele oferece suporte a instalações lado a lado.</span><span class="sxs-lookup"><span data-stu-id="41036-109">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="41036-110">Este artigo pressupõe que você sabe como usar uma linha de comando e tem um texto preferencial editor.</span><span class="sxs-lookup"><span data-stu-id="41036-110">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="41036-111">Se você já não usá-lo, [código do Visual Studio](https://code.visualstudio.com) é uma ótima opção como um editor de texto para F #.</span><span class="sxs-lookup"><span data-stu-id="41036-111">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="41036-112">Para obter o incríveis recursos como IntelliSense, melhor realce de sintaxe e muito mais, você pode baixar o [Ionide extensão](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="41036-112">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="building-a-simple-multi-project-solution"></a><span data-ttu-id="41036-113">Criando uma solução multiprojeto Simple</span><span class="sxs-lookup"><span data-stu-id="41036-113">Building a Simple Multi-project Solution</span></span>

<span data-ttu-id="41036-114">Abra um prompt de comando/terminal e use o `dotnet new` comando para criar um novo arquivo de solução chamado `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="41036-114">Open a command prompt/terminal and use the `dotnet new` command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="41036-115">A estrutura de diretório seguinte é produzida como resultado de concluir o comando:</span><span class="sxs-lookup"><span data-stu-id="41036-115">The folowing directory structure is produced as a result of the command completing:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

<span data-ttu-id="41036-116">Altere os diretórios para *FSNetCore* e comece a adicionar projetos para a pasta de solução.</span><span class="sxs-lookup"><span data-stu-id="41036-116">Change directories to *FSNetCore* and start adding projects to the solution folder.</span></span>
 
### <a name="writing-a-class-library"></a><span data-ttu-id="41036-117">Gravar uma biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="41036-117">Writing a Class library</span></span>

<span data-ttu-id="41036-118">Use o `dotnet new` de comando, crie um projeto de biblioteca de classes no **src** pasta denominada biblioteca.</span><span class="sxs-lookup"><span data-stu-id="41036-118">Use the `dotnet new` command, create a Class Library project in the **src** folder named Library.</span></span> 

```bash
dotnet new lib -lang F# -o src/Library 
```

<span data-ttu-id="41036-119">A seguinte estrutura de diretório é produzida como resultado de concluir o comando:</span><span class="sxs-lookup"><span data-stu-id="41036-119">The following directory structure is produced as a result of the command completing:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="41036-120">Substitua o conteúdo do `Library.fs` com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="41036-120">Replace the contents of `Library.fs` with the following:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="41036-121">Adicione o pacote NuGet newtonsoft. JSON para o projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="41036-121">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="41036-122">Adicionar o `Library` de projeto para o `FSNetCore` solução usando o `dotnet sln add` comando:</span><span class="sxs-lookup"><span data-stu-id="41036-122">Add the `Library` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="41036-123">Restaure as dependências do NuGet, `dotnet restore` ([consulte a Observação](#dotnet-restore-note)) e execute `dotnet build` para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="41036-123">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="writing-a-console-application-which-consumes-the-class-library"></a><span data-ttu-id="41036-124">Escrevendo um aplicativo de Console que consome a biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="41036-124">Writing a Console Application which Consumes the Class Library</span></span>

<span data-ttu-id="41036-125">Use o `dotnet new` de comando, crie um aplicativo de Console no **src** pasta denominada de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="41036-125">Use the `dotnet new` command, create a Console app in the **src** folder named App.</span></span> 

```bash
dotnet new console -lang F# -o src/App 
```

<span data-ttu-id="41036-126">A seguinte estrutura de diretório é produzida como resultado de concluir o comando:</span><span class="sxs-lookup"><span data-stu-id="41036-126">The following directory structure is produced as a result of the command completing:</span></span>

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

<span data-ttu-id="41036-127">Alterar `Program.fs` para:</span><span class="sxs-lookup"><span data-stu-id="41036-127">Change `Program.fs` to:</span></span>

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

<span data-ttu-id="41036-128">Adicione uma referência para o `Library` projeto usando `dotnet add reference`.</span><span class="sxs-lookup"><span data-stu-id="41036-128">Add a reference to the `Library` project using `dotnet add reference`.</span></span>

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="41036-129">Adicionar o `App` de projeto para o `FSNetCore` solução usando o `dotnet sln add` comando:</span><span class="sxs-lookup"><span data-stu-id="41036-129">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="41036-130">Restaure as dependências do NuGet, `dotnet restore` ([consulte a Observação](#dotnet-restore-note)) e execute `dotnet build` para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="41036-130">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="41036-131">Altere o diretório para o `src/App` projeto de console e executar o projeto passando `Hello World` como argumentos.</span><span class="sxs-lookup"><span data-stu-id="41036-131">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments.</span></span>

```bash
cd src/App
dotnet run Hello World
``` 

<span data-ttu-id="41036-132">Você verá os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="41036-132">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]