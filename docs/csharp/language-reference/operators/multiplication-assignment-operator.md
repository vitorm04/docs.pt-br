---
title: Operador *= – Referência de C#
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 70461f79e714e44354fe4137e5360769fa048d3e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967380"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4882b-102">\*Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4882b-102">\*= Operator (C# Reference)</span></span>

<span data-ttu-id="4882b-103">O operador de atribuição de multiplicação.</span><span class="sxs-lookup"><span data-stu-id="4882b-103">The multiplication assignment operator.</span></span>

<span data-ttu-id="4882b-104">Uma expressão que usa o operador `*=`, como</span><span class="sxs-lookup"><span data-stu-id="4882b-104">An expression using the `*=` operator, such as</span></span>

```csharp
x *= y
```

<span data-ttu-id="4882b-105">equivale a</span><span class="sxs-lookup"><span data-stu-id="4882b-105">is equivalent to</span></span>

```csharp
x = x * y
```

<span data-ttu-id="4882b-106">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="4882b-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="4882b-107">Para tipos numéricos, o [\*operador ](multiplication-operator.md) calcula o produto dos operandos.</span><span class="sxs-lookup"><span data-stu-id="4882b-107">For numeric types, the [\* operator](multiplication-operator.md) computes the product of its operands.</span></span>

<span data-ttu-id="4882b-108">O exemplo a seguir demonstra o uso do operador `*=`:</span><span class="sxs-lookup"><span data-stu-id="4882b-108">The following example demonstrates the usage of the `*=` operator:</span></span>

[!code-csharp-interactive[multiply and assign](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#MultiplyAndAssign)]

## <a name="operator-overloadability"></a><span data-ttu-id="4882b-109">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="4882b-109">Operator overloadability</span></span>

<span data-ttu-id="4882b-110">Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de multiplicação](multiplication-operator.md) `*`, o operador de atribuição de multiplicação `*=` ficará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="4882b-110">If a user-defined type [overloads](../keywords/operator.md) the [multiplication operator](multiplication-operator.md) `*`, the multiplication assignment operator `*=` is implicitly overloaded.</span></span> <span data-ttu-id="4882b-111">Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição de multiplicação.</span><span class="sxs-lookup"><span data-stu-id="4882b-111">A user-defined type cannot explicitly overload the multiplication assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4882b-112">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4882b-112">C# language specification</span></span>

<span data-ttu-id="4882b-113">Para obter mais informações, veja a seção [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4882b-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4882b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4882b-114">See also</span></span>

- [<span data-ttu-id="4882b-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="4882b-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4882b-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4882b-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4882b-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="4882b-117">C# Operators</span></span>](index.md)
