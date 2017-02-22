---
title: Comando dotnet-new | Microsoft Docs
description: "O comando dotnet-new cria novos projetos .NET Core no diretório atual."
keywords: dotnet-new, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 263c3d05-3a47-46a6-8023-3ca16b488410
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: a49fe94ca8f678c614fb7f58767693c73e34c737

---

#<a name="dotnet-new"></a>dotnet-new

> [!WARNING]
> Este tópico se aplica à Visualização 2 das Ferramentas do .NET Core. Para a versão do Ferramentas do .NET Core RC4, consulte o tópico [dotnet-new (Ferramentas do .NET Core RC4)](../preview3/tools/dotnet-new.md).

## <a name="name"></a>Nome
`dotnet-new` – Cria um novo projeto do .NET Core no diretório atual.

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


<!--HONumber=Feb17_HO2-->


