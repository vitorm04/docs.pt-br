---
title: "Comando dotnet-list reference – CLI do .NET Core"
description: "O comando de referência dotnet-list fornece uma opção conveniente para listar referências projeto a projeto."
keywords: dotnet-list, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8f954a0c-03f8-4fbc-a529-b313ab12c623
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 701345e4db51d26b9eefe8f02b6c0526934de5c9
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-list-reference"></a>Referência dotnet-list

## <a name="name"></a>Nome

`dotnet-list reference` – lista as referências projeto a projeto.

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

