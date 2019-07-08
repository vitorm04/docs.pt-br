---
title: + Operadores e += – referência de C#
ms.custom: seodec18
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 41355dbadd566648b45d825cdd6515bfc6d411aa
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610031"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="8d230-102">Operadores + e += (referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8d230-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="8d230-103">O operador `+` é compatível com os tipos numéricos internos, o tipo [cadeia de caracteres](../keywords/string.md) e o tipo [delegado](../keywords/delegate.md).</span><span class="sxs-lookup"><span data-stu-id="8d230-103">The `+` operator is supported by the built-in numeric types, [string](../keywords/string.md) type, and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="8d230-104">Para obter informações sobre o operador `+` aritmético, consulte as seções [Operadores de adição e subtração unários](arithmetic-operators.md#unary-plus-and-minus-operators) e [Operador de adição +](arithmetic-operators.md#addition-operator-) do artigo [Operadores aritméticos](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="8d230-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="8d230-105">Concatenação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8d230-105">String concatenation</span></span>

<span data-ttu-id="8d230-106">Quando um ou os dois operandos forem do tipo [cadeia de caracteres](../keywords/string.md), o operador `+` concatenará as representações de cadeia de caracteres de seus operandos:</span><span class="sxs-lookup"><span data-stu-id="8d230-106">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="8d230-107">Começando com C# 6, [interpolação de cadeia de caracteres](../tokens/interpolated.md) oferece uma maneira mais conveniente de formatar cadeias de caracteres:</span><span class="sxs-lookup"><span data-stu-id="8d230-107">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="8d230-108">Combinação de delegados</span><span class="sxs-lookup"><span data-stu-id="8d230-108">Delegate combination</span></span>

<span data-ttu-id="8d230-109">Para operandos do mesmo tipo [delegado](../keywords/delegate.md), o operador `+` retorna uma nova instância de delegado que, quando invocada, chama o operando esquerdo e, em seguida, chama o operando direito.</span><span class="sxs-lookup"><span data-stu-id="8d230-109">For operands of the same [delegate](../keywords/delegate.md) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="8d230-110">Se qualquer um dos operandos for `null`, o operador `+` retornará o valor de outro operando (que também pode ser `null`).</span><span class="sxs-lookup"><span data-stu-id="8d230-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="8d230-111">O exemplo a seguir mostra como os delegados podem ser combinados com o operador `+`:</span><span class="sxs-lookup"><span data-stu-id="8d230-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="8d230-112">Para executar a remoção de delegado, use o [operador `-`](subtraction-operator.md#delegate-removal).</span><span class="sxs-lookup"><span data-stu-id="8d230-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="8d230-113">Para obter mais informações sobre tipos de delegado, veja [Delegados](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d230-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="8d230-114">Operador de atribuição de adição +=</span><span class="sxs-lookup"><span data-stu-id="8d230-114">Addition assignment operator +=</span></span>

<span data-ttu-id="8d230-115">Uma expressão que usa o operador `+=`, como</span><span class="sxs-lookup"><span data-stu-id="8d230-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="8d230-116">equivale a</span><span class="sxs-lookup"><span data-stu-id="8d230-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="8d230-117">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="8d230-117">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="8d230-118">O exemplo a seguir demonstra o uso do operador `+=`:</span><span class="sxs-lookup"><span data-stu-id="8d230-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="8d230-119">Você também usará o operador `+=` para especificar um método de manipulador de eventos ao assinar um [evento](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="8d230-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="8d230-120">Para obter mais informações, confira [Como assinar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="8d230-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="8d230-121">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="8d230-121">Operator overloadability</span></span>

<span data-ttu-id="8d230-122">Um tipo definido pelo usuário pode [sobrecarregar](operator-overloading.md) o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="8d230-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="8d230-123">Quando um operador `+` binário é sobrecarregado, o operador `+=` também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="8d230-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="8d230-124">Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador `+=`.</span><span class="sxs-lookup"><span data-stu-id="8d230-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8d230-125">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8d230-125">C# language specification</span></span>

<span data-ttu-id="8d230-126">Para obter mais informações, veja as seções [Operador de adição unário](~/_csharplang/spec/expressions.md#unary-plus-operator) e [Operador de adição](~/_csharplang/spec/expressions.md#addition-operator) da [Especificação de linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8d230-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d230-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d230-127">See also</span></span>

- [<span data-ttu-id="8d230-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8d230-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8d230-129">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="8d230-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="8d230-130">Interpolação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8d230-130">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="8d230-131">Como concatenar várias cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="8d230-131">How to: concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="8d230-132">Delegados</span><span class="sxs-lookup"><span data-stu-id="8d230-132">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="8d230-133">Eventos</span><span class="sxs-lookup"><span data-stu-id="8d230-133">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="8d230-134">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="8d230-134">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="8d230-135">Operadores - e -=</span><span class="sxs-lookup"><span data-stu-id="8d230-135">- and -= operators</span></span>](subtraction-operator.md)
