---
title: Operador = – Referência de C#
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: ef9c9bab5c1cebb06edf934254507180e2197349
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306564"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="baaea-102">Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="baaea-102">= operator (C# reference)</span></span>

<span data-ttu-id="baaea-103">O operador de atribuição `=` atribui o valor do operando do lado direito a uma variável, uma [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um elemento [indexador](../../../csharp/programming-guide/indexers/index.md) fornecido pelo operando do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="baaea-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../../csharp/programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="baaea-104">O resultado de uma expressão de atribuição é o valor atribuído a um operando do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="baaea-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="baaea-105">O tipo do operandos do lado direito deve ser do mesmo tipo ou implicitamente conversível para o operando do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="baaea-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="baaea-106">O operador de atribuição é associativo direito, ou seja, uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="baaea-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="baaea-107">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="baaea-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="baaea-108">O exemplo a seguir demonstra o uso do operador de atribuição com uma variável local, uma propriedade e um elemento do indexador como seu operando esquerdo:</span><span class="sxs-lookup"><span data-stu-id="baaea-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="baaea-109">Operador de atribuição ref</span><span class="sxs-lookup"><span data-stu-id="baaea-109">ref assignment operator</span></span>

<span data-ttu-id="baaea-110">Começando pelo C# 7.3, você pode usar o operador de atribuição ref `= ref` para reatribuir uma variável [ref local](../keywords/ref.md#ref-locals) ou [ref readonly local](../keywords/ref.md#ref-readonly-locals).</span><span class="sxs-lookup"><span data-stu-id="baaea-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="baaea-111">O exemplo a seguir demonstra o uso do operador de atribuição ref:</span><span class="sxs-lookup"><span data-stu-id="baaea-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="baaea-112">No caso do operador de atribuição ref, o tipo dos seus operandos deve ser o mesmo.</span><span class="sxs-lookup"><span data-stu-id="baaea-112">In the case of the ref assignment operator, the type of both its operands must be the same.</span></span>

<span data-ttu-id="baaea-113">Para saber mais, confira a [nota da proposta do recurso](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="baaea-113">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="baaea-114">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="baaea-114">Compound assignment</span></span>

<span data-ttu-id="baaea-115">Para um operador binário `op`, uma expressão de atribuição composta do formato</span><span class="sxs-lookup"><span data-stu-id="baaea-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="baaea-116">equivale a</span><span class="sxs-lookup"><span data-stu-id="baaea-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="baaea-117">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="baaea-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="baaea-118">A atribuição composta é tem suporte dos operadores [aritmético](arithmetic-operators.md#compound-assignment), [lógico booliano](boolean-logical-operators.md#compound-assignment) e [bit a bit lógico e shift](bitwise-and-shift-operators.md#compound-assignment).</span><span class="sxs-lookup"><span data-stu-id="baaea-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="baaea-119">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="baaea-119">Operator overloadability</span></span>

<span data-ttu-id="baaea-120">Um tipo definido pelo usuário não pode sobrecarregar o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="baaea-120">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="baaea-121">No entanto, um tipo definido pelo usuário pode definir uma conversão implícita em outro tipo.</span><span class="sxs-lookup"><span data-stu-id="baaea-121">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="baaea-122">Dessa forma, o valor de um tipo definido pelo usuário pode ser atribuído a uma variável, uma propriedade ou um elemento do indexador de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="baaea-122">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="baaea-123">Para saber mais, confira o artigo de palavra-chave [implícito](../keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="baaea-123">For more information, see the [implicit](../keywords/implicit.md) keyword article.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="baaea-124">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="baaea-124">C# language specification</span></span>

<span data-ttu-id="baaea-125">Saiba mais na seção [Operadores de atribuição](~/_csharplang/spec/expressions.md#assignment-operators) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="baaea-125">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="baaea-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baaea-126">See also</span></span>

- [<span data-ttu-id="baaea-127">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="baaea-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="baaea-128">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="baaea-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="baaea-129">ref keyword</span><span class="sxs-lookup"><span data-stu-id="baaea-129">ref keyword</span></span>](../keywords/ref.md)
