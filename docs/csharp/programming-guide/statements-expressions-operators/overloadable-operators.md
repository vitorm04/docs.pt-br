---
title: Operadores sobrecarregáveis – Guia de Programação em C#
ms.custom: seodec18
ms.date: 08/27/2018
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: 63079569050a70f551887dae837e012044984f85
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306938"
---
# <a name="overloadable-operators-c-programming-guide"></a>Operadores sobrecarregáveis (Guia de Programação em C#)

O C# permite que tipos definidos pelo usuário sobrecarreguem operadores definindo funções de membro estático usando a palavra-chave [operator](../../language-reference/keywords/operator.md). No entanto, nem todos os operadores podem ser sobrecarregados e outros têm restrições, conforme listado nesta tabela:

| Operadores | Capacidade de sobrecarga |
| --------- | --------------- |
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [!](../../language-reference/operators/boolean-logical-operators.md#logical-negation-operator-), [~](../../language-reference/operators/bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](../../language-reference/operators/arithmetic-operators.md#increment-operator-), [--](../../language-reference/operators/arithmetic-operators.md#decrement-operator---), [true](../../language-reference/operators/true-false-operators.md), [false](../../language-reference/operators/true-false-operators.md)|Esses operadores unários podem ser sobrecarregados.|
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [\*](../../language-reference/operators/arithmetic-operators.md#multiplication-operator-), [/](../../language-reference/operators/arithmetic-operators.md#division-operator-), [%](../../language-reference/operators/arithmetic-operators.md#remainder-operator-), [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-), [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-), [^](../../language-reference/operators/boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](../../language-reference/operators/bitwise-and-shift-operators.md#left-shift-operator-), [>>](../../language-reference/operators/bitwise-and-shift-operators.md#right-shift-operator-)|Esses operadores binários podem ser sobrecarregados.|
|[==](../../language-reference/operators/equality-operators.md#equality-operator-), [!=](../../language-reference/operators/equality-operators.md#inequality-operator-), [\<](../../language-reference/operators/comparison-operators.md#less-than-operator-), [>](../../language-reference/operators/comparison-operators.md#greater-than-operator-), [\<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-), [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-)|Operadores de comparação podem ser sobrecarregados (consulte a observação após esta tabela).|
|[&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)|Os operadores lógicos condicionais não podem ser sobrecarregados, mas são avaliados usando `&` e <code>&#124;</code>, que podem ser sobrecarregados.|
|[&#91;&#93;](../../language-reference/operators/member-access-operators.md#indexer-operator-)|O operador de indexação de matriz não pode ser sobrecarregado, mas você pode definir [indexadores](../indexers/index.md).|
|[(T)x](../../language-reference/operators/type-testing-and-conversion-operators.md#cast-operator-)|O operador de conversão não pode ser sobrecarregado, mas você pode definir novos operadores de conversão (consulte [explicit](../../language-reference/keywords/explicit.md) e [implicit](../../language-reference/keywords/implicit.md)).|
|[+=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [-=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [\*=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [/=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [%=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [&=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [&#124;=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [^=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [\<\<=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment), [>>=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment)|Operadores de atribuição não podem ser sobrecarregados explicitamente. No entanto, quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado. Por exemplo, `+=` é avaliado usando `+`, que pode ser sobrecarregado.|
|[=](../../language-reference/operators/assignment-operator.md), [.](../../language-reference/operators/member-access-operators.md#member-access-operator-), [?:](../../language-reference/operators/conditional-operator.md), [??](../../language-reference/operators/null-coalescing-operator.md), [->](../../language-reference/operators/pointer-related-operators.md#pointer-member-access-operator--), [=>](../../language-reference/operators/lambda-operator.md), [f(x)](../../language-reference/operators/member-access-operators.md#invocation-operator-), [as](../../language-reference/operators/type-testing-and-conversion-operators.md#as-operator), [checked](../../language-reference/keywords/checked.md), [unchecked](../../language-reference/keywords/unchecked.md), [default](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [is](../../language-reference/operators/type-testing-and-conversion-operators.md#is-operator), [new](../../language-reference/keywords/new.md), [sizeof](../../language-reference/keywords/sizeof.md), [typeof](../../language-reference/operators/type-testing-and-conversion-operators.md#typeof-operator)|Esses operadores não podem ser sobrecarregados.|

> [!NOTE]
> Os operadores de comparação, se sobrecarregados, devem ser sobrecarregados em pares. Ou seja, se `==` for sobrecarregado, `!=` também deve ser sobrecarregado. O contrário também é verdadeiro, no qual sobrecarregar `!=` requer uma sobrecarga para `==`. O mesmo vale para os operadores de comparação `<` e `>` e para `<=` e `>=`.

Para obter informações sobre como sobrecarregar um operador, consulte o artigo da palavra-chave [operador](../../language-reference/keywords/operator.md).

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Instruções, expressões e operadores](index.md)
- [Operadores](operators.md)
- [Operadores do C#](../../language-reference/operators/index.md)
- [Por que os operadores sobrecarregados sempre são estáticos em C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
