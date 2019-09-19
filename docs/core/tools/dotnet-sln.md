---
title: Comando dotnet sln
description: O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução.
ms.date: 06/13/2018
ms.openlocfilehash: 84508aaefff61b31e2965576ebc2daaae7331951
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117591"
---
# <a name="dotnet-sln"></a>dotnet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet sln` – modifica um arquivo de solução do .NET Core.

## <a name="synopsis"></a>Sinopse

```dotnetcli
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

```dotnetcli
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

> [!NOTE]
> O recurso de curinga não é um recurso CLI, mas do shell de comando. Para expandir os arquivos com êxito, você deve usar um shell que dê suporte ao recurso de curinga. Para saber mais sobre o recurso de curinga, confira [Wikipédia](https://en.wikipedia.org/wiki/Glob_(programming)).
