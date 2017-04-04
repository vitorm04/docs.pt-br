---
title: Comando dotnet-add reference - CLI do .NET Core | Microsoft Docs
description: "O comando de referência dotnet-add fornece uma opção conveniente para adicionar referências projeto a projeto."
keywords: dotnet-add, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e2a3efd-443c-4f23-a1b1-a662a5387879
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 1b342f0aea19c01d7bdae94552019f4c171fd1a2
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-add-reference"></a>Referência dotnet-add

## <a name="name"></a>Nome

`dotnet-add reference` – Adiciona as referências P2P (projeto a projeto).

## <a name="synopsis"></a>Sinopse

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet add reference` fornece uma opção conveniente para adicionar referências de projeto a um projeto. Depois de executar o comando, os elementos [`<ProjectReference>`](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-items) são adicionados ao arquivo de projeto.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

`PROJECT`

Especifica o arquivo do projeto. Se não for especificado, o comando irá procurar um no diretório atual.

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

Adicionar várias referências de projeto:

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

Adicionar várias referências de projeto usando um padrão de recurso de curinga no Linux/Unix:

`dotnet add app/app.csproj reference **/*.csproj`

