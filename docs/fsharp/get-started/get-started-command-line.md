---
title: "Introdução ao F # com as ferramentas de linha de comando"
description: "Saiba como usar o F # em qualquer sistema operacional (Windows, MacOS, Linux) com várias plataformas .NET Core CLI."
keywords: "visual f#, f#, programação funcional, .NET, .NET Core"
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: 4820a8a306bd478429b497a8b7c70ff170c1c655
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Introdução à linguagem F # com o .NET Core CLI

Este artigo aborda como você pode começar em qualquer sistema operacional (Windows, macOS ou Linux) usando F # com o .NET Core CLI. Ele percorrerá criando uma solução multiprojeto com uma biblioteca de classe que é chamado por um aplicativo de Console.

## <a name="prerequisites"></a>Pré-requisitos

Para começar, você deve instalar o [.NET Core SDK 1.0 ou posterior](https://dot.net/core). Não é necessário desinstalar uma versão anterior do SDK .NET Core, pois ele oferece suporte a instalações lado a lado.

Este artigo pressupõe que você sabe como usar uma linha de comando e tem um texto preferencial editor. Se você já não usá-lo, [código do Visual Studio](https://code.visualstudio.com) é uma ótima opção como um editor de texto para F #. Para obter o incríveis recursos como IntelliSense, melhor realce de sintaxe e muito mais, você pode baixar o [Ionide extensão](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).

## <a name="building-a-simple-multi-project-solution"></a>Criando uma solução multiprojeto Simple

Abra um prompt de comando/terminal e use o `dotnet new` comando para criar um novo arquivo de solução chamado `FSNetCore`:

```
dotnet new sln -o FSNetCore
```

A estrutura de diretório seguinte é produzida como resultado de concluir o comando:

```
FSNetCore
    ├── FSNetCore.sln
```

Altere os diretórios para *FSNetCore* e comece a adicionar projetos para a pasta de solução.
 
### <a name="writing-a-class-library"></a>Gravar uma biblioteca de classes

Use o `dotnet new` de comando, crie um projeto de biblioteca de classes no **src** pasta denominada biblioteca. 

```bash
dotnet new lib -lang F# -o src/Library 
```

A seguinte estrutura de diretório é produzida como resultado de concluir o comando:

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Substitua o conteúdo do `Library.fs` com o seguinte:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

Adicione o pacote NuGet newtonsoft. JSON para o projeto de biblioteca.

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Adicionar o `Library` de projeto para o `FSNetCore` solução usando o `dotnet sln add` comando:

```bash
dotnet sln add src/Library/Library.fsproj
```

Restaure as dependências do NuGet, `dotnet restore` ([consulte a Observação](#dotnet-restore-note)) e execute `dotnet build` para compilar o projeto.

### <a name="writing-a-console-application-which-consumes-the-class-library"></a>Escrevendo um aplicativo de Console que consome a biblioteca de classes

Use o `dotnet new` de comando, crie um aplicativo de Console no **src** pasta denominada de aplicativo. 

```bash
dotnet new console -lang F# -o src/App 
```

A seguinte estrutura de diretório é produzida como resultado de concluir o comando:

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

Alterar `Program.fs` para:

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

Adicione uma referência para o `Library` projeto usando `dotnet add reference`.

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Adicionar o `App` de projeto para o `FSNetCore` solução usando o `dotnet sln add` comando:

```bash
dotnet sln add src/App/App.fsproj
```

Restaure as dependências do NuGet, `dotnet restore` ([consulte a Observação](#dotnet-restore-note)) e execute `dotnet build` para compilar o projeto.

Altere o diretório para o `src/App` projeto de console e executar o projeto passando `Hello World` como argumentos.

```bash
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
