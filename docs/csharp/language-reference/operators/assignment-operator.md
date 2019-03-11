---
title: Operador = – Referência de C#
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 40dc844f2a4b6411ea82aa2f029b36d7dd8f6e5a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716303"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e199a-102">Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e199a-102">= Operator (C# Reference)</span></span>

<span data-ttu-id="e199a-103">O operador de atribuição `=` atribui o valor do operando do lado direito a uma variável, uma [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um elemento [indexador](../../../csharp/programming-guide/indexers/index.md) fornecido pelo operando do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="e199a-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../../csharp/programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="e199a-104">O resultado de uma expressão de atribuição é o valor atribuído a um operando do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="e199a-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="e199a-105">O tipo do operandos do lado direito deve ser do mesmo tipo ou implicitamente conversível para o operando do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="e199a-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="e199a-106">O operador de atribuição é associativo direito, ou seja, uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="e199a-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="e199a-107">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="e199a-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="e199a-108">O exemplo a seguir demonstra o uso do operador de atribuição para atribuir valores a uma variável local, uma propriedade e um elemento do indexador:</span><span class="sxs-lookup"><span data-stu-id="e199a-108">The following example demonstrates the usage of the assignment operator to assign values to a local variable, a property, and an indexer element:</span></span>

[!code-csharp-interactive[assignment operator](~/samples/snippets/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="e199a-109">Operador de atribuição ref</span><span class="sxs-lookup"><span data-stu-id="e199a-109">ref assignment operator</span></span>

<span data-ttu-id="e199a-110">Começando pelo C# 7.3, você pode usar o operador de atribuição ref `= ref` para reatribuir uma variável [ref local](../keywords/ref.md#ref-locals) ou [ref readonly local](../keywords/ref.md#ref-readonly-locals).</span><span class="sxs-lookup"><span data-stu-id="e199a-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="e199a-111">O exemplo a seguir demonstra o uso do operador de atribuição ref:</span><span class="sxs-lookup"><span data-stu-id="e199a-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/snippets/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

<span data-ttu-id="e199a-112">No caso do operador de atribuição ref, o tipo do operando esquerdo e do direito deve ser o mesmo.</span><span class="sxs-lookup"><span data-stu-id="e199a-112">In the case of the ref assignment operator, the type of the left operand and the right operand must be the same.</span></span>

<span data-ttu-id="e199a-113">Para saber mais, confira a [nota da proposta do recurso](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="e199a-113">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e199a-114">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="e199a-114">Operator overloadability</span></span>

<span data-ttu-id="e199a-115">Um tipo definido pelo usuário não pode sobrecarregar o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="e199a-115">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="e199a-116">No entanto, um tipo definido pelo usuário pode definir uma conversão implícita em outro tipo.</span><span class="sxs-lookup"><span data-stu-id="e199a-116">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="e199a-117">Dessa forma, o valor de um tipo definido pelo usuário pode ser atribuído a uma variável, uma propriedade ou um elemento do indexador de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="e199a-117">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="e199a-118">Para saber mais, confira o artigo de palavra-chave [implícito](../keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="e199a-118">For more information, see the [implicit](../keywords/implicit.md) keyword article.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e199a-119">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e199a-119">C# language specification</span></span>

<span data-ttu-id="e199a-120">Para saber mais, confira a seção [Atribuição simples](~/_csharplang/spec/expressions.md#simple-assignment) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e199a-120">For more information, see the [Simple assignment](~/_csharplang/spec/expressions.md#simple-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e199a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e199a-121">See also</span></span>

- [<span data-ttu-id="e199a-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e199a-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e199a-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e199a-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e199a-124">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e199a-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="e199a-125">ref keyword</span><span class="sxs-lookup"><span data-stu-id="e199a-125">ref keyword</span></span>](../keywords/ref.md)
