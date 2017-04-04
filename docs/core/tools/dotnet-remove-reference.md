---
title: Comando dotnet-remove reference - CLI do .NET Core | Microsoft Docs
description: "O comando de referência dotnet-remove fornece uma opção conveniente para remover referências projeto a projeto."
keywords: dotnet-remove, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 889c6b7e-a313-40b1-9fd3-6a6f4c52f1d0
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 22db4037195afa2c49ef038832e09a99c6a0d54e
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-remove-reference"></a>Referência dotnet-remove

## <a name="name"></a>Nome

`dotnet-remove reference` – Remove as referências projeto a projeto.

## <a name="synopsis"></a>Sinopse

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet remove reference` fornece uma opção conveniente para remover referências de projeto de um projeto.

## <a name="arguments"></a>Arguments

`PROJECT`

Arquivo de projeto de destino. Se não for especificado, o comando pesquisará um no diretório atual.

`PROJECT_REFERENCES`

Projeto a projeto (Referências de P2P a serem removidas). É possível especificar um ou vários projetos. Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-f|--framework <FRAMEWORK>`

Remove a referência somente quando houver uma [estrutura](../../standard/frameworks.md) específica como destino.

## <a name="examples"></a>Exemplos

Remover uma referência de projeto do projeto especificado:

`dotnet remove app/app.csproj reference lib/lib.csproj`

Remover várias referências de projeto do projeto no diretório atual:

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

Remova várias referências de projeto usando o padrão glob em Unix/Linux:

`dotnet remove app/app.csproj reference **/*.csproj`

