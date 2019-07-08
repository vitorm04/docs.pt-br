---
title: Sobrecarga de Operador – referência de C#
description: Saiba como sobrecarregar um operador C# e quais operadores C# podem ser sobrecarregados.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: f9085f2a550dfacc670857a70f5b22de9e028107
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610589"
---
# <a name="operator-overloading-c-reference"></a>Sobrecarga de operador (referência de C#)

Um tipo definido pelo usuário pode sobrecarregar um operador C# predefinido. Ou seja, um tipo pode fornecer a implementação personalizada de uma operação quando um ou ambos os operandos são desse mesmo tipo. A seção [Operadores sobrecarregáveis](#overloadable-operators) mostra quais operadores do C# podem ser sobrecarregados.

Use a palavra-chave `operator` para declarar um operador. Uma declaração de operador deve satisfazer as regras a seguir:

- Ela inclui os modificadores `public` e `static`.
- Um operador unário assume um parâmetro. Um operador binário assume dois parâmetros. Em cada caso, pelo menos um parâmetro deve ter o tipo `T` ou `T?`, em que `T` é o tipo que contém a declaração do operador.

O exemplo a seguir define uma estrutura simplificada para representar um número racional. A estrutura sobrecarrega alguns dos [operadores aritméticos](arithmetic-operators.md):

[!code-csharp[fraction example](~/samples/csharp/language-reference/operators/OperatorOverloading.cs)]

## <a name="overloadable-operators"></a>Operadores sobrecarregáveis

A tabela a seguir fornece informações sobre capacidade de sobrecarga de operadores do C#:

| Operadores | Capacidade de sobrecarga |
| --------- | --------------- |
|[+](arithmetic-operators.md#unary-plus-and-minus-operators), [-](arithmetic-operators.md#unary-plus-and-minus-operators), [!](boolean-logical-operators.md#logical-negation-operator-), [~](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---), [true](true-false-operators.md), [false](true-false-operators.md)|Esses operadores unários podem ser sobrecarregados.|
|[+](addition-operator.md), [-](subtraction-operator.md), [\*](arithmetic-operators.md#multiplication-operator-), [/](arithmetic-operators.md#division-operator-), [%](arithmetic-operators.md#remainder-operator-), [&](boolean-logical-operators.md#logical-and-operator-), [&#124;](boolean-logical-operators.md#logical-or-operator-), [^](boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](bitwise-and-shift-operators.md#left-shift-operator-), [>>](bitwise-and-shift-operators.md#right-shift-operator-), [==](equality-operators.md#equality-operator-), [!=](equality-operators.md#inequality-operator-), [\<](comparison-operators.md#less-than-operator-), [>](comparison-operators.md#greater-than-operator-), [\<=](comparison-operators.md#less-than-or-equal-operator-), [>=](comparison-operators.md#greater-than-or-equal-operator-)|Esses operadores binários podem ser sobrecarregados. Determinados operadores devem ser sobrecarregados em pares; para obter mais informações, consulte a observação após esta tabela.|
|[&&](boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](boolean-logical-operators.md#conditional-logical-or-operator-)|Operadores lógicos condicionais não podem ser sobrecarregados. No entanto, se um tipo definido com os [operadores `true` e `false`](true-false-operators.md) sobrecarregados também sobrecarrega o operador `&` ou o operador <code>&#124;</code> de uma determinada maneira, o operador `&&` ou o operador <code>&#124;&#124;</code>, respectivamente, podem ser avaliados para os operandos desse tipo. Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).|
|[&#91;&#93;](member-access-operators.md#indexer-operator-)|O acesso de elemento não é considerado um operador que pode ser sobrecarregado, mas você pode definir um [indexador](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-conversion-operators.md#cast-operator-)|O operador de conversão não pode ser sobrecarregado, mas você pode definir novos operadores de conversão (consulte [explicit](../keywords/explicit.md) e [implicit](../keywords/implicit.md)).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Operadores de atribuição compostos não podem ser sobrecarregados explicitamente. No entanto, quando um operador binário estiver sobrecarregado, o operador de atribuição composto correspondente, se houver, também estará implicitamente sobrecarregado. Por exemplo, `+=` é avaliado usando `+`, que pode ser sobrecarregado.|
|[=](assignment-operator.md), [.](member-access-operators.md#member-access-operator-), [?:](conditional-operator.md), [??](null-coalescing-operator.md), [->](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md), [f(x)](member-access-operators.md#invocation-operator-), [as](type-testing-and-conversion-operators.md#as-operator), [checked](../keywords/checked.md), [unchecked](../keywords/unchecked.md), [default](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [is](type-testing-and-conversion-operators.md#is-operator), [nameof](../keywords/nameof.md), [new](new-operator.md), [sizeof](../keywords/sizeof.md), [typeof](type-testing-and-conversion-operators.md#typeof-operator)|Esses operadores não podem ser sobrecarregados.|

> [!NOTE]
> Os operadores de comparação precisam ser sobrecarregados em pares. Ou seja, se o operador de um par está sobrecarregado, o outro operador precisa estar sobrecarregado também. Esses pares são os seguintes:
>
> - Operadores `==` e `!=`
> - Operadores `<` e `>`
> - Operadores `<=` e `>=`

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Sobrecarga de operador](~/_csharplang/spec/expressions.md#operator-overloading)
- [Operadores](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Por que os operadores sobrecarregados sempre são estáticos em C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
