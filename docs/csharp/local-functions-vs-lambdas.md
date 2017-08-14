---
title: "Funções locais vs. expressões lambda"
description: "Saiba porque as funções locais podem ser uma escolha melhor que as expressões lambda."
keywords: "C#, .NET, .NET Core, Últimos Recursos, Novidades, funções locais, expressões lambda"
author: BillWagner
ms.author: wiwagn
ms.date: 06/27/2016
ms.topic: article
ms.prod: visual-studio-dev-15
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.translationtype: HT
ms.sourcegitcommit: a7eda5cde2998bfb2b6a609a4ffc90019ab57a7c
ms.openlocfilehash: 4cace9b5549b2d8c08c993e7c22e5f1b5fc8a9c3
ms.contentlocale: pt-br
ms.lasthandoff: 08/01/2017

---

### <a name="local-functions-compared-to-lambda-expressions"></a>Funções locais comparadas com expressões lambda

À primeira vista, [funções locais](programming-guide/classes-and/structs/local-functions.md) e [expressões lambda](lambda-expressions.md) são muito semelhantes.
Dependendo de suas necessidades, funções locais podem ser uma solução muito melhor e mais simples.

Examinaremos as diferenças entre a função local e as implementações de expressão lambda do algoritmo fatorial. Primeiro a versão usando uma função local:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Fatorial recursiva usando a função local")]

Compare essa implementação com uma versão que usa expressões lambda:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Fatorial recursiva usando expressões lambda")]

Primeiro, as expressões lambda são implementadas instanciando um delegado e invocando esse delegado. As funções locais são implementadas como chamadas de método.
A instanciação necessária para expressões lambda significa alocações de memória extra, o que podem ser um fator de desempenho em caminhos de código crítico de tempo.
As funções locais não incorrem nessa sobrecarga. No exemplo acima, a versão das funções locais tem 2 alocações a menos que a versão da expressão lambda.

Esse método recursivo é simples o suficiente para que a função local seja implementada como um método privado com um nome gerado pelo compilador. A única diferença de outros métodos privados é que ele é semanticamente delimitado dentro da função externa.

Segundo, as funções locais podem ser chamadas antes de serem definidas. As expressões lambda devem ser declaradas antes de serem definidas. Isso significa que funções locais são mais fáceis de usar em algoritmos recursivos, conforme mostrado acima.

Observe que a versão usando a expressão lambda deve declarar e inicializar a expressão lambda, `nthFactorial` antes de defini-la. Não fazer isso resulta em um erro em tempo de compilação para referenciar `nthFactorial` antes de atribuí-lo.
Os algoritmos recursivos são mais fáceis de criar usando funções locais.

Terceiro, para as expressões lambda, o compilador deve sempre criar uma classe anônima e uma instância dessa classe para armazenar todas as variáveis capturadas pelo fechamento. Considere este exemplo assíncrono:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Método de retorno de tarefa com uma expressão lambda")]

O fechamento desta expressão lambda contém as variáveis `address`, `index` e `name`. No caso de funções locais, o objeto que implementa o encerramento pode ser um tipo `struct`. Isso poderia gerar economia em uma alocação.

> [!NOTE]
> A função local equivalente desse método também usa uma classe para o fechamento. O fechamento de uma função local ser implementado como um `class` ou como um `struct`, trata-se de um detalhe de implementação. Uma função local pode usar um `struct`, enquanto uma lambda sempre usará um `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Método de retorno de tarefa com função local")]

Uma vantagem final não demonstrada neste exemplo é que as funções locais podem ser implementadas como iteradores, usando a sintaxe `yield return` para produzir uma sequência de valores.

Embora as funções locais possam parecer redundantes para expressões lambda, elas realmente têm finalidades e usos diferentes.
As funções locais são mais eficientes para quando você deseja escrever uma função que é chamada apenas do contexto de outro método.

