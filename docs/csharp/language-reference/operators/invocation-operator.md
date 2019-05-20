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
# <a name="-operator-c-reference"></a><span data-ttu-id="92b6e-102">Operador () (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="92b6e-102">() operator (C# Reference)</span></span>

<span data-ttu-id="92b6e-103">Os parênteses, `()`, normalmente são usados para invocação de método ou de delegado ou em expressões de conversão.</span><span class="sxs-lookup"><span data-stu-id="92b6e-103">Parentheses, `()`, are typically used for method or delegate invocation or in cast expressions.</span></span>

<span data-ttu-id="92b6e-104">Você também pode usar parênteses para especificar a ordem na qual as operações em uma expressão são avaliada.</span><span class="sxs-lookup"><span data-stu-id="92b6e-104">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="92b6e-105">Para obter mais informações, confira a seção [Adicionando parênteses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) o artigo [Operadores](../../programming-guide/statements-expressions-operators/operators.md).</span><span class="sxs-lookup"><span data-stu-id="92b6e-105">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="92b6e-106">Para obter a lista de operadores ordenada pelo nível de precedência, confira [Operadores do C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="92b6e-106">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="method-invocation"></a><span data-ttu-id="92b6e-107">Invocação de método</span><span class="sxs-lookup"><span data-stu-id="92b6e-107">Method invocation</span></span>

<span data-ttu-id="92b6e-108">O exemplo a seguir demonstra como invocar um método, com ou sem argumentos, e um delegado:</span><span class="sxs-lookup"><span data-stu-id="92b6e-108">The following example demonstrates how to invoke a method, with or without arguments, and a delegate:</span></span>

[!code-csharp-interactive[use for invocation](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

<span data-ttu-id="92b6e-109">Você também pode usar parênteses ao invocar um [construtor](../../programming-guide/classes-and-structs/constructors.md) com um operador [`new`](../keywords/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="92b6e-109">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with a [`new`](../keywords/new-operator.md) operator.</span></span>

<span data-ttu-id="92b6e-110">Para obter mais informações sobre os métodos, confira [Métodos](../../programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="92b6e-110">For more information about methods, see [Methods](../../programming-guide/classes-and-structs/methods.md).</span></span> <span data-ttu-id="92b6e-111">Para obter mais informações sobre delegados, confira [Delegados](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="92b6e-111">For more information about delegates, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="cast-expression"></a><span data-ttu-id="92b6e-112">Expressão de conversão</span><span class="sxs-lookup"><span data-stu-id="92b6e-112">Cast expression</span></span>

<span data-ttu-id="92b6e-113">Uma expressão de conversão do formulário `(T)E` invoca um operador de conversão para converter o valor da expressão `E` para o tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="92b6e-113">A cast expression of the form `(T)E` invokes a conversion operator to convert the value of expression `E` to type `T`.</span></span> <span data-ttu-id="92b6e-114">Se não existir nenhuma conversão explícita do tipo `E` para o tipo `T`, ocorrerá um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="92b6e-114">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="92b6e-115">Para obter informações de como definir um operador de conversão, confira os artigos sobre as palavras-chave [explicit](../keywords/explicit.md) e [implicit](../keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="92b6e-115">For information about how to define a conversion operator, see the [explicit](../keywords/explicit.md) and [implicit](../keywords/implicit.md) keyword articles.</span></span>

<span data-ttu-id="92b6e-116">O exemplo a seguir demonstra a conversão de tipo entre tipos numéricos:</span><span class="sxs-lookup"><span data-stu-id="92b6e-116">The following example demonstrates type conversion between numeric types:</span></span>

[!code-csharp-interactive[use for cast](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

<span data-ttu-id="92b6e-117">Para obter mais informações sobre as conversões explícitas predefinidas entre tipos numéricos, confira [Tabela de conversões numéricas explícitas](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="92b6e-117">For more information about predefined explicit conversions between numeric types, see [Explicit numeric conversions table](../keywords/explicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="92b6e-118">Para obter mais informações, confira [Coerção e conversões e o tipo](../../programming-guide/types/casting-and-type-conversions.md) e [Operadores de conversão](../../programming-guide/statements-expressions-operators/conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="92b6e-118">For more information, see [Casting and type conversions](../../programming-guide/types/casting-and-type-conversions.md) and [Conversion operators](../../programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="92b6e-119">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="92b6e-119">Operator overloadability</span></span>

<span data-ttu-id="92b6e-120">O operador `()` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="92b6e-120">The operator `()` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="92b6e-121">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="92b6e-121">C# language specification</span></span>

<span data-ttu-id="92b6e-122">Para obter mais informações, confira as seções [Expressões de invocação](~/_csharplang/spec/expressions.md#invocation-expressions) e [Expressões de conversão](~/_csharplang/spec/expressions.md#cast-expressions) da [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="92b6e-122">For more information, see the [Invocation expressions](~/_csharplang/spec/expressions.md#invocation-expressions) and [Cast expressions](~/_csharplang/spec/expressions.md#cast-expressions) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="92b6e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92b6e-123">See also</span></span>

- [<span data-ttu-id="92b6e-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="92b6e-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="92b6e-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="92b6e-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="92b6e-126">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="92b6e-126">C# Operators</span></span>](index.md)
