---
title: Comando dotnet remove reference
description: O comando dotnet remove reference fornece uma opção conveniente para remover referências projeto a projeto.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503624"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet remove reference` – Remove as referências projeto a projeto.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet remove reference` fornece uma opção conveniente para remover referências de projeto de um projeto.

## <a name="arguments"></a>Argumentos

`PROJECT`

Arquivo de projeto de destino. Se não for especificado, o comando pesquisará um no diretório atual.

`PROJECT_REFERENCES`

Referências P2P (projeto a projeto) a serem removidas. É possível especificar um ou vários projetos. Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.

## <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`-f|--framework <FRAMEWORK>`**

  Remove a referência somente quando houver uma [estrutura](../../standard/frameworks.md) específica como destino.

## <a name="examples"></a>Exemplos

- Remover uma referência de projeto do projeto especificado:

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- Remover várias referências de projeto do projeto no diretório atual:

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Remova várias referências de projeto usando o padrão glob em Unix/Linux:

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
