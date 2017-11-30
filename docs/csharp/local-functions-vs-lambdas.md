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
ms.openlocfilehash: 20312b58a24dc991791edad4bb92d3a8ca6d501a
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2017
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Funções locais em comparação comparadas expressões lambda

À primeira vista, [funções locais](programming-guide/classes-and-structs/local-functions.md) e [expressões lambda](lambda-expressions.md) são muito semelhantes. Em muitos casos, a escolha entre usar expressões lambda e funções de locais é uma questão de estilo e preferência pessoal. No entanto, há diferenças reais em onde você pode usar um ou outro que você deve estar atento.

Examinaremos as diferenças entre a função local e as implementações de expressão lambda do algoritmo fatorial. Primeiro a versão usando uma função local:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Compare essa implementação com uma versão que usa expressões lambda:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

As funções locais têm nomes. As expressões lambda são métodos anônimos que são atribuídos a variáveis que são `Func` ou `Action` tipos. Quando você declara uma função local, os tipos de argumento e o tipo de retorno são parte da declaração da função. Em vez de ser parte do corpo do lambda da expressão, os tipos de argumento e o tipo de retorno são parte da declaração de variável de tipo da expressão lambda. Essas duas diferenças podem resultar em código mais claro.

Funções locais têm diferentes regras de atribuição definida de expressões lambda. Uma declaração de função local pode ser referenciada de qualquer local de código onde ele está no escopo. Uma expressão lambda deve ser atribuída a uma variável de delegado antes que ele pode ser acessado (ou chamado por meio de delgate fazendo referência a expressão lambda.) Observe que a versão usando a expressão lambda deve declarar e inicializar a expressão lambda, `nthFactorial` antes de defini-la. Não fazer isso resulta em um erro em tempo de compilação para referenciar `nthFactorial` antes de atribuí-lo.
Essas diferenças significam que algoritmos recursivos são mais fáceis de criar usando funções locais. Você pode declarar e definir uma função local que chama a mesmo. Expressões lambda devem ser declaradas e atribuídas um valor padrão antes de poderem ser reatribuídas a um corpo que referencia a mesma expressão lambda.

As regras de atribuição definido também afetam todas as variáveis que são capturadas pelo epression local de função ou lamdba. Funções locais e as regras de expressões lambda exigem que todas as variáveis capturadas definitivamente são atribuídas no momento quando a expressão lambda ou de função local é convertida em um representante. A diferença é que as expressões lambda são convertidas em delegates quando eles são declarados. Funções locais são convertidas em delegates somente quando usado como um representante. Se você declara uma função local e só referenciá-lo chamando-o como um método, ele não será convertido em um representante. Essa regra permite que você declare uma função local em qualquer local conveniente em seu escopo delimitador. É comum para declarar funções locais no final do método pai, após as instruções de retorno.

Em terceiro lugar, o compilador pode executar uma análise estática que permite que funções locais definitivamente atribuir variáveis capturadas no escopo delimitador. Considere este exemplo:

```csharp
bool M()
{
    int y;
    Local();
    return y;

    void Local() => y = 0;
}
```

O compilador pode determinar que `Local` definitivamente atribui `y` quando chamado. Porque `Local` é chamado antes de `return` instrução, `y` definitiely que é atribuído ao `return` instrução.

A análise que permite que a análise permite que a diferença quarta.
Dependendo de seu uso, funções locais podem evitar as alocações de heap que sempre são necessárias para expressões lambda. Se uma função local nunca é convertida em um delegado, e nenhuma das variáveis capturadas pela função local é capturada por outros lambdas ou funções locais que são convertidas em delegates, o compilador pode evitar alocações de heap. 

Considere este exemplo assíncrono:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

O fechamento desta expressão lambda contém as variáveis `address`, `index` e `name`. No caso de funções locais, o objeto que implementa o encerramento pode ser um tipo `struct`. Esse tipo de struct seria passado por referência à função local. Essa diferença na implementação poderia economizar em uma alocação.

A instanciação necessária para expressões lambda significa que as alocações de memória extra, que podem ser um fator de desempenho em caminhos de código crítico em termos de tempo.
As funções locais não incorrem nessa sobrecarga. No exemplo acima, a versão das funções locais tem 2 alocações a menos que a versão da expressão lambda.

> [!NOTE]
> A função local equivalente desse método também usa uma classe para o fechamento. O fechamento de uma função local ser implementado como um `class` ou como um `struct`, trata-se de um detalhe de implementação. Uma função local pode usar um `struct`, enquanto uma lambda sempre usará um `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

Uma vantagem final não demonstrada neste exemplo é que as funções locais podem ser implementadas como iteradores, usando a sintaxe `yield return` para produzir uma sequência de valores. O `yield return` instrução não é permitida em expressões lambda.

Embora as funções locais possam parecer redundantes para expressões lambda, elas realmente têm finalidades e usos diferentes.
As funções locais são mais eficientes para quando você deseja escrever uma função que é chamada apenas do contexto de outro método.
