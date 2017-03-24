---
title: Comando dotnet-sln | Microsoft Docs
description: "O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução."
keywords: dotnet-sln, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 84c2a9cab36dcfa76f90d75c83f4988ba441b0a8
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-sln"></a>dotnet-sln

## <a name="name"></a>Nome

`dotnet-sln` – modifica um arquivo de solução do .NET Core.

## <a name="synopsis"></a>Sinopse

```
dotnet sln [<solution_name>] add <project> <project>
dotnet sln [<solution_name>] add **/**
dotnet sln [<solution_name>] remove <project> <project>
dotnet sln [<solution_name>] remove **/**
dotnet sln [<solution_name>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet sln` oferece uma maneira conveniente de adicionar, remover e listar projetos em um arquivo de solução.

## <a name="commands"></a>Comandos

`add <project>`

`add **/*`

Adiciona um projeto ou vários projetos ao arquivo de solução. O padrão Glob é compatível com terminais baseados em Unix/Linux.

`remove <project>`

`remove **/*`

Remova um projeto ou vários projetos do arquivo de solução. O padrão Glob é compatível com terminais baseados em Unix/Linux.

`list`

Liste todos os projetos em um arquivo de solução.

## <a name="arguments"></a>Arguments

`solution_name`

Arquivo de solução a ser usado. Se não for especificado, o comando irá procurar um no diretório atual. Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.

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

Adicione vários projetos a uma solução usando o padrão de recurso curinga:

`dotnet sln add **/**/*.fsproj`

