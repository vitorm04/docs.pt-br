---
title: Operador ^= – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: 12189d6469a9716d3b7ebcffef23423a75692d1a
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333545"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="45b61-102">Operador ^= (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="45b61-102">^= operator (C# Reference)</span></span>

<span data-ttu-id="45b61-103">O operador de atribuição OR exclusivo.</span><span class="sxs-lookup"><span data-stu-id="45b61-103">The exclusive-OR assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="45b61-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="45b61-104">Remarks</span></span>

<span data-ttu-id="45b61-105">Uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="45b61-105">An expression of the form</span></span>

```csharp
x ^= y
```

<span data-ttu-id="45b61-106">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="45b61-106">is evaluated as</span></span>

```csharp
x = x ^ y
```

<span data-ttu-id="45b61-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="45b61-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="45b61-108">O [operador ^](xor-operator.md) realiza uma operação OR exclusiva bit a bit em operandos integrais e OR exclusiva lógica em operandos [bool](../keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="45b61-108">The [^ operator](xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="45b61-109">O operador ^= não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador ^](xor-operator.md) (consulte [operador](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="45b61-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](xor-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="45b61-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45b61-110">Example</span></span>

[!code-csharp[csRefOperators#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#23)]

## <a name="see-also"></a><span data-ttu-id="45b61-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45b61-111">See also</span></span>

- [<span data-ttu-id="45b61-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="45b61-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="45b61-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="45b61-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="45b61-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="45b61-114">C# operators</span></span>](index.md)