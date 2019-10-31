---
title: Comando dotnet sln
description: O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução.
ms.date: 10/29/2019
ms.openlocfilehash: 18702c7638798117bd04d5c6a829d64cc6bf18a8
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191824"
---
# <a name="dotnet-sln"></a>dotnet sln

**Este artigo se aplica a: ✓** SDK do .NET Core 1.x e versões posteriores

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet sln` – modifica um arquivo de solução do .NET Core.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet sln` oferece uma maneira conveniente de adicionar, remover e listar projetos em um arquivo de solução.

Para usar o comando `dotnet sln`, o arquivo de solução já deve existir. Se você precisar criar um, use o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  O arquivo de solução a ser usado. Se não for especificado, o comando pesquisará um no diretório atual. Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.

## <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

## <a name="commands"></a>Comandos

### `add`

Adiciona um projeto ou vários projetos ao arquivo de solução.

#### <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH>
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  O arquivo de solução a ser usado. Se não for especificado, o comando pesquisará um no diretório atual. Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.

- **`PROJECT_PATH`**

  O caminho para o projeto a ser adicionado à solução. Adicione vários projetos adicionando um após o outro separado por espaços. As expansões de [padrão de mascaramento](https://en.wikipedia.org/wiki/Glob_(programming)) do shell do UNIX/Linux são processadas corretamente pelo comando `dotnet sln`.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--in-root`**

  Coloca os projetos na raiz da solução, em vez de criar uma pasta de solução. Disponível desde o SDK do .NET Core 3.0.

- **`-s|--solution-folder`**

  O caminho da pasta da solução de destino para a qual adicionar os projetos. Disponível desde o SDK do .NET Core 3.0.

### `remove`

Remova um projeto ou vários projetos do arquivo da solução.

#### <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH>
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  O arquivo de solução a ser usado. Se não for especificado, o comando pesquisará um no diretório atual. Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.

- **`PROJECT_PATH`**

  O caminho para o projeto a ser removido da solução. Remova vários projetos adicionando um após o outro separado por espaços. As expansões de [padrão de mascaramento](https://en.wikipedia.org/wiki/Glob_(programming)) do shell do UNIX/Linux são processadas corretamente pelo comando `dotnet sln`.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

### `list`

Lista todos os projetos em um arquivo de solução.

#### <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln list [-h|--help]
```
  
#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  O arquivo de solução a ser usado. Se não for especificado, o comando pesquisará um no diretório atual. Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

Adicione um projeto C# a uma solução:

```dotnetcli
dotnet sln todo.sln add todo-app/todo-app.csproj
```

Remova um projeto C# de uma solução:

```dotnetcli
dotnet sln todo.sln remove todo-app/todo-app.csproj
```

Adicione vários projetos C# a uma solução:

```dotnetcli
dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
```

Remova vários projetos C# de uma solução:

```dotnetcli
dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
```

Adicionar vários C# projetos a uma solução usando um padrão de mascaramento (somente UNIX/Linux):

```dotnetcli
dotnet sln todo.sln add **/*.csproj
```

Remover vários C# projetos de uma solução usando um padrão de mascaramento (somente UNIX/Linux):

```dotnetcli
dotnet sln todo.sln remove **/*.csproj
```
