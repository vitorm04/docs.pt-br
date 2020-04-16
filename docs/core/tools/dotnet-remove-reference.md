---
title: Comando dotnet remove reference
description: O comando dotnet remove reference fornece uma opção conveniente para remover referências projeto a projeto.
ms.date: 02/14/2020
ms.openlocfilehash: 92d36bbbde64d806abc8f223c5f08e3f3d79ce9d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463439"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet remove reference` – Remove as referências projeto a projeto.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>] <PROJECT_REFERENCES>

dotnet remove reference -h|--help
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
