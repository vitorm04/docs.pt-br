---
title: "Comando dotnet-add reference – CLI do .NET Core"
description: "O comando dotnet add reference fornece uma opção conveniente para adicionar referências projeto a projeto."
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 9c6b0f434a9d6b1431e375ec6a437497aaddfc61
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-add-reference"></a>Referência dotnet-add

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet add reference` – Adiciona as referências P2P (projeto a projeto).

## <a name="synopsis"></a>Sinopse

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet add reference` fornece uma opção conveniente para adicionar referências de projeto a um projeto. Depois de executar o comando, os elementos [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) são adicionados ao arquivo de projeto.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

`PROJECT`

Especifica o arquivo do projeto. Se não for especificado, o comando pesquisará um no diretório atual.

`PROJECT_REFERENCES`

Referências P2P (projeto a projeto) a serem adicionadas. Especifique um ou mais projetos. Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com sistemas baseados em Unix/Linux.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-f|--framework <FRAMEWORK>`

Adiciona referências de projeto somente quando há uma [estrutura](../../standard/frameworks.md) específica como destino.

## <a name="examples"></a>Exemplos

Adicionar referência de projeto:

`dotnet add app/app.csproj reference lib/lib.csproj`

Adicione várias referências de projeto para o projeto no diretório atual:

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

Adicionar várias referências de projeto usando um padrão de recurso de curinga no Linux/Unix:

`dotnet add app/app.csproj reference **/*.csproj`
