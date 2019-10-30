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
ms.openlocfilehash: 709994632d704c6a9c6c7f4fc7180ae08cb901d7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039088"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="87984-102">Operadores + e += (referência de C#)</span><span class="sxs-lookup"><span data-stu-id="87984-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="87984-103">Os operadores de `+` e `+=` têm suporte dos tipos numéricos de [ponto flutuante](../builtin-types/floating-point-numeric-types.md) e [integral](../builtin-types/integral-numeric-types.md) internos, o tipo de [cadeia de caracteres](../builtin-types/reference-types.md#the-string-type) e os tipos [delegados](../builtin-types/reference-types.md#the-delegate-type) .</span><span class="sxs-lookup"><span data-stu-id="87984-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="87984-104">Para obter informações sobre o operador `+` aritmético, consulte as seções [Operadores de adição e subtração unários](arithmetic-operators.md#unary-plus-and-minus-operators) e [Operador de adição +](arithmetic-operators.md#addition-operator-) do artigo [Operadores aritméticos](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="87984-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="87984-105">Concatenação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="87984-105">String concatenation</span></span>

<span data-ttu-id="87984-106">Quando um ou os dois operandos forem do tipo [cadeia de caracteres](../builtin-types/reference-types.md#the-string-type), o operador `+` concatenará as representações de cadeia de caracteres de seus operandos:</span><span class="sxs-lookup"><span data-stu-id="87984-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="87984-107">A partir C# do 6, a [interpolação de cadeia de caracteres](../tokens/interpolated.md) fornece uma maneira mais conveniente de Formatar cadeias:</span><span class="sxs-lookup"><span data-stu-id="87984-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="87984-108">Combinação de delegados</span><span class="sxs-lookup"><span data-stu-id="87984-108">Delegate combination</span></span>

<span data-ttu-id="87984-109">Para operandos do mesmo tipo [delegado](../builtin-types/reference-types.md#the-delegate-type), o operador `+` retorna uma nova instância de delegado que, quando invocada, chama o operando esquerdo e, em seguida, chama o operando direito.</span><span class="sxs-lookup"><span data-stu-id="87984-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="87984-110">Se qualquer um dos operandos for `null`, o operador `+` retornará o valor de outro operando (que também pode ser `null`).</span><span class="sxs-lookup"><span data-stu-id="87984-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="87984-111">O exemplo a seguir mostra como os delegados podem ser combinados com o operador `+`:</span><span class="sxs-lookup"><span data-stu-id="87984-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="87984-112">Para executar a remoção de delegado, use o [operador `-`](subtraction-operator.md#delegate-removal).</span><span class="sxs-lookup"><span data-stu-id="87984-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="87984-113">Para obter mais informações sobre tipos de delegado, veja [Delegados](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="87984-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="87984-114">Operador de atribuição de adição +=</span><span class="sxs-lookup"><span data-stu-id="87984-114">Addition assignment operator +=</span></span>

<span data-ttu-id="87984-115">Uma expressão que usa o operador `+=`, como</span><span class="sxs-lookup"><span data-stu-id="87984-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="87984-116">equivale a</span><span class="sxs-lookup"><span data-stu-id="87984-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="87984-117">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="87984-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="87984-118">O exemplo a seguir demonstra o uso do operador `+=`:</span><span class="sxs-lookup"><span data-stu-id="87984-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="87984-119">Você também usará o operador `+=` para especificar um método de manipulador de eventos ao assinar um [evento](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="87984-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="87984-120">Para obter mais informações, confira [Como assinar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="87984-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="87984-121">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="87984-121">Operator overloadability</span></span>

<span data-ttu-id="87984-122">Um tipo definido pelo usuário pode [sobrecarregar](operator-overloading.md) o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="87984-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="87984-123">Quando um operador `+` binário é sobrecarregado, o operador `+=` também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="87984-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="87984-124">Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador `+=`.</span><span class="sxs-lookup"><span data-stu-id="87984-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="87984-125">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="87984-125">C# language specification</span></span>

<span data-ttu-id="87984-126">Para obter mais informações, veja as seções [Operador de adição unário](~/_csharplang/spec/expressions.md#unary-plus-operator) e [Operador de adição](~/_csharplang/spec/expressions.md#addition-operator) da [Especificação de linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="87984-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87984-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87984-127">See also</span></span>

- [<span data-ttu-id="87984-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="87984-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="87984-129">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="87984-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="87984-130">Como concatenar várias cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="87984-130">How to: concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="87984-131">Eventos</span><span class="sxs-lookup"><span data-stu-id="87984-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="87984-132">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="87984-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="87984-133">Operadores - e -=</span><span class="sxs-lookup"><span data-stu-id="87984-133">- and -= operators</span></span>](subtraction-operator.md)
