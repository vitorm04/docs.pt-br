---
title: Operador == – Referência de C#
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: 6d86348eefc87e847267f262141ff49e5d51faae
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655953"
---
# <a name="-operator-c-reference"></a>Operador == (Referência de C#)

O operador de igualdade `==` retornará `true` se seus operandos forem iguais; caso contrário, `false`.

## <a name="value-types-equality"></a>Igualdade de tipos de valor

Os operandos dos [tipos de valor internos](../keywords/value-types-table.md) serão iguais se seus valores forem iguais:

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> No caso dos operadores relacionais `==`, `>`, `<`, `>=` e `<=`, se nenhum dos operandos for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`. Isso significa que o valor `NaN` não é maior, menor, nem igual a nenhum outro valor `double` (ou `float`). Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.

Dois operandos do mesmo tipo de [enum](../keywords/enum.md) serão iguais se os valores correspondentes do tipo integral subjacente forem iguais.

Por padrão, o operador `==` não está definido para um tipo de [struct](../keywords/struct.md) definido pelo usuário. Um tipo definido pelo usuário pode [sobrecarregar](#operator-overloadability) o operador `==`.

Começando com C# 7.3, os operadores `==`, [, `!=` e ](not-equal-operator.md) são compatíveis com as [tuplas](../../tuples.md) de C#. Para obter mais informações, consulte a seção [Igualdade e tuplas](../../tuples.md#equality-and-tuples) do artigo [Tipos de tupla do C#](../../tuples.md).

## <a name="string-equality"></a>Igualdade da cadeia de caracteres

Dois operandos da [cadeia de caracteres](../keywords/string.md) serão iguais quando ambos forem `null` ou ambas as instâncias da cadeia de caracteres tiverem o mesmo comprimento e caracteres idênticos em cada posição de caractere:

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

Essa é uma comparação ordinal que diferencia maiúsculas de minúsculas. Para obter mais informações sobre como comparar cadeias de caracteres, consulte [Como comparar cadeias de caracteres no C#](../../how-to/compare-strings.md).

## <a name="reference-types-equality"></a>Igualdade de tipos de referência

Dois operandos de um tipo de referência diferente de `string` serão iguais quando eles se referirem ao mesmo objeto:

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

O exemplo mostra que o operador `==` é compatível com os tipos de referência definidos pelo usuário. No entanto, um tipo de referência definido pelo usuário pode sobrecarregar o operador `==`. Se um tipo de referência sobrecarregar o operador `==`, use o método <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> para verificar se as duas referências desse tipo dizem respeito ao mesmo objeto.

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `==`. Se um tipo sobrecarregar o operador de igualdade `==`, ele também sobrecarregará o [operador de desigualdade](not-equal-operator.md) `!=`.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Comparações de igualdade](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
