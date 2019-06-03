---
title: Operadores lógicos boolianos - referência do C#
description: Saiba mais sobre operadores C# que executam operações de negação lógica, conjunção (AND) e disjunção inclusiva e exclusiva (OR) com operandos booleanos.
ms.date: 04/08/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: 3ac3479de0bd3c95256741a8b3075f2e5786b65c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300094"
---
# <a name="boolean-logical-operators-c-reference"></a>Operadores lógicos boolianos (referência do C#)

Os operadores a seguir executam operações lógicas com os operandos [bool](../keywords/bool.md):

- Operador unário [`!` (negação lógica)](#logical-negation-operator-).
- Operadores binários [`&` (AND lógico)](#logical-and-operator-), [`|` (OR lógico)](#logical-or-operator-) e [`^` (OR exclusivo lógico)](#logical-exclusive-or-operator-). Esses operadores sempre avaliam os dois operandos.
- Operadores binários [`&&` (AND lógico condicional)](#conditional-logical-and-operator-) e [`||` (OR lógico condicional)](#conditional-logical-or-operator-). Esses operadores avaliam o segundo operando apenas se for necessário.

Para os operandos de tipos [integrais](../keywords/integral-types-table.md), os operadores `&`, `|` e `^` executam operações lógicas bit a bit. Para obter mais informações, veja [Operadores bit a bit e shift](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Operador de negação lógica !

O operador `!` calcula a negação lógica de seu operando. Ou seja, ele produz `true`, se o operando for avaliado como `false`, e `false`, se o operando for avaliado como `true`:

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a>Operador AND lógico &amp;

O operador `&` computa o AND lógico de seus operandos. O resultado de `x & y` será `true` se ambos `x` e `y` forem avaliados como `true`. Caso contrário, o resultado será `false`.

O operador `&` avalia os dois operandos, mesmo se o primeiro operando for avaliado como `false`, de modo que o resultado deve ser `false`, independentemente do valor do segundo operando.

No exemplo a seguir, o segundo operando do operador `&` é uma chamada de método, que é executada independentemente do valor do primeiro operando:

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

O [operador AND lógico condicional](#conditional-logical-and-operator-) `&&` também computa o AND lógico e seus operandos, mas não avalia o segundo operando se o primeiro for avaliado como `false`.

Para os operandos de tipos integrais, o operador `&` computa o [AND lógico bit a bit](bitwise-and-shift-operators.md#logical-and-operator-) de seus operandos. O operador `&` unário é o [operador address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Operador OR exclusivo lógico ^

O operador `^` computa o OR exclusivo lógico, também conhecido como o XOR lógico, de seus operandos. O resultado de `x ^ y` é `true` se `x` é avaliado como `true` e `y` avaliado como `false`, ou `x` avaliado como `false` e `y` avaliado como `true`. Caso contrário, o resultado será `false`. Ou seja, para os operandos `bool`, o operador `^` computa o mesmo resultado que o [operador de desigualdade](equality-operators.md#inequality-operator-) `!=`.

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

Para os operandos de tipos integrais, o operador `^` computa o [OR exclusivo bit a bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de seus operandos.

## <a name="logical-or-operator-"></a>Operador OR lógico |

O operador `|` computa o OR lógico de seus operandos. O resultado de `x | y` será `true` se `x` ou `y` for avaliado como `true`. Caso contrário, o resultado será `false`.

O operador `|` avalia os dois operandos, mesmo se o primeiro operando for avaliado como `true`, de modo que o resultado deve ser `true`, independentemente do valor do segundo operando.

No exemplo a seguir, o segundo operando do operador `|` é uma chamada de método, que é executada independentemente do valor do primeiro operando:

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

O [operador OR lógico condicional](#conditional-logical-or-operator-) `||` também computa o OR lógico e seus operandos, mas não avalia o segundo operando se o primeiro for avaliado como `true`.

Para os operandos de tipos integrais, o operador `|` computa o [OR lógico bit a bit](bitwise-and-shift-operators.md#logical-or-operator-) de seus operandos.

## <a name="conditional-logical-and-operator-ampamp"></a>Operador AND lógico condicional &amp;&amp;

O operador AND lógico condicional `&&`, também conhecido como operador AND lógico de "curto-circuito", computa o AND lógico de seus operandos. O resultado de `x && y` será `true` se ambos `x` e `y` forem avaliados como `true`. Caso contrário, o resultado será `false`. Se o primeiro operando for avaliado como `false`, o segundo operando não é avaliado.

No exemplo a seguir, o segundo operando do operador `&&` é uma chamada de método, que não é executada se o primeiro operando for avaliado como `false`:

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

O [operador AND lógico](#logical-and-operator-) `&` também computa o AND lógico de seus operandos, mas sempre avalia os dois operandos.

## <a name="conditional-logical-or-operator-"></a>Operador OR lógico condicional ||

O operador OR lógico condicional `||`, também conhecido como operador OR lógico de "curto-circuito", computa o OR lógico de seus operandos. O resultado de `x || y` será `true` se `x` ou `y` for avaliado como `true`. Caso contrário, o resultado será `false`. Se o primeiro operando for avaliado como `true`, o segundo operando não é avaliado.

No exemplo a seguir, o segundo operando do operador `||` é uma chamada de método, que não é executada se o primeiro operando for avaliado como `true`:

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

O [operador OR lógico](#logical-or-operator-) `|` também computa o OR lógico de seus operandos, mas sempre avalia os dois operandos.

## <a name="nullable-boolean-logical-operators"></a>Operadores lógicos booleanos anuláveis

Para os operandos `bool?`, os operadores `&` e `|` oferecem suporte à lógica de três valores. A semântica desses operadores é definida pela tabela a seguir:  
  
|x|y|x&y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|false|false|true|  
|true|nulo|nulo|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|nulo|false|nulo|  
|nulo|true|nulo|true|  
|nulo|false|false|nulo|  
|nulo|nulo|nulo|nulo|  

O comportamento desses operadores difere do comportamento típico do operador com tipos de valores anuláveis. Normalmente, um operador que é definido para operandos de um tipo de valor também pode ser usado com operandos do tipo de valor anulável correspondente. Esse operador produz `null` se algum de seus operandos for `null`. No entanto, os operadores `&` e `|` podem produzir não nulos, mesmo se um dos operandos for `null`. Para obter mais informações sobre o comportamento do operador com tipos de valor nulos, confira a seção [Operadores](../../programming-guide/nullable-types/using-nullable-types.md#operators) no artigo [Usando tipos nulos](../../programming-guide/nullable-types/using-nullable-types.md).

Você também pode usar os operadores `!` e `^`com os operandos`bool?`, como mostra o exemplo a seguir:

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

Os operadores lógicos condicionais `&&` e `||` não oferecem suporte aos operandos `bool?`.

## <a name="compound-assignment"></a>Atribuição composta

Para um operador binário `op`, uma expressão de atribuição composta do formato

```csharp
x op= y
```

equivale a

```csharp
x = x op y
```

exceto que `x` é avaliado apenas uma vez.

Os operadores `&`, `|` e `^` suportam a atribuição de compostos, conforme mostrado no exemplo a seguir:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

Os operadores lógicos condicionais `&&` e `||` não suportam a atribuição composta.

## <a name="operator-precedence"></a>Precedência do operador

A lista a seguir ordena os operadores lógicos, começando da mais alta precedência até a mais baixa:

- Operador de negação lógico `!`
- Operador AND lógico `&`
- Operador OR exclusivo lógico `^`
- Operador OR lógico `|`
- Operador AND lógico condicional `&&`
- Operador OR lógico condicional `||`

Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência do operador:

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

Para obter a lista completa de operadores do C# ordenada pelo nível de precedência, confira [Operadores do C#](index.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) os operadores `!`, `&`, `|` e `^`. Quando um operador binário está sobrecarregado, o operador de atribuição composta correspondente também é implicitamente sobrecarregado. Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.

Um tipo definido pelo usuário não pode sobrecarregar os operadores lógicos condicionais `&&` e `||`. No entanto, se um tipo definido pelo usuário sobrecarregar os operadores [true e false](true-false-operators.md) e o operador `&` ou `|` de uma determinada maneira, a operação `&&` ou `||`, respectivamente, pode ser avaliada para os operandos desse tipo. Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Operador de negação lógico](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Operadores lógicos](~/_csharplang/spec/expressions.md#logical-operators)
- [Operadores lógicos condicionais](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Operadores shift e bit a bit](bitwise-and-shift-operators.md)
