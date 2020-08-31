---
description: Operadores de atribuição-referência C#
title: Operadores de atribuição-referência C#
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 3df118143b692cc8655de31cce23af41f7da125c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117877"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="ca84a-103">Operadores de atribuição (referência C#)</span><span class="sxs-lookup"><span data-stu-id="ca84a-103">Assignment operators (C# reference)</span></span>

<span data-ttu-id="ca84a-104">O operador de atribuição `=` atribui o valor do operando do lado direito a uma variável, uma [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um elemento [indexador](../../programming-guide/indexers/index.md) fornecido pelo operando do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="ca84a-104">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="ca84a-105">O resultado de uma expressão de atribuição é o valor atribuído a um operando do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="ca84a-105">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="ca84a-106">O tipo do operandos do lado direito deve ser do mesmo tipo ou implicitamente conversível para o operando do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="ca84a-106">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="ca84a-107">O operador de atribuição `=` é associativo à direita, ou seja, uma expressão do formulário</span><span class="sxs-lookup"><span data-stu-id="ca84a-107">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="ca84a-108">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="ca84a-108">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="ca84a-109">O exemplo a seguir demonstra o uso do operador de atribuição com uma variável local, uma propriedade e um elemento do indexador como seu operando esquerdo:</span><span class="sxs-lookup"><span data-stu-id="ca84a-109">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="ca84a-110">Operador de atribuição ref</span><span class="sxs-lookup"><span data-stu-id="ca84a-110">ref assignment operator</span></span>

<span data-ttu-id="ca84a-111">Começando pelo C# 7.3, você pode usar o operador de atribuição ref `= ref` para reatribuir uma variável [ref local](../keywords/ref.md#ref-locals) ou [ref readonly local](../keywords/ref.md#ref-readonly-locals).</span><span class="sxs-lookup"><span data-stu-id="ca84a-111">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="ca84a-112">O exemplo a seguir demonstra o uso do operador de atribuição ref:</span><span class="sxs-lookup"><span data-stu-id="ca84a-112">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="ca84a-113">No caso do operador de atribuição de referência, os dois operandos devem ser do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="ca84a-113">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="ca84a-114">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="ca84a-114">Compound assignment</span></span>

<span data-ttu-id="ca84a-115">Para um operador binário `op`, uma expressão de atribuição composta do formato</span><span class="sxs-lookup"><span data-stu-id="ca84a-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="ca84a-116">é equivalente a</span><span class="sxs-lookup"><span data-stu-id="ca84a-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="ca84a-117">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="ca84a-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="ca84a-118">A atribuição composta é tem suporte dos operadores [aritmético](arithmetic-operators.md#compound-assignment), [lógico booliano](boolean-logical-operators.md#compound-assignment) e [bit a bit lógico e shift](bitwise-and-shift-operators.md#compound-assignment).</span><span class="sxs-lookup"><span data-stu-id="ca84a-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="ca84a-119">Atribuição de União nula</span><span class="sxs-lookup"><span data-stu-id="ca84a-119">Null-coalescing assignment</span></span>

<span data-ttu-id="ca84a-120">A partir do C# 8,0, você pode usar o operador de atribuição de União nula `??=` para atribuir o valor de seu operando à direita para seu operando à esquerda somente se o operando à esquerda for avaliado como `null` .</span><span class="sxs-lookup"><span data-stu-id="ca84a-120">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="ca84a-121">Para obter mais informações, consulte [?? e?? =](null-coalescing-operator.md) artigo de operadores.</span><span class="sxs-lookup"><span data-stu-id="ca84a-121">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ca84a-122">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="ca84a-122">Operator overloadability</span></span>

<span data-ttu-id="ca84a-123">Um tipo definido pelo usuário não pode [sobrecarregar](operator-overloading.md) o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="ca84a-123">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="ca84a-124">No entanto, um tipo definido pelo usuário pode definir uma conversão implícita em outro tipo.</span><span class="sxs-lookup"><span data-stu-id="ca84a-124">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="ca84a-125">Dessa forma, o valor de um tipo definido pelo usuário pode ser atribuído a uma variável, uma propriedade ou um elemento do indexador de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="ca84a-125">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="ca84a-126">Para saber mais, confira [Operadores de conversão definidos pelo usuário](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ca84a-126">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="ca84a-127">Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="ca84a-127">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="ca84a-128">No entanto, se um tipo definido pelo usuário sobrecarregar um operador binário `op` , o `op=` operador, se existir, também será sobrecarregado implicitamente.</span><span class="sxs-lookup"><span data-stu-id="ca84a-128">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ca84a-129">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ca84a-129">C# language specification</span></span>

<span data-ttu-id="ca84a-130">Saiba mais na seção [Operadores de atribuição](~/_csharplang/spec/expressions.md#assignment-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ca84a-130">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="ca84a-131">Para obter mais informações sobre o operador de atribuição de referência `= ref` , consulte a [Nota de proposta de recurso](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="ca84a-131">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca84a-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="ca84a-132">See also</span></span>

- [<span data-ttu-id="ca84a-133">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ca84a-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ca84a-134">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="ca84a-134">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="ca84a-135">ref keyword</span><span class="sxs-lookup"><span data-stu-id="ca84a-135">ref keyword</span></span>](../keywords/ref.md)
