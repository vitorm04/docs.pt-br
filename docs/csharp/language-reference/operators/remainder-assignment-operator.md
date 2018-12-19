---
title: Operador %= – Referência de C#
ms.custom: seodec18
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: d0732f9578b64c894ecc1d3bb15cee11a8d5b6a3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245555"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2283a-102">Operador %= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="2283a-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="2283a-103">Operador de atribuição restante.</span><span class="sxs-lookup"><span data-stu-id="2283a-103">The remainder assignment operator.</span></span>

<span data-ttu-id="2283a-104">Uma expressão que usa o operador `%=`, como</span><span class="sxs-lookup"><span data-stu-id="2283a-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="2283a-105">equivale a</span><span class="sxs-lookup"><span data-stu-id="2283a-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="2283a-106">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="2283a-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="2283a-107">O [operador remainder](remainder-operator.md) `%` calcula o restante após a divisão de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="2283a-107">The [remainder operator](remainder-operator.md) `%` computes the remainder after division of its operands.</span></span> <span data-ttu-id="2283a-108">Ele é compatível com todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="2283a-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="2283a-109">Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de resto](remainder-operator.md) `%`, o operador de atribuição de resto `%=` ficará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="2283a-109">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="2283a-110">O exemplo a seguir demonstra o uso do operador `%=`:</span><span class="sxs-lookup"><span data-stu-id="2283a-110">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="2283a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2283a-111">See also</span></span>

- [<span data-ttu-id="2283a-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="2283a-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2283a-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2283a-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2283a-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="2283a-114">C# Operators</span></span>](index.md)
