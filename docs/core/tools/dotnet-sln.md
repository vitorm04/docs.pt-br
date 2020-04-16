---
title: Comando dotnet sln
description: O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução.
ms.date: 02/14/2020
ms.openlocfilehash: 231287477d986f9ec4a5404cc5278e76c297faa4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463407"
---
# <a name="dotnet-sln"></a>dotnet sln

**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet sln`- Lista ou modifica os projetos em um arquivo de solução .NET Core.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a>Descrição

O `dotnet sln` comando fornece uma maneira conveniente de listar e modificar projetos em um arquivo de solução.

Para usar o comando `dotnet sln`, o arquivo de solução já deve existir. Se você precisar criar um, use o novo comando [dotnet,](dotnet-new.md) como no exemplo a seguir:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Argumentos

- **`SOLUTION_FILE`**

  O arquivo de solução para usar. Se esse argumento for omitido, o comando procurará o diretório atual por um. Se não encontrar nenhum arquivo de solução ou vários arquivos de solução, o comando falhará.

## <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma descrição de como usar o comando.

## <a name="commands"></a>Comandos

### `list`

Lista todos os projetos em um arquivo de solução.

#### <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Argumentos

- **`SOLUTION_FILE`**

  O arquivo de solução para usar. Se esse argumento for omitido, o comando procurará o diretório atual por um. Se não encontrar nenhum arquivo de solução ou vários arquivos de solução, o comando falhará.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma descrição de como usar o comando.
  
### `add`

Adiciona um ou mais projetos ao arquivo de solução.

#### <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Argumentos

- **`SOLUTION_FILE`**

  O arquivo de solução para usar. Se não for especificado, o comando procura o diretório atual por um e falha se houver vários arquivos de solução.

- **`PROJECT_PATH`**

  O caminho para o projeto ou projetos para adicionar à solução. As expansões de [padrão de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell `dotnet sln` Unix/Linux são processadas corretamente pelo comando.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma descrição de como usar o comando.

- **`--in-root`**

  Coloca os projetos na raiz da solução, em vez de criar uma pasta de solução. Disponível desde o SDK do .NET Core 3.0.

- **`-s|--solution-folder <PATH>`**

  O caminho da pasta de solução de destino para adicionar os projetos. Disponível desde o SDK do .NET Core 3.0.

### `remove`

Remova um projeto ou vários projetos do arquivo da solução.

#### <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Argumentos

- **`SOLUTION_FILE`**

  O arquivo de solução para usar. Se for deixado não especificado, o comando procura o diretório atual por um e falha se houver vários arquivos de solução.

- **`PROJECT_PATH`**

  O caminho para o projeto ou projetos para adicionar à solução. As expansões de [padrão de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell `dotnet sln` Unix/Linux são processadas corretamente pelo comando.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma descrição de como usar o comando.

## <a name="examples"></a>Exemplos

- Liste os projetos em uma solução:

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- Adicione um projeto C# a uma solução:

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- Remova um projeto C# de uma solução:

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- Adicionar vários projetos C# à raiz de uma solução:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- Adicione vários projetos C# a uma solução:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Remova vários projetos C# de uma solução:

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Adicionar vários projetos C# a uma solução usando um padrão globbing (somente Unix/Linux):

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Adicionar vários projetos C# a uma solução usando um padrão globbing (somente windows PowerShell):

  ```dotnetcli
  dotnet sln todo.sln add (ls **/*.csproj)
  ```

- Remova vários projetos C# de uma solução usando um padrão globbing (somente Unix/Linux):

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- Remova vários projetos C# de uma solução usando um padrão globbing (somente windows PowerShell):

  ```dotnetcli
  dotnet sln todo.sln remove (ls **/*.csproj)
  ```
