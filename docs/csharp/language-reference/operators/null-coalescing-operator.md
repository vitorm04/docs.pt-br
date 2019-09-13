---
title: ?? e?? = operadores- C# referência
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 1e94038a41a6a6cc19be6c67bff2891397793fb3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924688"
---
# <a name="-and--operators-c-reference"></a>?? e?? = OperatorsC# (referência)

O operador de coalescência nula `??` retornará o valor do operando esquerdo se não for `null`; caso contrário, ele avaliará o operando direito e retornará seu resultado. O operador `??` não avaliará seu operando direito se o operando esquerdo for avaliado como não nulo.

Disponível no C# 8,0 e posterior, o operador `??=` de atribuição de União nula atribui o valor de seu operando à direita para seu operando à esquerda somente se o operando esquerdo for avaliado como. `null` O operador `??=` não avaliará seu operando direito se o operando esquerdo for avaliado como não nulo.

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

O operando da esquerda do `??=` operador deve ser uma variável, uma [Propriedade](../../programming-guide/classes-and-structs/properties.md)ou um elemento do [indexador](../../programming-guide/indexers/index.md) . Para obter mais informações sobre a atribuição de União nula, consulte a [Nota de proposta de recurso](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

Em C# 7,3 e anterior, o tipo do operando à esquerda do `??` operador deve ser um tipo de referência ou um tipo de [valor anulável](../../programming-guide/nullable-types/index.md). A partir C# do 8,0, esse requisito é substituído pelo seguinte: o tipo do operando à esquerda dos `??` operadores e `??=` não pode ser um tipo de valor não anulável. Em particular, você pode usar os operadores de União nulo com parâmetros de tipo irrestrito no C# 8,0 e posterior:

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

Os operadores de União nulos são associativos à direita. Ou seja, expressões do formulário

```csharp
a ?? b ?? c
d ??= e ??= f
```

são avaliados como

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a>Exemplos

Os `??` operadores `??=` e podem ser úteis nos seguintes cenários:

- Em expressões com os [operadores condicionais nulos ?. e ?[]](member-access-operators.md#null-conditional-operators--and-), você pode usar o operador de coalescência nula para fornecer uma expressão alternativa a ser avaliada caso o resultado da expressão com operação condicional nula seja `null`:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- Quando você trabalhar com [tipos que permitem valor nulo](../../programming-guide/nullable-types/index.md) e precisar fornecer o valor de um tipo subjacente, use o operador de coalescência nula para especificar o valor a ser fornecido caso o tipo que permite valor nulo seja `null`:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> se o valor a ser usado quando um valor de tipo que permite valor nulo for `null` tiver que ser o valor padrão do tipo de valor subjacente.

- A partir do C# 7.0, você pode usar uma expressão [`throw` ](../keywords/throw.md#the-throw-expression) como o operando direito do operador de coalescência nula para tornar o código de verificação de argumento mais conciso:

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  O exemplo anterior também demonstra como usar [membros aptos para expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) para definir uma propriedade.

- A partir C# do 8,0, você pode usar `??=` o operador para substituir o código do formulário

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  com o código a seguir:

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Os operadores `??` e `??=` não podem ser sobrecarregados.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações sobre `??` o operador, consulte [a seção operador de União nula](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) da [ C# especificação da linguagem](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Operadores ?. e ?[]](member-access-operators.md#null-conditional-operators--and-)
- [Operador ?:](conditional-operator.md)
