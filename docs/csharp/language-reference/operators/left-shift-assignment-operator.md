---
title: Operador <<= – Referência de C#
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: d2105fbee4ddfe1b2cb3325d82b0f2f8c5559297
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219434"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e9104-102">Operador \<\<= (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="e9104-102">\<\<= operator (C# Reference)</span></span>

<span data-ttu-id="e9104-103">O operador de atribuição de deslocamento para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="e9104-103">The left-shift assignment operator.</span></span>

<span data-ttu-id="e9104-104">Uma expressão que usa o operador `<<=`, como</span><span class="sxs-lookup"><span data-stu-id="e9104-104">An expression using the `<<=` operator, such as</span></span>

```csharp
x <<= y
```

<span data-ttu-id="e9104-105">equivale a</span><span class="sxs-lookup"><span data-stu-id="e9104-105">is equivalent to</span></span>

```csharp
x = x << y
```

<span data-ttu-id="e9104-106">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="e9104-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="e9104-107">O [operador `<<`](left-shift-operator.md) desloca o primeiro operando à esquerda pelo número de bits definido pelo seu segundo operando.</span><span class="sxs-lookup"><span data-stu-id="e9104-107">The [`<<` operator](left-shift-operator.md) shifts its first operand left by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="e9104-108">O exemplo a seguir demonstra o uso do operador `<<=`:</span><span class="sxs-lookup"><span data-stu-id="e9104-108">The following example demonstrates the usage of the `<<=` operator:</span></span>

[!code-csharp-interactive[left shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="e9104-109">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="e9104-109">Operator overloadability</span></span>

<span data-ttu-id="e9104-110">Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador `<<`](left-shift-operator.md), o operador de atribuição à esquerda `<<=` ficará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="e9104-110">If a user-defined type [overloads](../keywords/operator.md) the [`<<` operator](left-shift-operator.md), the left-shift assignment operator `<<=` is implicitly overloaded.</span></span> <span data-ttu-id="e9104-111">Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição à esquerda.</span><span class="sxs-lookup"><span data-stu-id="e9104-111">A user-defined type cannot explicitly overload the left-shift assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e9104-112">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e9104-112">C# language specification</span></span>

<span data-ttu-id="e9104-113">Para obter mais informações, veja a seção [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9104-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9104-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9104-114">See also</span></span>

- [<span data-ttu-id="e9104-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e9104-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e9104-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e9104-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e9104-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e9104-117">C# Operators</span></span>](index.md)
