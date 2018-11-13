---
title: Operador += (Referência de C#)
ms.date: 10/29/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ac9330e283cb58ae4e0ee7b644aa2c22bdf64c46
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50192025"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8024b-102">Operador += (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8024b-102">+= Operator (C# Reference)</span></span>

<span data-ttu-id="8024b-103">Operador de atribuição de adição.</span><span class="sxs-lookup"><span data-stu-id="8024b-103">The addition assignment operator.</span></span>

<span data-ttu-id="8024b-104">Uma expressão que usa o operador `+=`, como</span><span class="sxs-lookup"><span data-stu-id="8024b-104">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="8024b-105">equivale a</span><span class="sxs-lookup"><span data-stu-id="8024b-105">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="8024b-106">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="8024b-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="8024b-107">Para tipos numéricos, o [operador de adição](addition-operator.md) `+` calcula a soma dos operandos.</span><span class="sxs-lookup"><span data-stu-id="8024b-107">For numeric types, the [addition operator](addition-operator.md) `+` computes the sum of its operands.</span></span> <span data-ttu-id="8024b-108">Se um ou ambos os operandos for do tipo [cadeia de caracteres](../keywords/string.md), ele concatenará as representações de cadeia de caracteres de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="8024b-108">If one or both operands is of type [string](../keywords/string.md), it concatenates the string representations of its operands.</span></span> <span data-ttu-id="8024b-109">Para tipos de delegado, o operador `+` retorna uma nova instância de delegado que é a combinação de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="8024b-109">For delegate types, the `+` operator returns a new delegate instance that is combination of its operands.</span></span>

<span data-ttu-id="8024b-110">Você também usará o operador `+=` para especificar um método de manipulador de eventos ao assinar um [evento](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="8024b-110">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="8024b-111">Para obter mais informações, consulte [Como Realizar e Cancelar a Assinatura de Eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="8024b-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

<span data-ttu-id="8024b-112">O exemplo a seguir demonstra o uso do operador `+=`:</span><span class="sxs-lookup"><span data-stu-id="8024b-112">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

## <a name="operator-overloadability"></a><span data-ttu-id="8024b-113">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="8024b-113">Operator overloadability</span></span>

<span data-ttu-id="8024b-114">Se um tipo definido pelo usuário [sobrecarregar](../keywords/operator.md) o [operador de adição](addition-operator.md) `+`, o operador de atribuição de adição`+=` ficará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="8024b-114">If a user-defined type [overloads](../keywords/operator.md) the [addition operator](addition-operator.md) `+`, the addition assignment operator `+=` is implicitly overloaded.</span></span> <span data-ttu-id="8024b-115">Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador de atribuição de adição.</span><span class="sxs-lookup"><span data-stu-id="8024b-115">A user-defined type cannot explicitly overload the addition assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8024b-116">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8024b-116">C# language specification</span></span>

<span data-ttu-id="8024b-117">Para obter mais informações, veja as seções [Atribuição composta](~/_csharplang/spec/expressions.md#compound-assignment) e [Atribuição de eventos](~/_csharplang/spec/expressions.md#event-assignment) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8024b-117">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) and [Event assignment](~/_csharplang/spec/expressions.md#event-assignment) sections of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8024b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8024b-118">See also</span></span>

- [<span data-ttu-id="8024b-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8024b-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8024b-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="8024b-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8024b-121">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="8024b-121">C# Operators</span></span>](index.md)
- [<span data-ttu-id="8024b-122">Eventos</span><span class="sxs-lookup"><span data-stu-id="8024b-122">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="8024b-123">Delegados</span><span class="sxs-lookup"><span data-stu-id="8024b-123">Delegates</span></span>](../../programming-guide/delegates/index.md)
