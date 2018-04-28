---
title: Comando dotnet remove reference – CLI do .NET Core
description: O comando dotnet remove reference fornece uma opção conveniente para remover referências projeto a projeto.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 0b7fb2788ccc04b54bf02f0387141d501612c16d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet remove reference` – Remove as referências projeto a projeto.

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
