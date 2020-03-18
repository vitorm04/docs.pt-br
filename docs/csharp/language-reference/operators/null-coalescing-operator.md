---
title: ?? E?? = operadores - Referência C#
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
ms.openlocfilehash: 69294f0fb706868b48b8d7fe8b95fa345af169b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847307"
---
# <a name="-and--operators-c-reference"></a>?? E?? = operadores (referência C#)

O operador de coalescência nula `??` retornará o valor do operando esquerdo se não for `null`; caso contrário, ele avaliará o operando direito e retornará seu resultado. O operador `??` não avaliará seu operando direito se o operando esquerdo for avaliado como não nulo.

Disponível em C# 8.0 e posteriormente, o `??=` operador de atribuição de coalizão nula atribui o valor de seu oper direito e `null`ao seu oper esquerdo e somente se o oper e a mão esquerda avaliar para . O operador `??=` não avaliará seu operando direito se o operando esquerdo for avaliado como não nulo.

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

O operand esquerdo do `??=` operador deve ser uma variável, uma [propriedade](../../programming-guide/classes-and-structs/properties.md)ou um elemento [indexador.](../../programming-guide/indexers/index.md)

Em C# 7.3 e anteriormente, o tipo de `??` operador à esquerda do operador deve ser um [tipo](../keywords/reference-types.md) de referência ou um [tipo de valor anulado](../builtin-types/nullable-value-types.md). A partir de C# 8.0, essa exigência é substituída pelo seguinte: o `??` tipo `??=` de operador à esquerda dos operadores e operadores não pode ser um tipo de valor não anulado. Em particular, começando com C# 8.0, você pode usar os operadores de coalizão nula com parâmetros de tipo não restritos:

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

Os operadores de coalizão nula são associativos. Ou seja, expressões da forma

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

Os `??` `??=` operadores e operadores podem ser úteis nos seguintes cenários:

- Em expressões com os [operadores condicionais nulos ?. e ?[]](member-access-operators.md#null-conditional-operators--and-), você pode usar o `??` operador para fornecer uma `null`expressão alternativa para avaliar caso o resultado da expressão com operações condicionais nulas seja:

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- Quando você trabalha com [tipos de valor anulados](../builtin-types/nullable-value-types.md) e precisa fornecer `??` um valor de um tipo de valor subjacente, use o operador para especificar o valor a fornecer no caso de um valor de tipo anulado ser: `null`

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  Use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> se o valor a ser usado quando um valor de tipo que permite valor nulo for `null` tiver que ser o valor padrão do tipo de valor subjacente.

- Começando com C# 7.0, [ `throw` ](../keywords/throw.md#the-throw-expression) você pode usar uma expressão como `??` operand direito do operador para tornar o código de verificação de argumentos mais conciso:

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  O exemplo anterior também demonstra como usar [membros aptos para expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) para definir uma propriedade.

- Começando com C# 8.0, `??=` você pode usar o operador para substituir o código do formulário

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  pelo código a seguir:

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Os `??` operadores `??=` e não podem ser sobrecarregados.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais `??` informações sobre o operador, consulte A seção de operador de [coalizão nula](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) da [especificação do idioma C#.](~/_csharplang/spec/introduction.md)

Para obter mais `??=` informações sobre o operador, consulte a [nota de proposta do recurso](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
- [Operadores ?. e ?[]](member-access-operators.md#null-conditional-operators--and-)
- [?: operador](conditional-operator.md)
