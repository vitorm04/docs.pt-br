---
title: Comando dotnet-msbuild | Microsoft Docs
description: "O comando dotnet-msbuild fornece acesso à linha de comando MSBuild."
keywords: dotnet-msmsbuild, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: 06d4210e5dff97d3e96efff8ae8e84efc27fb7d2
ms.lasthandoff: 01/21/2017

---

#<a name="dotnet-msbuild"></a>dotnet-msbuild

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>Nome 
dotnet-msbuild – Compila um projeto e todas as suas dependências.

## <a name="synopsis"></a>Sinopse

`dotnet msbuild <msbuild_arguments>`

## <a name="description"></a>Descrição
O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional 

O comando tem exatamente os mesmos recursos do cliente de linha de comando existente do MSBuild. As opções são todas iguais. Você pode usar a [Referência de linha de comando do MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) para se familiarizar com as opções. 

## <a name="examples"></a>Exemplos

Compile um projeto e suas dependências:

`dotnet msbuild`

Compile um projeto e suas dependências usando a configuração da Versão:

`dotnet msbuild /p:Configuration=Release`

Execute o destino de publicação e publique para o RID `osx.10.11-x64`:

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

