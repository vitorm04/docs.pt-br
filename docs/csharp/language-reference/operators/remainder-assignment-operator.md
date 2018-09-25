---
title: Operador %= (Referência de C#)
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: c475517666bdadaa457dbb4188808b3a96fcdf0e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085630"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e14da-102">Operador %= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e14da-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="e14da-103">Operador de atribuição restante.</span><span class="sxs-lookup"><span data-stu-id="e14da-103">The remainder assignment operator.</span></span>

<span data-ttu-id="e14da-104">Uma expressão que usa o operador `%=`, como</span><span class="sxs-lookup"><span data-stu-id="e14da-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="e14da-105">equivale a</span><span class="sxs-lookup"><span data-stu-id="e14da-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="e14da-106">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="e14da-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="e14da-107">O [operador de resto](remainder-operator.md) `%` é compatível com todos os tipos numéricos e calcula o resto após a divisão de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="e14da-107">The [remainder operator](remainder-operator.md) `%` is supported by all numeric types and computes the remainder after division of its operands.</span></span>

<span data-ttu-id="e14da-108">Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de resto](remainder-operator.md) `%`, o operador de atribuição de resto `%=` ficará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="e14da-108">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="e14da-109">O exemplo a seguir demonstra o uso do operador `%=`:</span><span class="sxs-lookup"><span data-stu-id="e14da-109">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="e14da-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e14da-110">See also</span></span>

- [<span data-ttu-id="e14da-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e14da-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e14da-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e14da-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e14da-113">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e14da-113">C# Operators</span></span>](index.md)
