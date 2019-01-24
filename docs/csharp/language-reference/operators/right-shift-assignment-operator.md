---
title: Operador &gt;&gt;= – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 02a9559a5c4086eeed09094c15c3620366ffad8c
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333676"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="05aec-102">Operador &gt;&gt;= (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="05aec-102">&gt;&gt;= operator (C# Reference)</span></span>

<span data-ttu-id="05aec-103">O operador de atribuição de deslocamento para a direita.</span><span class="sxs-lookup"><span data-stu-id="05aec-103">The right-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="05aec-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="05aec-104">Remarks</span></span>

<span data-ttu-id="05aec-105">Uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="05aec-105">An expression of the form</span></span>

```csharp
x >>= y
```

<span data-ttu-id="05aec-106">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="05aec-106">is evaluated as</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="05aec-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="05aec-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="05aec-108">O [operador >>](right-shift-operator.md) desloca `x` para a direita em um valor especificado pelo `y`.</span><span class="sxs-lookup"><span data-stu-id="05aec-108">The [>> operator](right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>

<span data-ttu-id="05aec-109">O operador >>= não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador >>](right-shift-operator.md) (consulte [operador](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="05aec-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](right-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="05aec-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05aec-110">Example</span></span>

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a><span data-ttu-id="05aec-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05aec-111">See also</span></span>

- [<span data-ttu-id="05aec-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="05aec-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="05aec-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="05aec-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="05aec-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="05aec-114">C# operators</span></span>](index.md)