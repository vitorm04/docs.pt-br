---
title: Comando dotnet list reference
description: O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto.
ms.date: 06/26/2019
ms.openlocfilehash: 496cbcd8fa4d921e30b363904ad0273bd5ebacd5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733226"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Este artigo aplica-se a:** ✔️ SDK do .NET Core 1. x e versões posteriores

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet list reference` – lista as referências projeto a projeto.

## <a name="synopsis"></a>Sinopse

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto ou solução.

## <a name="arguments"></a>Arguments

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
