---
title: "Comando de referência dotnet-remove | Microsoft Docs"
description: "O comando de referência dotnet-remove fornece uma opção conveniente para remover referências projeto a projeto."
keywords: dotnet-remove, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 889c6b7e-a313-40b1-9fd3-6a6f4c52f1d0
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 1f1a364b703c6b83a9b21ee420d62411bf9cd3ec
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-remove-reference"></a>Referência dotnet-remove

## <a name="name"></a>Nome

`dotnet-remove reference` – remove as referências projeto a projeto.

## <a name="synopsis"></a>Sinopse

```
dotnet remove [project] reference [-f|--framework] <project_references>
dotnet remove reference [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet remove reference` fornece uma opção conveniente para remover referências de projeto de um projeto.

## <a name="arguments"></a>Arguments

`project`

Arquivo de projeto no qual operar. Se não for especificado, o comando irá procurar um no diretório atual.

`project_references`

Referências projeto a projeto a serem removidas. É possível especificar um ou vários projetos. O padrão Glob é compatível com terminais baseados em Unix/Linux.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-f|--framework <FRAMEWORK>`

Remove uma referência somente quando há uma estrutura específica como destino.

## <a name="examples"></a>Exemplos

Remover uma referência de projeto do projeto especificado:

`dotnet remove app/app.csproj reference lib/lib.csproj`

Remover várias referências de projeto do projeto no diretório atual:

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

Remover várias referências de projeto usando o padrão glob:

`dotnet remove app/app.csproj reference **/*.csproj`
