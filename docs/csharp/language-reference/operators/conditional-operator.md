---
title: 'Operador ?: – referência do C#'
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 7397c5b2b2278f487a98b029b00924d3151913db
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036299"
---
# <a name="-operator-c-reference"></a>Operador ?: (referência do C#)

O operador condicional `?:`, também conhecido como operador condicional Ternário, avalia uma expressão booliana e retorna o resultado de uma das duas expressões, dependendo se a expressão booliana é avaliada como `true` ou `false`. Começando com C# 7.2, a [expressão de referência condicional](#conditional-ref-expression) retorna a referência ao resultado de uma de duas expressões.

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

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Expressão condicional ref

Começando com C# 7.2, use a expressão de referência condicional para retornar a referência ao resultado de uma de duas expressões. Você pode atribuir essa referência a uma variável [ref local](../keywords/ref.md#ref-locals) ou [ref readonly local](../keywords/ref.md#ref-readonly-locals) ou usá-la como um [valor de retorno de referência](../keywords/ref.md#reference-return-values) ou como um [parâmetro do método `ref`](../keywords/ref.md#passing-an-argument-by-reference).

A sintaxe da expressão condicional ref é a seguinte:

```csharp
condition ? ref consequent : ref alternative
```

Como o operador condicional original, a expressão condicional ref avalia apenas uma das duas expressões: `consequent` ou `alternative`.

No caso da expressão condicional ref, o tipo de `consequent` e `alternative` devem ser iguais.

O exemplo a seguir demonstra o uso da expressão condicional ref:

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Operador condicional e uma instrução `if..else`

O uso do operador condicional em vez de uma instrução [If-Else](../keywords/if-else.md) pode resultar em um código mais conciso em casos em que você precisa de uma condição para computar um valor. O exemplo a seguir demonstra duas maneiras de classificar um inteiro como negativo ou não negativo:

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Um tipo definido pelo usuário não pode sobrecarregar o operador condicional.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira a seção [Operador condicional](~/_csharplang/spec/expressions.md#conditional-operator) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).

Para obter mais informações sobre a expressão ref condicional, consulte a [Nota de proposta de recurso](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Instrução if-else](../keywords/if-else.md)
- [Operadores ?. e ?[]](member-access-operators.md#null-conditional-operators--and-)
- [?? e?? = operadores](null-coalescing-operator.md)
- [ref keyword](../keywords/ref.md)
