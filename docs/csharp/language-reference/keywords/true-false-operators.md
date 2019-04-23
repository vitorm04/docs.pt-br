---
title: Operadores true e false – Referência de C#
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 869eeab6515340b2f1884ab7206979e83654a10b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328238"
---
# <a name="true-and-false-operators-c-reference"></a>Operadores true e false (Referência de C#)

O operador `true` retorna o valor [bool](bool.md) `true` para indicar que um operando é definitivamente true. O operador `false` retorna o valor `bool` `true` para indicar que um operando é definitivamente false. Não há garantia de que os operadores `true` e `false` se complementarão. Ou seja, ambos os operadores `true` e `false` podem retornar o valor `bool` `false` para o mesmo operando. Se um tipo define um dos dois operadores, ele também deve definir outro operador.

Se um tipo com os operadores `true` e `false` definidos [sobrecarregar](operator.md) o [operador OR lógico](../operators/boolean-logical-operators.md#logical-or-operator-) `|` ou o [operador AND lógico](../operators/boolean-logical-operators.md#logical-and-operator-) `&` de uma determinada maneira, o [operador OR lógico condicional](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) `||` ou [operador AND lógico condicional](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, respectivamente, poderá ser avaliado para os operandos desse tipo. Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).

Um tipo com o operador `true` definido pode ser o tipo de resultado de uma expressão condicional de controle nas instruções [if](if-else.md), [do](do.md), [while](while.md) e [for](for.md) e no [operador condicional `?:` ](../operators/conditional-operator.md). Para saber mais, confira a seção [Expressões boolianas](~/_csharplang/spec/expressions.md#boolean-expressions) da [Especificação da linguagem C#](../language-specification/index.md).

> [!TIP]
> Use o tipo `bool?`, se você precisar oferecer suporte à lógica de três valores, por exemplo, ao trabalhar com bancos de dados que dão suporte a um tipo booliano de três valores. C# fornece os operadores `&` e `|` que suportam a lógica de três valores com os operandos `bool?`. Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../operators/boolean-logical-operators.md).

O exemplo a seguir apresenta o tipo que define os dois operadores, `true` e `false`. Além disso, ele sobrecarrega o operador AND lógico `&` de uma forma que o operador `&&` também possa ser avaliado para os operandos desse tipo.

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

Observe o comportamento de curto-circuito do operador `&&`. Quando o método `GetFuelLaunchStatus` retorna `LaunchStatus.Red`, o segundo operando do operador `&&` não é avaliado. Isso ocorre porque `LaunchStatus.Red` é, definitivamente, false. Depois, o resultado do AND lógico não depende do valor do segundo operando. A saída do exemplo é a seguinte:

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave C#](index.md)
- [Operadores em C#](../operators/index.md)
- [`true` literal](true-literal.md)
- [`false` literal](false-literal.md)