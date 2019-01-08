---
title: Operador &gt;= – Referência de C#
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- '>=_CSharpKeyword'
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
ms.openlocfilehash: 34437742d33cff97e53c6dfb163df083e80d41f3
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655927"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="531af-102">&gt;Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="531af-102">&gt;= Operator (C# Reference)</span></span>

<span data-ttu-id="531af-103">O operador relacional “maior ou igual a” `>=` retornará `true` se o primeiro operando for maior ou igual ao segundo operando; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="531af-103">The "greater than or equal" relational operator `>=` returns `true` if its first operand is greater than or equal to its second operand, `false` otherwise.</span></span> <span data-ttu-id="531af-104">Todos os tipos numéricos e de enumeração são compatíveis com o operador `>=`.</span><span class="sxs-lookup"><span data-stu-id="531af-104">All numeric and  enumeration types support the `>=` operator.</span></span> <span data-ttu-id="531af-105">No caso dos operandos do mesmo tipo de [enum](../keywords/enum.md), os valores correspondentes do tipo integral subjacente são comparados.</span><span class="sxs-lookup"><span data-stu-id="531af-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="531af-106">No caso dos operadores relacionais `==`, `>`, `<`, `>=` e `<=`, se nenhum dos operandos for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`.</span><span class="sxs-lookup"><span data-stu-id="531af-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="531af-107">Isso significa que o valor `NaN` não é maior, menor, nem igual a nenhum outro valor `double` (ou `float`).</span><span class="sxs-lookup"><span data-stu-id="531af-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="531af-108">Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="531af-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="531af-109">O exemplo a seguir demonstra o uso do operador `>=`:</span><span class="sxs-lookup"><span data-stu-id="531af-109">The following example demonstrates the usage of the `>=` operator:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="531af-110">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="531af-110">Operator overloadability</span></span>

<span data-ttu-id="531af-111">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `>=`.</span><span class="sxs-lookup"><span data-stu-id="531af-111">User-defined types can [overload](../keywords/operator.md) the `>=` operator.</span></span> <span data-ttu-id="531af-112">Se um tipo sobrecarregar o operador “maior ou igual a” `>=`, ele também sobrecarregará o [operador “menor ou igual a”](less-than-equal-operator.md) `<=`.</span><span class="sxs-lookup"><span data-stu-id="531af-112">If a type overloads the "greater than or equal" operator `>=`, it must also overload the ["less than or equal" operator](less-than-equal-operator.md) `<=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="531af-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="531af-113">C# language specification</span></span>

<span data-ttu-id="531af-114">Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="531af-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="531af-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="531af-115">See also</span></span>

- [<span data-ttu-id="531af-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="531af-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="531af-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="531af-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="531af-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="531af-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="531af-119">Operador ></span><span class="sxs-lookup"><span data-stu-id="531af-119">> Operator</span></span>](greater-than-operator.md)
- [<span data-ttu-id="531af-120">Operador ==</span><span class="sxs-lookup"><span data-stu-id="531af-120">== Operator</span></span>](equality-comparison-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
