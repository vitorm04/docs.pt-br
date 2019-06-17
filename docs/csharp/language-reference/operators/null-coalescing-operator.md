---
title: ?? Operador – referência do C#
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 8ca97261b348b7813ab179abbc1f2c5f535966a1
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816015"
---
# <a name="-operator-c-reference"></a>?? operator (Referência de C#)

O operador de coalescência nula `??` retornará o valor do operando esquerdo se não for `null`; caso contrário, ele avaliará o operando direito e retornará seu resultado. O operador `??` não avaliará seu operando direito se o operando esquerdo for avaliado como não nulo.

O operador de coalescência nula é associativo direito, ou seja, uma expressão do formulário

```csharp
a ?? b ?? c
```

é avaliada como

```csharp
a ?? (b ?? c)
```

O operador `??` pode ser útil nos seguintes cenários:

- Em expressões com os [operadores condicionais nulos ?. e ?[]](member-access-operators.md#null-conditional-operators--and-), você pode usar o operador de coalescência nula para fornecer uma expressão alternativa a ser avaliada caso o resultado da expressão com operação condicional nula seja `null`:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- Quando você trabalhar com [tipos que permitem valor nulo](../../programming-guide/nullable-types/index.md) e precisar fornecer o valor de um tipo subjacente, use o operador de coalescência nula para especificar o valor a ser fornecido caso o tipo que permite valor nulo seja `null`:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> se o valor a ser usado quando um valor de tipo que permite valor nulo for `null` tiver que ser o valor padrão do tipo de valor subjacente.

- A partir do C# 7.0, você pode usar uma expressão [`throw` ](../keywords/throw.md#the-throw-expression) como o operando direito do operador de coalescência nula para tornar o código de verificação de argumento mais conciso:

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  O exemplo anterior também demonstra como usar [membros aptos para expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) para definir uma propriedade.

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

O operador de coalescência nula não pode ser sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira a seção [O operador coalescente nulo](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Operadores ?. e ?[]](member-access-operators.md#null-conditional-operators--and-)
- [Operador ?:](conditional-operator.md)
