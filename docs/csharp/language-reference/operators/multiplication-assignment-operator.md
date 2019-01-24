---
title: Operador *= – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 2038f3b55d46f3503496275b3d25b17663b8c1db
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333428"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="84bf1-102">\*Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="84bf1-102">\*= Operator (C# Reference)</span></span>

<span data-ttu-id="84bf1-103">O operador de atribuição de multiplicação binária.</span><span class="sxs-lookup"><span data-stu-id="84bf1-103">The binary multiplication assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="84bf1-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="84bf1-104">Remarks</span></span>

<span data-ttu-id="84bf1-105">Uma expressão que usa o operador de atribuição `*=`, como</span><span class="sxs-lookup"><span data-stu-id="84bf1-105">An expression using the `*=` assignment operator, such as</span></span>

```csharp
x *= y
```

<span data-ttu-id="84bf1-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="84bf1-106">is equivalent to</span></span>

```csharp
x = x * y
```

<span data-ttu-id="84bf1-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="84bf1-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="84bf1-108">O [operador\*](multiplication-operator.md) é predefinido para que os tipos numéricos executem multiplicação.</span><span class="sxs-lookup"><span data-stu-id="84bf1-108">The [\* operator](multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>

<span data-ttu-id="84bf1-109">O operador `*=` não pode ser sobrecarregado diretamente, mas os tipos definidos pelo usuário podem sobrecarregar o [operador \*](multiplication-operator.md) (confira [operator](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="84bf1-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [\* operator](multiplication-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="84bf1-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84bf1-110">Example</span></span>

[!code-csharp[csRefOperators#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#13)]

## <a name="see-also"></a><span data-ttu-id="84bf1-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84bf1-111">See also</span></span>

- [<span data-ttu-id="84bf1-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="84bf1-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="84bf1-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="84bf1-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="84bf1-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="84bf1-114">C# Operators</span></span>](index.md)
