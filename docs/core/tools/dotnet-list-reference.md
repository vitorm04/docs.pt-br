---
title: "Comando de referência dotnet-list | Microsoft Docs"
description: "O comando de referência dotnet-list fornece uma opção conveniente para listar referências projeto a projeto."
keywords: dotnet-list, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8f954a0c-03f8-4fbc-a529-b313ab12c623
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: e95aa43bfed78d72ef1ea5f3883ae64e06ffaa99
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-list-reference"></a>Referência dotnet-list

## <a name="name"></a>Nome

`dotnet-list reference` – lista as referências projeto a projeto.

## <a name="synopsis"></a>Sinopse

```
dotnet list [project] reference
dotnet list reference [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto.

## <a name="arguments"></a>Arguments

`project`

O arquivo de projeto para o qual as referências serão listadas. Se não for especificado, o comando irá procurar um no diretório atual.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

Listar as referências de projeto do projeto especificado:

`dotnet list app/app.csproj reference`

Listar as referências de projeto do projeto no diretório atual:

`dotnet list reference`

