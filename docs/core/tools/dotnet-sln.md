---
title: "Comando dotnet-sln – CLI do .NET Core"
description: "O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução."
keywords: dotnet-sln, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 04/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 606929fbcafddf47abf5da6d3c8ce97d5af06909
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-sln"></a>dotnet-sln

## <a name="name"></a>Nome

`dotnet-sln` – modifica um arquivo de solução do .NET Core.

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

## <a name="commands"></a>Comandos

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Adiciona um projeto ou vários projetos ao arquivo de solução. Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Remova um projeto ou vários projetos do arquivo da solução. Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.

`list`

Liste todos os projetos em um arquivo de solução.

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

