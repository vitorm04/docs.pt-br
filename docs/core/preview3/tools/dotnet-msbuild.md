---
title: Comando dotnet-msbuild | SDK do .NET Core
description: "O comando dotnet-msbuild fornece acesso à linha de comando MSmsbuild"
keywords: dotnet-msmsbuild, CLI, comando da CLI, .NET Core
author: mairaw
manager: wpickett
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
translationtype: Human Translation
ms.sourcegitcommit: cde9d9577246a9025d646ce2a6d574a18512146e
ms.openlocfilehash: 51a3afdcf591b8147790d78471c6fee63ceb7f2d

---

#<a name="dotnet-msbuild"></a>dotnet-msbuild

## <a name="name"></a>Nome 
dotnet-build – Compila um projeto e todas as suas dependências 

## <a name="synopsis"></a>Sinopse

`dotnet msbuild <msbuild_arguments>`

## <a name="description"></a>Descrição
O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional 

O comando tem exatamente os mesmos recursos do cliente de linha de comando existente do MSBuild. As opções são todas iguais. É possível usar a [documentação existente](https://msdn.microsoft.com/en-us/library/ms164311.aspx) para se familiarizar com a referência de comando. 

## <a name="examples"></a>Exemplos

Compile um projeto e suas dependências:

`dotnet msbuild`

Compile um projeto e suas dependências usando a configuração da Versão:

`dotnet msbuild /p:Configuration=Release`

Execute o destino de publicação e publique para o RID `osx.10.11-x64`:

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`



<!--HONumber=Nov16_HO3-->


