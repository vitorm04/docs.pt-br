---
title: Comando dotnet sln – CLI do .NET Core
description: O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução.
author: mairaw
ms.author: mairaw
ms.date: 06/13/2018
ms.openlocfilehash: 65ae402ef5519863886c8cf833598f5314b4bdad
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207754"
---
# <a name="dotnet-sln"></a>dotnet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet sln` – modifica um arquivo de solução do .NET Core.

## <a name="synopsis"></a>Sinopse

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet sln` oferece uma maneira conveniente de adicionar, remover e listar projetos em um arquivo de solução.

Para usar o comando `dotnet sln`, o arquivo de solução já deve existir. Se você precisar criar um, use o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:

```
dotnet new sln
```

## <a name="commands"></a>Comandos

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Adiciona um projeto ou vários projetos ao arquivo de solução. Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Remova um projeto ou vários projetos do arquivo da solução. Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.

`list`

Lista todos os projetos em um arquivo de solução.

## <a name="arguments"></a>Arguments

`SOLUTION_NAME`

Arquivo de solução a ser usado. Se não for especificado, o comando pesquisará um no diretório atual. Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

Adicione um projeto C# a uma solução:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Remova um projeto C# de uma solução:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Adicione vários projetos C# a uma solução:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Remova vários projetos C# de uma solução:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Adicione vários projetos C# a uma solução usando um padrão de recurso de curinga:

`dotnet sln todo.sln add **/*.csproj`

Remova vários projetos C# de uma solução usando um padrão de recurso de curinga:

`dotnet sln todo.sln remove **/*.csproj`
