---
title: Comando dotnet sln
description: O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543476"
---
# <a name="dotnet-sln"></a>dotnet sln

**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores

## <a name="name"></a>Nome

`dotnet sln`-lista ou modifica os projetos em um arquivo de solução do .NET Core.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>DESCRIÇÃO

O comando `dotnet sln` fornece uma maneira conveniente de listar e modificar projetos em um arquivo de solução.

Para usar o comando `dotnet sln`, o arquivo de solução já deve existir. Se você precisar criar um, use o comando [dotnet New](dotnet-new.md) , como no exemplo a seguir:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Argumentos

- **`SOLUTION_FILE`**

  O arquivo de solução a ser usado. Se esse argumento for omitido, o comando pesquisará o diretório atual em busca de um. Se ele não encontrar nenhum arquivo de solução ou vários arquivos de solução, o comando falhará.

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

  O arquivo de solução a ser usado. Se esse argumento for omitido, o comando pesquisará o diretório atual em busca de um. Se ele não encontrar nenhum arquivo de solução ou vários arquivos de solução, o comando falhará.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma descrição de como usar o comando.
  
### `add`

Adiciona um ou mais projetos ao arquivo de solução.

#### <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Argumentos

- **`SOLUTION_FILE`**

  O arquivo de solução a ser usado. Se não for especificado, o comando pesquisará o diretório atual em busca de um e falhará se houver vários arquivos de solução.

- **`PROJECT_PATH`**

  O caminho para o projeto ou projetos a serem adicionados à solução. As expansões de [padrão de mascaramento](https://en.wikipedia.org/wiki/Glob_(programming)) do shell do UNIX/Linux são processadas corretamente pelo comando `dotnet sln`.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma descrição de como usar o comando.

- **`--in-root`**

  Coloca os projetos na raiz da solução, em vez de criar uma pasta de solução. Disponível desde o SDK do .NET Core 3.0.

- **`-s|--solution-folder`**

  O caminho da pasta da solução de destino para a qual adicionar os projetos. Disponível desde o SDK do .NET Core 3.0.

### `remove`

Remova um projeto ou vários projetos do arquivo da solução.

#### <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Argumentos

- **`SOLUTION_FILE`**

  O arquivo de solução a ser usado. Se for Left não especificado, o comando pesquisará o diretório atual em busca de um e falhará se houver vários arquivos de solução.

- **`PROJECT_PATH`**

  O caminho para o projeto ou projetos a serem adicionados à solução. As expansões de [padrão de mascaramento](https://en.wikipedia.org/wiki/Glob_(programming)) do shell do UNIX/Linux são processadas corretamente pelo comando `dotnet sln`.

#### <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma descrição de como usar o comando.

## <a name="examples"></a>Exemplos

- Listar os projetos em uma solução:

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

- Adicionar vários C# projetos à raiz de uma solução:

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

- Adicionar vários C# projetos a uma solução usando um padrão de mascaramento (somente UNIX/Linux):

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Remover vários C# projetos de uma solução usando um padrão de mascaramento (somente UNIX/Linux):

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
