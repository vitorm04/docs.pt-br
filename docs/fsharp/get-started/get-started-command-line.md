---
title: 'Introdução ao F # com as ferramentas de linha de comando'
description: 'Saiba como criar uma solução multiprojeto simples em F # usando a CLI do .NET Core em qualquer sistema operacional (Windows, macOs ou Linux).'
author: cartermp
ms.author: phcart
ms.date: 03/26/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e48e1291bbe91da0d9ca2adbb08662bd106c8fb4
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Introdução à linguagem F # com o .NET Core CLI

Este artigo aborda como você pode começar com F # em qualquer sistema operacional (Windows, macOS ou Linux) com o .NET Core CLI. Ele passa pelo criando uma solução multiprojeto com uma biblioteca de classe que é chamada por um aplicativo de console.

## <a name="prerequisites"></a>Pré-requisitos

Para começar, você deve instalar o [.NET Core SDK 1.0 ou posterior](https://www.microsoft.com/net/download/). Não é necessário desinstalar uma versão anterior do SDK .NET Core, pois ele oferece suporte a instalações lado a lado.

Este artigo pressupõe que você sabe como usar uma linha de comando e tem um texto preferencial editor. Se você já não usá-lo, [código do Visual Studio](https://code.visualstudio.com) é uma ótima opção como um editor de texto para F #. Para obter o incríveis recursos como IntelliSense, melhor realce de sintaxe e muito mais, você pode baixar o [Ionide extensão](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).

## <a name="build-a-simple-multi-project-solution"></a>Criar uma solução multiprojeto simple

Abra um prompt de comando/terminal e use o [dotnet novo](../../core/tools/dotnet-new.md) comando para criar um novo arquivo de solução chamado `FSNetCore`:

```
dotnet new sln -o FSNetCore
```

A seguinte estrutura de diretório é gerada depois de executar o comando anterior:

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Gravar uma biblioteca de classes

Altere os diretórios para *FSNetCore*.

Use o `dotnet new` de comando, crie um projeto de biblioteca de classe no **src** pasta denominada biblioteca.

```
dotnet new lib -lang F# -o src/Library
```

A seguinte estrutura de diretório é gerada depois de executar o comando anterior:

```
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

Adicione o pacote NuGet newtonsoft. JSON para o projeto de biblioteca.

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Adicionar o `Library` de projeto para o `FSNetCore` solução usando o [dotnet sln adicionar](../../core/tools/dotnet-sln.md) comando:

```
dotnet sln add src/Library/Library.fsproj
```

Restaure as dependências do NuGet usando o `dotnet restore` comando ([consulte a Observação](#dotnet-restore-note)) e execute `dotnet build` para compilar o projeto.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Escrever um aplicativo de console que consome a biblioteca de classes

Use o `dotnet new` de comando, crie um aplicativo de console no **src** pasta denominada de aplicativo.

```
dotnet new console -lang F# -o src/App
```

A seguinte estrutura de diretório é gerada depois de executar o comando anterior:

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

Substitua o conteúdo do `Program.fs` arquivo com o código a seguir:

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

Adicione uma referência para o `Library` projeto usando [dotnet adicionar referência](../../core/tools/dotnet-add-reference.md).

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Adicionar o `App` de projeto para o `FSNetCore` solução usando o `dotnet sln add` comando:

```
dotnet sln add src/App/App.fsproj
```

Restaure as dependências do NuGet, `dotnet restore` ([consulte a Observação](#dotnet-restore-note)) e execute `dotnet build` para compilar o projeto.

Altere o diretório para o `src/App` projeto de console e executar o projeto passando `Hello World` como argumentos:

```
cd src/App
dotnet run Hello World
```

Você verá os seguintes resultados:

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]