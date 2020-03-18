---
title: Comando dotnet list reference
description: O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503709"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet list reference` – lista as referências projeto a projeto.

## <a name="synopsis"></a>Sinopse

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto ou solução.

## <a name="arguments"></a>Argumentos

* **`PROJECT | SOLUTION`**

  Especifica o arquivo de solução ou de projeto para usar para listar referências. Se não é especificado, o comando pesquisa um arquivo de projeto no diretório atual.

## <a name="options"></a>Opções

* **`-h|--help`**

  Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

* Listar as referências de projeto do projeto especificado:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Listar as referências de projeto do projeto no diretório atual:

  ```dotnetcli
  dotnet list reference
  ```
