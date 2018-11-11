---
title: Introdução ao F# com ferramentas de linha de comando
description: Saiba como criar uma solução multiprojeto simples em F# usando a CLI do .NET Core em qualquer sistema operacional (Windows, macOs ou Linux).
ms.date: 03/26/2018
ms.openlocfilehash: 8a82970f33c8bbe1b8cdd8fb6499b59b16d3cbf3
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45673903"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Introdução ao F# com a CLI do .NET Core

Este artigo aborda como você pode começar com o F# em qualquer sistema operacional (Windows, macOS ou Linux) com a CLI do .NET Core. Ele percorre a criação de uma solução multiprojeto com uma biblioteca de classes que é chamada por um aplicativo de console.

## <a name="prerequisites"></a>Pré-requisitos

Para começar, você deve instalar a versão mais recente [SDK do .NET Core](https://www.microsoft.com/net/download/).

Este artigo pressupõe que você sabe como usar uma linha de comando e tiver um texto preferido de editor. Se você não usá-lo, já [Visual Studio Code](get-started-vscode.md) é uma ótima opção como um editor de texto para F#.

## <a name="build-a-simple-multi-project-solution"></a>Crie uma solução multiprojeto simples

Abra um prompt de comando/terminal e use o [dotnet new](../../core/tools/dotnet-new.md) comando para criar um novo arquivo de solução chamado `FSNetCore`:

```console
dotnet new sln -o FSNetCore
```

A seguinte estrutura de diretório é produzida depois de executar o comando anterior:

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Escrever uma biblioteca de classes

Altere os diretórios para *FSNetCore*.

Use o `dotnet new` de comando, crie um projeto de biblioteca de classes na **src** pasta denominada biblioteca.

```console
dotnet new classlib -lang F# -o src/Library
```

A seguinte estrutura de diretório é produzida depois de executar o comando anterior:

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Substitua o conteúdo do `Library.fs` com o código a seguir:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

Adicione o pacote do NuGet newtonsoft. JSON ao projeto de biblioteca.

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Adicione a `Library` do projeto para o `FSNetCore` solução usando o [dotnet sln adicionar](../../core/tools/dotnet-sln.md) comando:

```console
dotnet sln add src/Library/Library.fsproj
```

Executar `dotnet build` para compilar o projeto. Dependências não resolvidas serão restauradas ao compilar.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Escrever um aplicativo de console que consome a biblioteca de classes

Use o `dotnet new` de comando, crie um aplicativo de console na **src** pasta aplicativo de chamada.

```console
dotnet new console -lang F# -o src/App
```

A seguinte estrutura de diretório é produzida depois de executar o comando anterior:

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

Substitua o conteúdo do `Program.fs` arquivo pelo código a seguir:

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

Adicione uma referência para o `Library` projeto usando o [dotnet adicionar referência](../../core/tools/dotnet-add-reference.md).

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Adicione a `App` do projeto para o `FSNetCore` solução usando o `dotnet sln add` comando:

```console
dotnet sln add src/App/App.fsproj
```

Restaure as dependências do NuGet `dotnet restore` ([veja Observação](#dotnet-restore-note)) e execute `dotnet build` para compilar o projeto.

Altere o diretório para o `src/App` projeto de console e executar o projeto passando `Hello World` como argumentos:

```console
cd src/App
dotnet run Hello World
```

Você verá os seguintes resultados:

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>Próximas etapas

Em seguida, confira a [Tour do F#](../tour.md) para saber mais sobre os diferentes recursos do F#.
