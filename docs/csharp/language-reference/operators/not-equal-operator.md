---
title: Operador != – Referência de C#
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 939b5664dba4345e62a43fb2f8d4d5379659d6aa
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610171"
---
# <a name="-operator-c-reference"></a>Operador != (Referência de C#)

O operador de desigualdade `!=` retornará `true` se seus operandos não forem iguais; caso contrário, `false`. No caso dos operandos de [tipos internos](../keywords/built-in-types-table.md), a expressão `x != y` gera o mesmo resultado que a expressão `!(x == y)`. Para obter mais informações, consulte o artigo [Operador ==](equality-comparison-operator.md).

O exemplo a seguir demonstra o uso do operador `!=`:

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `!=`. Se um tipo sobrecarregar o operador de desigualdade `!=`, ele também sobrecarregará o [operador de igualdade](equality-comparison-operator.md) `==`.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Comparações de igualdade](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
