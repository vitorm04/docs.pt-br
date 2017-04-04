---
title: Comando dotnet-sln - CLI do .NET Core | Microsoft Docs
description: "O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução."
keywords: dotnet-sln, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 2cdfd02f7735b106fde910b8906ba4dfae860952
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-sln"></a>dotnet-sln

## <a name="name"></a>Nome

`dotnet-sln` – modifica um arquivo de solução do .NET Core.

## <a name="synopsis"></a>Sinopse

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add **/**
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove **/**
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet sln` oferece uma maneira conveniente de adicionar, remover e listar projetos em um arquivo de solução.

## <a name="commands"></a>Comandos

`add <PROJECT> ...`

`add **/*`

Adiciona um projeto ou vários projetos ao arquivo de solução. Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.

`remove <PROJECT> ...`

`remove **/*`

Remova um projeto ou vários projetos do arquivo de solução. Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.

`list`

Liste todos os projetos em um arquivo de solução.

## <a name="arguments"></a>Arguments

`SOLUTION_NAME`

Arquivo de solução a ser usado. Se não for especificado, o comando pesquisará um no diretório atual. Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

Adicione um projeto a uma solução:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Adicione um projeto à solução no diretório atual:

`dotnet sln add todo-app.csproj`

Remova um projeto de uma solução:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Adicione vários projetos a uma solução usando um padrão de recurso curinga:

`dotnet sln add **/**/*.fsproj`

