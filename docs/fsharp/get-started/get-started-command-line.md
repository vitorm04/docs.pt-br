---
title: 'Introdução ao F # com ferramentas de linha de comando'
description: 'Saiba como criar uma solução de vários projetos simples em F # usando o CLI do .NET Core em qualquer sistema operacional (Windows, macOS ou Linux).'
ms.date: 08/15/2020
ms.openlocfilehash: e652b66337a3122de8e6bd4d62d86fb6082b759d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811984"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Introdução ao F # com o CLI do .NET Core

Este artigo aborda como você pode começar a usar o F # em qualquer sistema operacional (Windows, macOS ou Linux) com o CLI do .NET Core. Ele passa pela criação de uma solução de vários projetos com uma biblioteca de classes chamada por um aplicativo de console.

## <a name="prerequisites"></a>Pré-requisitos

Para começar, você deve instalar a [SDK do .NET Core](https://dotnet.microsoft.com/download)mais recente.

Este artigo pressupõe que você saiba como usar uma linha de comando e ter um editor de texto preferido. Se você ainda não o utiliza, [Visual Studio Code](get-started-vscode.md) é uma ótima opção como um editor de texto para F #.

## <a name="build-a-simple-multi-project-solution"></a>Criar uma solução simples de vários projetos

Abra um prompt de comando/terminal e use o comando [dotnet New](../../core/tools/dotnet-new.md) para criar um novo arquivo de solução chamado `FSNetCore` :

```dotnetcli
dotnet new sln -o FSNetCore
```

A seguinte estrutura de diretório é produzida após a execução do comando anterior:

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Escrever uma biblioteca de classes

Altere os diretórios para *FSNetCore*.

Use o `dotnet new` comando, crie um projeto de biblioteca de classes na pasta **src** denominada library.

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

A seguinte estrutura de diretório é produzida após a execução do comando anterior:

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Substitua o conteúdo de `Library.fs` pelo código a seguir:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    let json = JsonConvert.SerializeObject(value)
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value json
```

Adicione o Newtonsoft.Jsno pacote NuGet ao projeto de biblioteca.

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Adicione o `Library` projeto à `FSNetCore` solução usando o comando [dotnet DPD Add](../../core/tools/dotnet-sln.md) :

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

Execute `dotnet build` para compilar o projeto. As dependências não resolvidas serão restauradas durante a compilação.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Escrever um aplicativo de console que consome a biblioteca de classes

Use o `dotnet new` comando, crie um aplicativo de console na pasta **src** chamada app.

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

A seguinte estrutura de diretório é produzida após a execução do comando anterior:

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

Substitua o conteúdo do arquivo `Program.fs` pelo seguinte código:

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    for arg in argv do
        let value = getJsonNetJson arg
        printfn "%s" value

    0 // return an integer exit code
```

Adicione uma referência ao `Library` projeto usando [dotnet Add Reference](../../core/tools/dotnet-add-reference.md).

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Adicione o `App` projeto à `FSNetCore` solução usando o `dotnet sln add` comando:

```dotnetcli
dotnet sln add src/App/App.fsproj
```

Restaure as dependências do NuGet `dotnet restore` e execute `dotnet build` para compilar o projeto.

Altere o diretório para o `src/App` projeto de console e execute o projeto passando `Hello World` como argumentos:

```dotnetcli
cd src/App
dotnet run Hello World
```

Você deve ver o seguintes resultados:

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>Próximas etapas

Em seguida, confira o [Tour do F #](../tour.md) para saber mais sobre os diferentes recursos do F #.
