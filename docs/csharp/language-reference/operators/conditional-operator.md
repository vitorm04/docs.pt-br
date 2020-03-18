---
title: 'Operador ?: – referência do C#'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 1a17ba092d4228ba909c8774a2f7e15c2c50cfdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399514"
---
# <a name="-operator-c-reference"></a>Operador ?: (referência do C#)

O operador `?:`condicional , também conhecido como operador condicionário ternário, avalia uma expressão booleana e retorna o resultado de `true` `false`uma das duas expressões, dependendo se a expressão booleana avalia ou .

A sintaxe do operador condicional é a seguinte:

```csharp
condition ? consequent : alternative
```

A expressão `condition` deve ser avaliada para `true` ou `false`. Se `condition` for avaliada como `true`, a expressão `consequent` será avaliada e seu resultado se tornará o resultado da operação. Se `condition` for avaliada como `false`, a expressão `alternative` será avaliada e seu resultado se tornará o resultado da operação. Somente `consequent` ou `alternative` é avaliada.

O tipo de `consequent` e `alternative` devem ser iguais ou deve haver uma conversão implícita de um tipo para outro.

O operador condicional é associativo direito, ou seja, uma expressão da forma

```csharp
a ? b : c ? d : e
```

é avaliada como

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> Você pode usar o seguinte dispositivo mnemônico para se lembrar de como o operador condicional é avaliado:
>
> ```text
> is this condition true ? yes : no
> ```

O exemplo a seguir demonstra o uso do operador condicional:

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Expressão condicional ref

Começando com C# 7.2, uma variável [local ou](../keywords/ref.md#ref-locals) [ref readonly](../keywords/ref.md#ref-readonly-locals) pode ser atribuída condicionalmente com a expressão condicional do ref. Você também pode usar a expressão condicional do ref como um [valor de retorno de referência](../keywords/ref.md#reference-return-values) ou como um [ `ref` argumento de método](../keywords/ref.md#passing-an-argument-by-reference).

A sintaxe da expressão condicional ref é a seguinte:

```csharp
condition ? ref consequent : ref alternative
```

Como o operador condicional original, a expressão condicional ref avalia apenas uma das duas expressões: `consequent` ou `alternative`.

No caso da expressão condicional ref, o tipo de `consequent` e `alternative` devem ser iguais.

O exemplo a seguir demonstra o uso da expressão condicional ref:

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Operador condicional e uma instrução `if..else`

O uso do operador condicional em vez de uma declaração [if-else](../keywords/if-else.md) pode resultar em um código mais conciso nos casos em que você precisa de condicionalmente para calcular um valor. O exemplo a seguir demonstra duas maneiras de classificar um inteiro como negativo ou não negativo:

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Um tipo definido pelo usuário não pode sobrecarregar o operador condicional.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para saber mais, confira a seção [Operador condicional](~/_csharplang/spec/expressions.md#conditional-operator) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).

Para obter mais informações sobre a expressão condicional do árbitro, consulte a [nota de proposta do recurso](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
- [se-else declaração](../keywords/if-else.md)
- [Operadores ?. e ?[]](member-access-operators.md#null-conditional-operators--and-)
- [?? E?? = operadores](null-coalescing-operator.md)
- [ref keyword](../keywords/ref.md)
