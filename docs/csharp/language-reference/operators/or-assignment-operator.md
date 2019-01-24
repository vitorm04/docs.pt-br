---
title: Operador |= – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: f4f7806c8679af400a371decd0c367929b3fb81d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333259"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f5661-102">Operador |= (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="f5661-102">|= operator (C# Reference)</span></span>

<span data-ttu-id="f5661-103">O operador de atribuição OR.</span><span class="sxs-lookup"><span data-stu-id="f5661-103">The OR assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5661-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5661-104">Remarks</span></span>

<span data-ttu-id="f5661-105">Uma expressão que usa o operador de atribuição `|=`, como</span><span class="sxs-lookup"><span data-stu-id="f5661-105">An expression using the `|=` assignment operator, such as</span></span>

```csharp
x |= y
```

<span data-ttu-id="f5661-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="f5661-106">is equivalent to</span></span>

```csharp
x = x | y
```

<span data-ttu-id="f5661-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="f5661-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f5661-108">O [operador &#124;](or-operator.md) executa uma operação OR lógica bit a bit em operandos integrais e OR lógica em operandos bool.</span><span class="sxs-lookup"><span data-stu-id="f5661-108">The [&#124; operator](or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>

<span data-ttu-id="f5661-109">O operador `|=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador &#124;](or-operator.md) (consulte [operador](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f5661-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](or-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="f5661-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5661-110">Example</span></span>

[!code-csharp[csRefOperators#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#10)]

## <a name="see-also"></a><span data-ttu-id="f5661-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5661-111">See also</span></span>

- [<span data-ttu-id="f5661-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f5661-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f5661-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f5661-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f5661-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="f5661-114">C# operators</span></span>](index.md)