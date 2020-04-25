---
title: Comando dotnet remove reference
description: O comando dotnet remove reference fornece uma opção conveniente para remover referências projeto a projeto.
ms.date: 02/14/2020
ms.openlocfilehash: a45153376d7d6eb764c1d2c6b473d04a273a2de1
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158327"
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores

## <a name="name"></a>Nome

`dotnet remove reference`-Remove referências ponto a projeto (P2P).

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     <PROJECT_REFERENCES>

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

  Remove a referência somente ao direcionar a uma [estrutura](../../standard/frameworks.md) específica usando o formato TFM.

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
