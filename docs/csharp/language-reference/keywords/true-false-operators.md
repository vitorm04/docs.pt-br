---
title: Operadores true e false – Referência de C#
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 0a75566fdb6222157ecda12a50fd78e22f92fcb4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245727"
---
# <a name="true-and-false-operators-c-reference"></a>Operadores true e false (Referência de C#)

O operador `true` retorna o valor [bool](bool.md) `true` para indicar que um operando é definitivamente true. O operador `false` retorna o valor `bool` `true` para indicar que um operando é definitivamente false. Não há garantia de que os operadores `true` e `false` se complementarão. Ou seja, ambos os operadores `true` e `false` podem retornar o valor `bool` `false` para o mesmo operando. Se um tipo define um dos dois operadores, ele também deve definir outro operador.

Se um tipo com os operadores `true` e `false` definidos [sobrecarregar](operator.md) o [operador OR lógico](../operators/or-operator.md) `|` ou o [operador AND lógico](../operators/and-operator.md) `&` de uma determinada maneira, o [operador OR lógico condicional](../operators/conditional-or-operator.md) `||` ou [operador AND lógico condicional](../operators/conditional-and-operator.md) `&&`, respectivamente, poderá ser avaliado para os operandos desse tipo. Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](../language-specification/index.md).

Um tipo com o operador `true` definido pode ser o tipo de resultado de uma expressão condicional de controle nas instruções [if](if-else.md), [do](do.md), [while](while.md) e [for](for.md) e no [operador condicional `?:` ](../operators/conditional-operator.md). Para saber mais, confira a seção [Expressões boolianas](~/_csharplang/spec/expressions.md#boolean-expressions) da [Especificação da linguagem C#](../language-specification/index.md).

> [!TIP]
> Use o tipo `bool?`, se você precisar oferecer suporte à lógica de três valores, por exemplo, ao trabalhar com bancos de dados que dão suporte a um tipo de lógico de três valores. Para saber mais, confira a seção [O tipo bool?](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) do artigo [Como usar tipos que permitem valor nulo](../../programming-guide/nullable-types/using-nullable-types.md).

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
- [Palavras-chave do C#](index.md)
- [Operadores do C#](../operators/index.md)
- [`true` literal](true-literal.md)
- [`false` literal](false-literal.md)