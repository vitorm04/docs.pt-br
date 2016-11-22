---
title: Comando dotnet-new | .NET Core
description: "O comando dotnet-new cria novos projetos .NET Core no diretório atual."
keywords: dotnet-new, CLI, comando da CLI, .NET Core
author: mairaw
manager: wpickett
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 263c3d05-3a47-46a6-8023-3ca16b488410
translationtype: Human Translation
ms.sourcegitcommit: c6ee3f5663d0a3f62914e8de474cca4d15340c9d
ms.openlocfilehash: 29ccc12ff893d316c816d22da862f90bfc9334ff

---

#<a name="dotnetnew"></a>dotnet-new

## <a name="name"></a>Nome
dotnet-new – Cria um novo projeto .NET Core no diretório atual

## <a name="synopsis"></a>Sinopse
`dotnet new [--help] [--type] [--lang]`

## <a name="description"></a>Descrição
O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido código-fonte de exemplo para experimentar o conjunto de ferramentas da CLI (Interface de Linha de Comando). 

Esse comando é invocado no contexto de um diretório. Quando invocado, o comando resultará na remoção de dois artefatos principais do diretório atual: 

1. Um arquivo `Program.cs` (ou `Program.fs`) arquivo que contém um programa de exemplo “Hello World”.
2. Um arquivo `project.json` válido.

Depois disso, o projeto estará pronto para ser compilado e/ou editado com mais detalhes. 

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-l|--lang <C#|F#>`

Linguagem do projeto. Assume o padrão de `C#`. Outros valores válidos são `csharp`, `fsharp`, `cs` e `fs`.

`-t|--type`

Tipo do projeto. Os valores válidos para C# são `console`, `web`, `lib` e `xunittest`, e para F# apenas `console` é válido. 

## <a name="examples"></a>Exemplos

Crie um projeto de aplicativo de console C# no diretório atual:

`dotnet new` ou `dotnet new --lang c#` 
   
Crie um projeto de aplicativo de console F# no diretório atual:

`dotnet new --lang f#`
  
Crie um novo projeto de aplicativo C# do ASP.NET Core no diretório atual:

`dotnet new -t web`


<!--HONumber=Nov16_HO1-->


