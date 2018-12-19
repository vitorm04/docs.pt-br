---
title: '&amp;Operador = – Referência de C#'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 223d2f30ee77457e1f9d5304ec299517932499d0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237019"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="0bbd4-102">&amp;Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0bbd4-102">&amp;= Operator (C# Reference)</span></span>

<span data-ttu-id="0bbd4-103">O operador de atribuição AND.</span><span class="sxs-lookup"><span data-stu-id="0bbd4-103">The AND assignment operator.</span></span>

<span data-ttu-id="0bbd4-104">Uma expressão que usa o operador `&=`, como</span><span class="sxs-lookup"><span data-stu-id="0bbd4-104">An expression using the `&=` operator, such as</span></span>

```csharp
x &= y
```

<span data-ttu-id="0bbd4-105">equivale a</span><span class="sxs-lookup"><span data-stu-id="0bbd4-105">is equivalent to</span></span>

```csharp
x = x & y
```

<span data-ttu-id="0bbd4-106">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="0bbd4-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="0bbd4-107">Para operandos inteiros, o [operador `&`](and-operator.md) computa o AND lógico bit a bit de seus operandos. Para operandos [bool](../keywords/bool.md), ele computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="0bbd4-107">For integer operands, the [`&` operator](and-operator.md) computes the bitwise logical AND of its operands; for [bool](../keywords/bool.md) operands, it computes the logical AND of its operands.</span></span>

<span data-ttu-id="0bbd4-108">O exemplo a seguir demonstra o uso do operador `&=`:</span><span class="sxs-lookup"><span data-stu-id="0bbd4-108">The following example demonstrates the usage of the `&=` operator:</span></span>

[!code-csharp-interactive[AND assignment example](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#AndAssignmentExample)]

## <a name="operator-overloadability"></a><span data-ttu-id="0bbd4-109">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="0bbd4-109">Operator overloadability</span></span>

<span data-ttu-id="0bbd4-110">Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador `&`](and-operator.md), o operador de atribuição AND `&=` ficará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="0bbd4-110">If a user-defined type [overloads](../keywords/operator.md) the [`&` operator](and-operator.md), the AND assignment operator `&=` is implicitly overloaded.</span></span> <span data-ttu-id="0bbd4-111">Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição AND.</span><span class="sxs-lookup"><span data-stu-id="0bbd4-111">A user-defined type cannot explicitly overload the AND assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0bbd4-112">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0bbd4-112">C# language specification</span></span>

<span data-ttu-id="0bbd4-113">Para obter mais informações, veja a seção [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0bbd4-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0bbd4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bbd4-114">See also</span></span>

- [<span data-ttu-id="0bbd4-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0bbd4-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0bbd4-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0bbd4-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0bbd4-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="0bbd4-117">C# Operators</span></span>](index.md)
