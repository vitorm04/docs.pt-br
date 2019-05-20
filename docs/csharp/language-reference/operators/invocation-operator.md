---
title: Operador () – referência do C#
ms.custom: seodec18
ms.date: 01/15/2019
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 412d3ac5296eaf7d67f4a5e84b7a42f6fa5bb8a5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633843"
---
# <a name="-operator-c-reference"></a>Operador () (referência do C#)

Os parênteses, `()`, normalmente são usados para invocação de método ou de delegado ou em expressões de conversão.

Você também pode usar parênteses para especificar a ordem na qual as operações em uma expressão são avaliada. Para obter mais informações, confira a seção [Adicionando parênteses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) o artigo [Operadores](../../programming-guide/statements-expressions-operators/operators.md). Para obter a lista de operadores ordenada pelo nível de precedência, confira [Operadores do C#](index.md).

## <a name="method-invocation"></a>Invocação de método

O exemplo a seguir demonstra como invocar um método, com ou sem argumentos, e um delegado:

[!code-csharp-interactive[use for invocation](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

Você também pode usar parênteses ao invocar um [construtor](../../programming-guide/classes-and-structs/constructors.md) com um operador [`new`](../keywords/new-operator.md).

Para obter mais informações sobre os métodos, confira [Métodos](../../programming-guide/classes-and-structs/methods.md). Para obter mais informações sobre delegados, confira [Delegados](../../programming-guide/delegates/index.md).

## <a name="cast-expression"></a>Expressão de conversão

Uma expressão de conversão do formulário `(T)E` invoca um operador de conversão para converter o valor da expressão `E` para o tipo `T`. Se não existir nenhuma conversão explícita do tipo `E` para o tipo `T`, ocorrerá um erro em tempo de compilação. Para obter informações de como definir um operador de conversão, confira os artigos sobre as palavras-chave [explicit](../keywords/explicit.md) e [implicit](../keywords/implicit.md).

O exemplo a seguir demonstra a conversão de tipo entre tipos numéricos:

[!code-csharp-interactive[use for cast](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

Para obter mais informações sobre as conversões explícitas predefinidas entre tipos numéricos, confira [Tabela de conversões numéricas explícitas](../keywords/explicit-numeric-conversions-table.md).

Para obter mais informações, confira [Coerção e conversões e o tipo](../../programming-guide/types/casting-and-type-conversions.md) e [Operadores de conversão](../../programming-guide/statements-expressions-operators/conversion-operators.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

O operador `()` não pode ser sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seções [Expressões de invocação](~/_csharplang/spec/expressions.md#invocation-expressions) e [Expressões de conversão](~/_csharplang/spec/expressions.md#cast-expressions) da [Especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
