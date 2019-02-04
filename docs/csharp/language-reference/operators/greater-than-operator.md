---
title: '> Operador – Referência de C#'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 3b036c491d9663bf4ab0971d84a0a8d58d902ee6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287203"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e7070-102">Operador > (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e7070-102">> Operator (C# Reference)</span></span>

<span data-ttu-id="e7070-103">O operador relacional “maior do que” `>` retornará `true` se o primeiro operando for maior do que o segundo operando; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e7070-103">The "greater than" relational operator `>` returns `true` if its first operand is greater than its second operand, `false` otherwise.</span></span> <span data-ttu-id="e7070-104">Todos os tipos numéricos e de enumeração são compatíveis com o operador `>`.</span><span class="sxs-lookup"><span data-stu-id="e7070-104">All numeric and enumeration types support the `>` operator.</span></span> <span data-ttu-id="e7070-105">No caso dos operandos do mesmo tipo de [enum](../keywords/enum.md), os valores correspondentes do tipo integral subjacente são comparados.</span><span class="sxs-lookup"><span data-stu-id="e7070-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="e7070-106">No caso dos operadores relacionais `==`, `>`, `<`, `>=` e `<=`, se nenhum dos operandos for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`.</span><span class="sxs-lookup"><span data-stu-id="e7070-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="e7070-107">Isso significa que o valor `NaN` não é maior, menor, nem igual a nenhum outro valor `double` (ou `float`).</span><span class="sxs-lookup"><span data-stu-id="e7070-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="e7070-108">Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e7070-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="e7070-109">O exemplo a seguir demonstra o uso do operador `>`:</span><span class="sxs-lookup"><span data-stu-id="e7070-109">The following example demonstrates the usage of the `>` operator:</span></span>

[!code-csharp-interactive[greater than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Greater)]

## <a name="operator-overloadability"></a><span data-ttu-id="e7070-110">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="e7070-110">Operator overloadability</span></span>

<span data-ttu-id="e7070-111">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `>`.</span><span class="sxs-lookup"><span data-stu-id="e7070-111">User-defined types can [overload](../keywords/operator.md) the `>` operator.</span></span> <span data-ttu-id="e7070-112">Se um tipo sobrecarregar o operador “maior do que” `>`, ele também sobrecarregará o [operador “menor do que”](less-than-operator.md) `<`.</span><span class="sxs-lookup"><span data-stu-id="e7070-112">If a type overloads the "greater than" operator `>`, it must also overload the ["less than" operator](less-than-operator.md) `<`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e7070-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e7070-113">C# language specification</span></span>

<span data-ttu-id="e7070-114">Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e7070-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e7070-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7070-115">See also</span></span>

- [<span data-ttu-id="e7070-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e7070-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e7070-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e7070-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e7070-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e7070-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="e7070-119">Operador >=</span><span class="sxs-lookup"><span data-stu-id="e7070-119">>= Operator</span></span>](greater-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
