---
title: Introdução ao C# – familiarize-se com as ferramentas de desenvolvimento
description: Este artigo fornece uma introdução básica às ferramentas que você usará para desenvolver aplicativos C# e .NET no seu computador.
ms.date: 10/23/2018
ms.openlocfilehash: b18c71c54e4450902f576a1074058abcd5e8aa91
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834084"
---
# <a name="become-familiar-with-the-net-development-tools"></a>Familiarize-se com as ferramentas de desenvolvimento .NET

A primeira etapa para executar um tutorial em seu computador é configurar um ambiente de desenvolvimento.
O tutorial do .NET [Olá, mundo em 10 minutos](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) tem instruções para configurar seu ambiente de desenvolvimento local no Windows, Linux ou MacOS.

Como alternativa, você pode instalar o [SDK do .NET Core](https://dotnet.microsoft.com/download) e o [Visual Studio Code](https://code.visualstudio.com/).

## <a name="basic-application-development-flow"></a>Fluxo de desenvolvimento de aplicativos básico

Você criará aplicativos usando o comando [`dotnet new`](../../../core/tools/dotnet-new.md). Este comando gera os arquivos e ativos necessários para o seu aplicativo. Todos os tutoriais de introdução ao C# usam o tipo de aplicativo `console`. Depois de conhecer as noções básicas, você poderá expandir para outros tipos de aplicativo.

Os outros comandos que você usará são [`dotnet build`](../../../core/tools/dotnet-build.md) para compilar o executável, e [`dotnet run`](../../../core/tools/dotnet-run.md) para executar o executável.

## <a name="pick-your-tutorial"></a>Escolha seu tutorial

Você pode iniciar com qualquer um dos seguintes tutoriais:

## <a name="numbers-in-cnumbers-in-csharp-localmd"></a>[Números em C#](numbers-in-csharp-local.md)

No tutorial [Números em C#](numbers-in-csharp-local.md), você aprenderá como os computadores armazenam números e como executar cálculos com diferentes tipos de número. Você aprenderá os conceitos básicos de arredondamento e como executar cálculos matemáticos usando C#.

Esse tutorial pressupõe a conclusão da lição [Olá, Mundo](hello-world.yml).

## <a name="branches-and-loopsbranches-and-loops-localmd"></a>[Ramificações e loops](branches-and-loops-local.md)

O tutorial [Branches e loops](branches-and-loops-local.md) ensina os conceitos básicos da seleção de diferentes caminhos de execução de código com base nos valores armazenados em variáveis. Você aprenderá os conceitos básicos do fluxo de controle, que são os fundamentos de como os programas tomam decisões e escolhem ações diferentes.

Esse tutorial pressupõe a conclusão das lições [Olá, Mundo](hello-world.yml) e [Números em C#](numbers-in-csharp-local.md).

## <a name="list-collectionarrays-and-collectionsmd"></a>[Coleções de lista](arrays-and-collections.md)

A lição [Coleções de lista](arrays-and-collections.md) fornece um tour pelo tipo Coleções de lista que armazena as sequências de dados. Você aprenderá a adicionar e remover itens, pesquisar itens e classificar listas. Você explorará os diferentes tipos de listas. 

Esse tutorial pressupõe a conclusão das lições listadas acima.

## <a name="introduction-to-classesintroduction-to-classesmd"></a>[Introdução às classes](introduction-to-classes.md)

Esse tutorial final de introdução ao C# está disponível apenas para execução no seu computador usando seu próprio ambiente de desenvolvimento local e o .NET Core.
Você compilará um aplicativo de console e verá os recursos básicos orientados para objeto que fazem parte da linguagem C#.
