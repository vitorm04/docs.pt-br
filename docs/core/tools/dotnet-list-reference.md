---
title: "Comando dotnet list reference – CLI do .NET Core"
description: "O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: b3e903c15a7486faa279d47ad5e2e00c090b19af
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

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

