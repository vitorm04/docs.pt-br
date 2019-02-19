---
title: '>>Operador = – Referência de C#'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 51914bb5e9ebffd5d868528b5a8d3072a956cea6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220907"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f2c70-102">Operador >>= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f2c70-102">>>= operator (C# Reference)</span></span>

<span data-ttu-id="f2c70-103">O operador de atribuição de deslocamento para a direita.</span><span class="sxs-lookup"><span data-stu-id="f2c70-103">The right-shift assignment operator.</span></span>

<span data-ttu-id="f2c70-104">Uma expressão que usa o operador `>>=`, como</span><span class="sxs-lookup"><span data-stu-id="f2c70-104">An expression using the `>>=` operator, such as</span></span>

```csharp
x >>= y
```

<span data-ttu-id="f2c70-105">equivale a</span><span class="sxs-lookup"><span data-stu-id="f2c70-105">is equivalent to</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="f2c70-106">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="f2c70-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="f2c70-107">O [operador `>>`](right-shift-operator.md) desloca o primeiro operando à direita pelo número de bits definido pelo seu segundo operando.</span><span class="sxs-lookup"><span data-stu-id="f2c70-107">The [`>>` operator](right-shift-operator.md) shifts its first operand right by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="f2c70-108">O exemplo a seguir demonstra o uso do operador `>>=`:</span><span class="sxs-lookup"><span data-stu-id="f2c70-108">The following example demonstrates the usage of the `>>=` operator:</span></span>

[!code-csharp-interactive[right shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="f2c70-109">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="f2c70-109">Operator overloadability</span></span>

<span data-ttu-id="f2c70-110">Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador `>>`](right-shift-operator.md), o operador de atribuição à direita `>>=` ficará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="f2c70-110">If a user-defined type [overloads](../keywords/operator.md) the [`>>` operator](right-shift-operator.md), the right-shift assignment operator `>>=` is implicitly overloaded.</span></span> <span data-ttu-id="f2c70-111">Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição à direita.</span><span class="sxs-lookup"><span data-stu-id="f2c70-111">A user-defined type cannot explicitly overload the right-shift assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f2c70-112">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f2c70-112">C# language specification</span></span>

<span data-ttu-id="f2c70-113">Para obter mais informações, veja a seção [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2c70-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2c70-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2c70-114">See also</span></span>

- [<span data-ttu-id="f2c70-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f2c70-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f2c70-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f2c70-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f2c70-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="f2c70-117">C# operators</span></span>](index.md)