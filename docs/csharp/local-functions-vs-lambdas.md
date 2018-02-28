---
title: "Funções locais vs. expressões lambda"
description: "Saiba porque as funções locais podem ser uma escolha melhor que as expressões lambda."
keywords: "C#, .NET, .NET Core, Últimos Recursos, Novidades, funções locais, expressões lambda"
author: BillWagner
ms.author: wiwagn
ms.date: 06/27/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 5aa097c19a86e9ae62a37d91fb1b54067280286d
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Funções locais comparadas com expressões lambda

À primeira vista, [funções locais](programming-guide/classes-and-structs/local-functions.md) e [expressões lambda](lambda-expressions.md) são muito semelhantes. Em muitos casos, a escolha entre usar expressões lambda e funções locais é uma questão de estilo e preferência pessoal. No entanto, há diferenças reais nos casos em que você pode usar uma ou outra, e é importante conhecer essas diferenças.

Examinaremos as diferenças entre a função local e as implementações de expressão lambda do algoritmo fatorial. Primeiro a versão usando uma função local:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Compare essa implementação com uma versão que usa expressões lambda:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

As funções locais têm nomes. As expressões lambda são métodos anônimos que são atribuídos a variáveis dos tipos `Func` ou `Action`. Quando você declara uma função local, os tipos de argumento e o tipo de retorno fazem parte da declaração da função. Em vez de fazer parte do corpo da expressão lambda, os tipos de argumento e o tipo de retorno são parte da declaração de tipo de variável da expressão lambda. Essas duas diferenças podem resultar em um código mais claro.

As funções locais têm diferentes regras para atribuição definida em relação às expressões lambda. Uma declaração de função local pode ser referenciada em qualquer local do código em que ela esteja no escopo. Uma expressão lambda deve ser atribuída a uma variável delegada antes de ser acessada (ou chamada por meio do delegado que faz referência à expressão lambda). Observe que a versão usando a expressão lambda deve declarar e inicializar a expressão lambda, `nthFactorial` antes de defini-la. Não fazer isso resulta em um erro em tempo de compilação para referenciar `nthFactorial` antes de atribuí-lo.
Essas diferenças significam que os algoritmos recursivos são mais fáceis de criar usando funções locais. Você pode declarar e definir uma função local que chame a si mesma. As expressões lambda devem ser declaradas e atribuídas a um valor padrão antes que possam ser reatribuídas a um corpo que referencie a mesma expressão lambda.

As regras de atribuição definidas também afetam as variáveis que são capturadas pela função local ou expressão lambda. As regras das funções locais e das expressões lambda exigem que as variáveis capturadas sejam definitivamente atribuídas no momento em que a expressão lambda ou a função local é convertida em um delegado. A diferença é que as expressões lambda são convertidas em delegados no momento em que são declaradas. As funções locais são convertidas em delegados somente quando usadas como um delegado. Se você declarar uma função local e só referenciá-la ao chamá-la como um método, ela não será convertida em um delegado. Essa regra permite que você declare uma função local em qualquer local conveniente no respectivo escopo delimitador. É comum declarar funções locais ao final do método pai, depois das instruções de retorno.

Em terceiro lugar, o compilador pode executar uma análise estática que permite que as funções locais atribuam definitivamente as variáveis capturadas no escopo delimitador. Considere este exemplo:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

O compilador pode determinar que `LocalFunction` definitivamente atribua `y` quando chamada. Como `LocalFunction` é chamada antes da instrução `return`, `y` é atribuído definitivamente na instrução `return`.

Essa análise de exemplo permite a quarta diferença.
Dependendo do uso, as funções locais podem evitar as alocações de heap que são sempre necessárias nas expressões lambda. Se uma função local nunca é convertida em um delegado, e nenhuma das variáveis capturadas pela função local é capturada por outros lambdas ou funções locais que são convertidas em delegados, o compilador pode evitar alocações de heap. 

Considere este exemplo assíncrono:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

O fechamento desta expressão lambda contém as variáveis `address`, `index` e `name`. No caso de funções locais, o objeto que implementa o encerramento pode ser um tipo `struct`. Esse tipo de struct seria passado por referência à função local. Essa diferença na implementação poderia economizar em uma alocação.

A instanciação necessária para expressões lambda ocasiona alocações adicionais de memória, tornando-se um fator de desempenho em caminhos de código com tempo crítico.
As funções locais não incorrem nessa sobrecarga. No exemplo acima, a versão das funções locais tem 2 alocações a menos que a versão da expressão lambda.

> [!NOTE]
> A função local equivalente desse método também usa uma classe para o fechamento. O fechamento de uma função local ser implementado como um `class` ou como um `struct`, trata-se de um detalhe de implementação. Uma função local pode usar um `struct`, enquanto uma lambda sempre usará um `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

Uma vantagem final não demonstrada neste exemplo é que as funções locais podem ser implementadas como iteradores, usando a sintaxe `yield return` para produzir uma sequência de valores. A instrução `yield return` não é permitida em expressões lambda.

Embora as funções locais possam parecer redundantes para expressões lambda, elas realmente têm finalidades e usos diferentes.
As funções locais são mais eficientes para quando você deseja escrever uma função que é chamada apenas do contexto de outro método.
