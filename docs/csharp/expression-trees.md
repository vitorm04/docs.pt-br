---
title: "Árvores de expressão"
description: "Saiba mais sobre árvores de expressão no .NET Core e como usá-las para representar o código como estruturas que você pode examinar, modificar e executar."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: 3935906d9fca81a094999eefdd49ae4ed56990bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="expression-trees"></a>Árvores de expressão

Se tiver usado o LINQ, você tem experiência com uma rica biblioteca em que os tipos `Func` fazem parte do conjunto de API. (Se não estiver familiarizado com o LINQ, você provavelmente deveria ler o [tutorial do LINQ](linq/index.md) e o tutorial sobre [expressões lambda](lambda-expressions.md) antes deste.) *Árvores de expressão* fornecem uma interação mais avançada com os argumentos que são funções.

Você escreve argumentos de função, normalmente usando expressões lambda, quando cria consultas LINQ. Em uma consulta LINQ típica, esses argumentos de função são transformados em um delegado que o compilador cria. 

Quando quiser ter uma interação mais avançada, você precisa usar *Árvores de expressão*.
Árvores de expressão representam o código como uma estrutura que você pode examinar, modificar ou executar. Essas ferramentas oferecem a capacidade de manipular o código em tempo de execução. Você pode escrever código que examina algoritmos em execução ou injeta novos recursos. Em cenários mais avançados, você pode modificar algoritmos em execução e até mesmo converter expressões C# para outro formato para execução em outro ambiente.

Provavelmente, você já escreveu código usando Árvores de expressão. APIs do LINQ do Entity Framework aceitam Árvores de expressão como os argumentos para o padrão de expressão de consulta do LINQ.
Isso permite que o [Entity Framework](http://docs.efproject.net/en/latest/) converta a consulta que você escreveu em C# em SQL, que é executado no mecanismo do banco de dados. Outro exemplo é [Moq](https://github.com/Moq/moq), que é uma estrutura de simulação popular para .NET.

As seções restantes deste tutorial explorarão o que são as árvores de expressão, examinarão as classes de estrutura que dão suporte a árvores de expressão e mostrarão como trabalhar com árvores de expressão. Você aprenderá a ler árvores de expressão, criar árvores de expressão, criar árvores de expressão modificadas e executar o código representado pelas árvores de expressão. Após a leitura, você estará pronto para usar essas estruturas para criar algoritmos adaptáveis avançados.

1. [Árvores de Expressão Explicadas](expression-trees-explained.md)

    Compreender a estrutura e os conceitos por trás das *Árvores de Expressão*.
    
2. [Tipos de Framework com Suporte a Árvores de Expressão](expression-classes.md)
    
    Saiba mais sobre as estruturas e classes que definem e manipulam as árvores de expressão.
    
3. [Executando Expressões](expression-trees-execution.md)

    Saiba como converter uma árvore de expressão representada como uma expressão lambda em um delegado e como executar o delegado resultante.

4. [Interpretando Expressões](expression-trees-interpreting.md)

    Saiba como percorrer e examinar *árvores de expressão* para entender que código a árvore de expressão representa.

5. [Compilando Expressões](expression-trees-building.md)

    Saiba como construir os nós de uma árvore de expressão e compilar árvores de expressão.

6. [Traduzindo Expressões](expression-trees-translating.md)

    Saiba como compilar uma cópia modificada de uma árvore de expressão ou converter uma árvore de expressão em um formato diferente.

7. [Resumindo](expression-trees-summary.md)

    Examine informações sobre as árvores de expressão.
    
