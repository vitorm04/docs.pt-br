---
title: Operador %= (Referência de C#)
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: ab3a6a8d5cbfeb4d527ca1f9c233ddfaba3d35ff
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188710"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="64013-102">Operador %= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="64013-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="64013-103">Operador de atribuição restante.</span><span class="sxs-lookup"><span data-stu-id="64013-103">The remainder assignment operator.</span></span>

<span data-ttu-id="64013-104">Uma expressão que usa o operador `%=`, como</span><span class="sxs-lookup"><span data-stu-id="64013-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="64013-105">equivale a</span><span class="sxs-lookup"><span data-stu-id="64013-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="64013-106">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="64013-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="64013-107">O [operador remainder](remainder-operator.md) `%` calcula o restante após a divisão de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="64013-107">The [remainder operator](remainder-operator.md) `%` computes the remainder after division of its operands.</span></span> <span data-ttu-id="64013-108">Ele é compatível com todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="64013-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="64013-109">Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de resto](remainder-operator.md) `%`, o operador de atribuição de resto `%=` ficará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="64013-109">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="64013-110">O exemplo a seguir demonstra o uso do operador `%=`:</span><span class="sxs-lookup"><span data-stu-id="64013-110">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="64013-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64013-111">See also</span></span>

- [<span data-ttu-id="64013-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="64013-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="64013-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="64013-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="64013-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="64013-114">C# Operators</span></span>](index.md)
