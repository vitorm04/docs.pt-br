---
title: Operador &lt; – Referência de C#
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: bb0f590bb547c4e632bd14c773f095435c8986f0
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655940"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="e8104-102">Operador &lt; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e8104-102">&lt; Operator (C# Reference)</span></span>

<span data-ttu-id="e8104-103">O operador relacional “menor do que” `<` retornará `true` se o primeiro operando for menor do que o segundo operando; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e8104-103">The "less than" relational operator `<` returns `true` if its first operand is less than its second operand, `false` otherwise.</span></span> <span data-ttu-id="e8104-104">Todos os tipos numéricos e de enumeração são compatíveis com o operador `<`.</span><span class="sxs-lookup"><span data-stu-id="e8104-104">All numeric and enumeration types support the `<` operator.</span></span> <span data-ttu-id="e8104-105">No caso dos operandos do mesmo tipo de [enum](../keywords/enum.md), os valores correspondentes do tipo integral subjacente são comparados.</span><span class="sxs-lookup"><span data-stu-id="e8104-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="e8104-106">No caso dos operadores relacionais `==`, `>`, `<`, `>=` e `<=`, se nenhum dos operandos for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`.</span><span class="sxs-lookup"><span data-stu-id="e8104-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="e8104-107">Isso significa que o valor `NaN` não é maior, menor, nem igual a nenhum outro valor `double` (ou `float`).</span><span class="sxs-lookup"><span data-stu-id="e8104-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="e8104-108">Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8104-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="e8104-109">O exemplo a seguir demonstra o uso do operador `<`:</span><span class="sxs-lookup"><span data-stu-id="e8104-109">The following example demonstrates the usage of the `<` operator:</span></span>

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Less)]

## <a name="operator-overloadability"></a><span data-ttu-id="e8104-110">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="e8104-110">Operator overloadability</span></span>

<span data-ttu-id="e8104-111">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `<`.</span><span class="sxs-lookup"><span data-stu-id="e8104-111">User-defined types can [overload](../keywords/operator.md) the `<` operator.</span></span> <span data-ttu-id="e8104-112">Se um tipo sobrecarregar o operador “menor do que” `<`, ele também sobrecarregará o [operador “maior do que”](greater-than-operator.md) `>`.</span><span class="sxs-lookup"><span data-stu-id="e8104-112">If a type overloads the "less than" operator `<`, it must also overload the ["greater than" operator](greater-than-operator.md) `>`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e8104-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e8104-113">C# language specification</span></span>

<span data-ttu-id="e8104-114">Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e8104-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8104-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8104-115">See also</span></span>

- [<span data-ttu-id="e8104-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e8104-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e8104-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e8104-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e8104-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e8104-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="e8104-119">Operador <=</span><span class="sxs-lookup"><span data-stu-id="e8104-119"><= Operator</span></span>](less-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
