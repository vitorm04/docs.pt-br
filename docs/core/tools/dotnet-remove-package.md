---
title: Comando dotnet remove package
description: O comando dotnet remove package fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503636"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet remove package` – remove a referência de pacote de um arquivo de projeto.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet remove package` fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.

## <a name="arguments"></a>Argumentos

`PROJECT`

Especifica o arquivo do projeto. Se não for especificado, o comando pesquisará um no diretório atual.

`PACKAGE_NAME`

A referência de pacote a ser removida.

## <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

- Remover `Newtonsoft.Json` o pacote NuGet de um projeto no diretório atual:

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
