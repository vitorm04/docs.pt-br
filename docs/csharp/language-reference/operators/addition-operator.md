---
title: + Operador (Referência de C#)
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 27ea47d698b20f112880750ec0bc931f1917f142
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50192287"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d6fc4-102">Operador + (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d6fc4-102">+ Operator (C# Reference)</span></span>

<span data-ttu-id="d6fc4-103">Há suporte para o operador `+` de duas formas: unário mais operador ou um operador de adição binário.</span><span class="sxs-lookup"><span data-stu-id="d6fc4-103">The `+` operator is supported in two forms: a unary plus operator or a binary addition operator.</span></span>

## <a name="unary-plus-operator"></a><span data-ttu-id="d6fc4-104">Operador unário de adição</span><span class="sxs-lookup"><span data-stu-id="d6fc4-104">Unary plus operator</span></span>

<span data-ttu-id="d6fc4-105">O operador unário `+` retorna o valor do operando.</span><span class="sxs-lookup"><span data-stu-id="d6fc4-105">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="d6fc4-106">Compatível com todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="d6fc4-106">It's supported by all numeric types.</span></span>

## <a name="numeric-addition"></a><span data-ttu-id="d6fc4-107">Adição numérica</span><span class="sxs-lookup"><span data-stu-id="d6fc4-107">Numeric addition</span></span>

<span data-ttu-id="d6fc4-108">Para tipos numéricos, o operador `+` calcula a soma dos operandos:</span><span class="sxs-lookup"><span data-stu-id="d6fc4-108">For numeric types, the `+` operator computes the sum of its operands:</span></span>

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

## <a name="string-concatenation"></a><span data-ttu-id="d6fc4-109">{1&gt;Concatenação de cadeia de caracteres&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d6fc4-109">String concatenation</span></span>

<span data-ttu-id="d6fc4-110">Quando um ou os dois operandos forem do tipo [cadeia de caracteres](../keywords/string.md), o operador `+` concatenará as representações de cadeia de caracteres de seus operandos:</span><span class="sxs-lookup"><span data-stu-id="d6fc4-110">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="d6fc4-111">Começando com C# 6, [interpolação de cadeia de caracteres](../tokens/interpolated.md) oferece uma maneira mais conveniente de formatar cadeias de caracteres:</span><span class="sxs-lookup"><span data-stu-id="d6fc4-111">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="d6fc4-112">Combinação de delegados</span><span class="sxs-lookup"><span data-stu-id="d6fc4-112">Delegate combination</span></span>

<span data-ttu-id="d6fc4-113">Para tipos [delegados](../keywords/delegate.md), o operador `+` retorna uma nova instância de delegado que, quando invocada, invoca o primeiro operando e, em seguida, invoca o segundo operando.</span><span class="sxs-lookup"><span data-stu-id="d6fc4-113">For [delegate](../keywords/delegate.md) types, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="d6fc4-114">Se qualquer um dos operandos for `null`, o operador `+` retornará o valor de outro operando (que também pode ser `null`).</span><span class="sxs-lookup"><span data-stu-id="d6fc4-114">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="d6fc4-115">O exemplo a seguir mostra como os delegados podem ser combinados com o operador `+`:</span><span class="sxs-lookup"><span data-stu-id="d6fc4-115">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="d6fc4-116">Para obter mais informações sobre tipos de delegado, veja [Delegados](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="d6fc4-116">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d6fc4-117">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="d6fc4-117">Operator overloadability</span></span>

<span data-ttu-id="d6fc4-118">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) os operadores `+` unários e binários.</span><span class="sxs-lookup"><span data-stu-id="d6fc4-118">User-defined types can [overload](../keywords/operator.md) the unary and binary `+` operators.</span></span> <span data-ttu-id="d6fc4-119">Quando um operador `+` binário é sobrecarregado, o [operador de atribuição de adição](addition-assignment-operator.md) `+=` também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="d6fc4-119">When a binary `+` operator is overloaded, the [addition assignment operator](addition-assignment-operator.md) `+=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d6fc4-120">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d6fc4-120">C# language specification</span></span>

<span data-ttu-id="d6fc4-121">Para obter mais informações, veja as seções [Operador de adição unário](~/_csharplang/spec/expressions.md#unary-plus-operator) e [Operador de adição](~/_csharplang/spec/expressions.md#addition-operator) da [Especificação de linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d6fc4-121">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6fc4-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6fc4-122">See also</span></span>

- [<span data-ttu-id="d6fc4-123">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d6fc4-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d6fc4-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d6fc4-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d6fc4-125">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="d6fc4-125">C# Operators</span></span>](index.md)
- [<span data-ttu-id="d6fc4-126">Interpolação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d6fc4-126">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="d6fc4-127">Como concatenar várias cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d6fc4-127">How to: Concatenate Multiple Strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="d6fc4-128">Delegados</span><span class="sxs-lookup"><span data-stu-id="d6fc4-128">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="d6fc4-129">Checked e unchecked</span><span class="sxs-lookup"><span data-stu-id="d6fc4-129">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
