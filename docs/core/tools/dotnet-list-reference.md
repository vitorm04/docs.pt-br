---
title: Comando dotnet list reference – CLI do .NET Core
description: O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 24cb1124fc3f8707afe727e6a73d35d5dde39937
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-list-reference"></a>dotnet list reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet list reference` – lista as referências projeto a projeto.

## <a name="synopsis"></a>Sinopse

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto.

## <a name="arguments"></a>Arguments

`PROJECT`

Especifica o arquivo de projeto para usar para listar referências. Se não for especificado, o comando procurará um arquivo de projeto no diretório atual.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

Listar as referências de projeto do projeto especificado:

`dotnet list app/app.csproj reference`

Listar as referências de projeto do projeto no diretório atual:

`dotnet list reference`
