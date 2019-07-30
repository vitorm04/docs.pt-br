---
title: 'Exceções: A expressão try...with'
description: Saiba como usar o F# ' Try... expressão with para tratamento de exceção.
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630254"
---
# <a name="exceptions-the-trywith-expression"></a>Exceções: A expressão try...with

Este tópico descreve a `try...with` expressão, a expressão usada para manipulação de exceção no F# idioma.

## <a name="syntax"></a>Sintaxe

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>Comentários

A `try...with` expressão é usada para tratar exceções no F#. É semelhante à `try...catch` instrução em. C# Na sintaxe anterior, o código em *expression1* pode gerar uma exceção. A `try...with` expressão retorna um valor. Se nenhuma exceção for gerada, a expressão inteira retornará o valor de *expressão1*. Se uma exceção for lançada, cada *padrão* será comparado com a exceção, e para o primeiro padrão correspondente, a *expressão*correspondente, conhecida como o manipulador de *exceção*, para essa ramificação é executada e a expressão geral Retorna o valor da expressão nesse manipulador de exceção. Se nenhum padrão corresponder, a exceção propagará a pilha de chamadas até que um manipulador correspondente seja encontrado. Os tipos de valores retornados de cada expressão nos manipuladores de exceção devem corresponder ao tipo retornado da expressão no `try` bloco.

Frequentemente, o fato de que ocorreu um erro também significa que não há nenhum valor válido que possa ser retornado das expressões em cada manipulador de exceção. Um padrão frequente é fazer com que o tipo da expressão seja um tipo de opção. O exemplo de código a seguir ilustra esse padrão.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

As exceções podem ser exceções .NET ou podem ser F# exceções. Você pode definir F# exceções usando a `exception` palavra-chave.

Você pode usar uma variedade de padrões para filtrar o tipo de exceção e outras condições; as opções são resumidas na tabela a seguir.

|Padrão|Descrição|
|-------|-----------|
|:? *exception-type*|Corresponde ao tipo de exceção .NET especificado.|
|:? *tipo de exceção* como *identificador*|Corresponde ao tipo de exceção .NET especificado, mas dá à exceção um valor nomeado.|
|*nome da exceção* (*argumentos*)|Corresponde a F# um tipo de exceção e associa os argumentos.|
|*identifier*|Faz a correspondência de qualquer exceção e associa o nome ao objeto de exceção. Equivalente a **:? System. Exception como**_identificador_|
|*identificador* quando *condição*|Corresponde a qualquer exceção se a condição for verdadeira.|

## <a name="examples"></a>Exemplos

Os exemplos de código a seguir ilustram o uso dos vários padrões de manipulador de exceção.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> A `try...with` construção é uma expressão separada `try...finally` da expressão. Portanto, se o seu código exigir um `with` bloco e um `finally` bloco, você terá que aninhar as duas expressões.

> [!NOTE]
> Você pode usar `try...with` em fluxos de trabalho assíncronos e outras expressões de computação, caso em que uma versão `try...with` personalizada da expressão é usada. Para obter mais informações, consulte [fluxos de trabalho assíncronos](../asynchronous-workflows.md)e expressões de [computação](../computation-expressions.md).

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Tipos de Exceção](exception-types.md)
- [Exceções: A `try...finally` expressão](the-try-finally-expression.md)
