---
title: Operador += (Referência de C#)
ms.date: 10/22/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ee335e3e2e7d352d4e26b802bad2b08a05c666ab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192025"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7fbe5-102">Operador += (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7fbe5-102">+= Operator (C# Reference)</span></span>

<span data-ttu-id="7fbe5-103">Operador de atribuição de adição.</span><span class="sxs-lookup"><span data-stu-id="7fbe5-103">The addition assignment operator.</span></span>

<span data-ttu-id="7fbe5-104">Uma expressão que usa o operador `+=`, como</span><span class="sxs-lookup"><span data-stu-id="7fbe5-104">An expression using the `+=` operator, such as</span></span>  

```csharp
x += y
```  

<span data-ttu-id="7fbe5-105">equivale a</span><span class="sxs-lookup"><span data-stu-id="7fbe5-105">is equivalent to</span></span>  

```csharp
x = x + y
```  

<span data-ttu-id="7fbe5-106">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="7fbe5-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="7fbe5-107">Para tipos numéricos, o [operador de adição](addition-operator.md) `+` calcula a soma dos operandos.</span><span class="sxs-lookup"><span data-stu-id="7fbe5-107">For numeric types, the [addition operator](addition-operator.md) `+` computes the sum of its operands.</span></span> <span data-ttu-id="7fbe5-108">Se um ou ambos os operandos for do tipo [cadeia de caracteres](../keywords/string.md), ele concatenará as representações de cadeia de caracteres de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="7fbe5-108">If one or both operands is of type [string](../keywords/string.md), it concatenates the string representations of its operands.</span></span> <span data-ttu-id="7fbe5-109">Para tipos de delegado, o operador `+` retorna uma nova instância de delegado que é a combinação de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="7fbe5-109">For delegate types, the `+` operator returns a new delegate instance that is combination of its operands.</span></span>

<span data-ttu-id="7fbe5-110">Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de adição](addition-operator.md) `+`, o operador de atribuição de adição`+=` ficará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="7fbe5-110">If a user-defined type [overloads](../keywords/operator.md) the [addition operator](addition-operator.md) `+`, the addition assignment operator `+=` is implicitly overloaded.</span></span>

<span data-ttu-id="7fbe5-111">Você também usará o operador `+=` para especificar um método de manipulador de eventos ao assinar um [evento](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="7fbe5-111">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="7fbe5-112">Para obter mais informações, consulte [Como Realizar e Cancelar a Assinatura de Eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="7fbe5-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

<span data-ttu-id="7fbe5-113">O exemplo a seguir demonstra o uso do operador `+=`:</span><span class="sxs-lookup"><span data-stu-id="7fbe5-113">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]
  
## <a name="see-also"></a><span data-ttu-id="7fbe5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fbe5-114">See also</span></span>

- [<span data-ttu-id="7fbe5-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7fbe5-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7fbe5-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7fbe5-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7fbe5-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="7fbe5-117">C# Operators</span></span>](index.md)
- [<span data-ttu-id="7fbe5-118">Eventos</span><span class="sxs-lookup"><span data-stu-id="7fbe5-118">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="7fbe5-119">Delegados</span><span class="sxs-lookup"><span data-stu-id="7fbe5-119">Delegates</span></span>](../../programming-guide/delegates/index.md)
