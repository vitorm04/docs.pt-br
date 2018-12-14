---
title: Comando dotnet list reference – CLI do .NET Core
description: O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto.
ms.date: 12/03/2018
ms.openlocfilehash: 58b4e07abfe95d1febdd54d117825ecedf502e61
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152586"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet list reference` – lista as referências projeto a projeto.

## <a name="synopsis"></a>Sinopse

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto ou solução.

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Especifica o arquivo de projeto para usar para listar referências. Se não é especificado, o comando pesquisa um arquivo de projeto no diretório atual.

## <a name="options"></a>Opções

* **`-h|--help`**

  Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

* Listar as referências de projeto do projeto especificado:

  ```console
  dotnet list app/app.csproj reference
  ```

* Listar as referências de projeto do projeto no diretório atual:

  ```console
  dotnet list reference
  ```