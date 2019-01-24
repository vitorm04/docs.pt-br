---
title: Operador -= – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 3b6890be4460a599a5d2f5f5f6ee1627be933f0b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333324"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="e857c-102">Operador -= (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="e857c-102">-= operator (C# Reference)</span></span>

<span data-ttu-id="e857c-103">O operador de atribuição de subtração.</span><span class="sxs-lookup"><span data-stu-id="e857c-103">The subtraction assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="e857c-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="e857c-104">Remarks</span></span>

<span data-ttu-id="e857c-105">Uma expressão que usa o operador de atribuição `-=`, como</span><span class="sxs-lookup"><span data-stu-id="e857c-105">An expression using the `-=` assignment operator, such as</span></span>

```csharp
x -= y
```

 <span data-ttu-id="e857c-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="e857c-106">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="e857c-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="e857c-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="e857c-108">O significado do [operador –](subtraction-operator.md) depende dos tipos do `x` e `y` (subtração para operandos numéricos, remoção de delegado para operandos de delegado e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="e857c-108">The meaning of the [- operator](subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>

<span data-ttu-id="e857c-109">O operador `-=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [- operador](subtraction-operator.md) (consulte [operador](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="e857c-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](subtraction-operator.md) (see [operator](../keywords/operator.md)).</span></span>

<span data-ttu-id="e857c-110">O operador -= também é usado em C# para cancelar a assinatura de um evento.</span><span class="sxs-lookup"><span data-stu-id="e857c-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="e857c-111">Para obter mais informações, confira [Como: realizar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="e857c-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="e857c-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e857c-112">Example</span></span>

[!code-csharp[csRefOperators#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#6)]

## <a name="see-also"></a><span data-ttu-id="e857c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e857c-113">See also</span></span>

- [<span data-ttu-id="e857c-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e857c-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e857c-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e857c-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e857c-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e857c-116">C# operators</span></span>](index.md)
