---
title: '>>Operador = – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 8cc341c14ee1b90fde2abb369c187e57b4ce5c00
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278974"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="46ac4-102">Operador >>= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="46ac4-102">>>= operator (C# Reference)</span></span>

<span data-ttu-id="46ac4-103">O operador de atribuição de deslocamento para a direita.</span><span class="sxs-lookup"><span data-stu-id="46ac4-103">The right-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="46ac4-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="46ac4-104">Remarks</span></span>

<span data-ttu-id="46ac4-105">Uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="46ac4-105">An expression of the form</span></span>

```csharp
x >>= y
```

<span data-ttu-id="46ac4-106">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="46ac4-106">is evaluated as</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="46ac4-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="46ac4-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="46ac4-108">O [operador >>](right-shift-operator.md) desloca `x` para a direita em um valor especificado pelo `y`.</span><span class="sxs-lookup"><span data-stu-id="46ac4-108">The [>> operator](right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>

<span data-ttu-id="46ac4-109">O operador >>= não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador >>](right-shift-operator.md) (consulte [operador](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="46ac4-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](right-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="46ac4-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="46ac4-110">Example</span></span>

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a><span data-ttu-id="46ac4-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46ac4-111">See also</span></span>

- [<span data-ttu-id="46ac4-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="46ac4-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="46ac4-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="46ac4-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="46ac4-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="46ac4-114">C# operators</span></span>](index.md)