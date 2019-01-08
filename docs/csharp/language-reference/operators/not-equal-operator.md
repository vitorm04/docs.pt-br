---
title: Operador != – Referência de C#
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 939b5664dba4345e62a43fb2f8d4d5379659d6aa
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610171"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="54307-102">Operador != (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="54307-102">!= Operator (C# Reference)</span></span>

<span data-ttu-id="54307-103">O operador de desigualdade `!=` retornará `true` se seus operandos não forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="54307-103">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="54307-104">No caso dos operandos de [tipos internos](../keywords/built-in-types-table.md), a expressão `x != y` gera o mesmo resultado que a expressão `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="54307-104">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="54307-105">Para obter mais informações, consulte o artigo [Operador ==](equality-comparison-operator.md).</span><span class="sxs-lookup"><span data-stu-id="54307-105">For more information, see the [== Operator](equality-comparison-operator.md) article.</span></span>

<span data-ttu-id="54307-106">O exemplo a seguir demonstra o uso do operador `!=`:</span><span class="sxs-lookup"><span data-stu-id="54307-106">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="54307-107">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="54307-107">Operator overloadability</span></span>

<span data-ttu-id="54307-108">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `!=`.</span><span class="sxs-lookup"><span data-stu-id="54307-108">User-defined types can [overload](../keywords/operator.md) the `!=` operator.</span></span> <span data-ttu-id="54307-109">Se um tipo sobrecarregar o operador de desigualdade `!=`, ele também sobrecarregará o [operador de igualdade](equality-comparison-operator.md) `==`.</span><span class="sxs-lookup"><span data-stu-id="54307-109">If a type overloads the inequality operator `!=`, it must also overload the [equality operator](equality-comparison-operator.md) `==`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="54307-110">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="54307-110">C# language specification</span></span>

<span data-ttu-id="54307-111">Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="54307-111">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54307-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54307-112">See also</span></span>

- [<span data-ttu-id="54307-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="54307-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="54307-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="54307-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="54307-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="54307-115">C# Operators</span></span>](index.md)
- [<span data-ttu-id="54307-116">Comparações de igualdade</span><span class="sxs-lookup"><span data-stu-id="54307-116">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
