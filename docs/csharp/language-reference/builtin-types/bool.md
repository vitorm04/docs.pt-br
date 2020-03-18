---
title: tipo bool - referência C#
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2ba2e54a6b0f24402fc3728dfe19b548a2368830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846439"
---
# <a name="bool-c-reference"></a>bool (referência C#)

A `bool` palavra-chave tipo é um <xref:System.Boolean?displayProperty=nameWithType> alias para o tipo de estrutura .NET `false`que representa um valor booleano, que pode ser ou `true` .

Para realizar operações lógicas com valores do `bool` tipo, use operadores [lógicos booleanos.](../operators/boolean-logical-operators.md) O `bool` tipo é o tipo de resultado de [comparação](../operators/comparison-operators.md) e [igualdade](../operators/equality-operators.md) dos operadores. Uma `bool` expressão pode ser uma expressão condicional controladora no [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), e [para](../keywords/for.md) declarações e no [operador `?:`condicional ](../operators/conditional-operator.md).

O valor padrão `bool` do `false`tipo é .

## <a name="literals"></a>Literais

Você pode `true` usar `false` o e literals para inicializar uma `bool` variável ou para passar um `bool` valor:

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Lógica booleana de três valores

Use o `bool?` tipo anulado, se você precisar suportar a lógica de três valores, por exemplo, quando você trabalha com bancos de dados que suportam um tipo booleano de três valores. Para os operandos `bool?`, os operadores `&` e `|` predefinidos oferecem suporte à lógica de três valores. Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../operators/boolean-logical-operators.md).

Para obter mais informações sobre tipos de valor anulados, consulte [tipos de valor anulados](nullable-value-types.md).

## <a name="conversions"></a>Conversões

C# fornece apenas duas conversões que envolvem o `bool` tipo. São uma conversão implícita para `bool?` o tipo nulo `bool?` correspondente e uma conversão explícita do tipo. No entanto, o .NET fornece métodos adicionais `bool` que você pode usar para converter para ou a partir do tipo. Para obter mais informações, consulte a [seção Conversão para e de valores booleanos](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) da página de referência da <xref:System.Boolean?displayProperty=nameWithType> API.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte A seção [do tipo bool](~/_csharplang/spec/types.md#the-bool-type) da [especificação do idioma C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Tipos de valor](value-types.md)
- [operadores true e false](../operators/true-false-operators.md)
