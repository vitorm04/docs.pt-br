---
title: "Comando de referência dotnet-add | Microsoft Docs"
description: "O comando de referência dotnet-add fornece uma opção conveniente para adicionar referências projeto a projeto."
keywords: dotnet-add, CLI, comando da CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e2a3efd-443c-4f23-a1b1-a662a5387879
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 7d23377244cfe60730b50bd247209de6e90bec70
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-add-reference"></a>Referência dotnet-add

## <a name="name"></a>Nome

`dotnet-add reference` – adiciona as referências projeto a projeto.

## <a name="synopsis"></a>Sinopse

```
dotnet add [project] reference [-f|--framework] <project_references>
dotnet add reference [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet add reference` fornece uma opção conveniente para adicionar referências de projeto a um projeto. Depois de executar o comando, os fragmentos [`<ProjectReference>`](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-items) são adicionados ao arquivo de projeto.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

`project`

Arquivo de projeto no qual operar. Se não for especificado, o comando irá procurar um no diretório atual.

`project_references`

Referências projeto a projeto a serem adicionadas. É possível especificar um ou vários projetos. Há suporte para o padrão glob em terminais baseados em Unix/Linux.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-f|--framework <FRAMEWORK>`

Adiciona referências de projeto somente quando há uma estrutura específica como destino.

## <a name="examples"></a>Exemplos

Adicionar referência de projeto:

`dotnet add app/app.csproj reference lib/lib.csproj`

Adicionar várias referências de projeto:

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

Adicionar várias referências de projeto usando o padrão glob no Linux/Unix:

`dotnet add app/app.csproj reference **/*.csproj`
