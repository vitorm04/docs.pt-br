---
title: '>Operador = – Referência de C#'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- '>=_CSharpKeyword'
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
ms.openlocfilehash: 821369734e64648714bf89efb0c02d12d4d816e3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256547"
---
# <a name="-operator-c-reference"></a>Operador >= (Referência de C#)

O operador relacional “maior ou igual a” `>=` retornará `true` se o primeiro operando for maior ou igual ao segundo operando; caso contrário, `false`. Todos os tipos numéricos e de enumeração são compatíveis com o operador `>=`. No caso dos operandos do mesmo tipo de [enum](../keywords/enum.md), os valores correspondentes do tipo integral subjacente são comparados.

> [!NOTE]
> No caso dos operadores relacionais `==`, `>`, `<`, `>=` e `<=`, se nenhum dos operandos for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`. Isso significa que o valor `NaN` não é maior, menor, nem igual a nenhum outro valor `double` (ou `float`). Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.

O exemplo a seguir demonstra o uso do operador `>=`:

[!code-csharp-interactive[greater than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `>=`. Se um tipo sobrecarregar o operador “maior ou igual a” `>=`, ele também sobrecarregará o [operador “menor ou igual a”](less-than-equal-operator.md) `<=`.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Operador >](greater-than-operator.md)
- [Operador ==](equality-comparison-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
