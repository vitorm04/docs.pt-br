---
title: Comando dotnet-new | Microsoft Docs
description: "O comando dotnet-new cria novos projetos .NET Core no diretório atual."
keywords: dotnet-new, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
translationtype: Human Translation
ms.sourcegitcommit: 99254f84873003496ee00214d55ff908f9fd47d3
ms.openlocfilehash: f0df2efe732912abbdb2d63e918b7ee1a4178b07
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-new"></a>dotnet-new

## <a name="name"></a>Nome
`dotnet-new` – cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.

## <a name="synopsis"></a>Sinopse
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template arguments]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

## <a name="description"></a>Descrição
O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido código-fonte de exemplo para experimentar o conjunto de ferramentas da CLI (Interface de linha de comando). 

Quando invocado, o comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.

## <a name="arguments"></a>Arguments

`<TEMPLATE>`

O modelo para o qual criar uma instância quando o comando é invocado. Cada modelo pode ter opções específicas que podem ser passadas. Para obter mais informações, consulte [Opções de modelo](#template-options).

O comando contém uma lista padrão de modelos. Use `dotnet new -all` para ver todos eles.

A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK. O idioma padrão do modelo é mostrado entre parênteses, como `[C#]`.

|Descrição do modelo  | Nome do modelo  | Linguagens |
|----------------------|----------------|-----------|
| Aplicativo de console  | console        | [C#], F#  |
| Biblioteca de classes        | classlib       | [C#], F#  |
| Projeto de teste de unidade    | mstest         | [C#], F#  |
| Projeto de teste de xUnit   | xunit          | [C#], F#  |
| ASP.NET Core vazio   | web            | [C#]      |
| Aplicativo Web ASP.NET Core | mvc            | [C#], F#  |
| API Web do ASP.NET Core | webapi         | [C#]      |
| Configuração do NuGet         | nugetconfig    |           |
| Configuração da Web           | webconfig      |           |
| Arquivo de solução        | sln            |           |

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda para o comando. Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.

`-l|--list`

Lista os modelos que contêm o nome especificado. Se for invocado para o próprio comando `dotnet new`, listará os possíveis modelos a serem usados no diretório especificado.
Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.

`-lang|--language <C#|F#>`

A linguagem do modelo a ser criada. A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)). Não é válida para alguns modelos.

`-n|--name <OUTPUT_NAME>`

O nome da saída que está sendo criada. Se nenhum nome for especificado, o nome do diretório atual será usado.

`-o|--output <OUTPUT_DIRECTORY>`

Local para colocar a saída gerada. O padrão é o diretório atual.

`-all|--show-all`

Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado. Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força. Isso poderá ocorrer quando o diretório de saída já contiver um projeto.

## <a name="template-options"></a>Opções de modelo
Cada modelo de projeto pode ter opções adicionais disponíveis. Os principais modelos têm as seguintes opções:

**console, xunit, mstest, web, webapi **

`-f|--framework` – especifica a qual estrutura se destina. Valores: netcoreapp1.0 ou netcoreapp1.1 (Padrão: netcoreapp1.0)

**mvc**

`-f|--framework` – especifica a qual estrutura se destina. Valores: netcoreapp1.0 ou netcoreapp1.1 (Padrão: netcoreapp1.0)

`-au|--authentication` – o tipo de autenticação usado. Valores: Nenhum ou Individual (Padrão: Nenhum)

`-uld|--use-local-db` – Se deve usar ou não o LocalDB em vez do SQLite. Valores: verdadeiro ou falso (Padrão: falso)

**classlib**

`-f|--framework` – especifica a qual estrutura se destina. Valores: netcoreapp1.0, netcoreapp1.1 e netstandard1.0 – 1.6 (Padrão: netstandard1.4).

## <a name="examples"></a>Exemplos

Crie um projeto de aplicativo de console F# no diretório atual:

`dotnet new console -lang f#` 
   
Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação destinado ao .NET Core 1.0:  

`dotnet new mvc -au None -f netcoreapp1.0`
 
Crie um novo aplicativo XUnit destinado ao .NET Core 1.1:

`dotnet new xunit --Framework netcoreapp1.1`

Lista todos os modelos disponíveis para o MVC:

`dotnet new mvc -l`

