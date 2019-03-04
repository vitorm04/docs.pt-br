---
title: '?: Operador – Referência de C#'
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
ms.openlocfilehash: c3c875cf5b8d1b5e69cd76cb0ee4df0a989a35a0
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202893"
---
# <a name="-operator-c-reference"></a>?: Operador (Referência de C#)

O operador condicional `?:`, comumente conhecido como o operador condicional ternário, avalia uma expressão booliana e retorna o resultado da avaliação de uma de duas expressões, dependendo se a expressão booliana é avaliada como `true` ou `false`. Começando com C# 7.2, a [expressão de referência condicional](#conditional-ref-expression) retorna a referência ao resultado de uma de duas expressões.

A sintaxe do operador condicional é a seguinte:

```csharp
condition ? consequence : alternative
```

A expressão `condition` deve ser avaliada para `true` ou `false`. Se `condition` for avaliada como `true`, a expressão `consequence` será avaliada e seu resultado se tornará o resultado da operação. Se `condition` for avaliada como `false`, a expressão `alternative` será avaliada e seu resultado se tornará o resultado da operação. Somente `consequence` ou `alternative` é avaliada.

O tipo de `consequence` e `alternative` devem ser iguais ou deve haver uma conversão implícita de um tipo para outro.

O operador condicional é associativo direito, ou seja, uma expressão da forma

```csharp
a ? b : c ? d : e
```

é avaliada como

```csharp
a ? b : (c ? d : e)
```

O exemplo a seguir demonstra o uso do operador condicional:

[!code-csharp[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Expressão condicional ref

Começando com C# 7.2, use a expressão de referência condicional para retornar a referência ao resultado de uma de duas expressões. Você pode atribuir essa referência a uma variável [ref local](../keywords/ref.md#ref-locals) ou [ref readonly local](../keywords/ref.md#ref-readonly-locals) ou usá-la como um [valor de retorno de referência](../keywords/ref.md#reference-return-values) ou como um [parâmetro do método `ref`](../keywords/ref.md#passing-an-argument-by-reference).

A sintaxe da expressão condicional ref é a seguinte:

```csharp
condition ? ref consequence : ref alternative
```

Como o operador condicional original, a expressão condicional ref avalia apenas uma das duas expressões: `consequence` ou `alternative`.

No caso da expressão condicional ref, o tipo de `consequence` e `alternative` devem ser iguais.

O exemplo a seguir demonstra o uso da expressão condicional ref:

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

Para saber mais, confira a [nota da proposta do recurso](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md).

## <a name="conditional-operator-and-an-ifelse-statement"></a>Operador condicional e uma instrução `if..else`

O uso do operador condicional em uma instrução [ if-else ](../keywords/if-else.md) pode resultar em código mais conciso em casos onde você precisa calcular um valor condicionalmente. O exemplo a seguir demonstra duas maneiras de classificar um inteiro como negativo ou não negativo:

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

O operador condicional não pode ser sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira a seção [Operador condicional](~/_csharplang/spec/expressions.md#conditional-operator) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Instrução if-else](../keywords/if-else.md)
- [Operadores ?. e ?[]](null-conditional-operators.md)
- [Operador ??](null-coalescing-operator.md)
- [ref keyword](../keywords/ref.md)
