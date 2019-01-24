---
title: Operador &lt;&lt;= – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 4513c4b78dea3e8102c72a43249b4a44ffa2421d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333246"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="e82aa-102">Operador &lt;&lt;= (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="e82aa-102">&lt;&lt;= operator (C# Reference)</span></span>

<span data-ttu-id="e82aa-103">O operador de atribuição de deslocamento para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="e82aa-103">The left-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="e82aa-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="e82aa-104">Remarks</span></span>

<span data-ttu-id="e82aa-105">Uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="e82aa-105">An expression of the form</span></span>

```csharp
x <<= y
```

<span data-ttu-id="e82aa-106">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="e82aa-106">is evaluated as</span></span>

```csharp
x = x << y
```

<span data-ttu-id="e82aa-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="e82aa-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="e82aa-108">O [operador <<](left-shift-operator.md) desloca `x` para a esquerda pelo número de bits especificado pelo `y`.</span><span class="sxs-lookup"><span data-stu-id="e82aa-108">The [<< operator](left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>

<span data-ttu-id="e82aa-109">O operador `<<=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador <<](left-shift-operator.md) (consulte [operador](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="e82aa-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](left-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="e82aa-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e82aa-110">Example</span></span>

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a><span data-ttu-id="e82aa-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e82aa-111">See also</span></span>

- [<span data-ttu-id="e82aa-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e82aa-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e82aa-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e82aa-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e82aa-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e82aa-114">C# Operators</span></span>](index.md)
