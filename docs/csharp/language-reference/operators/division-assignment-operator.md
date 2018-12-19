---
title: Operador /= – Referência de C#
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: ed4dd6c0c944b77543aae4de8d51534b4df4f4ef
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286514"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f71e8-102">Operador /= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f71e8-102">/= Operator (C# Reference)</span></span>

<span data-ttu-id="f71e8-103">O operador de atribuição de divisão.</span><span class="sxs-lookup"><span data-stu-id="f71e8-103">The division assignment operator.</span></span>

<span data-ttu-id="f71e8-104">Uma expressão que usa o operador `/=`, como</span><span class="sxs-lookup"><span data-stu-id="f71e8-104">An expression using the `/=` operator, such as</span></span>

```csharp
x /= y
```

<span data-ttu-id="f71e8-105">equivale a</span><span class="sxs-lookup"><span data-stu-id="f71e8-105">is equivalent to</span></span>

```csharp
x = x / y
```

<span data-ttu-id="f71e8-106">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="f71e8-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="f71e8-107">O [operador de divisão](division-operator.md) `/` divide o primeiro operando pelo segundo.</span><span class="sxs-lookup"><span data-stu-id="f71e8-107">The [division operator](division-operator.md) `/` divides its first operand by its second operand.</span></span> <span data-ttu-id="f71e8-108">Ele é compatível com todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="f71e8-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="f71e8-109">O exemplo a seguir demonstra o uso do operador `/=`:</span><span class="sxs-lookup"><span data-stu-id="f71e8-109">The following example demonstrates the usage of the `/=` operator:</span></span>

[!code-csharp-interactive[divide and assign](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#DivisionAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="f71e8-110">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="f71e8-110">Operator overloadability</span></span>

<span data-ttu-id="f71e8-111">Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de divisão](division-operator.md) `/`, o operador de atribuição de divisão`/=` ficará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="f71e8-111">If a user-defined type [overloads](../keywords/operator.md) the [division operator](division-operator.md) `/`, the division assignment operator `/=` is implicitly overloaded.</span></span> <span data-ttu-id="f71e8-112">Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição de divisão.</span><span class="sxs-lookup"><span data-stu-id="f71e8-112">A user-defined type cannot explicitly overload the division assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f71e8-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f71e8-113">C# language specification</span></span>

<span data-ttu-id="f71e8-114">Para obter mais informações, veja a seção [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f71e8-114">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f71e8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f71e8-115">See also</span></span>

- [<span data-ttu-id="f71e8-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f71e8-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f71e8-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f71e8-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f71e8-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="f71e8-118">C# Operators</span></span>](index.md)
